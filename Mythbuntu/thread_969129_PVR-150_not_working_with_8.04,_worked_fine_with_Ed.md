---
title: "PVR-150 not working with 8.04, worked fine with Edgy"
date: 2008-11-03
forum: Mythbuntu
---

### Post by andyfromtucson on 2008-11-03
I have had MythTV running for a long time on a Via Epia SP8000e (C3 Eden processor) with a PVR-150 (vintage 2006) running Edgy Eft. Last night I decided to upgrade to Mythbuntu 8.04.  After using the Live CD to install Mythbuntu and rebooting I couldn't get Watch TV to work (If I clicked on it the screen would go blank for a second and then bounce me back to the main MythTV menu).

I tried to troubleshoot by checking mplayer /dev/video0 and got a message about /dev/video0 not being found.  In the terminal I went to /dev and did ls v* and there are no devices starting with video, no video0, no video1.

Next I ran lspci and this is what I got for the PVR-150 card:

"Multimedia video controller: Internext Compression Inc Unknown device"

Does anyone have any ideas about what to try next? Could it have something to do with the fact that my PVR-150 is from two years ago?

---

### Post by klc5555 on 2008-11-03
> **andyfromtucson said:**
> I have had MythTV running for a long time on a Via Epia SP8000e (C3 Eden processor) with a PVR-150 (vintage 2006) running Edgy Eft. Last night I decided to upgrade to Mythbuntu 8.04.  After using the Live CD to install Mythbuntu and rebooting I couldn't get Watch TV to work (If I clicked on it the screen would go blank for a second and then bounce me back to the main MythTV menu).

I tried to troubleshoot by checking mplayer /dev/video0 and got a message about /dev/video0 not being found.  In the terminal I went to /dev and did ls v* and there are no devices starting with video, no video0, no video1.

Next I ran lspci and this is what I got for the PVR-150 card:

"Multimedia video controller: Internext Compression Inc Unknown device"

Does anyone have any ideas about what to try next? Could it have something to do with the fact that my PVR-150 is from two years ago?

A couple of first steps:

Use synaptic to find and install the various ivtv packages for Hardy. There ought to be about four of them.

Then from a terminal sudo modprobe ivtv and see if the drivers are being found and can load. sudo lsmod  will list the installed modules.

If the ivtv firmware is installed and the modules are loaded, a PVR 150 ought to be detected and run perfectly.

Cheers! :)

---

### Post by fryed_1 on 2008-11-03
I posted up a few days ago how I got my pvr150 working with 8.04.  I think it was my first post on the forum.

---

