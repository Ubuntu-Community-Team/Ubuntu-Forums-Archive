---
title: "No Sound with Intel card"
date: 2010-05-02
forum: Multimedia Software
---

### Post by puzzler995 on 2010-05-02
I am running Ubuntu 10.04 with an Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller, and no sound output. I have both pulseaudio and ALSA installed. I have already checked with 
```
alsamixer
```that my sound isnt muted and aplay -l outputs this
```
 xxxx@xxxx-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```but no avail.
Thank You for any help
Puzzler995

---

### Post by cprofitt on 2010-05-02
> **puzzler995 said:**
> I am running Ubuntu 10.04 with an Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller, and no sound output. I have both pulseaudio and ALSA installed. I have already checked with 
```
alsamixer
```that my sound isnt muted and aplay -l outputs this
```
 xxxx@xxxx-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```but no avail.
Thank You for any help
Puzzler995

I had to kill pulseaudio and restart it... then mine worked... still not sure what that did... and it stayed fixed after several reboots.

[PHP]
killall pulseaudio && pulseaudio
[/PHP]

If not I can post some links to troubleshooting some other items.

---

### Post by puzzler995 on 2010-05-02
no luck :(

---

### Post by TBABill on 2010-05-02
Do you have no sound at all or just no sound from speakers? Did you try headphones to confirm? I had a problem where my HP TouchSmart IQ804t had no sound from the internal speakers, but the headphones worked great. Mine was also Intel HDA sound. My sound troubleshooting path is here: [http://ubuntuforums.org/showthread.php?t=1467307](http://ubuntuforums.org/showthread.php?t=1467307)

User Lidex has assisted many users with sound problems. A search of posts by Lidex within the forum may give you some great info to help you troubleshoot.

---

### Post by puzzler995 on 2010-05-02
no sound from the headphones eather.

---

