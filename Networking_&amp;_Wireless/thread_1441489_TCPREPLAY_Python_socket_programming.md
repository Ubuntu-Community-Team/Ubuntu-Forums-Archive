---
title: "TCPREPLAY Python socket programming"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by darkdrone on 2010-03-28
I'm running Ubuntu 9.10.  I have a pcap file that I'm replaying using TCPREPLAY.

sudo tcpreplay -i eth0 file.pcap

Everything works fine, packets are send, I can see them in wireshark, but my python code
will not detect it. I don't know what else I need to do. 

Python code: I'm using a very similar generic python code found in the web..
(with different port numbers)
---------------------------------python 2.6------------------------------
from socket import *

# Set the socket parameters
host = "localhost"
port = 21567
buf = 1024
addr = (host,port)

# Create socket and bind to address
UDPSock = socket(AF_INET,SOCK_DGRAM)
UDPSock.bind(addr)

# Receive messages
while 1:
	data,addr = UDPSock.recvfrom(buf)
	if not data:
		print "Client has exited!"
		break
	else:
		print "\nReceived message '", data,"'"

UDPSock.close()

----------------------------------------------------------------

Can anyone tell me what else I may be overlooking?
(source dest ips on the pcap file, hardware ids, etc)
Why does wireshark see the packets but not the python code?
Data is mainly udp.

---

### Post by bcramet on 2011-10-13
Hello, I have the same problem.
Did you find a solution?

Thx

B

---

