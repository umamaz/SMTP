Experience and Challenges 
Paragraph 1: Implementation & Protocol Logic

Implementing the raw TCP socket SMTP client provided valuable practical experience with application-layer network protocols. Manually constructing each SMTP 
command—including HELO, MAIL FROM, RCPT TO, DATA, and QUIT—helped clarify the strict sequence of state transitions required during an email transmission session.
By capturing and printing the response buffer after each transmission, I was able to observe how client-server protocol handshakes rely on explicit numeric status 
codes (such as 220 for server readiness, 250 for standard success, 354 for accepting data input, and 221 for closing the connection) to verify that both endpoints stay 
synchronized.

Paragraph 2: Challenges & Technical Solutions

The primary challenge during development was ensuring correct message formatting and handling environment-specific execution steps. Standard SMTP rules require every line
to be terminated with carriage return and line feed characters (\r\n) and encoded into UTF-8 bytes before socket transmission; missing these delimiters causes socket
operations to hang while waiting for an end-of-line signal. Additionally, navigating directory paths in PowerShell to locate mail_client.py and configuring a local loopback
SMTP debugging server on port 1025 were crucial setup steps to bypass commercial security restrictions like TLS encryption and SPF authentication, allowing the core socket 
logic to be tested directly.
