---
title: "[SOLVED] Arg! I broke spdif again :("
date: 2008-07-30
forum: Multimedia Software
---

### Post by Clappy on 2008-07-30
Howdy gang,

Well, I couldn't leave well enough alone. I finally got spdif working by adding this to my .asoundrc:

pcm.!default {
       type spdif
       card 0
       device 0
}

I got the devicename from /etc/asound.names file and it worked like a charm. However, I had to do something stupid and install realplayer. Now spdif doesn't work anymore.

Here's the output from aplay -L:

ubuntu:~$ aplay -L
front:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Front speakers
surround40:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


Here's my output from aplay -l:
ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here's the error I get when I try to use aplay on the command line:

-ubuntu:~$ aplay -D default /usr/share/sounds/generic.wav 
ALSA lib pcm.c:2104:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_spdif.so


I don't see the spdif device anymore, can someone please help me? I'm totally lost here. Thanks. Let me know if you need any more info.

---

### Post by Clappy on 2008-08-02
Nevermind, the problem was that my optical cable came loose. Let this be a lesson kids, check the basics before you start messing with things you don't fully understand and having to reinstall Ubuntu fresh because gnome won't load anymore.

---

