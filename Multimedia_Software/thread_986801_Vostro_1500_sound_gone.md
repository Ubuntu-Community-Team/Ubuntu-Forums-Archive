---
title: "Vostro 1500 sound gone"
date: 2008-11-18
forum: Multimedia Software
---

### Post by Nitrosyncretic on 2008-11-18
Ubuntu 8.10 just loaded onto my Dell Vostro laptop. Sound worked when I played one format of video, then I tried to run an mpg and the system offered to install something. I let it and now the sound does not work on anything. 

I've followed the instructions in Comprehensive Multimedia & Video Howto sticky and was successful in getting codecs, but still no sound.

I've gotten into Sticky: Comprehensive Sound Problem Solutions Guide but am stumped finding my sound driver. Here's what lspci -v gave me (I think)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio
Controller (rev 02)

From alsa I got the idea that snd-hda-intel should work so I ran, 

 sudo modprobe snd-hda-intel

After that though, still no sound!

What am I missing?

---

### Post by Nitrosyncretic on 2008-11-20
I could really use some help. I'm stumped.

---

### Post by psyke83 on 2008-11-20
It could be a very simple problem: your PCM mixer.

Ensure the level is high and the mixer isn't muted:
```
$ alsamixer -Dhw
```

Also note that Intrepid uses PulseAudio by default. Look [here]("http://ubuntuforums.org/showthread.php?t=789578") for a comprehensive guide, and Appendix A is devoted to troubleshooting. I recommend you take the time to learn about PulseAudio.

---

### Post by Nitrosyncretic on 2008-12-04
I realized I had not followed all of the steps in the [sticky]multimedia global solutions thread. I went back and finished the instructions and ta da! I have sound now.

---

### Post by jago25_98 on 2009-02-07
Nitro, is [this]("http://ubuntuforums.org/showthread.php?t=766683") the thread you mean?

What did you do to fix the sound problem?

Thanks

(I got crackly sound with Alsa, but OSS output is ok. Same soundcard as you)

---

