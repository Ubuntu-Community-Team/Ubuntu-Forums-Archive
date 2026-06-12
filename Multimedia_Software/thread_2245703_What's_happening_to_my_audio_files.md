---
title: "What's happening to my audio files?"
date: 2014-09-25
forum: Multimedia Software
---

### Post by fizikz on 2014-09-25
I have audio files that I know used to play fine (I'm usually using clementine v1.2.3) but now have small gaps/discontinuities in the audio, and at times cause the player to give an error (like "could not decode stream") and completely jump to the next track. I tried using a different player (VLC v2.1.4) and in this particular instance the gap in audio was still there but it did not skip the track or stop playing. This specific file is a FLAC if that makes any difference.

Over time, the number of audio files in my collection exhibiting these issues is growing. What's going on and can it be fixed?

---

### Post by Rob Sayer on 2014-09-26
My first impulse would be to increase the buffer size in clementine.

---

### Post by fizikz on 2014-09-27
I increased the buffer from 1000ms to 3000ms. It helped a little bit, i.e. reduced the number of skips but didn't get rid of them. Strangely what did help was rebooting the system. Some tracks that used to skip no longer do so. I should have kept a full list of all tracks that had issues. I usually only reboot for kernel updates so I often have an uptime of 20-30 days. Towards the end I start getting a lot of swapping but it's still strange that some tracks would consistently skip and have errors at certain points after buffering.

---

### Post by Yellow Pasque on 2014-09-27
Make sure smartmontools package is installed and check the SMART data of your hard disk:
```
sudo apt-get install smartmontools
smartctl -a /dev/sda  #assuming your hard disk is /dev/sda
```

---

### Post by Yellow Pasque on 2014-09-27
Another possibility would be to check the files with flac:
```
flac -t filename.flac
```

---

