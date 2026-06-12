---
title: "hooking up to samsung 40' tv"
date: 2013-02-19
forum: Multimedia Software
---

### Post by gordie69 on 2013-02-19
Hey guys I'm hooking my small computer desktop to my 40' Samsung lcd tv and was wonddering how to get sound from tv speakers I've ran my hdmi cord from video card to hdmi port on tv and thought I'd could use tv speakers but didn't work unless there's settings in sound but haven't found them yet

---

### Post by efflandt on 2013-02-19
First see what shows up for Output in your sound settings when HDMI is connected, and whether selecting Digital Output (S/PDIF) works.  That may depend what video card/chip and which video drivers you are using.

Also see what audio devices are listed in the output of **aplay -l** (small L or capital L).

Normally I use analog stereo with a 2.1 speaker system. But when recently using wireless headphones/headset, and I had that set to digital instead of analog, I was quite surprised that sound switched to my HDTV speakers when I unplugged the wireless dongle instead of to my analog speakers. The reason I was surprised is that I thought that I am using a DVI to HDMI cable (maybe a pin on DVI can be used for digital audio).

---

