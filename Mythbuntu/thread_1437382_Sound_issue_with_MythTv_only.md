---
title: "Sound issue with MythTv only"
date: 2010-03-23
forum: Mythbuntu
---

### Post by guilly on 2010-03-23
Has anyone had an issue where your sound works fine except for when using mythtv? I installed ubuntu 9.10 with mythtv packages and my sound works fine except for if I used mythtv.

my board is a GA-MA78GM-US2H and I'm using the HDMI output with ATI proprietary drivers.

---

### Post by My Name on 2010-03-24
in the settings/general pages in mythtv there are options for setting which audio output to use, try flicking through a few of the options there. i think there should be an option for HDMI. I don't use it but I'm sure I've seen it there.

---

### Post by AKADAP on 2010-03-24
If you are attempting to get audio pass through working (TOSLINK to receiver to get surround), I usually have to run "sudo /etc/init.d/alsa-utils restart" every time before I get sound out.

---

### Post by guilly on 2010-03-24
Strange either of your suggestions seem to work, I've tried setting audio:hdmi in general tabs but with no luck.

---

