---
title: "Do I need to install vnc on windows server in order to remote login?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2009-01-15
Hi,

This is what I do

Applications->Remote Desktop Viewer

when I try to login

It prompt connection to host 192.168.aa.bb :5900 was closed.

Do I need to install vnc on windows server in order to remote login?

thanks

---

### Post by movingover on 2009-01-15
To establish a VNC connection between two machines, you need two things:

1) A VNC client on the computer you are connecting FROM
2) A VNC server on the computer you want to connect TO

Sounds like you want to connect from Ubuntu to a Windows machine. Ubuntu, as you noticed, already has the VNC client, but you need to install any VNC server on the Windows machine to make the connection.

One simple & free VNC server for Windows can be found in TightVNC:
[http://www.tightvnc.com/](http://www.tightvnc.com/)

Try installing that on the Windows machine, and make sure you have the firewall port open! If you still have trouble, ensure the VNC server on the Windows machine is running and that you can ping the IP address in question.

Hope this helps!

---

### Post by pdtpatrick on 2009-01-15
if you are on the same LAN line then just use rdesktop

sudo apt-get install rdesktop

to login to the machine

rdesktop -u <username> -n <computername> -f (this means fullscreen) <ipaddress>

or you can run:

man rdesktop  --- for more information.

---

### Post by pdtpatrick on 2009-01-15
Just make sure under system properties on your windows machine that you have remote desktop connection checked to allow the use of it. 

However if you want to remote in from outside your network then you will need to port forward and make sure you are using an SSH protocol to connect.This scenario you can use TightVNC as the user above mentioned.

---

### Post by ubantuwannabe on 2009-01-15
rdesktop -u <user_id> <ipaddress>

I encounter the following error

system could not log you on make sure your user name and domain are correct, then your password again. letters in passwords must be type using the correct case.

May I know how to resolve this issue?

thanks

---

