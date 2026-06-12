---
title: "[SOLVED] No Sound"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by abhilash82 on 2007-09-23
I have been using Ubuntu Feisty for last 2 months and have no problems with it. It worked seamlessly with my hardware and I didn't have to install any extra drivers. 
But my problem started today.. suddenly I am not getting anything out of my sound output (or mic) and I tried fiddling with the ALSA mixer settings and still no sound output. My sound works fine on my dual boot Windows XP. Do i have to upgrade any drivers?

i have given the output of my detected sound card.

```
aplay -l
```

> **** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**My System spec.:**
Intel 865GBF motherboard with on-board sound.
Intel 2.4GHz HT with 256 MB RAM.

---

### Post by scrooge_74 on 2007-09-23
Strange, check again on alsamixer(either from the GUI or the command line)  that the jack sense is not off

---

### Post by abhilash82 on 2007-09-23
No it is not off. I have checked the entire ALSA mixer settings and still no result.

---

### Post by abhilash82 on 2007-10-01
Can anyone help meout with the audio configuration files so that I can zero in on the problem? I have tried all settings with ALSA mixer. It was working perfectly fine and suddenly one fine day I have this problem.
:confused:

---

### Post by NotoriousTF on 2007-10-01
I've just had this problem too. All was working perfectly last night, and today its just gone. Booting on XP shows that there is no problems with the sound at all on the other side. Anyone out there have any ideas? 
Other threads out there have been solved by re-installing the OS, but surely that isn't the only solution...:(

```
aplay -l
```

> **** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by rzrgenesys187 on 2007-10-01
I read somewhere about a guy who was having the problem but when he booted up xp and unmuted the volume in xp it worked in linux?  I'm looking for the article right now

EDIT: [http://ubuntuforums.org/showthread.php?t=561576&highlight=xp+sound+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=xp+sound+solved)

---

### Post by NotoriousTF on 2007-10-01
Ok so after getting home from college and booting for the million-th time its working fine for me. Very strange.....

---

### Post by abhilash82 on 2007-10-01
Does it have any relation with the kernel build version?
I am also using a dual boot with winxp. I don't understand how an OS in a completely different filesystem/partition can affect the settings of Ubuntu?

---

### Post by donfletcher on 2007-10-02
If a hardware device like a speaker system is muted, it will stay muted until unmuted, either by some startup task or manual intervention.

If then unix is not unmuting the device, but one goes back to an OS that does unmute it, then the device will stay unmuted until muted again.

Is that how this works?

---

### Post by abhilash82 on 2007-10-02
My sound works now!!!
I removed the Headphone jack sense option in the Volume control menu.
Ihope this works for others having the same problem also!!!

:guitar:

---

