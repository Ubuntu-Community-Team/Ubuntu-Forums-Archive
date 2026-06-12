---
title: "HDMI HdA Intel ICH9 familly - Silicon Image SiI1392 HDMI NO SOUND!"
date: 2008-07-13
forum: Multimedia Software
---

### Post by e_labranche on 2008-07-13
Hello Community!

Well, after DAYS of going through many, many, many threads, I need help since I can't have my sound card working.

Basically, The sound works with the green jack output behind the shuttle, but when plugin in the HDMI, I get nothing! I was able to get the screen res right, but still no sound.

here is what I get when:

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Silicon Image SiI1392 HDMI

alplay -l
carte  0: Intel [HDA Intel], périphérique 0 : ALC883 Analog [ALC883 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC883 Digital [ALC883 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

1- I have checked to see if the audio was muted (was not)
2- installed the latest drivers from alsa & libs etc(curently:alsa-driver-1.0.16)

I just don't know where to turn too!. In the sound controls, when I choose the ATI HDMI selection and press TEST, I get sound...but only in the left speaker??

I have read the most important threads about sound config and can't get things to work. "Comprehensive Sound Problem Solutions Guide"

does any one else have the same issues?

I'm running ubuntu 8.04.1

thanks for helping out.

---

### Post by cariboo on 2008-07-13
With a HDMI  the sound is transfered through the HDMi cable. HDMI stands for High Definition Multimedia Interface. If you have a spdif output I would try that.

Jim

---

### Post by e_labranche on 2008-07-13
> **cariboo907 said:**
> With a HDMI  the sound is transfered through the HDMi cable. HDMI stands for High Definition Multimedia Interface. If you have a spdif output I would try that.

Jim
Thanks cariboo907, but the way the setup is made, I need to have the HDMI sound output.
HDMI sound quality is really good, and the shuttle was built to play BLU RAY, and projected on a screen at 1080p(looks great!).

The sound works like it should with the normal jack outputs, but not with the HDMI. The investment made in it makes it normal for me to have HDMI working on it.

thanks

---

### Post by brundles on 2008-07-25
[This post](http://ubuntuforums.org/showpost.php?p=5452551&postcount=132) helped me get the audio over HDMI working for the ICH9 chipset - only problem is the left only bit which may be an unresolved ALSA bug.

---

### Post by e_labranche on 2008-07-27
> **brundles said:**
> [This post](http://ubuntuforums.org/showpost.php?p=5452551&postcount=132) helped me get the audio over HDMI working for the ICH9 chipset - only problem is the left only bit which may be an unresolved ALSA bug.

thanks for the help.

i will try out the steps that is nmentionned in the link you gave me and come back to this thread to give you the results. Thanks for the help.

---

### Post by ashgromnies on 2008-07-29
> **e_labranche said:**
> thanks for the help.

i will try out the steps that is nmentionned in the link you gave me and come back to this thread to give you the results. Thanks for the help.

You have any success? I tried his instructions and they did not work for me.

---

