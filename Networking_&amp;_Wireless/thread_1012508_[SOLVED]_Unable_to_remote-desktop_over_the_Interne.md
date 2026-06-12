---
title: "[SOLVED] Unable to remote-desktop over the Internet"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by pmulgaonkar on 2008-12-15
Folks: I have a Hardy box behind a wireless NAT. I can connect to the box using VNC viewer from another computer on the wireless (using local IP address 192.168.1.x). The Hardy box is on a fixed IP address. I have the router set up to forward port 5900 to that fixed IP for both TCP and UDP protocols. 

The computer is using DynDNS and ddclient to report its IP address and I can ping that IP it over the internet.

However, I cannot use VNC viewer over the internet to connect to the Hardy box. I get Connection Refused 10061. How can I test if the router is actually forwarding anything to the Hardy box? Is there a remote desktop log that I can look at to see if it shows any incoming connection attempts when I try to VNC to it over the internet? 

Any help and pointers appreciated.

BTW, I used canyouseeme.org to check, and it shows that port 5900 is open. I *can* connect to the remote-desktop on my local area net using the local address, so the box is responding right. I cant tell if there is any kind of a firewall or something else that is preventing the connection from the internet reaching the unix box.

I posted this message on the desktop part of the forum and got no responses. I hope that the networking group has more ideas on what to try next.

--p

---

### Post by ThaddeusW on 2008-12-16
pmulgaonkar, 

Which router are you using? Some can be real fickle about port forwarding. Since I dont know your router make I can say that you need three setting to get it working right! 

First off VNC is TCP so get rid of any UDP entries.

Second you need to enter the "source" or "incoming" port number so the router knows which port to listen for incoming connections. Second you need the ip of the VNC system for the destination or NAT IP. Then you need the destination port number. Sometimes routers allow you to enter a range of ports to listen to. Just enter the one port number in both boxes if yours has that option. 

You also need to realize that leaving 5900 open is very risky. I just have 8080 for my web server (locked down) and 22 for SSH. Which Operating system are you using to access your hardy box? [Either way please read this article]("http://souptonuts.sourceforge.net/sshtips.htm") and setup an SSH server on your hardy box. Is the hardy box a server or desktop (I am guessing desktop) 

I have an ubuntu server that has XORG but is only started from the command line when needed and runs Fluxbox. So this will allow you setup a headless vnc server. Here is what I do to easily allow me to SSH and then vnc into my ubuntu server:

Grab the exe only version of putty. Then download the exe only version of TightVNC and put them both on a usb key and/or your cellphone (only takes up 816kB!). On your hardy box: ```
#sudo apt-get install x11vnc xvfb
``` Now follow the instructions on the SSH tutorial page to enable you to VNC through an SSH tunnel. Once you have successfully logged into you system via putty you then follow my instructions. You ned to get the virtual X frame buffer up and then run x11vnc on top of that to give you a VNC only X server :KS: (you just type the following commands into putty once logged in)

> 
First we need to start the virtual framebuffer X server:
$Xvfb :1 -screen 0 800x600x16 -ac &

Next we need to export the virtual x server screen as an environment variable:
$export DISPLAY=:1

Now we can start the x11vnc server:
$x11vnc &

Now start the vnc client and login using 127.0.0.1 as the host. Putty will route vnc through ssh to your Linux box. You may start a window manager such as icewm or fluxbox as a daemon as well by just typing "$fluxbox &" or "$icewm &". Then you will have a usable X desktop.   

note: Typing an "&" symbol after a command means we are starting the program as a daemon to run in the background. just hit enter a second time to get back to the prompt. Once you log out of putty those daemons will be terminated. 



Note that you can change the resolution and color depth to vary bandwidth used. so if you want true color and 1024x768 you just replace 800x600x16 with 1024x768x24. I also recommend using fluxbox or icewm to minimize the amount of bandwidth used. You can also simultaneously run this along side your normal X server on the system to create a more bandwidth efficient VNC server. This setup is super convenient as it doesn't require you to install putty or vnc on a system to work. You simply run the exe's off the usb key. My friends are always amazed when I have a few terms open on their pc using vnc and wondering how the hell i did it. :guitar: 
 
Oh and for a router [I recommend m0n0wall]("http://m0n0.ch/wall/")!
I used an old PC and installed m0n0wall to a 64mb flash card plugged into an ata adapter. That has to be the best router software I have ever seen. Feature packed and compares to commercial routers costing thousands of dollars. Easy to use too!

---

### Post by pmulgaonkar on 2008-12-16
Thanks for the detailed recipe. The router is an Indian brand called a Beetel 450 BXI, combination WiFi router and ADSL modem. I cant find any info on the details. So before I try any of the secure connection stuff, any ideas on how I can verify if the router is indeed forwarding the port (unsafe though it may be)? I have all the other details set up correctly as far as I can tell. I turned off the UDP forwarding.

--p

---

### Post by doobiest on 2008-12-16
instead of doing port forwarding a much better solution is to use SSH forwarding.

This is a benefit for 2 reasons.  

1) It's over a secure tunnel, If I were you I'd want a full gui connection to your main box at home to be secure.  Especially if doing this from work/school

2) You aren't leaving a vnc session open to the internet vulnerable to bruteforce attacks.  I'd much rather have my ssh daemon be my front end.  You'd be surprised how much you likely get bruteforced, check your /var/log/auth.log  I get quite a lot of attacks.

This is really easy to set up, in your /etc/ssh/sshd_config file just make sure this line is set, AllowTcpForwarding yes

Then from the connecting client, assuming it's linux, issue this from the command line. vncviewer -via yourdomain.com localhost

To break it down what's happening is, vncviewer is establishing a secure ssl tunnel vis yourdomain.com and then connecting to the vnc server on localhost.  Presuming that your ssh and vnc server are both on the same box.

SSH forwarding for the win, I use it for everything.  The major benefit is you can forward so much stuff over ssh, it's secure, and you only need one open port to the internet vs. a port for each service you want to use.

Additionally if the connecting client is using windows, install putty for ssh and tightvnc viewer.  Then in Putty under connection > SSH > Tunnels, add source port of 5900, and destination of localhost:5900.  Connect to yourdomain.com, open tightvnc viewer and connect to localhost:5900


***Eventhought ThaddeusW provided a great and detailed response, when I first tried doing this method my first time I found the instructions and the concept extremely confusing. It's actually quite simple just the explanation in the provided article has some rough edges, so I hope the information I provided is easier for newbs to follow**

---

### Post by doobiest on 2008-12-16
To answer your question about verifying ports being open you can do to things.

Go to a linux box that isnt on your local network and issue nmap yourdomain.com  and also try telnet yourdomain.com 5900, or whatever port you have vnc on.

---

### Post by pmulgaonkar on 2008-12-16
Thanks doobiest. I suppose I still need to open some ports on the router to allow external connections into the ssh server? That still leaves me with the question of whether my router is doing port forwarding correctly.

What ports need to be opened for SSH?

[EDITED-- Got it. Port 22]
--p

---

### Post by pmulgaonkar on 2008-12-31
Thanks to all who helped, I got the SSH forwarding to work (as suggested by Doobiest). Key problem was that my router was messing up when I tried to use an external IP address to get out and back through it. I had to have someone who could login from a true remote machine, run the test for me.

--prasanna

---

