---
title: "several audio/hardware questions"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by andale on 2008-01-13
I am using an Ensoniq 5880 sound card, VIA Technologies, Inc. VT8363/8365 for onboard, and the SOCOM headset for the playstation.
1) I seem to have issues controlling what sound goes where, not that I don't like where it is, but I can't figure out how to get it to change if i *should* want it to.
2) Can only 1 device make audio on ALSA or OSS?
3) I don't seem to be able to tell what device to use what (ALSA/OSS)
4) Been trying to find info on installing my Ensoniq card, which works, but I believe would work better with real drivers, not just pluggin it in.
5) I don't remember what five was. Do you?
6) Is it just me or does Last Exit not output any audio?
7) Just noting this in case it's related. Volume Monitor doesn't work. says to run 'esd' in error message. Did. Still says to do it in error window.
8) Volume controls work and I can access everything fine.

---

### Post by andale on 2008-01-13
i see a lot of views occuring, but no replies, so i'll say this, i'm not looking to resolve everything, i am really just interested in installing a driver for the ensoniq to see if it improves my day.

---

### Post by Legendário on 2008-05-02
Your driver is already installed, or the card wouldn't be working. If you type ```
lsmod | grep snd
``` on terminal you will see the sound drivers loaded to your system

---

