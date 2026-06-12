---
title: "3x Monitor, Nvidia v-card, how to set default monitor?"
date: 2009-02-11
forum: Multimedia Software
---

### Post by cigoldab on 2009-02-11
Hey guys, ive been be tryin for a few days to look it up but i all the info i've tracked down hasnt really applied to my scenario..

first, some quick specs, im runnin' 8.10 x64, 9800 GX2 video card w/ 169.12 drivers...

On gpu0 i've got a 22" monitor via dvi, and a 40" hdtv via hdmi, on gpu1 i've got another 22" monitor via dvi

(currently running as 3x X-Screens using Nvidia Xserver)

whenever I boot, my bios defaults to Monitor1 on GPU0, the "Ubuntu" loading bar also shows on Monitor1 (this is the display i'd like to have setup as my main display), however for some reason X-server has decided that the 40" hdtv should be main, and my notification area as well as auto-launching programs and screenlets all default to the TV... (weirder yet, when I xfer files from disk to disk, the "transferring files..." box defaults to Monitor1...

AND! to make things stranger, as per X-server, the monitors are listed as such:

40" HDTV: X-Screen 0 (but, DFP 0 on GPU 0)
22" GPU0: X-Screen 2 (but, DFP 1 on GPU 0)
22" GPU1: X-Screen 1 (but, DFP 0 on GPU 1)



please help me figure out how to change the "default Monitor"!!!

---

