---
title: "Playing audio CDs in analog mode"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by whatteaux on 2006-11-09
The headphone jack on my PC case is dodgy, so I need to use the CD drive's headphone jack (luckily it has one, and a volume control, but has no other controls) to listen to audio CDs. But this requires a CD-playing program that supports analog play mode, in order to stop, skip, pause, etc.

I've tried the following:
1. kscd: 'Pause' function has been broken for years (does a complete 'stop' instead, can't restart except at start of CD). Also dies after a random amount of time (maybe 2 or 3 tracks). Fundamentally broken. Is it still supported?

2. xmms: Apart from the new brokenness in Edgy Eft (which I can work around - barely), it'll only play the first 12 tracks on a CD (huh?). Plenty of other minor annoyances but also, in general, broken. Is it still supported?

Can someone recommend a modern (i.e. supported/maintained and working properly) CD-playing program that supports analog play mode? All of those that come with my distros (apart from the ancient/broken xmms and kscd) seem to only support digital playback, but maybe I've missed something.

(BTW, analog playback works perfectly on Windows's Media Player, so I know it's not a hardware problem.)

---

### Post by Jeisson on 2008-03-09
I am interested in this topic also, because digital playback causes high noise while the CD is spinning on the drive.

I solved the problem with Audacious, a player similar to Winamp and XMMS. In "Preferences (Ctrl+P) | Plugins | CD Audio Plugin | Preferences | Device", you can select the Analog radio button in "Playback mode". Next change the mount point in "Device |Directory" from "/mnt/cdrom" to "/media/cdrom". Finally, ajust the volume control in the mixer and done!

Best regards.
-Jhc

---

