---
title: "Sharing video from Ubuntu 8.10 to Xbox 360"
date: 2009-03-17
forum: Multimedia Software
---

### Post by Yerknutz on 2009-03-17
I am now on hour 8 of trying to get this to work. I really want to make Ubuntu my everyday/only OS. Over the weekend I was able to successfully get everything that I love doing on my computer in Windows working in Ubuntu. I am only 1 step away from being able to say goodbye to Windows completely.

I have read every tutorial I can find. I have tryed Twonky Media Server (easiest setup of them all), fuppes and ushare. I have even been able to what appears to be successfully getting them installed from both apt-get and manually compiling from source. In all 3 softwares I have been able to get the server configured, started AND listening on the specified IP address. From all angles it looks like it should be working perfectly yet my xbox 360 cannot seem to find my server. 

ufw is disabled and there is no other firewall running as far as I know. I can get to the configuration page from 127.0.0.1 and my computers IP address 192.168.0.120 but only from itself. Not from other computers on my network. With all three servers running (only 1 installed/running on my system at a time) the 360 also does not see the machine.

I am hopeful someone can help me figure out what I am missing and get this working so I can truly be Windows free... and free up a nice chunk of needed hard drive space :)

---

### Post by Kaneda187 on 2009-03-18
I need help with this too, we but im looking for a step by step idiot proof guide from installing twonky to getting it connected ther has to be an up to date post, twonkys site is no use!

---

### Post by CK05 on 2009-03-18
Try PS3 Media Server. 

Despite it's name, it can stream videos to 360. Obviously it's not made for 360, but it has basic support...it's also an opensource app.

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

---

### Post by Kaneda187 on 2009-03-18
WWWWWWWWWWWWWWWOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO HHHHHHHHHHHHHHHHHHHHOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!;):popcorn::D:P:guitar:
It worked that guide is exactly what i was looking for!!! woop woop! if you dont know you just made my day thank you so much!!

---

### Post by Yerknutz on 2009-03-19
Thanks for the advice CK05. Unfortunately like every other media server I have tried, it didn't work. I am really at a loss for how to get this working when it seems that so many others are having success with ushare, fruppes and PS3 media server.

I have checked my router and UPnP and Multicast are enabled. I have no firewall running in ubuntu that I know of. 'sudo ufw status' reports back disabled. I can even ping my PS3 and my 360 from my linux box but once I have any of the media servers configured and running and broadcasting on eth0, none of my game systems recognize any media servers on my network.

It is killing me that this is the only thing left that I can't get working in ubuntu but works fine in Windows. I really want to make Ubuntu my only OS.

---

### Post by Yerknutz on 2009-03-23
SUCCESS!

After... ok I don't really know how many hours I spent trying to finally get Ubuntu setup so there was nothing I needed Windows to do, I have achieved my goal. I can now happily remove all traces of a Windows installation from my home desktop computer and run Ubuntu 8.10 exclusively.

The last hurdle was streaming video to both my xbox 360 and ps3. With a clean fuppes install and some custom config file manipulations it is working like a charm. I keep a seperate config file for when I want to stream to the 360 and when I want to use the ps3 but it is a small price to pay to have them both working when I want them too.

Props go out to neilsumpter and Ensign R for the custom fuppes.cfg and vfolder.cfg files that got me finally on the right path to streaming media glory. [http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37)

I am officially a Linux user!

oh almost forgot, Handbrake is a beautiful piece of software for converting DVD to H.264, DiVX etc.

---

