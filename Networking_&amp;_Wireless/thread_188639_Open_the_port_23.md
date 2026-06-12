---
title: "Open the port 23"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by romaluca on 2006-06-04
I want do a connection client-server with protocol telnet that uses the port 23

But it's close.
How can i open localhost:23?
Thanks.

---

### Post by jgoguen on 2006-06-04
Did you enable the firewall?  By default there's no rules in place so anything can come in/out.

And did you install a telnet server or write a program that accepts connections on port 23?

---

### Post by romaluca on 2006-06-04
No i haven't a firewall but nmap tell me this:
Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-06-04 16:04 CEST
Interesting ports on localhost (127.0.0.1):
(The 1673 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.213 seconds

I use the port 23 for my java server.
Thanks

---

### Post by jgoguen on 2006-06-04
Is the Java server running when you're trying to connect?  I did that once :)  Also, were there any exceptions thrown when trying to bind to port 23?  Remember that since this port is below 1024 you need to run the server as root for it to bind properly.

---

