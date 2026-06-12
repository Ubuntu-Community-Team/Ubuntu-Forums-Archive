---
title: "Two NICs, two FTPds, one computer - how can iproute make this work for me?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Thasp on 2009-01-19
Here is my present conondrum. 

I have two NICs in my present machine. eth0 is 10.10.10.2/255.255.255.0 with a gateway of 10.10.10.1. eth1 is 192.168.1.248/255.255.255.0 with a gateway of 192.168.1.1. Let's say eth0's gateway has a WAN IP of 1.1.1.1 and eth1's gateway has a WAN IP or 2.2.2.2.

I cannot run both at the same time. If I turn one interface off, I can get an ftpd to work on the other. However if both are up, it is as if the port is closed when I try to connect to the ftpd, which it isn't. I've read the instructions for setting up two instances of vsftpd, and tried it with pure-ftpd as well. 


I can set these daemons to bind to one particular interface, but I know there is some iproute stuff I need to do that I am not yet doing.

My goal is this - when someone connects to 1.1.1.1, they connect to the ftpd that is bound to eth0/10.10.10.2, with traffic flowing through 1.1.1.1/eth0. When someone connects to 2.2.2.2, they connect tot he ftpd that is bound to eth1/192.168.1.248 through eth1.

I want this to work as if I had separate machines on separate connections with separate ftpds - except I want it to be in one machine. I'd rather not have multiple machines running(even though I have more PIIs than I know what to do with) if I can get this done in one machine.

Thanks. :)

---

### Post by rev0lv3r on 2009-01-19
[http://ubuntuforums.org/showthread.php?t=388341](http://ubuntuforums.org/showthread.php?t=388341)

Maybe you can use the idea of specific ports...?

---

