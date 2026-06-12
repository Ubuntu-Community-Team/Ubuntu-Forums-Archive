---
title: "No sound in Skype or Youtub"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Torgeir on 2007-11-04
Updated to 7.10, and everything working perfect, but 2 days ago no sound in Skyoe nor at youtube.com were present. Everything else work, VLC, Mplayer, etc. 

I'm using the internal soundcard ICH6 in my Dell Latitude D610, but I can't find any solution on this issue - :(.

aplay -l shows as follows:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


Have reinstalled Skype and flash plugin for Firefox, but nothing happen. 

Any Ideas?

Torgeir
- 95% happy

---

### Post by cchevy on 2007-11-05
I had the same problem, but I fixed the audio in YouTube videos. 

Right now, I only want to make the sound on my Skype 1.4 to work

Everything else is perfect

Anyone?

I have sound on every application, except Skype...

---

### Post by hofsmo on 2007-11-05
Try:
> asoundconf list 
**list of sound cards**

asoundconf set-default-card **name of sound card**

---

### Post by cchevy on 2007-11-05
I fixed it. It was pulseaudio... removed it

but after this preview of mp3's doest work quite well like with PA. u have to highlite a song...

---

### Post by cchevy on 2007-11-06
this is unbelievable...now i have a problem with the flash

when i play flash(youtube) in ffox i cant play audio in mplayer or amarok.

i reinstalled the latest flash and nothing...

mplayer says : *The audio device is busy. Is another application using it? *

amarok says: [I]Audio output unavailable; the device is busy.
xine parameters: [/I]

if i get over this without having to reinstall the whole system, i will be a very happy ubuntu user.

---

### Post by SnowPunk98 on 2008-07-18
Also have the same youtube with no sound issue on a Latitude D830.

---

