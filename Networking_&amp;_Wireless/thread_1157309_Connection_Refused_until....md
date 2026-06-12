---
title: "Connection Refused until..."
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by edwanji on 2009-05-12
I've searched the forums, and found several threads about sshd refusing connections, but none of them match my problem:
I have 2 Ubuntu machines. I'll call one Desktop, and one Server.  Desktop is running regular 8.10, and Server is running 8.10 Server.  They are sitting right next to each other.

Step 1: Boot up Server, and once it's booted, on Desktop, run $ ssh [email]serveruser@<server.ip[/email]>
The response is : ssh: connect to host <server.ip> port 22: Connection refused

Step 2: Log into Server's console, and run $ ssh [email]myuser@<desktop.ip[/email]>
I am able to log into my desktop. Exit out of the session

Step 3: Again, on the desktop, run $ ssh [email]serveruser@<server.ip[/email]>
Now it works!
However, once I reboot Server, it stops working again.

Any ideas what the problem is?  Logging into the console and ssh'ing out in order to get back in really isn't an option...

EDIT: I have also discovered that the web server on Sever also doesn't accept connections until I connect FROM Server to Desktop...

---

### Post by puppywhacker on 2009-05-12
sounds like a strange firewalling rule. whatever it is run
ssh -v user@ip to give you the full output of the client, and run sshd with the debugging options on the server. there should be solid information in those to work from

---

