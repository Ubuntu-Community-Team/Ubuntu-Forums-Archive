---
title: "VLC plays AVI sound but no picture"
date: 2012-03-30
forum: Multimedia Software
---

### Post by Orinoco on 2012-03-30
VLC no longer shows pictures when playing video files, but the sound still comes through loud and clear. The files work fine when played with VLC on a Windows box. Banchee has the same problem playing video files: sound is fine, no picture. Files are avi, and they worked a few days ago. 

I have removed and reinstalled VLC player. No change. 
System Info:
Ubuntu 11.10
2.0 Gib memory
Pentium Dual CPU
GeForce 8400 GS/PCI/SSE2
32 bit
Driver: GeForce 8400 GS/PCI/SSE2
Displays setting shows unknown monitor with 1600 x 900 resolution, detect displays doesn't seem to do anything. The actual display is LG Flatron W2053 TQ.

---

### Post by papibe on 2012-03-30
Hi Orinoco.

Could you post the codecs the avis have?
You can do that by coping what it says in 'Tools -> Codec Information' while playing the video.

Also, are you using video acceleration (Tools -> Preferences and Input & Codecs -> GPU acceleration)?
Have you tried changing that settings? (it requires restart VLC)

Regards.

---

### Post by anmatr on 2012-08-23
Hi, 
 I have the same problem with same ubuntu version.

The codec details are:
MPEG-4 Video (XVID)
Resolution: 576x320
Frame rate: 23.976000

The movie is visible for about 9 minutes and then it goes black. Restart of vlc does no good, still shows black video but sound is good.

The details could not be retrieved by the Tools -> ... as you described. In Ubuntu VLC they are under Interface -> Codec Information or (CTRL-J).

Thanks.

---

