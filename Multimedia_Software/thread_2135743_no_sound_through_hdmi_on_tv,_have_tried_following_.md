---
title: "no sound through hdmi on tv, have tried following other fixes"
date: 2013-04-15
forum: Multimedia Software
---

### Post by slgtheindividual on 2013-04-15
hdmi picture on my tv works fine but sound does not, hdmi doesn't come up on the sound or pulseaudio menu, 

sudo aplay -l

gives

```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried 

sudo alsamixer -c 0

and then unmuted S/PDIF but nothing changes (also whenever I start a new session S/PDIF is once again muted)

also tried running 

speaker-test -c 2 -r 48000 -D hw:0,3

but again nothing happened. I have intel HD graphics 4000 and an i5 processor.

Thank you in advance for any help

---

### Post by slgtheindividual on 2013-04-15
Any help would be greatly appreciated, I'm still having this problem, if you need any more information I will happily provide it, thank you.

---

### Post by e-San on 2013-04-16
open movie, play it

> pavucontrol

First tab:
select default out for your player (something with HDMI).

Third tab:
set up volume

Last tab:
check if there is everything ok

Regards!

edit. this topic might be very useful if it is a case: [http://askubuntu.com/questions/69820/how-do-i-set-a-pulseaudio-card-profile-persistently-across-reboots](http://askubuntu.com/questions/69820/how-do-i-set-a-pulseaudio-card-profile-persistently-across-reboots)

---

### Post by slgtheindividual on 2013-04-16
nothing with HDMI appears anywhere on any tab in pulse audio, even when playing video, all that appears are speakers (which alters the laptop speakers) and headphones, no hdmi or tv speakers.

---

### Post by slgtheindividual on 2013-04-19
I have since upgraded to 13.04 raring ringtail and I'm still having this problem, any help would be greatly appreciated

---

### Post by slgtheindividual on 2013-04-21
please? anybody?

---

### Post by slgtheindividual on 2013-05-06
the following solved my problem [http://ubuntuforums.org/showthread.php?t=2141858](http://ubuntuforums.org/showthread.php?t=2141858)

---

