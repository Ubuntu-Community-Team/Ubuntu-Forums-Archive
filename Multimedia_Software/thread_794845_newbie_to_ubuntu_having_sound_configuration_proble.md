---
title: "newbie to ubuntu having sound configuration problems"
date: 2008-05-15
forum: Multimedia Software
---

### Post by torsui on 2008-05-15
hi,

just installed ubuntu 8.04 on a dell inspiron 9100 laptop today and besides fun with the wireless, it's not been going too badly -- save for my sound.

my master audio channel isn't -- that is, nothing i do to the settings on that channel affects the sound, whereas fiddling with the headphone and PCM channels adjusts the sound in varying ways. headphones seems to affect the treble, but i'm not sure. the volume buttons located above my keyboard affect the master control, but as previously stated, the master control doesn't actually affect the sound. ^^;

my list of playback devices is as follows:

card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

help? i'm trying to get this computer set up for my non-native-english-speaking mother before i leave, and it's been like the blind leading the blind. ^_^;

---

### Post by Metaljaz on 2008-05-16
Try this:
right click on the volume control button on the top right hand corner of the screen
select preferences and make sure that you have selected the Intel ICH5 (Alsa Mixer) then scroll down and select PCM. 
Then double click on the same volume button top right hand corner. Now select file, then select change device and make sure that the Intel ICH5 (Alsa Mixer) is selected.
Next go to System>Preferences>Sound. Select your device as the Intel ICH5(Alsa Mixer) and PCM. This should allow your volume control on the keyboard to control your volume. You can put the other items on autodetect but set the sound capture to Alsa.

---

