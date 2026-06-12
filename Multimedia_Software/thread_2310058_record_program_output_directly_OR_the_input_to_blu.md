---
title: "record program output directly OR the input to bluetooth dongle - NOT soundcard out"
date: 2016-01-15
forum: Multimedia Software
---

### Post by Dreamer Fithp Apprentice on 2016-01-15
Working with a Gateway laptop. Internal sound"card" on the mobo is apparently bad because:
-built in speakers just put out white noise
-plugging earphones in gets the same noise
-recording output of "soundcard" is the same noise

BUT, bluetooth headset works fine.

Been beating my head against the wall all day trying to figure out how to record the same stream that is going out a usb port, through a bluetooth transciever to a  bluetooth headset. Most every technique I read about just gets the noise. I've installed stuff left and right. Grecord just created a gigantic directory with so much in it it makes thunar hang trying to read it. The only way I could tell anything about it was to do df and see how many gb of disk space had disappeared. So I gave up on reading it and am just deleting it, but even that is causing thunar to choke, despite using 1.3 gb of my RAM & most of my cpu (saith lxtask) & the "file operation progress" has been going on for about 15 minutes now and bogging down my system the whole time. (Journaling makes deleting large files such a pain, I swear I'm honestly thinking about going back to  ext2 or even FAT32.)  So I'm kinda reluctant to use grecord again. When thunar lets me have some cpu back, I'll uninstall it.

Anyway, could anyone suggest some reasonably easy way to do this, short of buying a new computer, or installing another OS?

---

### Post by Dreamer Fithp Apprentice on 2016-01-15
I'm not sure what I did that fixed this, but it is working now. I re-installed some of my sound and bluetooth programs, maybe that was it. Anyway this works fine:```
arecord -f S16_LE -c1 -r 192000 out.wav

```

---

