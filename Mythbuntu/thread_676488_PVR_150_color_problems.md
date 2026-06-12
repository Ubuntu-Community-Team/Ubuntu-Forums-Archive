---
title: "PVR 150 color problems"
date: 2008-01-23
forum: Mythbuntu
---

### Post by bcully on 2008-01-23
I've got a newish mythbuntu box built and everything mostly works well, but TV recordings have some strange color problems. Areas of the picture with a lot of red seem to bleed the red to the right about a quarter inch. I think this may also happen with solid green and blue, but the halo effect is most noticeable with red. I don't think it's TV out -- picture quality when playing videos from mplayer or vlc is terrific. But I can't decide whether it's an encoding problem or perhaps myth's internal player that's causing the error. I haven't had much luck googling for the symptoms. Has anyone else seen anything like this?

Thanks!

---

### Post by ian dobson on 2008-01-24
HI,

Does the picture look OK when you use a normal monitor?

What graphic card are you using? Maybe you can play with the Hue/Intensity settings for you graphic card.

I had a small problem that white blocks/texts that smear to the right, I almost solved it by playing with the sliders in the graphic driver for Hue and Intensity. I my case I knew it was a cable problem (SVIDEO to SCART) as I measured the signal strength on the 2 signal lines (using an osciloscope) and they were above the maximal allowed signal strength.

Regards
Ian Dobson

---

### Post by jeremynd01 on 2008-11-27
I had similar problems with my PVR-150 (pictures seemed too red and the red seemed to bleed, and dark scenes had very little contrast).  However, the color was fine on online vids (e.g. youTube or hulu.com), so I figured it was the PVR-150 and not the video card.

I fixed this by using the seldom-discussed v4l2-ctl utility ([http://ivtvdriver.org/index.php/V4l2-ctl](http://ivtvdriver.org/index.php/V4l2-ctl)).

Install it with

sudo apt-get install ivtv-utils

The four parameters I toyed with were brightness, contrast, hue, and saturation.  I turned the first two up (to adjust for the darkness problem) and the second two down, like this:
v4l2-ctl -c brightness=176
v4l2-ctl -c contrast=96
v4l2-ctl -c hue=32
v4l2-ctl -c saturation=48

I eventually dropped these four lines into /etc/rc.local so they would execute at startup.  If you can get a live TV feed running, you can execute these commands in another terminal and see the effects right away, for ease in adjustment.  I also found that with MythTV, it seems to reset these on new recordings... still working on solving that.

---

### Post by ian dobson on 2008-11-27
Hi,

Have you setup the TV standard correctly in Myth-setup. On my box here in Switzerland I found that PAL-BG/europe-west gave the best results.

Regards
Ian Dobson

---

