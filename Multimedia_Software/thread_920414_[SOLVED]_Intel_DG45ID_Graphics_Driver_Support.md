---
title: "[SOLVED] Intel DG45ID Graphics Driver Support"
date: 2008-09-15
forum: Multimedia Software
---

### Post by Junkieman on 2008-09-15
Hello all

Following a clean Hardy install, my resolution is stuck at 800x600. Obviously i need to install some driver support, but im not so sure how to do this.

**Technical details**
It is an Intel chipset, board model DG45ID, the [product page]("http://www.intel.com/cd/products/services/emea/eng/motherboards/392471.htm") saying it has the X4500HD onboard gfx subsystem. Anyway there are no graphics drivers for linux on the driver disk. also searched through synaptic, the problem is im not sure what to look for.

[Intel Linux Graphics]("http://www.intellinuxgraphics.org") doesn't have my chipset listed in the docmentation section either, and the intel support page doesnt have linux drivers either. i suspect i could probably use a more generic intel driver. 

i also searched the forums and closest i got was [this thread]("http://ubuntuforums.org/showthread.php?t=889323") but i didnt get any results installing the drivers found at the [mentioned package.]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/")

i will need a widescreen resolution too. can anyone give any tips what i can do before i start installing drivers im not meant to... ?

thanks!

---

### Post by josephhitt on 2008-09-20
I don't think there's a working 3D driver for this chipset yet.

If I weren't so fed up with working on this pc I'd take this half-baked-non-linux-driver-having junk back to the store and get something with NVidia (although I'm hearing the linux suport is flaky on the newer incarnations of those too).

Ho hum, such is the case with assuming anything about hardware.  Feels like the good ole days circa 1995 when I first tried to get my Matrox Millennia card working in Linux.  I had even gotten lazy in the past few years with pretty much every piece of hardware working so well... I had even let myself fall under some false assumption that manufacturers like Intel were on board with getting drivers into the kernel BEFORE dumping their junk onto the market (wrong).  For me, this board really puts the Win back in Wintel.

Great CPU (45nm quad core), runs cool... but the board is basically a Winmodem with a CPU socket.  Take it back if you still have the receipt.  Maybe I will do that after all...

Oh yeah and the sound doesn't work either. ](*,)

---

### Post by josephhitt on 2008-09-20
oh yeah forgot to mention I did get the video to go 1280x1024, but only with fedora 9 (ubuntu and other distros still would not boot with the AHCI setting mentioned in the other thread, possibly due to my particular HP SATA dvd-rw.  Even after burning ubuntu install to a DVD no dice.  But I pretty much gave up on that as fedora works with the IDE/native setting and not too worried about it as I think I can boot it from a USB key if necessary.  It's using the "vesa" driver for X.  I'm also using the DVI connection where it sounds like you are using HDMI.  Without real drivers I'm not sure how well HDMI will work though.  sound is not happening for me though.

so, to reiterate - it sounds like our options are 1) wait like 3 years for driver support to eventually appear or 2) try to get a refund..

---

### Post by Junkieman on 2008-09-22
> **josephhitt said:**
> If I weren't so fed up with working on this pc I'd take this half-baked-non-linux-driver-having junk back to the store and get something with NVidia

ditto! but i cant swap my board, at least not at this time :/ 

anyway im also using the vga adapter, and by playing with the drivers i got the res up to a high widescreen res. but now my OpenGL doesnt work :( i will just use a spare pci card for the moment until drivers arrive...

*i played around with different drivers and resolutions and found vesa 1280x1024 worked*
```
gksudo displayconfig-gtk
```

funnily enough my sound worked from the first boot. Not the front headphone jack however, the one in the back. i did install all the codecs to play media. 

This just reminds me why i got out of hardware :p but at least i have learned much in the process. at least ;)


So the conclusion is to wait for drivers...

---

### Post by josephhitt on 2008-10-07
Some more updates (for any interested DG45ID owners):

You might want to try out 8.10 beta (if you aren't bothered by occasional system crashes)  I'm up and running on Ubuntu now using the 8.10 beta and it seems to have resolved a few (but not all) issues:  

Booting From CD: I can actually boot from the CD now.  I think there was some kernel fix that was also in Fedora 9, but not in Ubuntu 8.04.  Note that I think this has to do more with my HP dvd1070 sata drive and not the DG45ID.

Network: The docs say the e1000e network driver issues are going to be resolved in the final release (woohoo, that was fast!).  When I did a system update the onboard nic showed up as eth1, so it might even be working now but I don't want to try it out of fear of frying the firmware (WARNING: apparently you can actually do that according to 8.10beta release notes) so I'll wait for the 8.10 gold release and keep my 3c905 card in there for now.

Sound:  Still no sound, but if I turn the speakers way up I can barely hear some sound.  Other people are having my same sound problem here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271519)

Like the bug submitter, I do hear some sound but it's very muffled.  One person said that a newer ALSA makes the SPDIF work - I might try that, probably has to be compiled from source as there is no apt package available for that version of ALSA yet.

Occasional Crashes:  Yes, unfortunately getting those.

Video: GL is working for me in 1280x1024 so it's possible that 8.10 fixed this either with the new kernel or some other package.  I know that GL is working by typing:
```

glxinfo | grep rendering

```
..which for me returns:
direct rendering: Yes

---

### Post by audiosteve on 2008-10-27
I'm running the DG45ID board with the latest daily build of Ubuntu 8.10 and it seems to work automatically and just fine at 1920 x 1080 through the HDMI port. eth0 also works just fine.

I have two issues left to resolve
1) Compiz will crash occasionally when switching users or windows
2) I can't get any audo out of the TOSLINK or HDMI ports. I haven't tried the analog ports.

If anyone has any pointers on solving these issues I'd love to hear from them.

BTW, the official 8.10 release is slated for 8/30 so waiting a few days rather than using a daily build could be worthwhile.

---

### Post by Junkieman on 2008-10-28
> **audiosteve said:**
> waiting a few days rather than using a daily build could be worthwhile.

yup, that's the plan and i cant wait! 

oh my audio works out of the box on the analogue ports

Update: Ubuntu 8.10 Intrepid Ibex installed without problems on my DG45ID board. Graphics Network and Sound all picked up fine.

---

