---
title: "Which video output driver for s/mplayer should I use?"
date: 2011-04-04
forum: Multimedia Software
---

### Post by sleepitoff on 2011-04-04
I always use the default "xv" video output in SMplayer, but I noticed if I watch the same video in VLC or in WMP on Win7, the quality is noticeably better in those than it is in SMplayer. 

I have an ATI Mobility Radeon HD 5470 in my notebook, and both Mplayer and Smpalyer are the latest versions from the PPAs. 

Any tips on getting better video quality playback through SMplayer?

---

### Post by andrew.46 on 2011-04-04
> **sleepitoff said:**
> I always use the default "xv" video output in SMplayer, but I noticed if I watch the same video in VLC or in WMP on Win7, the quality is noticeably better in those than it is in SMplayer. 

I guess it begs the question: what video output is being used by vlc? Best choices would be xv (I use this all the time) or any gl video out.

> I have an ATI Mobility Radeon HD 5470 in my notebook, and both Mplayer and Smpalyer are the latest versions from the PPAs. 

Just for my own personal curiosity can I ask which PPAs you are using?

---

### Post by sleepitoff on 2011-04-04
mplayer: 
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily) 

smplayer:
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer) 

and my VLC player is selected to "default" for video output driver. I'd rather use SMplayer because I prefer the interface, but maybe VLC just performs better... I don't know.

---

### Post by SeijiSensei on 2011-04-04
My guess is that the proprietary ATI video drivers for Windows are better than the drivers available for Linux.  That's why I have an NVIDIA card and use VDPAU.

Which ATI driver are you using?

---

### Post by sleepitoff on 2011-04-04
-Catalyst 10.11, driver 8.791-101026a-107895C-ATI.

edit: i should note the problem more specifically is that i see blurry lines every few moments when i'm playing a video.

---

