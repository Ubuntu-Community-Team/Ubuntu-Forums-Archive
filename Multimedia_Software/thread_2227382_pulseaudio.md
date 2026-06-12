---
title: "pulseaudio"
date: 2014-06-01
forum: Multimedia Software
---

### Post by 0536g007ve on 2014-06-01
I have the indication of audio from looking at pulseaudio volume control,output device because the bars at the bottom move when YouTube plays a video.
I have been looking for weeks, please help me find my sound on ubuntu 12.04.  I purged it some weeks ago and have been putting the parts back together that purge goofed up and can not seem to fix the final part.

robin@robin-HP-G62-Notebook-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
robin@robin-HP-G62-Notebook-PC:~$ 

I think I found a problem, take a look, let me know what you think. Thanks for your help
speaker-test 1.0.25


Playback device is surround51:Live
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Live'

---

### Post by Yellow Pasque on 2014-06-02
Was/Is there another card (like a SoundBlaster 'Live') in the machine?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by 0536g007ve on 2014-06-02
Thanks for your help.  I think I only have one card.  Here is the info.
[http://www.alsa-project.org/db/?f=1ac4aa3b9de2015c3776516ad0bf23bd4030c50d](http://www.alsa-project.org/db/?f=1ac4aa3b9de2015c3776516ad0bf23bd4030c50d)

---

### Post by 0536g007ve on 2014-06-02
cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xd4400000 irq 44

---

### Post by Yellow Pasque on 2014-06-02
```
!!ALSA Version
!!------------

Driver version:     k3.8.0-41-generic
Library version:    1.0.16
Utilities version:  1.0.25
```

Wow, the ALSA lib version is ancient. You must have installed an old version. If you're lucky, this will fix it:
```
sudo apt-get install --reinstall libasound2
```

EDIT: I also see you have made some customizations in /etc/modprobe.d/alsa-base.conf that you probably want to remove
```
snd-hda-intel: model=generic
snd-hda-intel: probe_mask=0xff
snd-hda-intel: probe_mask=0xff
```

---

### Post by 0536g007ve on 2014-06-02
I did this ([COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall libasound2)
How do I remove the customizations?[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-06-02
> **0536g007ve said:**
> How do I remove the customizations?

It depends on how you added them. Most likely, you edited /etc/modprobe.d/alsa-base.conf (or added a new file in /etc/modprobe.d).

This may help:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by 0536g007ve on 2014-06-02
Yes it helped, thanks.  After the edit I rebooted and audio is working now.  Thanks, I hope as I learn more I can be the help some day.

---

