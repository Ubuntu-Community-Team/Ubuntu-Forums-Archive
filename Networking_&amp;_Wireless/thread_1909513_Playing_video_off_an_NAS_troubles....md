---
title: "Playing video off an NAS troubles..."
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by chris48083 on 2012-01-15
SSoooo I wasn't sure where to put this, maybe in hardware, maybe in installations, maybe in beginners help....at anyrate, searched around and couldn't find anything with a similar problem so here it is-

I'm running Ubuntu 11.0 on my home-built machine.  I have it connect via a router to a Netgear Stora NAS with (2) 1TB drives RAIDed together.

I use this device to store mostly media.  Playing back music doesn't seem to be a big issue, and I can transfer large amounts of data to/from without error....except whenever I playback video (VLC, however I've tried others, but they freeze too or have codec issues) it will play for a seemingly random amount of time and freeze.  Once frozen ) will allow me to close the window, but not exit the program.  Obviously from this point I cannot load another video, stop the current or do anything except close the window....

Any run across the samething?  Any suggestions?

Thanks guys!

-CW

---

### Post by SeijiSensei on 2012-01-16
Are you using wifi or wired ethernet?

If you can easily connect the devices with an Ethernet cable, I'd start with that method and see whether you still have the problem.

Also what protocol are you using on the NAS to share files?  I find NFS much better for streaming than Samba.

---

