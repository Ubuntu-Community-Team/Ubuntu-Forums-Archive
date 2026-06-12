---
title: "A few VDPAU glitches"
date: 2010-03-28
forum: Mythbuntu
---

### Post by itlarson on 2010-03-28
By following the tweaks described in this wiki: [http://www.mythtv.org/wiki/VDPAU]("http://www.mythtv.org/wiki/VDPAU") I have gotten fairly acceptable playback from my motherboard's 8300 graphics.  There are several glitchs though.  

-If I alt-tab to a different app during playback, it's window will not be written  over by the frontend when I switch back.  I will be able to control the frontend (fastforward, etc) but the image of the other window remains on the screen untill I exit playback.

-Playback stutters for a few seconds after starting playback, or skipping ahead/back.  OSD fade is turned off.

-Most anoyingly: the mouse pointer (which normaly is hidden in the frontend) appears when playback starts.  It can't be moved during playback.  To get rid of it I have to exit playback, move the (now invisible) mouse pointer off the edge of the screen, and restart playback.

I don't know if this effects anything, but I have set up the frontend to switch from 720p to 1080p when I start playback.  I have tried the 195 driver, but it had no effect.  I am now back to 185.  

Can anything be done about these glitches?  Or is this the best I can do with my current hardware?  Has anyone else seen something similar?  Are these bugs I should report?

---

### Post by itlarson on 2010-04-03
I did find a workaround for the mouse pointer issue.  If you set it to "visible" It can at least be moved off the screen without stopping playback.

---

### Post by geekyhawkes on 2010-04-04
Which of the tweaks did you apply from the myth website?  Also, what playback settings are you using (i have the same hardware but am still getting the odd artifact with temporal x2 or x1 HW selected). 

Thanks.

---

### Post by itlarson on 2010-04-04
I get juddery playback from both temporal deinterlacers for 1080i source material.  Could you tell me what your output resolution and video source are?  Mine are 1080p and over the air ATSC.  Also could you describe the artifact?

My  setup is as follows---

I added the following new section to xorg:
 Section "Extensions"
   Option "Composite" "Disabled"
 EndSection

Also, I added the following to the "Devices" section:
Option	"TripleBuffer"	 "True"

I also set the amount of memory allocated for video to 512mb in BIOS.

In Mythfrontend->Utilities/setup->Setup->TV Settings->Playback->General playback I made sure I had the following settings:
Enable OpenGL VSync
Enable Extra Audio Buffering
Disable Real-Time Priority

In Mythfrontend->Utilities/setup->Setup->TV Settings->Playback->Playback profiles I created a custom profile as follows:

Rez > 720p
VDPAU decoder, VDPAU renderer, VDPAU OSD renderer, 2 CPUs, OSD fade off.
Primary deinterlacer bob 2x, secondary deinterlacer temporal 1x
(I know Bob is being used, because as I mentioned before, temporal doesn't work)

Rez == 720p
VDPAU decoder, VDPAU renderer, VDPAU OSD renderer, 2 CPUs, OSD fade off.
Primary deinterlacer advanced 2x, secondary deinterlacer advanced 1x
(I don't know if the deinterlacer is doing anything here)

Rez > 720p
VDPAU decoder, VDPAU renderer, VDPAU OSD renderer, 2 CPUs, OSD fade off.
Primary deinterlacer advanced 2x, secondary deinterlacer advanced 1x
(Makes 480i almost watchable)

I now notice that I can get rid of the initial juddering I get playing 1080i material by using the linear deinterlace.  This only lasts a few seconds, though,  so I am tolerating it for bob's reduced motion blur.


I am considering installing a passively cooled gt-210 card which MSI makes.  It supports the VDPAU "C" feature set, not just the "A" feature set my current graphics allow. But first I need to replace one of my PCI tuners with a PCI express tuner to allow for the heatsink on the MSI card.

---

### Post by geekyhawkes on 2010-04-06
Having read around a fair bit i think nvidia have id the problem within their driver (which is good news).  Read the thread here

[http://www.nvnews.net/vbulletin/showthread.php?t=123095](http://www.nvnews.net/vbulletin/showthread.php?t=123095)
[http://www.nvnews.net/vbulletin/showthread.php?t=125037](http://www.nvnews.net/vbulletin/showthread.php?t=125037)

I have tried all the tweaks but no luck, il just have to wait until nvidia sort out the vdpau a settings in the drivers for my card.

---

