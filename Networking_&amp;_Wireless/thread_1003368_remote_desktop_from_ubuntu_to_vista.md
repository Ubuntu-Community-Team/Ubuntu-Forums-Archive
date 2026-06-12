---
title: "remote desktop from ubuntu to vista"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by weirdorecords on 2008-12-06
I've been trying in vain for a couple of days to set up a remote desktop link from my ubuntu 8.04 pc to one running vista in another room.

1. I have enabled remote desktop on the vista machine, allowing for all connections.
2. I have installed tightvnc server application on the vista machine & set a password.
3. I have port-forwarded the tightvnc server application, because the vista machine and the ubuntu machine are not connected to the same router.
4. I have installed the remote desktop application 1.5.0 on the ubuntu machine.

I've tried downloading several applications on the ubuntu machine (such as gnome vnc), but none of them seem to work with vista well.

My best success has been by using the terminal to type:

rdesktop 66.30.112.xxx 

(where the xs are replaced by my ip address)

When I do this, I do not get an error message. However, the remote desktop also does not open. I just get a blinking cursor, and then after a few minutes the connection automatically terminates.

Anyone who can help me figure out what to do next?

Thanks for your time.

Angela

---

### Post by matpol on 2008-12-06
You need to run the vncserver application on the Vista machine and vncviewer on the ubuntu machine. Using vncviewer you need to connect to the ip address of the vista machine using the port number 5900 e.g. 192.168.6.8:5900. Also on vista you probably need to check the firewall settings to allow the access to the port and ip.

To make life easier I would try and put everything on the same network.

---

### Post by weirdorecords on 2008-12-06
Firewall is momentarily removed (forgot to mention it above).

I'm new to Ubuntu & having problems figuring out to get VNCviewer to run on it. That's why I was going through the terminal. I'll work on that & see where it gets me. Thanks. 

> **matpol said:**
> You need to run the vncserver application on the Vista machine and vncviewer on the ubuntu machine. Using vncviewer you need to connect to the ip address of the vista machine using the port number 5900 e.g. 192.168.6.8:5900. Also on vista you probably need to check the firewall settings to allow the access to the port and ip.

To make life easier I would try and put everything on the same network.

---

### Post by weirdorecords on 2008-12-06
Okay, maybe someone can help me figure out how to install a vnc viewer. I've tried using the terminal to install a package, downloading a gz file from the ubuntu forum, or using add/remove programs. Ten different vnc applications, and none of them run or open when I try to extract them....?

---

### Post by weirdorecords on 2008-12-06
Finally found vinagre on the ubuntu machine. I discovered that this *may* be a bug with vista, & am now using UltraVNC as a server side software, as it's said to be compatible with vista. Seem to be running all the software successfully, but as before, just getting a blank when I try to connect. Could really use some help from someone who's experienced the same problem.

---

