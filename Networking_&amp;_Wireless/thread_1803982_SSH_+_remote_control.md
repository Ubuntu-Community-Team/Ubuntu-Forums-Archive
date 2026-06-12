---
title: "SSH + remote control"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by metalnisse on 2011-07-14
Hi,
 
I'm relatively new to the ubuntu community. One of my many questions is: I've setup my Ubuntu 10.04 desktop version as a home fileserver. I've installed the openSSH server on the machine. I have no problem connecting to the server from another computer on the same LAN or from an "external" computer. I use a VNC client to remote controll my computer.
 
To the point: I can connect, and remotely control, my ubuntu server with a VNC program without connecting to the SSH server first. The whole point of installing the SSH server was to securely remotecontrol my ubuntu server. But if i can do this with or without the SSH conection - what is the point of having a SSH connection? 
 
As I've mentioned, and as you guys most certainly can read - I am new to the whole Ubuntu / SSH, I hope my questions isn't to dumb :)

---

### Post by mikewhatever on 2011-07-14
There are many ways to remotely control a computer. VNC is OK for a home network, when the computer you control is in another room of the same house (just disable UPNP on the router). On the other hand, ssh is more suitable to control servers half way across the world. As always, pick the tool that suites you best.

---

### Post by metalnisse on 2011-07-15
> **mikewhatever said:**
> There are many ways to remotely control a computer. VNC is OK for a home network, when the computer you control is in another room of the same house (just disable UPNP on the router). On the other hand, ssh is more suitable to control servers half way across the world. As always, pick the tool that suites you best.
 
 
Okey, thanks for your help.
 
I've done some research and found that use SSH Tunneling suits me best.

I've managed to setup the SSH server, and connect the external computer to the VNC Server by Using 127.0.0.1 (internal IP). The thing is, Can I still log in to the Ubuntu server by just putting in the server's external IP.

Is there a way to deny Computers That are Trying to Connect Directly to my computer (without logging in to the SSH server first)? I just want people (my self) to Be Able to remotely using SSH tunneling and VNC

---

### Post by idlemind324 on 2011-07-15
You will need to either:

- Disable UPNP on your router
- Disable the port forward for 5800/5900

---

### Post by metalnisse on 2011-07-15
> **idlemind324 said:**
> You will need to either:

- Disable UPNP on your router
- Disable the port forward for 5800/5900


Thanks, I'll try that.

I've read a Swedish toutourial (guess it's the same for the english ones :) ) There it says that I should run:

gksudo gedit /etc/hosts.deny

and add:

VINO-SERVER: ALL EXCEPT 127.0.0.1 : ALLOW 


Is it just to add that line to the bottom and than save?

---

### Post by metalnisse on 2011-07-18
> **idlemind324 said:**
> You will need to either:
 
- Disable UPNP on your router
- Disable the port forward for 5800/5900
 
 
You guys are freakin awsome, thanks alot for your help.
 
Tried to close port 5900, and now it works the way i want it - almost.
 
If I set up so you need a password to remotely control the Ubuntu PC, I can not remotely access it without turning into my admin password - locally on the ubuntu computer - there is not enough to enter the correct password on the computer I try to log on (eg Windows PC).

I add a picture of how it looks on the ubuntu computer when I try to connect via VNC. At the time for the screenshot, the SSH connection is up and running, so it is therefore just the VNC connection which puts up a fight. 
 
If I choose that one does not need a password to remotely control the computer - than it works without a hassle.

---

