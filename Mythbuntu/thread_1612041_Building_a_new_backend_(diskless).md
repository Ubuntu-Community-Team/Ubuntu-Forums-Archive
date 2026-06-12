---
title: "Building a new backend (diskless)"
date: 2010-11-02
forum: Mythbuntu
---

### Post by Spr0k3t on 2010-11-02
Okay, so I've moved all of my media over to an external server (6TB of redundant storage on an NFS share), now I'd like to make the primary backend disk free using a small bootable USB drive (much faster than the current hard drive).  Any suggestions or pointers on setting this up?

Distribution will be using Mythbuntu 10.10 32bit.  The case is an Antec Fusion Black 430 with the iMON Soundgraph OLED display.

---

### Post by LowSky on 2010-11-03
This sounds confusing I've heard of diskless frontends but never a backend. If the server your using is always online, why not have that device run the backend too?

Why build an extra machine just to run a backend?

---

### Post by Spr0k3t on 2010-11-03
The server holding the majority of the media files is running BSD (can't run mythbackend on BSD that I'm aware of) booting on a 1GB USB key.  I removed my storage from my primary computer system and moved it to the server.  I'm even in the process of moving /home/ to the server and keeping the primary operating system drives small.  So, in the kick of centralizing and downsizing this cluster of a network, everything has been running superflious.  The transfer rate over the network is more than enough to sustain over 30gb/s to multiple myth frontends.  The server holds six 2TB drives in 0+1 configuration.  The question is, why would I want to run the backend on an atom processor that's dedicated to doing not much more than NFS shares when I could set the primary backend up connected to the server as a mounted drive space using the primary backend on a small bootable USB drive?  The primary backend in the Antec case has an AMD processor capable of handling the transcoding over the gigabit network.

Now, one of the primary reasons for my doing this... I'm working on building a system for a local business in my area.  They like the idea of a mythtv setup, but they want to have all of the media and live recordings located on a separate (sic redundant) BSD server.  Since I don't have the funding to support the development of a full server farm, I'm doing my research on a much more scaled down model at home.  The primary backend running with a mounted share over the network works quite well... I just need to reduce the footprint to fit on a small USB key.

---

### Post by Sum Guy on 2010-11-04
Somewhere in Ubuntu's repositories is an application that allows you to customize Ubuntu CD images. If it works on Mythbuntu (it should), you could use this to set up the backend's packages the way you want (starting from a Mythbuntu CD image), and ensure a MythTV backend is on it, then use the USB Startup Disk Creator in System>Administration to make a USB drive like you describe. I'm not entirely sure whether the backend will actually work, but I can't see why not, and this method only requires a 1GB flash drive.

Or you could get a 4GB flash drive and install straight onto it, like a normal hard drive.

---

### Post by thatguruguy on 2010-11-04
How about [MiniMyth]("http://www.minimyth.org/")?

---

### Post by Spr0k3t on 2010-11-05
MiniMyth looks interesting... I'll give that a shot.

---

