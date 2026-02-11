# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
##SERVER SIDE
```
import socket


server_socket = socket.socket()
server_socket.bind(('localhost', 12345))
server_socket.listen(5)

print("Server is waiting for connection...")

conn, addr = server_socket.accept()
print("Connected to client:", addr)

while True:
    frame = conn.recv(1024).decode()

    if frame == "exit":
        print("Transmission completed.")
        break

    print("Received frame:", frame)

    
    ack = "ACK"
    conn.send(ack.encode())
    print("ACK sent\n")

conn.close()
server_socket.close()
```
##CLIENT SIDE
```
import socket
import time


client_socket = socket.socket()
client_socket.connect(('localhost', 12345))

n = int(input("Enter number of frames to send: "))

for i in range(1, n + 1):
    frame = f"Frame {i}"
    print("Sending:", frame)
    client_socket.send(frame.encode())

    
    ack = client_socket.recv(1024).decode()
    print("Received:", ack)
    time.sleep(1)

client_socket.send("exit".encode())
client_socket.close()
```
## OUTPUT
SERVER SIDE
<img width="1266" height="671" alt="image" src="https://github.com/user-attachments/assets/509db0a1-4a46-4d89-835f-5c1acebe28c0" />

CLIENT SIDE
<img width="1342" height="589" alt="image" src="https://github.com/user-attachments/assets/3747e09a-6b9e-46de-91a0-a127bc47f0b3" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
