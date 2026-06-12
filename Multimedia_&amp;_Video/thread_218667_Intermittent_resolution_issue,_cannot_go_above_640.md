---
title: "Intermittent resolution issue, cannot go above 640*480 using VNC"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by DigitalHunter on 2006-07-18
I recently installed Ubuntu to see what everyone was raving about. Right now I have it running an Apache server with my family webpage hosted on it. I find it to be a great operating system with tons of possibilities for me.

However I have one big (or should I say small) problem. Since installing the operating system I have limited myself to accessing the computer using VNC through my windows XP computer. However when I do this sometimes it gives me the 1024*768 resolution and sometimes it's 640*480. Lately it's been 640*480 and in the resolution application it does not give any other option for a resolution size.

I have narrowed my problem down to one thing that I believe to be wrong but I do not know how to fix it. Since I am just going to use it primarily for a web server I have disconnected the monitor and have left the mouse and keyboard attached. This way all I have to do is boot the machine, wait a bit, enter my username and password blind and then access the desktop via VNC. Since I have removed the monitor the resolution through VNC is stuck at 640*480 and it will not change. I have tried reinstalling the video driver, I have tried manually configuring the xorg.conf file to correct the driver. None of this has helped. 

I really don't want to reconnect the monitor as it is an old CRT and takes up a bunch of space and I have the perfect setup right now I just need to get this resolution problem through VNC fixed. Just so there is no confusion, I have been able to get resolutions up to 1024*768 through VNC with the monitor attached (as long as I had the monitor ON while logging in, strange as that is) but without the monitor I only get 640. So that pretty much rules out an issue with the VNC program.

Does anyone have any ideas?

Thanks. Sorry it was such a long post.

DH

---

### Post by DigitalHunter on 2006-07-19
I should probably clarify something. The remote desktop program I am connecting to is Gnome-RDP and not vncserver. I am using VNC client through Windows XP. I've been scouring my installation for a possible config file for Gnome-RDP but haven't found any. 

I've emailed the creator of Gnome-RDP and if he tells me anything interesting I will post it here.

Anyone else have any ideas on what I can do?

Thanks.

DH

---

