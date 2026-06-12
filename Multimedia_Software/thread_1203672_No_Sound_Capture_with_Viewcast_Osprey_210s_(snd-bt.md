---
title: "No Sound Capture with Viewcast Osprey 210s (snd-bt87x) on Ubuntu 9.04"
date: 2009-07-03
forum: Multimedia Software
---

### Post by codenexus2004 on 2009-07-03
I have a Linux machine with two Viewcast Osprey 210 PCI cards installed.
These correctly register to the system using lspci and I've successfully captured video and vbi data from the card using the bttv driver.

I have yet to successfully capture audio using the snd-bt87x driver, either directly from the device files with arecord or through something like gstreamer.    Both cards have been set to 100% volume with alsamixer, and the TV Tuner device is selected as the appropriate input (per advice from a Viewcast tech).  

I have tried both the digital and analog interfaces to the card; the actual audio is connected through each 210's breakout dongle, and the source is tested and known to work, as are the cards (on Windows).

I've tested this against the stock kernel and also against a 2.6.30 kernel I built myself, with no luck.
I have tested removing the bttv driver and loading only snd-bt87x with no luck.
I have configured my main sound card as an alias to snd-slot-0, and the ospreys to 1 and 2.

In my trials, programs like arecord will work, but an empty wav file gets created.

Anyone else out there having similar problems, or perhaps have been through this before?

---

### Post by codenexus2004 on 2009-07-10
I'm not out of the woods by a long shot, but I do have audio coming through the cards.

This was accomplished by using the following module options:

options bttv card=89 bttv_gpio=1 gpiomask=0x000302 audioall=0xFFFCFD

0x000302 seems to set the cards to spit out 44100 hz,
which is apparently the default for snd-bt87x.

just to be safe, I did include the additional options, although this setting only seems to get to my first osprey
card, not the 2nd.  Since this is the default for these cards, its not really that problematic unless you wanted to set the cards to 32000 or 48000 audio.

options snd-bt87x digital_rate=44100

This then does give audio on hw:1,0 and hw:2,0 for me, or via /dev/dsp1 and /dev/dsp2.

Previously, these provided no output at all. (dd if=/dev/dsp1 of=/dev/dsp bs=1K would fail with an input/output error)

Hopefully this will help someone else out there trying similar things.

---

