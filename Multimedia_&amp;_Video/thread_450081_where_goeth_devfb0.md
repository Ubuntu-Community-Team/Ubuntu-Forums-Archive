---
title: "where goeth /dev/fb0 ?"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by glenndavy on 2007-05-20
hi 
decided I was weary of trying to get fglrx to work, and to revert to fbdev, where at least I can set my resolutions to what I want, and get xinerama - less than I like, but all I need to actually get somework done... when I do /dev/fb0 no longer exists,  (*,)  so I cant start X with fbdev - ive searched and noticed a few others in similar results, but havent got any joy from those threads.

any one know what kernel module causes /dev/fb0 to be created? or is there a udev rule that needs writing? or.....????

grateful for any input.]

---

### Post by dawynn on 2007-09-27
* bump *

I'm now getting a similar problem with my machine.  Had been doing fine running non-Gutsy (read: Edgy / Feisty) kernels in Gutsy (still waiting for a Gutsy kernel that works).  But within the past week or so, after more upgrades, I'm now getting the following messages in Xorg.0.log when I try to run one of the older kernels:

(WW) open /dev/fb0: No such file or directory
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)

Any suggestions as to a package I could try to revert to an older version?

---

### Post by kerryhall on 2007-12-16
Bump. I am trying to do some framebuffer programming, (yes, I know about SDL and svgalib) and I have no idea how to set up /dev/fb0. Do I have to compile the kernel? Thanks!

---

