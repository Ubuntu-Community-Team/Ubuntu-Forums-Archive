---
title: "The Perfect Home Network"
date: 2008-03-18
forum: Mythbuntu
---

### Post by TheAddict on 2008-03-18
Okay, so here is my idea of the perfect home network (this is gonna be a long one so stick with me here):

1. A central file server to host all of my media files and other files that I want to be able to access from any client on the network
2. A standalone DVR, to record TV (and automagically remove ad's if possible)
3. A standalone bittorrent box, that I can control through a web-based interface.
4. A front-end media center for each TV in the house, and connected to the stereo or surround system if one is there
5. The standard client computers, for standard crap like web-browsing, word processing all of that
6. A repurposed palm pilot as universal remote control (so that I can control each front-end)

If it will make life easier I am willing to roll the PVR and the file server into the one system, its just that I want to keep them separate so that when the server gets attacked by more than one client wanting files, I don't want to have to compromise on either encoding quality, or access speed for the users.

I am planning on using Gigabit NIC's thoughout.

All simple enough tasks in theory (though practice may prove me wrong on that).

But there is a couple of extra things I want, but am not sure if they are possible

1. If having the DVR as a standalone sytem is viable, then I want completed files to be transfered to the file server either at the end of the encoding process, or at a scheduled time, and then delete the files off of its local HDD.

2. I want to run the PVR headless and be able to setup recording schedules remotely

3. I want to be able to use the pocket pc as sort of an extended output device - by this I mean when I have the telly turned off, to be able to navigate through menu's visually on the pocket PC so that I can select music to play without having to turn the telly on.

---

### Post by nasha on 2008-03-18
I would roll the fileserver, dvr and torrent box into one... Actually, thats exactly how i have my setup :P

The reason for this: My crappy backend setup can record two HD streams, as well as play one, and stream one, without any issues. If you were to move to a RAID array, then you would surely have no issues with bottlenecks, and not to mention save $$$'s on hardware.
> 
1. If having the DVR as a standalone sytem is viable, then I want completed files to be transfered to the file server either at the end of the encoding process, or at a scheduled time, and then delete the files off of its local HDD.
New version on MythTV 0.21, makes it much easier to add or customise your storage options with storage groups.

> 2. I want to run the PVR headless and be able to setup recording schedules remotely

MythTV is your answer :)

> 3. I want to be able to use the pocket pc as sort of an extended output device - by this I mean when I have the telly turned off, to be able to navigate through menu's visually on the pocket PC so that I can select music to play without having to turn the telly on.
I imagine theres a few ways you could do this, but the first that came to mind is VNC from the pocket pc, into your frontend?

My ideal setup would be exactly what i have now, except more storage and another tuner, sick of ironing out conflicts and deleting recordings to make space :P

Just my two cents,
Nasha

---

### Post by TheAddict on 2008-03-18
Thanks for the response... 

I never thought about using raid to conrol bottlenecks... mostly because I have only a very very rudimentary understanding of RAID.. sounds like a good plan though.. thanks

and as for VNC from the pocket pc.. nice.. i also hadn't though of that.. I was thinking along the lines of writing some basic text based program that tracked the remote inputs and displayed a text version of the front end if you follow what i'm saying.. vnc will eliminate that need..

---

### Post by nasha on 2008-03-18
I suggested raid because the HDD is the thing that would be pushed for resources the most for obvious reasons. RAID 0 would probably by the easiest option, providing you with just faster access times, followed by RAID 1, Or RAID 5 if you require redundancy. 
[HTML]http://en.wikipedia.org/wiki/RAID[/HTML]
Should provide you with some more info :)

And VNC will be a piece of cake, because all you need to do to get it working, is enable it in the MythBuntu install, and specify a password :P

---

### Post by ian dobson on 2008-03-19
Hi,

I'm running a quite powerful backend (Q6600/3Gb Ram) with a RAID5 array of 4 500Gb harddisks.

Although I've never tried to benchmark the system, all I can say is that recording 2 SD streams, watching 2 other streams while dumping 4Gb (DVD rip) over the network (1Gb) at the same time doesn't even get the box sweating.

Regards
Ian Dobson

---

### Post by Calash on 2008-03-19
I have a 2gig box with 1.5gb memory that does all of the following


Mythbuntu Frontend/Backend
File server
Remote BT system (Torrentflux)
Web Server
CUPS Server (Network Printing)
DHCP server (When testing diskless frontend)

Never have any load issues with it.  I admin it using SSH -X on my main Ubuntu system.  Even when running it full load it never has any issues (Running updates, watching TV, Remote Frontend pulling recording.)

As to the pocket PC question, what do you want to access?  I have had some luck on my WM6 phone streaming music from Mythweb.  Still have not tried Video yet, but in theory TCPMP should be able to process the data....just have not tried it yet.

There is also a project that turns your WM/PPC device into a TCP/IP or Bluetooth remote for your Myth setup.  The software did not seem to have much customization ability but it seemed to work ok.

---

