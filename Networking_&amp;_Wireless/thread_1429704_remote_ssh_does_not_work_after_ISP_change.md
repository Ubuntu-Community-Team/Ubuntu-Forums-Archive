---
title: "remote ssh does not work after ISP change"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by Sonicgoo on 2010-03-14
I set up my father's PC with Ubuntu over Christmas, he is 65 and lives in Tennessee. I live in Somerville Massachusetts. 

I set up SSH so that I could log on for support and updates etc. He changed his ISP last week. I was happy that dad was able to set up the internet service on his own but Since the change I have not been able to log on. I Tried to call the ISP but they are closed for the weekend. I have found a list of ports that the ISP blocks none of them match the two ports that I'm trying to use. 

When I set up his machine I shut down port 22 and opened up a random number to increase the security of the SSH. I also set up keys but didn't restrict password logins.

I am no longer able to log in on the port that I had opened up.  I am using the new ip for his computer. When I try and log in on the port that I assigned I get the following: 

debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx.xx.xxx.xx [xx.xx.xxx.xx] port xxxx.
debug1: connect to address xx.xx.xxx.xx port xxxx: Connection timed out
ssh: connect to host xx.xx.xxx.xx port xxxx: Connection timed out

So I ran nmap and found that port 4567 was open at his IP when I try and log in using that port and I got the following:

OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xx.xx.xxx.xx [xx.xx.xxx.xx] port xxxx.
debug1: Connection established.
debug1: identity file /home/sonicgrass/.ssh/identity type -1
debug1: identity file /home/sonicgrass/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/sonicgrass/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/sonicgrass/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: ssh_exchange_identification: UNKNOWN 408 Request Timeout


debug1: ssh_exchange_identification: Server: 


debug1: ssh_exchange_identification: Content-Type: text/html


debug1: ssh_exchange_identification: Date: Sun, 08 Sep 2002 12:16:22 GMT


debug1: ssh_exchange_identification: Last-Modified: Sun, 08 Sep 2002 12:16:22 GMT


debug1: ssh_exchange_identification: Accept-Ranges: bytes


debug1: ssh_exchange_identification: Connection: close


debug1: ssh_exchange_identification: 


debug1: ssh_exchange_identification: <HTML>

debug1: ssh_exchange_identification: <HEAD><TITLE>408 Request Timeout</TITLE></HEAD>

debug1: ssh_exchange_identification: <BODY BGCOLOR="#cc9999" TEXT="#000000" LINK="#2020ff" VLINK="#4040cc">

debug1: ssh_exchange_identification: <H2>408 Request Timeout</H2>

debug1: ssh_exchange_identification: No request appeared within a reasonable time period.

debug1: ssh_exchange_identification: <HR>

debug1: ssh_exchange_identification: <ADDRESS><A HREF=""></A></ADDRESS>

debug1: ssh_exchange_identification: </BODY>

debug1: ssh_exchange_identification: </HTML>

I can't call the ISP until tomorrow. Help with this would be greatly appreciated so that I can continue to support my Pops ubuntu experience. 

Thanks

---

### Post by joberly on 2010-03-14
Did he keep the same router or is he using the new ISP issued one? If it's new, did you do the port forwarding again?

---

### Post by Sonicgoo on 2010-03-14
Good question there was no router earlier just a modem, and I imagine that has changed but I don't know for sure. I will check it out. 

Thanks for the quick reply

---

### Post by joberly on 2010-03-14
Just as a side note, if there is no router, either think of purchasing one for him or run a firewall with strict rules. No protection + opening up a remote connection directly facing the internet, is not a good solution. (Even if your SSH setup is "secure")

---

### Post by Sonicgoo on 2010-04-03
The port forwarding was the problem. 

Thanks

---

### Post by Iowan on 2010-04-04
I noticed that you edited the thread's first post title... 
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is "How-To" mark the thread [SOLVED].

---

