---
title: "Poor Video on  Hauppauge HVR-1250"
date: 2011-11-25
forum: Mythbuntu
---

### Post by miscbs on 2011-11-25
Hi,

I have been using Mythbuntu 10.04 for a while and thought it was time for an upgrade. 

I bought a new HDD and started on a fresh 11.10 install. Everything seems to setup just fine except the HD channels on my HVR-1250 cards looks terrible. The video is smooth and does not pause or block - it just has nasty vertical lines in it. SD channels on the HVR-1250s look fine. 

It does not appear to be a signal issue since I am on cable and HD looks great on the same hardware when I boot to my 10.04 Mythbuntu HDD.

Any ideas?

Thanks
Darrell

---

### Post by nickrout on 2011-11-26
Yes, make sure you are not using a libmpeg2 playback method.

---

### Post by RideMan on 2011-11-28
What kind of video card do you have?  If you've got an NVIDIA video chipset, try one of the VDPAU settings.  The relevant setting is on Page 3 of:

Utilities/Setup -> Setup -> TV settings -> Playback

To verify that the problem is with your playback settings and not your tuner, hunt down one of the recordings and play it with VLC, you'll probably find it looks great.

--Dave Althoff, Jr.

---

### Post by beilman on 2011-12-03
Thank You! I was having the exact same problem.  Vertical lines in the HD channels only. I have Mythbuntu 11.10, a Hauppauge HVR 1250, and nVidia G210 video card (asus variety).  Changed the Myth tuner card settings as described in the previous post and it solved the problem (note which resolution you are changing the codec for however, 1080-720).  I thought it was my antenna.  This post saved me the hassle of going through all that headache only to find it wasn't the problem.

---

### Post by gabeheim on 2012-03-10
Wanted to add the comment that this was the only post on the Internet that helped me resolve my issue. After setting playback profile to VDPAU, HD video works flawlessly. Additionally, a certain SD video that would cause mythfrontend to crash no longer does so. Is there a way to pin this post/reply or add it to a community page?

Thanks

---

