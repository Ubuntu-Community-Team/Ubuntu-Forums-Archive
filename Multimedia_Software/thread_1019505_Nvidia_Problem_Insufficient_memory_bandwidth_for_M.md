---
title: "Nvidia Problem: Insufficient memory bandwidth for MetaMode."
date: 2008-12-23
forum: Multimedia Software
---

### Post by abisdad on 2008-12-23
Hi, Newbie trying to get going on Ubuntu 8.10 - and enjoying it so far, but one I'm stuck on is this...

I've loaded the Nvidia accelerated graphics driver (Ver 96), but when X loads, it then asks me if I want to go into low res mode (I think), view log files or trouble shoot. 

The screen is a Samsung 2053BW.

The last part of the Xorg.0.log.old (the file I see when I view the log) is here:

> (II) NVIDIA(0): NVIDIA GPU GeForce2 Integrated GPU at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.1a.01.03.02
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 Integrated GPU at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode
(WW) NVIDIA(0):     "nvidia-auto-select"; discarding.
(WW) NVIDIA(0): No valid modes for "nvidia-auto-select"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode
(WW) NVIDIA(0):     "nvidia-auto-select"; discarding.
(WW) NVIDIA(0): No valid modes for "nvidia-auto-select"; removing.
(EE) NVIDIA(0): Unable to use default mode "nvidia-auto-select".
(II) UnloadModule: "nvidia"
(II) UnloadModule: "xaa"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I've searched the Ubuntu Documentation, the Ubuntu Forums and Wiki.x.org, but I cannot find this error! (So I must be doing something wrong somewhere...)

If I use the open source driver, part of my screen is chopped off, and again, I have limited resolutions. At the moment I have 640x800 (I think), and I lose a few pixels on the LHS.

I'm fairly competent with PCs, but not too confident with the linux stuff to date...  (Also graphics card and screen both work fine under XP Pro).

What should I try now.  All suggestions gratefully received.  Thanks. Rob.

---

### Post by abisdad on 2008-12-25
[http://www.linuxquestions.org/questions/slackware-14/opengl-only-half-working...-slack-12.0-geforce4-mx-649840/](http://www.linuxquestions.org/questions/slackware-14/opengl-only-half-working...-slack-12.0-geforce4-mx-649840/)

Ah! Possible progress... :-) 

Going to try it out later...

However...

It was an interesting route to how I came across this post, and I'd like to thank the Forum in general, as this is the process I went through:  I had just checked in to see if anyone had replied as yet, got sidetracked, came across the term 'Bump' in another post, and thought "I'll try thay!", but checked the 'Official Ubuntu Code of Conduct' to make sure I wasn't breaking any webiket, and while doing that, saw one of the things that isn't allowed is to tell someone to: "Go look on google" - which then made me think "I haven't tried that, as I had assumed that it was a Ubuntu issue, and that the Ubuntu community would have come across this problem b4, but what the hell, I'll give it a try...", and that was when I found this thread via Google!  WaaaHoo!

---

