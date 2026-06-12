---
title: "Sound does not work in Ubuntu 14.04 LTS"
date: 2014-06-20
forum: Multimedia Software
---

### Post by MrinalSinghania on 2014-06-20
Hi All,

I'm having a problem with my sound. 
When I log-out of ubuntu, I'm able to hear the system sound (logout drum). 
However, even a single sound does not play while I'm logged in.

I have tried adding the following string in /etc/modprobe.d/alsa-base.conf:
"options snd-hda-intel model=3stack"

Details are as under:
    Codec: SigmaTel STAC9221 A2

$ sudo cat /proc/asound/pcm
00-00: STAC9221 A2 Analog : STAC9221 A2 Analog : playback 1 : capture 1
00-01: STAC9221 A2 Digital : STAC9221 A2 Digital : playback 1
00-02: STAC9221 A2 Alt Analog : STAC9221 A2 Alt Analog : capture 1

Settings are in attachments.


Thanks,
Mrinal

---

### Post by Yellow Pasque on 2014-06-20
Please give the alsa info. It will give the info in the screenshots (and a lot more) in an easier to read format: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by MrinalSinghania on 2014-06-20
Hi Temujin,
  Thanks for replying.
  My alsa-info is located at :  [http://www.alsa-project.org/db/?f=094abe8cd7da2690f7bc6470b4a00a479084e46f](http://www.alsa-project.org/db/?f=094abe8cd7da2690f7bc6470b4a00a479084e46f)

Thanks,
Mrinal

---

### Post by Yellow Pasque on 2014-06-20
> 
!!ALSA Version
!!------------

Driver version:     k3.13.0-29-generic
Library version:    **1.0.25**
Utilities version:  1.0.27.2

That's an incorrect version of libasound2 (it should also be 1.0.27.2). Was this a fresh install or an upgrade? Have you done anything that might have installed an old version?
```
apt-cache policy libasound2
```

---

### Post by MrinalSinghania on 2014-06-20
Hi Temujin,
  I tried removing and and re-installed the drivers again as mentioned in the troubleshooting guide ([https://help.ubuntu.com/community/SoundTroubleshooting):](https://help.ubuntu.com/community/SoundTroubleshooting):)
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
$ apt-cache policy libasound2
libasound2:
  Installed: 1.0.27.2-3ubuntu7
  Candidate: 1.0.27.2-3ubuntu7
  Version table:
 *** 1.0.27.2-3ubuntu7 0
        500 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status

Thanks,
Mrinal

---

### Post by Yellow Pasque on 2014-06-20
Was this a fresh install or an upgrade? Have you done anything that might have installed an old version of libasound?

---

### Post by MrinalSinghania on 2014-06-21
It is a fresh install, after which sound was working for a while. While listening to music the sound stopped in the middle and never came back.
To debug, I tried following the troubleshooting guide mentioned above and re-installed my driver, which may have installed a previous version of asound.

Thanks!

---

### Post by MrinalSinghania on 2014-06-23
Strange..
Sound came the same way as it went - By Itself !!

Cheers!!

---

