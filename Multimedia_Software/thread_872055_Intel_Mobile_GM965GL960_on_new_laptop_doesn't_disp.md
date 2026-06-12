---
title: "Intel Mobile GM965/GL960 on new laptop doesn't display video"
date: 2008-07-27
forum: Multimedia Software
---

### Post by mrblondeisback on 2008-07-27
I installed Ubuntu on this new laptop, it's a Gateway T series, and everything works well for the most part, but I can't play back video.  I got ever codec I could find, checked the driver, it's the newest version of xserver-xorg-video-intel, and I got vlc.  I get sound but no video.  Once, just once, it worked, but I could not repeat it.  Very frustrating.  Any suggestions?

---

### Post by leo1a0 on 2008-10-26
Hello. I have exactly the same issue. I've upgraded all drivers and still no video, only get sound. Even with DVDs.

I'll appreciate any help. Thanks

---

### Post by leo1a0 on 2008-10-27
:) Solved the problem. see [http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu) part 7. Although it was intended for different Intel driver. I followed the instructions and now everything is running fine. Actually only run the "apt-get remove xserver-xorg-video-intel" and rebooted.

---

