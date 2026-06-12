---
title: "Multiple connection problems using ubuntu 11.10 and Acer 8930g"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by thedemon13666 on 2012-03-25
Hey,

I apologise in advance for how vague, and most likely, unhelpful  this description of my problem is.

I have noticed several 'connection' problems when using my acer 8930g and attempting to do various transfer activities, in partiularly:

FTPing to consoles
Downloading High Energy Physics (T2K) software.

First FTP problem.  I have been trying to transfer some files to my ps2 (when it is running ulaunch elf) and my laptop is running filezilla in active mode.  During transfer (after say 30 seconds or so) the connection drops and any attempt at reconnection gives me the "no route to host".
The only way to get reconnection is with a ps2 reset and restarting filezilla.
This could be a problem with the ps2, however recently I Was also trying to transfer files to the xbox 360 and while the connection did not drop, the connection speed reduced to 0.

This leads me into my next problem.  I have been trying to download some software for my PhD, of which the workbook and installation information can be found here:

[http://www.hep.lancs.ac.uk/nd280Doc/stable/invariant/nd280Doc/workbook/Workbook.html](http://www.hep.lancs.ac.uk/nd280Doc/stable/invariant/nd280Doc/workbook/Workbook.html)

You will notice that the download involves using CVS and CMT which I thought may be causing the problem but due to the ftp problems I am no so sure now.  The problem arises during the download of the nd280 software, while it is downloading (at a random point, however it occurs quickly) the command line appears to hang which I believe is the connection speed dropping to 0.

Both of these above problems could be caused by so many things, such as the laptop or my router but I can't figure out where to start.

Here is my setup.

Laptop: Acer 8930g
Router: O2 Wireless box IV
OS: Ubuntu 11.10 x64

That is about all of the information I can give (really sorry it is all so generic)

Thanks

---

### Post by jonobr on 2012-03-26
Yep

Its pretty vague

I think both instances however are related.

The FTP to your courseware and the ftp to your devices I reckon all have the same root issue I would guess.

No route to host could mean a router issue , or an issue on either side of the connection,

The only thing I can recommend you do is that when  you try the copy or the move,

setup a continuous ping externally and see if the route dissapears as the message indicates.
If and when it does, run an ifconfig to see if you still have an ip address and are connected to the network.

Also running 
dmesg | grep <interface name>
may show something of interest also.

My guess is that your machine is loosing an IP address

---

### Post by thedemon13666 on 2012-04-04
I realise I let this temporarily die however I have news regarding it.  I have attempted to download the nd280 software (using CMT) while at my girlfriends parents house and it worked first time.

So I think this is a good indication that it isnt my laptop that is the problem (at least not completely), I am also beginning to think the router at my flat may be causing the issues....

---

