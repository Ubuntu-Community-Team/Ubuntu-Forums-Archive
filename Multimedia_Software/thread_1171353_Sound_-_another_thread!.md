---
title: "Sound - another thread!"
date: 2009-05-27
forum: Multimedia Software
---

### Post by redenex on 2009-05-27
Okay guys, here is ONE MORE sound issue thread.

I know that there are various threads in here with solutions. But ironically since the past two months I am without sound on my laptop.

I am using 64 bit on my TX 1005 AU (HP Lap Top), and I tried installing32 bit version yesterday in the hope of recovering sound, but no it didn't. I reinstalled 64 bit version now and surprisingly, after almost more than 2 months without sound, the songs were playing (You Tube) and Pidgin was making sounds as well. But my joy was short lived, the only mistake I did was to INCREASE the volume using the volume control icon!!!!

Any guidance how to recover my sound? At least this time, I am hopeful in doing the right things.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by redenex on 2009-05-27
All right, sound works perfect till I increase the volume control till 89%, but after 90% it cuts itself off!!! :confused:


Another issue is that, if I play a song from my hard disk and simultaneously open a youtube video, the sound stops! Any guidance?

---

### Post by redenex on 2009-06-25
Interesting, I did a fresh install of Ubuntu Jaunty 64 bit, and as of today everything works out of the box, except the external speakers. I had to add a line of code in the .conf file and things rocks.

but I do have a question, right now, laptop speakers as well as the external speakers and headphones all produce sound, how to limit this? Usually when an external speaker is plugged in the lappy speakers would be turned off, and likewise when the headphones are on, the external ones should be turned off.

Ideas?

---

