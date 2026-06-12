---
title: "How do I &quot;wake up&quot; /dev/video1 (Easycap DC 60)?"
date: 2012-03-23
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2012-03-23
I am using an Easycap DC60 adapter to input composite video to my PC. I use an mplayer command to view the input. The easycap is assigned /dev/video1 on boot due to built in webcam being on /dev/video0. /dev/video1 is there and easycap shows up in dmesg prior to running the command.

Command:
```
mplayer tv:// -tv driver=v4l2:norm=NTSC_M_JP:output=0:device=/dev/video1 -vo xv -fs
```

At first run of the command, I just get a green screen which won't allow me to simply "Esc" out of, I have to kill mplayer. On second run, I get a flash of green and then the output is displayed as expected. This is the case for subsequent uses in that session.

Can anyone advise of a way to "wake up" easycap or /dev/video1, so I can write a small script to activate my video input. Yes, I could run the command, kill it, then run it again, but wondering if there is a better way?

Alternatively, how do I test that mplayer has successfully delivered video to the screen, to avoid a restart?

---

### Post by Jose Catre-Vandis on 2012-04-02
bump anyone ?

---

### Post by BicyclerBoy on 2012-04-02
Maybe v4lctl

[http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing](http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing)

---

### Post by Jose Catre-Vandis on 2012-04-03
Hmmm, points to doing some kind of test with xawtv. Is it possible to do a test with mplayer using -vo dummy or similar?

---

### Post by BicyclerBoy on 2012-04-03
I would try to set/refresh the Easyap settings with 
dov4l
v4lctl

maybe these will wake the device & it will then work immediately.

---

### Post by Jose Catre-Vandis on 2012-04-04
I'll give it a go and report back, thanks for your input.

---

### Post by jmlm-1970 on 2012-10-06
I have the internal webcam has /dev/video0 and Easycap has /dev/video1, and no wake up is necessary, I just installed VLC (a video application) from "Ubuntu Software Center", and then start "VLC" and from menu "Media/Open Capture Device" dialog switch "Capture Mode" to "Video for Linux 2" and choose "/dev/video1" and hit "play" button...

---

