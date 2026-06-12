---
title: "Edgy, Audacity, Fast Track USB"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by uncle vernon on 2006-12-17
Hi,

I am trying to use an M-Audio FastTrack USB interface to record audio into Audacity.  The device works in other apps, I can hear system sounds through it, etc.  However, Audacity can neither record nor play through it.

Here's some info:

caseyd@*****-galore:~$ ls /dev/dsp*
/dev/dsp  /dev/dsp3

caseyd@*****-galore:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Not sure what else might be relevant, except that the preferences in Audacity will not let me select /dev/dsp3, it's set on /dev/dsp with no other options.  Any ideas?

---

### Post by funkythumb on 2007-08-18
I'm trying to do the same with Feisty. M-Audio Fastrack is recognized, Testing through System>Preferences>Sounds is successful, but can't get Audacity to record or play through Fast Track.

Did you ever find a solution?

---

