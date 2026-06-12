---
title: "How do I network between 8.10 and Vista"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by Vignesh S on 2009-09-24
I want to set up a file-sharing network between Ubuntu 8.10 and Windows Vista. I can't make head nor tail of the stuff I have got so far. So all I want is very easy to understand, and follow tutorial as to how I should do this. The specific purpose of this is to retrieve files from a vista laptop, and I am NOT going to use my USB to transfer the files back again! Way to slow.

If there isn't an easy to follow tutorial, can anyone at least tell me how to transfer files between Ubuntu 8.10 and Windows Vista via ethernet cable? Clearly, directly connecting the ethernet cable between the two computers doesn't work. Does anyone also know why that doesn't work?

---

### Post by weedcali on 2009-09-24
if theyre on the same machine cant you just go into your hard drive folder?

---

### Post by foremannz on 2009-09-24
Are you running a single cable between 2 computers without a switch?  If so, is the cable a crossover cable?

---

### Post by Vignesh S on 2009-09-24
OK lets get things right here

1. They are NOT on the same machine. The files are on a vista laptop, and I am using an Ubuntu 8.10 desktop

2. The cable isn't a crossover cable. Isn't there a way to make an ethernet cable into a crossover cable? No idea where to get one locally, and buying it over the internet will take a while to arrive. So I'm trying to avoid that.

The point is, I want to network between the two, but I just can't! :-(

But if no one can offer that solution for me, than I just want to know if I can transfer files over an ethernet cable.

EDIT: Looks like I found this [http://ubuntuforums.org/showthread.php?t=985415](http://ubuntuforums.org/showthread.php?t=985415). Looks like I'll need to configure Vista. I actually could get this to work...

---

### Post by foremannz on 2009-09-24
If you can get to an electronics shop, an ethernet crossover cable should be about the same price as a straight through cable.  You can also buy an add on adapter that turns a straight through cable into a crossover.

Another alternative is a USB network cable, but these would cost substantially more

Wiki to the rescue: [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

Oh, also, if you are using TCP/IP for networking, you might need to set up the IP addresses on each computer, because I doubt either of your computers will be distributing IP addresses.

Make it something like

Vista:
IP: 192.168.1.1
Mask: 255.255.255.0
Gateway: 192.168.1.1

Ubuntu:
IP: 192.168.1.2
Mask: 255.255.255.0
Gateway: 192.168.1.1

---

### Post by Iowan on 2009-09-24
Got an extra ethernet cable? You could modify it for a quick/dirty crossover cable... VERY dirty. *Might* work until you could get REAL one...
A hub/switch would also solve the problem (at least the connection part).

---

### Post by Vignesh S on 2009-09-24
How would I do that, Iowan?

---

### Post by False Dmitry II on 2009-09-24
It involves cutting the cable and re-wiring it...

---

### Post by Vignesh S on 2009-09-24
Is there a how to in regards to that?

---

### Post by Iowan on 2009-09-24
Basically, you could use the previously mentioned Wiki [link]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") as a schematic, connecting white-green from one end to white-orange on the other, etc.
Crimping on a new end would be preferred, of course...
[Here]("http://www.littlewhitedog.com/content-8.html") is a How-To, but it requires tools which most of us might not have.

---

### Post by Vignesh S on 2009-09-24
Well I seem to be the exception. With my Dad being a toolmaker and all :-) We also have some of those tools with a DIY networking kit. Yeah, we'll see how that goes...

Now, to networking...

EDIT: I now have 100 beans! YAY :-D

---

### Post by Iowan on 2009-09-25
OK, then the "proper" way would be to cut one end off a straight cable, and crimp on another connector wired for the crossover connection (starting with white-green instead of white-orange). Good luck! I *enjoy* making up cables - amongst my other quirks...

---

