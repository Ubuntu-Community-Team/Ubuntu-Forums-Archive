---
title: "Mplayer skipping frames &amp; Vlc audio issues"
date: 2013-09-08
forum: Multimedia Software
---

### Post by linuxyogi on 2013-09-08
Hi,
I am using 
lubuntu 13.04
Nvidia GeForce 6150SE nForce 430
NVIDIA Driver Version:304.88

Recently my PC got a bit physically damaged. The pci sound card took the direct hit & it immediately stopped responding. The PC hanged too. 

I purchased a **new sound card **

```
01:09.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
```

lubuntu detected the new card without any issues but **vlc** is acting weirdly. The audio is getting distorted. Here is vlc's messages
```

main warning: not synchronized (-122411 us), resampling
alsa warning: cannot write samples: Broken pipe
main warning: buffer way too early (-122828), clearing queue
alsa warning: cannot write samples: Broken pipe
alsa warning: cannot write samples: Broken pipe
main warning: not synchronized (-433454 us), resampling
main warning: buffer way too early (-433454), clearing queue
alsa warning: cannot write samples: Broken pipe
main warning: not synchronized (-432046 us), resampling
main warning: buffer way too early (-432046), clearing queue
main warning: not synchronized (-475470 us), resampling
main warning: computed PTS is out of range (40130), clearing out
alsa warning: cannot write samples: Broken pipe
main warning: not synchronized (-434967 us), resampling
main warning: buffer way too early (-434967), clearing queue
alsa warning: cannot write samples: Broken pipe
alsa warning: cannot write samples: Broken pipe
main warning: not synchronized (-437346 us), resampling
main warning: buffer way too early (-437346), clearing queue
main warning: not synchronized (-349274 us), resampling
alsa warning: cannot write samples: Broken pipe
main warning: buffer way too early (-349274), clearing queue
alsa warning: cannot write samples: Broken pipe
main warning: not synchronized (-435295 us), resampling
main warning: buffer way too early (-435295), clearing queue
```

A couple of days later my PC was not booting. After trying a new ram I removed my graphics card Nvidia 9500GT and the boot process completed with the help of onboard graphics (Nvidia GeForce 6150SE nForce 430).

The above mentioned integrated graphics has no vdpau capability so playing HD videos may cause video issues but while playing videos of resolution 320 by 240 I am facing frame skipping issues.

The frame skipping is occuring only in Smplayer (mplayer2). Since there is no longer vdpau support I have selected xv output.

This the mplayer log

```
Increasing filtered audio buffer size from 0 to 2048
Increasing filtered audio buffer size from 2048 to 67584
Increasing filtered audio buffer size from 67584 to 90240
A:  61.4 V:  61.2 A-V:  0.241 ct:  0.000   0/  0  2%  3%  0.5% 24 0 
Increasing filtered audio buffer size from 90240 to 90248
A:  93.9 V:  93.9 A-V:  0.000 ct:  0.000   0/  0  2%  3%  0.5% 81 0
```

---

### Post by linuxyogi on 2013-09-08
I just replaced the sound card and playback is normal now. :D

---

