---
title: "Setting up XBMC/MythTV to use xbox as frontend"
date: 2009-01-20
forum: Mythbuntu
---

### Post by arpnuke on 2009-01-20
Hi, first a huge thank you to all that have contributed to mythbuntu.  It took no time to set it up and begin watching and recording TV.  What I am looking to do is use my modded xbox running XBMC to stream liveTV and view recordings.  There is some documentation here:  [http://xbmc.org/wiki/?title=MythTV](http://xbmc.org/wiki/?title=MythTV)

The first problem I have run into is setting up the backend to allow external connections.  The IP of the backend is 192.168.0.108.  When I went to the Database Configuration screen and attempted to change the hostname from localhost to 192.168.0.108 the backend/frontend could not connect to itself.  Any ideas on allowing it to open connections?

To get the xbox frontend to connect a video source must be added.  myth://mythtv:PASSWORD@192.168.0.108 should do the trick once the backend is opened up.

---

### Post by tgm4883 on 2009-01-20
On the backend, open up mythbuntu-control-centre and enable the mythtv service

---

### Post by The Odometer on 2009-01-20
In my experience, XBMC will work fine to view recordings using it as a UPnP device. However, using the Myth Protocol seems to be choppy for me (both Live TV and recordings). I was doing it wirelessly using a wireless access point (actually an old router with DD-WRT).

If I remember correctly (it was 6 months ago when I did this), you need to set up NFS Shares. My notes on this seem to point to this link on how to do it [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server). Of course, setting up a static IP is a given, as well. 

To use the Myth Protocol, I think you have to set up MySQL. Again, its been a long while since I did all of this, and I'm not certain.

It might not have affected me doing it, but I think it did. Eventually, I'll be doing the same thing (again). My backend died on me a few months ago--and I haven't had a chance to work on it very much.

I might not have helped at all, but hopefully I got you started.

---

### Post by arpnuke on 2009-01-20
Adding an XBMC source for UPnP did the trick.  Automatically found the server and provides listing by title, channel, date, and more.  Unlike the automatic SMB share, the shows have proper titles rather than numbers.  I'm a bit sad that I can't watch liveTV like the myth:// protocol, but from what I have read it isn't well implemented.

Google has a summer of code project coming up in '09 for PVR support (mythTV being the focus) for XBMC.  I plan to revisit this once changes have been made to XBMC.

---

