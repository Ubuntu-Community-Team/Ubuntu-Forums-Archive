---
title: "Problem with Labtec USB Speakers"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by Redorb1790 on 2006-11-28
Hi Ubuntu members! I just made the jump from windows to Ubuntu and so far Ive been problem free except for the sound issue I am having right now. I just plugged up a pair of Labtec USB Speakers and in the Sound Preferences window that pops up I select the sound playback to be USB audio. Now I pressed the test sound button and it worked but when I actually start playing mp3 files, movies, and the like no sound comes out of my speakers. I am using Edgy Efft.

---

### Post by ozmont on 2007-11-29
I don't know if anyone has run into this before but there is a trick to it (suprise, suprise)

Go to your synaptic and load xmms as a sound device, when you go into the preferences in there you will see and option to configure the alsa settings. In the device list will be your labtec speakers, select them as the device.

Now test the playback in xmms, if it is OK go back and look at the preferences. Odds are it will read something like hw:1,0

this is a key to getting everything working. now go to your xine engine (preferably in master of the universe mode)set the audio driver from auto to als,  and set the output devices for audio mono and stereo to the hw:1.0 value.

You may need to repeat this for other multimedia apps, bui it does work, I am listening to my labtec USBs as I type.

good luck
:guitar:

---

