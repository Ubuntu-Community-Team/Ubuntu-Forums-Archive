---
title: "Gamma correction does not work with xvideo using Openchrome drivers"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by ropers on 2007-10-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152377](https://bugs.launchpad.net/ubuntu/+bug/152377) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am running Ubuntu 7.04 with the Openchrome video drivers ( [http://www.openchrome.org/](http://www.openchrome.org/) ). I have configured my xorg.conf to set a gamma correction of 1.7. The gamma adjustment works fine in X, but does not work with any application using xvideo, aka xv, aka the X video extension ( [http://en.wikipedia.org/wiki/X_video_extension](http://en.wikipedia.org/wiki/X_video_extension) ) to overlay graphics and thus render them directly on the screen. 

This means that if I try to watch videos with VLC or Totem Media Player, these videos are too dark (while the rest of the desktop is bright). Weirdly, this problem persists even if I deactivate "Overlay video output" in VLC's Settings - Preferences - Video. This could mean that VLCs option to deactivate overlay video output doesn't work, or there is something else going on. 
However, if I explicitly select VLC Settings - Preferences - Video - Output modules - Advanced options - Video output module: X11 video output, then the Gamma correction works properly. If I select Video output module:: Default or XVideo extionsion video output, then the Gamma correction does not work on the video.

I used to be able to watch properly Gamma-adjusted videos with another graphics chipset (Sis630) and the same 1.700 Gamma settings in my xorg.conf. Can anyone running the Openchrome driver confirm this problem? My graphics hardware is a Unichrome Pro, specifically the VIA P4M800 chipset (645 BGA).

Does anyone know how to get Gamma correction to work with XVideo?

I have submitted this as a new bug as well: 
[https://bugs.launchpad.net/ubuntu/+bug/152377](https://bugs.launchpad.net/ubuntu/+bug/152377)

---

### Post by Embryonic on 2008-01-05
I'm not sure if this will work in Ubuntu but when I use WinXP I have the same problem. The only way I've gotten around it is to open any video, pause it while its playing and open the next video, and for whatever reason the corrections on the 2nd video are there. You might try that. But like I said, not sure if it will work

---

