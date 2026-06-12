---
title: "IGRS protocol support"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by jimbolaya on 2010-05-13
There appears to be a new network protocol being implemented called IGRS.  There's a white paper [_here_]("http://hes-standards.org/doc/SC25_WG1_N1346.pdf") another article [_here_]("http://www.igrsnl.com/templates/nEO_IMG_2_en/index.aspx?nodeid=165") and a USB "infinite storage" device (from China/in Chinese) can be found [_here_]("http://www.dealextreme.com/details.dx/sku.36387").

Has anyone used one of these?  Are there plans to support this protocol at some point?

James

---

### Post by moefh on 2010-06-16
I just got one of these devices. I'm currently reverse-engineering the protocol, here's what I found so far.

[First, a little background: To use this device, you have to install a "media server" on a Windows PC. It basically consists of a few Windows services to handle the IGRS (as far as I can tell) and a GUI program that allows you to choose files that will be served to the device. My goal is to implement this "media server" on Linux.]

As far as I see, IGRS is a very simple UDP-based protocol (believe it or not, using HTTP and SOAP over UDP). The device uses it to locate the Windows server (broadcasting an UDP discovery packed to 239.255.255.250). The IGRS service on Windows replies with the IP of the file server (i.e., it's own IP). The device then connects to the file server on TCP port 31013 (no idea where this port comes from, maybe it's hard coded) and speaks a slightly modified [NBD protocol]("http://nbd.sourceforge.net/"). If anyone is interested in the modifications I discovered so far, I can send details. These modifications unfortunately mean that a vanilla nbd-client doesn't work with the windows server, and so a nbd-server will probably not work with the device.

I'll probably have a Linux server working in the next weeks. I'll put the IGRS server coupled with the modified NBD server for simplicity, but it would probably be best to make it a service. The problem is, I have found no detailed documentation on IGRS, so all I can do is make it work with the device I own.

---

### Post by jimbolaya on 2010-07-23
Please let me know when you have something to test.  I got one of these recently and I'm interested in seeing it work on Linux.

James

---

### Post by moefh on 2010-07-23
Here's what I have so far:

[http://code.google.com/p/igrs-media-server/](http://code.google.com/p/igrs-media-server/)

It serves a FAT32 image, so you'll have to build one first (I've included a shell script to make one from the contents of a given directory).

It works for a while (I can play some MP3 files), but for large videos, the device stops communicating after a few minutes and needs to be unplugged from the USB and re-plugged to work again (no idea why, I need to do more testing). There's also some code to build the FAT32 image on the fly (so the user won't need to pre-build an image), but it's not working yet. I'm currently busy with some other stuff, hopefully I'll be able to come back to it soon.

Any comments, testing or code will be greatly appreciated! (I you plan to contribute code, let me know if you want commit privileges to the SVN repository.)

---

### Post by jimbolaya on 2010-07-23
I did find that from the DealExtreme forums.  I got the code and compiled it fine.  I've got a FAT32 image mounted loopback so I can add and remove files.

I was having problems getting the LinkSee dongle connected to my network though.  I could see that my wireless router saw the dongle but I never saw any dhcp requests on my server.

I'm not sure what the issue is.  I have a long and random pre-shared key, so maybe I'll try shortening it when I play with it this weekend.

I also found it conflicts with djmount which also uses port 1900, so I had to kill my djmount to get this server running.

Thanks.

James

---

