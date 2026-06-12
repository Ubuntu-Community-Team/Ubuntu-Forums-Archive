---
title: "Hauppauge HVR 1800 and tv viewing"
date: 2010-03-26
forum: Multimedia Software
---

### Post by zanophol on 2010-03-26
I picked up an HVR 1800 off of ebay to replace my WinTV 150. I am only interested in watching live TV, as I have an AT&T Uverse box sitting on my desk with a cable coax out. The analog tuner only needs to see channel 3, and then I control the channels via the Uverse box. The digital input does not work for this.

This setup worked fine for my WinTV 150. The only problem is that when I would work with virtual machines AND watch tv, I sometimes experience lockups: hence, the move to a newer PCIE card.

I have the drivers loading fine in Kubuntu 9.10 with kernel 2.6.31-20. Under Windows 7, the card works fine with sound and video, but under linux with tvtime, only the video works. If I use vlc (or mplayer) with the pvr output like I used to, only the sound works. It seems there are two outputs: dev/video0 and dev/video1, but neither produces BOTH sound and video.

Has anyone else run into this? If so, how did you fix it?

---

