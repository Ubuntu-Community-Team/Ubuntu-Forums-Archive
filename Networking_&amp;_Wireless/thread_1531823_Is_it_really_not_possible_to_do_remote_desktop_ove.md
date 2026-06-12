---
title: "Is it really not possible to do remote desktop over the internet?"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2010-07-15
Hi guys.

I have ubuntu 8.10 amd64 on a PC connected to an Asus RT-N12 with the latest version of DD-WRT.  I get my internet through Comcast.

I would like to log into my home PC (running ubuntu) from a PC at another location (it also runs ubuntu), through the internet.  Is this possible?  Or is it only possible to do so through my local network, not over the internet?

If it is possible, then does anyone know how to do it?  I've tried following [this guide](http://ubuntuforums.org/showthread.php?p=8761388), but it doesn't work at all (perhaps because I can't understand half of it).  Any suggestions?

Thanks!

---

### Post by Endwin on 2010-07-15
Yes you can do it.

There is the secure way and the insecure way of doing this. 

The INSECURE way (for demonstration and conceptualizing). 

You open up the VNC port on your router and point it to the machine you want to connect to. For example if my internal machine bob is what I want to connect to I would forward port 5900 (default VNC port) to bob. Then whenever you connect to your external IP address the router will pass your VNC connection off to bob. 

What that article gets into is a way of doing that through an encrypted connection. There are a lot of ways to do this. I always found a simple SSH tunnel [Described Here]("http://ubuntuforums.org/showthread.php?t=872804") does the job just fine. Just make sure you forward port 22 (SSH to bob instead of 5900).

---

### Post by hurtstotalktoyou on 2010-07-16
Thanks for the verification.  That encouraged me to keep at it, and I finally figured it out.

Configuring the router is the tough part.  No set of instructions I've found thus far has been accurate with regard to that.  I managed to figure it out, though, for myself, and then the how-to guides worked with everything on the ubuntu side.

---

