---
title: "Use VNC to control a Ubuntu Desktop from a windows Desktop"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Ranger1230 on 2008-12-04
Ok as the title says I'm trying to control my ubuntu desktop remotely from my windows desktop on the same lan. I mostly want to do this because my ubuntu desktop is a vga out put and my monitors are dvi input. my windows desktop has all sorts of things that only work on windows so I don't want to change it to ubuntu. I tried starting the server by typing into the terminal vncserver and I entered a password and it seemed fine. but when I try to access it from windows it says that my ubuntu computer doesn't exist. I installed vnc through the package manger and I tried this with both tight and ultra vnc on my desktop. what am I doing wrong? and when I get it working can I make ubuntu load the vnc server on boot?

---

### Post by s3rgio on 2008-12-04
Hello

Have you tried system->preferences->remote desktop ?

After that you can use a vnc client to access the Ubuntu desktop from windows.

Bye,
Sérgio

---

### Post by Ranger1230 on 2008-12-04
Yea I tried that. same result

---

### Post by Ranger1230 on 2008-12-04
I have tried using the remote desktop and tight vnc but with ether one windows says it failed to connect to server

---

### Post by superprash2003 on 2008-12-05
are the two pcs able to ping each other??[http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)

---

### Post by Ranger1230 on 2008-12-06
well the windows computer can ping my ubuntu comp no prob but ubuntu fails to ping my windows comp. but ubuntu can connect to the windows comp through the network places.

---

### Post by jonobr on 2008-12-06
Here is what I would recommend.
Enable sharing as outlined by s3rgio in remote desktop on ubuntu.

Open a terminal window 
I hope you have tcpump on there (its a network monitoring tool, which I think is on by default.)

in the window enter
sudo tcpdump -v port 5900

(assuming the port vnc will use is 5900)

Go to the client and execute your VNC to your ubuntu machine.

If the terminal remains empty, you are not reaching the ubuntu machine and the packets are being stopped elsewhere.
You could also be monitoring the wrong port number (5900)

If you see a lot of packets (a lot of text) when you execute the client, the ubuntu machine needs to be looked at closer at it is receiving the packets

---

### Post by Ranger1230 on 2008-12-06
well I tried that and nothing happened. the terminal on ubuntu showed nothing happened. I looked closer at my computer and the remote desktop doesn't say vncveiwer it says vinagre would that make a difference?

---

### Post by s3rgio on 2008-12-06
Hello

Do you have any firewall working?

---

### Post by Ranger1230 on 2008-12-06
nope the router between them has no firewall built into it.

---

### Post by Ranger1230 on 2008-12-06
ok vnc doesn't seem to be working. is there a different program I can use that will work and is fool proof? also if there is a chance this might still work I can use ubuntu to remotely control my windows desktop. so windows just doesn't seem to know ubuntu is even there.

---

### Post by Ranger1230 on 2008-12-06
I got it to work for some reason when I say only allow local connections it blocks everything. thanks for your time and effort everyone.

---

### Post by superprash2003 on 2008-12-06
please mark thread as SOLVED

---

