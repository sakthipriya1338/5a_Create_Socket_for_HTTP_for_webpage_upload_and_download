# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
##PYTHON
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server_socket.bind(("127.0.0.1", 8080))
server_socket.listen(1)

print("Server running at http://127.0.0.1:8080")

conn, addr = server_socket.accept()
print("Connected by:", addr)
request = conn.recv(1024)
print(request.decode())

# Open HTML file
with open("index.html", "rb") as f:
    html_content = f.read()

# Send HTTP headers first
conn.send(b"HTTP/1.1 200 OK\r\n")
conn.send(b"Content-Type: text/html\r\n")
conn.send(b"\r\n")

# Send HTML content
conn.send(html_content)

conn.close()
server_socket.close()
```
##HTML
```<!DOCTYPE html>
<html>
<head>
    <title>Simple HTML Page</title>
</head>
<body>

<h1>Welcome to HTML</h1>
<p>This is a simple HTML file.</p>

<button onclick="showMessage()">Click Me</button>

<script>
function showMessage() {
    alert("Hello World!");
}
</script>

</body>
</html>
```

## OUTPUT
<img width="1870" height="1003" alt="image" src="https://github.com/user-attachments/assets/38f21c58-b6b6-4885-af95-962ec117e6da" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
