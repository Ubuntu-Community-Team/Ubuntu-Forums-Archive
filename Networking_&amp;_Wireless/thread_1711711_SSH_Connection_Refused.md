---
title: "SSH Connection Refused"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by nvdkgm on 2011-03-21
I know someone has probably asked this question before but I will again.
Why am I getting port 22 connection refused?

I have a Ubuntu desktop and laptop that has OpenSSH Client and Server installed. I want the desktop to be the host and have set the desktop local IP or network address to be static and set a port forwarding rule on the router that public IP to local static IP on port 22 to 22 for TCP and UDP. I figure port 22 is opened when needed and closed otherwise, I could be wrong. I do not know about firewall setting but when I checked "iptables --list" it shows all as Accept. Both computers ssh 127.0.0.1 fine with both client and server installed.

Both computers are on in the local network and I am trying to ssh from the laptop to the desktop.
What is the missing step?

---

### Post by conneco on 2011-03-21
You don't need port forwarding if your in the same LAN port forwaring is for going across the internet so say you were in one house and you want to ssh to a computer in another house using the Internet.

---

### Post by nvdkgm on 2011-03-21
Well thats the idea. But I want to be able to ssh into the desktop now while in the LAN before going out. I thought it was working already but I keep getting connection refused so I am wondering what I need to change to make it work now and for later when I am outside the LAN.

---

### Post by spiky001 on 2011-03-21
What are you putting in terminal?

---

### Post by nvdkgm on 2011-03-21
ssh [public ip]
I have also tried it with -X -l [user name]

---

### Post by spiky001 on 2011-03-21
have you used the local ip ```
ssh username@local ip
``` It might be worth installing GUFW to help set the firewall up

---

### Post by nvdkgm on 2011-03-21
Okay. I can connect to the computer which resolves the original question and I take it that is because I am in LAN and use the public IP when I am outside the network, right? (edited out. ssh -X forwards windows to open files which is also what I need in the command.)

And also you mentioned something about a firewall. How do I set up that to protect the connection?

---

### Post by spiky001 on 2011-03-21
Cant help you with the X part. I use GUFW it,s in the resportories it,s a graphical front for iptables

---

