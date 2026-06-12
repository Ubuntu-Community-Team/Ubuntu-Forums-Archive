---
title: "Flash in firefox kill audio or crashes firefox issues on Kubuntu 9.04"
date: 2009-08-08
forum: Multimedia Software
---

### Post by Braeden2 on 2009-08-08
I recently installed kubuntu 9.04 on my dell vostro 1510, aside from some easy to fix problems regarding wireless / dual monitors everything has been pretty painless.... Bar one thing. Flash playback in browser.

I have tried remedies from the Sticky:    "Comprehensive Sound Problem Solutions Guide" and other forum posts to no avail.

Audio will play from amarok / dragon player fine from boot. The issue arises when a flash file is played in firefox. 

If amarok or a video player are open, paused or not, and a flash movie (youtube etc.) is played in firefox the flash movie will have no audio and firefox will crash after a few seconds. 

If the flash file is played first in firefox and an audio or video file is opened after, the flash file plays with sound and the other plays without sound. Firefox does not crash. No audio will then play in amarok / video player until firefox has been exited.

Perhaps of note are the following: 

Firefox ver. 3.0.13
Shockwave flash add-on ver. 10.0 r32

Audio's lspci -v:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 0273                        
        Flags: bus master, fast devsel, latency 0, IRQ 22           
        Memory at f8300000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: HDA Intel                               
        Kernel modules: snd-hda-intel


Any help with this would be appreciated.

---

### Post by Braeden2 on 2009-08-08
Small update on the problem:

When I played a video file in dragon player and then opened a youtube clip in konqueror (rather than firefox) it played with no audio and the video disappeared leaving a white space in the webpage. 

I then navigated to a different video. It played with no audio, then video disappeared as well. This time however an error dialog appeared:

A Fatal Error Occurred
The application nspluginviewer (nspluginviewer) crashed and caused the signal 6 (SIGABRT).

Konquerer does not crash when flash dies, unlike firefox. 

What if anything can I try to remedy flash playback? If any more info is needed to troubleshoot this, by all means just ask, this is the last nagging thing I need to fix to be wholly happy with my kubuntu install.

Thanks,

Braeden

---

### Post by malkeink on 2009-08-08
You are not alone. I have the same problem and will therefore watch this thread closely.
Hope someone can help :)

Kind regards

---

### Post by Braeden2 on 2009-08-11
Has no-one any advice?

Is working flash a lost cause with my setup? If so, is it my audio hardware, graphics hardware, OS choice, browser, flash plugin?

Can anyone let me know of an alternative setup that would work with my hardware?

---

