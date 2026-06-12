---
title: "VNC Screen Sharing and nVidia Drivers"
date: 2010-02-04
forum: Multimedia Software
---

### Post by dlfuller on 2010-02-04
I have a laptop and desktop both with basic installations of 9.10 (Karmic). And, they are networked with a Mac running OS X 10.6.2. Screen sharing simply worked right from the beginning, to and from the Mac, and of course to and from both Ubuntu installs.

Except there was no feedback from one Ubuntu desktop screen being shared. Mouse clicks, mouse movements, and keyboard presses all seemed to have their correct effects. It was just that the results were not fed back to the remote screen.

During troubleshooting, I de-activated (removed) the nVidia accelerated graphics driver (version 185) that had been installed with 9.10 (Karmic). Then screen sharing started to work with the proper feedback to the remote screen. 

I tried the pre-upgrade nVidia driver (version 173) and again no feedback from the screen being shared. De-activate the driver and again screen sharing started to work with feedback.

The bottom line seems to be no nVidia proprietary drivers if I want remote screen sharing to work. But this desktop  is primarily used as a HTPC with a HDTV monitor. No games. No 3D. Screen sharing is probably more important, but essentially what am I giving up in graphics capabilities by not using those nVidia drivers? 

I'd appreciate any comments or suggestions to troubleshoot this oddity.

---

### Post by rushrtb2112 on 2010-03-05
I am having the same issue happen with and install of 9.04 and the nvidia 1.80 drivers.  Does anyone have any idea how to fix this?

---

### Post by Cr0n_J0b on 2010-04-15
This has been happening to me since the start of 9.10.  I just loaded the Beta 2 for 10.04 and it's still an issue.

Frustrating.

---

