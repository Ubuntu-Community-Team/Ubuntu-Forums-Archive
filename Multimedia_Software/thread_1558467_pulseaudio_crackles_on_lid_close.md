---
title: "pulseaudio crackles on lid close"
date: 2010-08-22
forum: Multimedia Software
---

### Post by nerdy_kid on 2010-08-22
Every time my screen turns off pulseaudio crackles and pops for a few seconds then resumes normal playback.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Anyone have any ideas of how to maybe fix this?
thanks

---

### Post by nerdy_kid on 2010-08-23
bump

---

### Post by nerdy_kid on 2010-08-26
oh come on! bump!

---

### Post by nerdy_kid on 2010-08-29
[http://pastebin.com/AHY3ZZZ8](http://pastebin.com/AHY3ZZZ8)

that is the pulse verbose log; anyone know what to make of it?

---

### Post by Linuxforall on 2010-08-29
[http://forum.linuxmint.com/viewtopic.php?f=48&t=36844&p=214460](http://forum.linuxmint.com/viewtopic.php?f=48&t=36844&p=214460)

---

### Post by nerdy_kid on 2010-08-30
I do have an Intel HDA card; but the power saving is already disabled:

```

$ cat sys/module/snd_hda_intel/parameters/power_save
0

```

---

