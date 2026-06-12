---
title: "Ubuntu 9.04 VNC Help?"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by syborfical on 2009-05-24
Like per-normal with each new release of ubuntu VNC breaks and I have to figure out how to get it working again.

What I use to have a head less ubuntu 6.10 machine.  Could not get the same setup 
working after 6.10

**What I would like is VNC working the same as windows. I would like a headless machine. **

Pretty much id like to be able to boot my machine a vncserver starts

When I load VNC it is the same as sitting in front of a montor I can log in and out with different users etc.

Also I don&#8217;t want to have to type the machinename:1. I don&#8217;t want to use VINO because its ****.

I had this working with ultra VNC server but since the boffins decided to change everything around I have not got this working.

I currently run 8.10 with tightvnc server I have to SSH in and tell VNC server to run. I can only run it as once user but I do have resumable sessions.  I cannot get this to work with 9.04

So if anyone out there has 9.04 and a VNC server working that is not the built in one feel free to give me some tips. 

Cheers and thank you for reading.

PS 

how i get VNC working on 8.10 with out the SSH tunnel as im only testing atm :P
[I]
Ubuntu 8.10 VNC

How to get Tight VNC to work with resumable sessions. 

Install Tight VNC apt-get install tightvncserver 

edit the following ~/.vnc/xstartup 

(or /root/.vnc/xstartup) 

the script should look like this 
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid black
gnome-session &

To run vnc server, shh into server and run the following. 
vncserver -geometry  1024x768 -depth 24 -fp /usr/lib/X11/fonts/misc/

For more commands type vncserver &#8211;help[/I]

---

### Post by syborfical on 2009-05-31
Bump!

---

