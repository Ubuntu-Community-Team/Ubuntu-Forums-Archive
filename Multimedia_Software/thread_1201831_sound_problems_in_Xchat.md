---
title: "sound problems in Xchat"
date: 2009-07-01
forum: Multimedia Software
---

### Post by anystupidname on 2009-07-01
In jaunty, for a while I wasn't getting any sound when triggering an alert that should make a sound. I gave up on it for a while and I just tested it again and now I get hissing static for the time period that the MP3 should last. I guess that is a slight improvement but there is still the problem that it doesn't play the actual sound and even the static doesn't seem to be triggered by the actual events I have selected. Only clicking the test button makes the static sound. Does anybody else have this problem? Any assistance would be appreciated!

---

### Post by james.wilde on 2009-07-06
Pretty much the same here.  Jaunty.  The signals when someone posts a chat message in pidgin or when I post an entry in the same place are drowned out by a crackling sound which lasts as long as the alert sound.

I've done a rough search on clicking problem/clicking sound, without success.  I have an idea this is a Pulse Audio problem, but I could be wrong.  Audio and video are definitely not my strong point, so if anyone could help me find a relevant thread I'd be very grateful.

//James

---

### Post by james.wilde on 2009-07-07
Guess who forgot info that could help people answer.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And lspci gives:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

//James

---

### Post by anystupidname on 2009-07-13
Guess who else... :tongue:

lspci:
> 00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)

lshw -C sound
> *-multimedia
       description: Multimedia audio controller
       product: 82801G (ICH7 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

asoundconf list
> Names of available sound cards:
ICH7

---

