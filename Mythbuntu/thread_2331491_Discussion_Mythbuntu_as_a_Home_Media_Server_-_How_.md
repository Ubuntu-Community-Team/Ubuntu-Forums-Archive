---
title: "Discussion: Mythbuntu as a Home Media Server - How are you using it?"
date: 2016-07-22
forum: Mythbuntu
---

### Post by elliott6 on 2016-07-22
Hi All!

QUESTION: How are you using Mythbuntu (or just mythTV)? Or what are you doing to share/utilize media around your home? Organize and remove duplicates? Thoughts and/or best practices? Other programs you are using (Kodi seems popular)? Anyone care to discuss, or direct me to another location for this topic?

Thanks! I've included more ramble below.

elliott

------

Been around for some time (since version 8 I think). More recently (now with kids) I've been using Mythbuntu as a home server, and not fully utilizing frontends and its interface. That's because I like to tinker and have a lot of projects going (although, I don't always follow them through to completion). So, I have a lot of hardware, and good intentions, just not sure where to go from here to clean up what I have accumulated.

The backend records shows, and I pull them off of mythweb to a windows machine hooked up to our main TV. I know I can do more, but my media's a mess (outside of recordings), and wondering if anyone out there has best practices they are willing to share? 

Looking to store all family media on the BE. From there, serve main TV in living room, and one bedroom TV. But then have a main desktop in office, two laptops, couple of Android tablets, and two Android smartphones. Would ultimately like to backup (pictures, documents, and music) everyone, as well as pull media from the BE centrally - cloud storage, but not possessed by Google, or others. And eventually access from the outside (been hesitant to open up the server to the interwebs - more time to spend, rather than worried about intruders) world. I have a couple Raspberry Pi, old laptops and desktops, drives, etc. Trying to organize it all.

---

### Post by Patrick27 on 2016-07-22
Hi Elliott!

It's funny - your situation sounds exactly like mine. I have my BE (running mythbuntu) on an old PC since the first mythbuntu.  It doubles as a file server for everyone. I have 3 TVs hooked up right now with additional old PCs also running Mythbuntu, but I'm moving to using Kodi on OpenELEC on [Orange Pi PC]("http://www.orangepi.org/orangepipc/") (because they are more powerful, silent, use less power, and are cheaper than Raspberry Pi).  Also, the kids keep grabbing the keyboard and mouse that I use to drive the TVs, so by using a tiny device, there is nothing within reach (the Orange Pi hides behind the mounted TV)

For your Windows PCs, you might try Kodi for Windows with the MythTV PVR Client because it really makes it look nicer than mythweb.  It 'feels' more like an entertainment center and less like a PC.  You can also control Kodi with your android devices as the remote control.  I've used the Kore and Yatse apps, and they both work really well.

I have simple samba shares set up on my BE for file sharing. I use external USB hard drives for storage, and I'm ok with that because I don't need great speed for file sharing. On occasion, I run an rsync script to back up one drive to the other, in case the usb disk fails.

In order to feed the other TVs in the house, I hijacked the old Cat5 cabling that was used for phone jacks and crimped it as network cable.  100Mbps is plenty for watching myth. Wireless might be enough, but I haven't used it because I haven't needed to.  I can say that Kodi on my android tablet and phone do work just fine over wireless, as long as I transcode my recordings to something that uses less bandwidth, like h.264.

Not sure if these are best practices or hacks (or both!) but hopefully it helps give you some direction in what you might want to try. That's the thing I love about these open solutions - you can really hack away and do whatever you want.  You aren't restricted to some canned approach.

-Patrick

---

