# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
# Server Side:
```

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
   while(i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
       print(ack)
       i+=s
```
# Client Side:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())

```
## OUPUT:
# Server Side:
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/6fe33e9e-7a4b-4497-915b-40cf2b73ae32" />

# Client Side:
<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/1530250d-e8e4-455d-b21b-3fd4419b8ad9" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
