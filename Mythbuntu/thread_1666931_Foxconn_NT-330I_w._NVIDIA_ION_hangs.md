---
title: "Foxconn NT-330I w. NVIDIA ION hangs"
date: 2011-01-14
forum: Mythbuntu
---

### Post by stefanst on 2011-01-14
I have a Foxconn NT-330I with NVIDIA ION, running a frontend for my TV. Installed is MYTHBUNTU 10.10 with MYTHTV 0.23.
Backend:
AMD Phoenix, recording via HD-PVR in 1080. 
Conenctions are via 100MBit Ethernet.

On the backend, as well as another AMD frontend I have no trouble at all playing any recorded programs.

Playback on the Foxconn is also trouble-free using VDPAU, but fast forward and fast rewind are extremely slow and the frontend often hangs. The same thing happens with skipping commercials. I'd say 1 in five tries hangs. The processor load in playback is always below 20%.

When it hangs, the frontend goes completely unresponsive. the image freezes and the sound goes into a 500ms (esimated) loop, playing the last half second of sound over and over and over.

The only way to get things back is a hard reset. 

There is nothing unusual in the log. It appears that whatever happens happens so fast and hard that it does not get logged.

It used to be worse, but decreasing the screen resolution from 1080 to 720 did help to improve things quite some. Before that nearly every forwarding, skipping or similar caused the freeze. Sometimes even changing the volume caused the freeze. 

Any ideas?

Thanks!

---

### Post by BicyclerBoy on 2011-01-14
I'll comment because no one else has..

Has this coincided with any nvidia driver updates ?
ION regression seems likely with new drivers.

ION frontends decoding 1080 seem to need more RAM.
It is recommended to have 512MB GPU ram (more system RAM & BIOS setting?)
It is suggested to increase the vdpaubuffersize (custom filter string playback profile vdpau)

ION can not do 2x de-interlace & as feature set B can not do vdpauhqscaling etc

Some revisions of Myth0.23 were sometimes a bit delicate in the GUI.

I found MythTV0.23+fixes to be excellent except for DVD playback.

MythTV0.24 is very good. The changes to OSD theming upsets some users.

---

### Post by BuggyDE on 2011-02-21
It appears that some of these systems have an Atheros ethernet controller, which is defaulting to using MSI for interrupts. Normally that’s a good thing, but sometimes it results in unexpected problems.

Have you folks tried booting with this Linux kernel parameter:

pci=nomsi

Credits to where i found this
[http://www.nvnews.net/vbulletin/showthread.php?t=150725&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=150725&page=6)

---

### Post by stefanst on 2012-01-13
Solved by updating to Mythbuntu 11.10.

---

