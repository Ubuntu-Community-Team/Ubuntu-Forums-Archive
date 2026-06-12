---
title: "only AC3/DTS working"
date: 2008-11-29
forum: Multimedia Software
---

### Post by IndieRockSteve on 2008-11-29
This all worked when I initially installed, then after one of the dist-upgrades this problem started occuring.

I use SPDIF output to my receiver, AC3/DTS and MPEG audio all work over SPDIF but trying to play anything with MP3 or AAC audio fails and I get:

Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = -1, can_write = 4096, errno = 22 (Invalid argument)
This might be a sound hardware/driver specific problem (see aRts FAQ)

I tried updating to the latest packages and removing the .pulse folder as I read in one of the other threads in the closed 8.10 development forum but no go.

anyone have any ideas or how I can further troubleshoot this?

thanks!

---

### Post by eleniontolto on 2008-12-01
I'm not sure if the error i get is the same, but I have teh same problem with ac3 files only playing.  I'm also using an onboard digital (optical) output to a receiver.  There's no startup sound or system/navigational sounds.  The only audio i've managed to get it to put out has been ac3 audio embedded in movies.  I'm not using mythbuntu like you though, i'm on ubuntu intrepid.  Everything worked fine until I went home for the weekend and came back, and now it does this.

---

### Post by CarloMagno on 2009-01-17
I have exactly the same problem.. after playing media with DD (AC3) tracks the sound icons in my amplifier vanish, as if there were no sound from Ubuntu. After that I can play DD tracks, but no other sound (mp3s or system sound) is working. I have a Gigabyte board with 690g northbridge and Realtec audio chip, "aplay -l" gives me the following audio devices:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I used the "cat /dev/urandom | ac3dec -R" suggested above for quite some time, but yesterday I upgraded to Intrepid and it seems that "ac3dec" has been removed from the alsa-tools package and the command no longer works.

This seems to be a looong bug in Alsa, reported in Launchpad  [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632)

The solution from Bob Sully described in the launchpad page works for me, in the terminal execute:
```
 iecset audio 1
```

Hope this problem get solved before next release..

---

