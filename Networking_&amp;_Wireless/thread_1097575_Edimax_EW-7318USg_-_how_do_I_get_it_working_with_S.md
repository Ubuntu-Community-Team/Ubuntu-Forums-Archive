---
title: "Edimax EW-7318USg - how do I get it working with Server 8.10?"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by usr33t on 2009-03-16
Hello everyone,

I know there are several posts in relation to this already, however, I wonder if anyone could help me please?

I am currently running Ubuntu Server 8.10 to service the needs of my Squeezebox (network music player), which is connected to the server via ethernet cable.  The server has no means of connecting to the internet.  I would like to install a USB wireless adapter on the server (Edimax 7318 ) to provide internet access.  I would also like to bridge the wireless adapter to the ethernet connection to provide the Squeezebox with internet access.

My questions:

(1) Has anyone had any luck getting the Edimax 7318 adapter working with Server 8.10?  I have tried following the various instructions on this forum but don't really know what I'm doing - I tried for 12 hours yesterday!  Could anyone give me a simplified step by step guide please?

(2) Is it possible to bridge the Edimax to the ethernet port?  Again, I have tried following various instructions but my inexperience with Linux is holding me back.

If anyone could help me I would be extremely grateful.

Many thanks

Russ

(usr33t)

---

### Post by ugm6hr on 2009-03-16
I would recommend the serialmonkey drivers, and connecting using the commandline:

[http://ubuntuforums.org/showthread.php?p=5670568#post5670568](http://ubuntuforums.org/showthread.php?p=5670568#post5670568)

My final post is good for WPA, and post 1 explains how to do all the rest (inc WEP)

As for a network bridge - someone else will hopefully help.  I have heard good things about ebox for configuration of such things: [http://ebox-platform.com/community/installation-guide/](http://ebox-platform.com/community/installation-guide/)

---

