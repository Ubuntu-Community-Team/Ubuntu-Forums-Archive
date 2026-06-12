---
title: "vnc for noob"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by wkuace on 2009-04-06
hey i'm pretty good at finding my way around a computer and i can usually figure out most any problem. But I cant for the life of me understand networking. My mom just got a mini 9 i'm trying to setup the remote desktop viewer to connect to vista desktop. but apparently i'm an idiot! I've got tightvnc server installed on the desktop but beyond that i'm clueless. Can anyone walkme though it in a way any idiot can understand.

---

### Post by gtr32 on 2009-04-06
Do you have vncviewer installed on the client? If not:

sudo apt-get install vncviewer

Then run:

vncviewer $ADDRESS_OF_REMOTE_MACHINE:$PORT

Let assume your Vista machine is at ip address 192.168.0.2, and VNC server was started at port 1 which would be 5901:

vncviewer 192.168.0.2:5901

Put this into a desktop shortcut and you should be good to go.

---

### Post by Velociraptor on 2009-04-07
I use "rdesktop" on Ubuntu to connect to a Windows XP machine. You have to enable Remote Desktop on the Windows machine.

Should work for Vista too, I think.

That works really well. :)

---

### Post by Iowan on 2009-04-07
[Here]("https://help.ubuntu.com/community/VNC") is a help page for VNC.

---

