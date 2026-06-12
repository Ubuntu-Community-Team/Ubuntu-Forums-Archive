---
title: "Unable to hear sound in Ubuntu 9.04"
date: 2009-07-05
forum: Multimedia Software
---

### Post by Ajit Wadekar on 2009-07-05
I am not able to hear sound in ubuntu 9.04, I have Intex PCI 3D sound card
it works fine in windows.

Do I need to install separate driver for it?

Please help So I dont wanna go to windows to just hear sound

---

### Post by wwuster on 2009-07-05
My sound was working fine, but I just rebooted after a few days of updates and now only hear a little static. 9.04. How can I get the sound back?

William

---

### Post by fleasbaby on 2009-07-05
Hi Guys,

Take a look here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am a complete newbie, but managed to fix the sound on my HP dv4 1120 us usinf the directions given.

---

### Post by arnoldjames on 2009-07-05
You may find it useful to run 'alsamixer' in a console.  You can then see if 'playback' settings are too low, and raise then up.  You have to navigate with a mixture of tabs and arrow keys.  And take notes of what the settings were and what you have tried, so you can 'undo' what you have changed if that doesn't fix the problem.

---

### Post by Ajit Wadekar on 2009-07-12
I have checked the settings, but still I am not able to sound at all,
I had on board sound chip but it suddenly stopped working so I have
installed sound card of Intex PCI,but I didn't seem to produce sound in ubuntu 
I am using ubuntu 9.10 ( Karmic Koalo ) pre release  
For the command aplay -l , I am attaching output of my sound hardware.

Can any one pleas help

**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

