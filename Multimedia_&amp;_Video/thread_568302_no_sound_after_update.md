---
title: "no sound after update"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by capaci on 2007-10-05
hi, i just did an update and after the update i have no sound. seconds before the update i had sound. is there any way to find out what was updated and does anyone have any suggestion what could have caused my sound to stop working? i need my sound to work so any help is appreciated. thanks.

some more details: 

i'm getting no errors that i can see. music in amarok looks like it's playing, but no sound. videos play, just with no sound. the speakers do work, i plugged them into another computer to test.

---

### Post by dabl on 2007-10-05
Probably a channel got set to "mute", if Amarok appears to be playing.  Open the ALSA mixer and look for "PCM" or "Front" or one of the other channels to be muted.

---

### Post by steven.burton on 2007-10-06
The same thing happened to me.  Around 2am last night (newfoundland time) the update-manager indicated there were updates available, so I went ahead and updated, after which I had no sound.

There was only one library marked for upgrade - however I do not know how to find out which library that was (I don't remember), or how to roll back to a previous version of that library.

Nothing is muted under the volume control.

Under System-Preferences-Sound. it indicates the device is VIA 8237 (Alsa Mixer) and everything is set to Autodetect.  None of the tests play any sounds (and there is no indication of sound being played either - the bar doesn't move)

I have had Ununtu 7.,04 since 2 days after its release and have always had sound.  My motherboard has onboard sound, and I have added a  separate sound card.  Sometimes Ubuntu recognizes the onboard sound and not the sound card, in which case plugging the speakers into the other port gets me sound - this is not the case this time..

Any suggestions for making my sound work, finding out what library I updated in the last updates, etc. would be greatly appreciated.

Thanks.


aplay -l     :

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ALS4000 [Avance Logic ALS4000], device 0: ALS4000 DSP []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by steven.burton on 2007-10-06
Oddly enough without changing any settings or anything, after a third reboot my sound is working again....

I'm not going to question it or complain, just enjoy it!

---

