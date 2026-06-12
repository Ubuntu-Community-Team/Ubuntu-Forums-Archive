---
title: "Lost Sound on BE machine"
date: 2013-07-11
forum: Mythbuntu
---

### Post by gga96 on 2013-07-11
Hi All,

I installed Kdenline on the BE machine to see what it was all about. Several days later I found that the myth FE on the the same machine had lost all sound volume and mute control. 

Having read [http://www.mythtv.org/wiki/configuring_Digital_Sound](http://www.mythtv.org/wiki/configuring_Digital_Sound) "Basics" I tested mythbuntu desktop and found no sound at all.  I suspected Kdenline so I removed it from the system but no improvement. The quote "For MythTV installations it is advisable to turn off any sound servers that sit on top of ALSA such as Pulse Audio or the KDE or Gnome sound servers." prompted an effort to remove additional sound servers, but I could not find any to remove. To date I have not been able to restore sound.

So far I have looked at the following:
> 
glen@backend-1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

File /etc/asound.conf is blank.

"alsamixer" F6 lists "0 HDA Intel" and the program echos "Chip: Anolog Devices AD1884A" with no mention of the digital card/device 0/1. The un-muted alsamixer channels are Master, PCM, Mic, S/PDIF, Beep and Mono.

Help.  What do I do to restore the system?

Thanks for any help offered.
Glen

---

### Post by BicyclerBoy on 2013-07-12
use the fe setup/audio settings to scan/test your audio devices.
Try to select an alsa device.
The KDE app might have pulled in pulse audio. I don't find it causes any trouble.

---

### Post by gga96 on 2013-07-12
Thanks.
I had tried and have just tried again to get a response using FE setup/audio. No luck.
Is it significant that alsamixer does not show a reference to the intel digital card/device 0/1?
What system hardware tests are available?
Glen

---

### Post by gga96 on 2013-07-18
Could not get audio working.
I chose to re-install, audio is fine but I am now having trouble with EPG data.
This thread is CLOSED and I will start a new thread re EPG.

---

