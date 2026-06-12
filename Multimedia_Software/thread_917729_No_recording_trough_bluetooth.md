---
title: "No recording trough bluetooth"
date: 2008-09-12
forum: Multimedia Software
---

### Post by mash-bb on 2008-09-12
I can't record sound trough bluetooth headset. Playback works. I'm using bluetooth-alsa, and I have configured my headphones trough alsa by using asoundrc like this:
pcm.bluetooth {
   type bluetooth
   device MA:CA:DR:ES:HE:RE
}

if I trie to record by 

arecord -Dplug:bluetooth -f S16_LE test.wav

arecord returns

Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono

but nothing actually gets recorted in the test.wav. It is always just 2,1 K, no mather how long have I been recording.

if I do

arecord -D bluetooth -f S16_LE test.wav

arecord returns 

Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
Warning: rate is not accurate (requested = 8000Hz, got = 16000Hz)
         please, try the plug plugin (-Dplug:bluetooth)

and the resulting test.wav is always under 1 K

recording doesn't work in skype either, so problem is not with arecord.

EDIT:
It seams, that the headset can provide two types of services, one with microphone and one with out. If the first thing I do after I start the headset is recording, it starts to record. But if I try listening something with the headset I can't record anything after that. However, in skype I would need to both listen and record. How can I do this? (This works fine on windows vista)

---

### Post by qubit67 on 2008-10-10
I am still having this same problem, i keep getitng a rate error when using the arecord command. Aplay plays the recording like alvin and the squirrels, and skype wont work at all.

---

### Post by kwha on 2008-11-21
I'm getting the same error and no recording...

Marius

---

