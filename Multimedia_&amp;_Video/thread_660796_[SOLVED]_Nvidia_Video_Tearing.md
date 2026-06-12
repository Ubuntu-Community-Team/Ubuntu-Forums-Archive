---
title: "[SOLVED] Nvidia Video Tearing"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by hyakugojuuichi on 2008-01-07
Greetings all, I have finally signed up at the forum that has solved most of my Linux issues.

I'm sorry to say it's because I have an unsolved issue though. I have read all the threads I can find about the video tearing issue here, and nothing seems to work for me.

I am currently using the latest Nvidia proprietary driver (169.07, as installed by Envy) with an 8800 GTS 640MB, I am not currently running a composite desktop, and I am using the "sync to vblank" option in the XVideo settings. With this option turned off, I get very bad tearing. With the option **on**, the tearing appears to be gone... but only for a little while. About 1 minute later a HUGE tear appears at the bottom of the screen and slowly crawls its way up. The tear itself is about 30 pixels in height, meaning it's a very slightly diagonal line, and it also changes shape constantly. Nothing I do seems to get rid of this.

I am running a Twinview setup, 1920x1200 + 1680x1050. I have tried disabling one of the panels as I thought that maybe running at that sort of resolution was causing the problem, but the issue is still there with just one panel.

I have tried running compiz to see if video playback is any better, but I still get nasty tearing in that, although not the huge slow tear, it's more typical small tears randomly appearing all over the screen. I have tried all guides I can find for compiz, OpenGL and syncing to vblank in both, including setting the triple buffer option in xorg.conf. Absolutely nothing works.

I hope there is a fix for this - I used to have an ATI card so I'm used to issues regarding graphics hardware and drivers, but at least I could play videos without tearing on the old card. :(

---

### Post by hyakugojuuichi on 2008-01-10
Problem solved - My two monitors, strangely enough, have very slightly different refresh rates (.01Hz or less!) and the card was syncing to the wrong monitor. A quick swap around of the DVI cables and reordering of TwinView orientation and the problem is no more!

---

