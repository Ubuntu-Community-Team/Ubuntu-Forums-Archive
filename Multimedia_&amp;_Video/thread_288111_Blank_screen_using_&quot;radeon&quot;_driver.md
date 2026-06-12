---
title: "Blank screen using &quot;radeon&quot; driver"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by pertheusual on 2006-10-29
My problems started when I tried to boot from the liveCD, so I knew this was going to be trouble. 

When I booted from the CD, it would finish the Ubuntu loading screen and then a slight flicker for X loading, but then it would just stay blank. I couldn't shift to terminal with ctrl+alt+f1, but the system itself was starting alright because I heard the sound and could shut it down properly by pressing power and waiting for a minute or so.

Anyway, I installed from the alternate disk and it worked fine, but now I'm trying to get the 'radeon' driver working again.

Any Suggestions?


Also, could someone confirm for me that the 'radeon' drivers are usable with AIGLX?
I'm trying to get my dual monitor setup working with XGL or AIGLX but obviously I can't use the 'fglrx' driver for that because both monitors are 1280x1024 and BigDesktop Sucks.

Thanks much.

---

### Post by qamelian on 2006-10-29
The radeon drivers do work with AIGLX. This is how I'm running Beryl on my laptop. The FGLRX drivers refuse to work even though the Docs from ATI say they support my card.

---

### Post by pertheusual on 2006-10-29
Cool, thanks for confirming. 

Any suggestions for my problems with the 'radeon' driver?

My card is a Radeon 9800XT.

I am pretty sure that the R360 line is at least sort of supported by this now, so I'm not really sure what's up. 

Could I need to disable or enable something in the xorg.conf?

---

### Post by pertheusual on 2006-10-29
Ok. So the radeon driver seems to work alright when I have 

Section "Device"
    .....
	Option	"BusType" "PCI"
EndSection

I've been working with AIGLX to try to get beryl working, but when I start it, I get:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

And I noticed in my Xorg log 

*** Direct rendering support is highly experimental for Radeon 9500
*** and newer cards. The 3d mesa driver is not provided in this tree.
*** A very experimental (and incomplete) version is available from Mesa CVS.
*** Additional information can be found on [http://r300.sourceforge.net](http://r300.sourceforge.net)
*** This message has been last modified on 2005-08-07.

glxinfo says:

name of display: :0.0
display: :0  screen: 0
direct rendering: No

Has anyone gotten DRI functioning on a 9800XT?
Would you point me in the right direction for trying the mesa 3d drivers?

Is that what is causing the Beryl problems?

Thanks much.

---

