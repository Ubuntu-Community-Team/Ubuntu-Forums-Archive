---
title: "Soundcard is not fully recognized (stuck on the troubleshooting procedure)"
date: 2012-10-01
forum: Multimedia Software
---

### Post by Shaq88 on 2012-10-01
Hi,

I'm trying to understand what exactly is the problem, but not so sure.
I&#8217;m using Ubuntu 11.10 (Kernel 3.0.0-26), and stuck on the troubleshooting procedure.
When using the command: **aplay -l**
It gives the following output: **aplay: device_list:240: no soundcards found...**
So I go to Procedure Ac (Make the system/ALSA recognize the sound card), and everything seem to be fine there, so I'm a little bit stuck.

Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)

Not sure what to do now... Appreciate your help!

---

### Post by Shaq88 on 2012-10-02
UP! please help!

---

### Post by jerrrys on 2012-10-02
The first link has a possible fix

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+Corporation+82801I&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+Corporation+82801I&as_qdr=all&sa=Google+Search&lang=en)

good luck

---

### Post by Shaq88 on 2012-10-04
Didn't work for me, any other ideas?

---

### Post by Yellow Pasque on 2012-10-04
Provide ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Linux sees the physical sound devices, but something goes wrong when loading the driver.

---

