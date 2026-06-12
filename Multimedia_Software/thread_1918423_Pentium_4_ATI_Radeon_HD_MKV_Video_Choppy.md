---
title: "Pentium 4 ATI Radeon HD MKV Video Choppy"
date: 2012-01-31
forum: Multimedia Software
---

### Post by Randy Flagg on 2012-01-31
I am sure this has been discussed at length but I am having choppy video when playing back mkv files.  I have been searching the forums for hours and tried a bunch of different things but nothing seems to work.

I am running a Pentium 4 3.4ghz, with 1 gig Ram, and a ATI Radeon HD 6750 vid card.

Ubuntu is 11.10 and I manually upgrade to the 12.1 latest AMD drivers.  I also disbled the vsync and detect refresh rate in CCSM.

Can anyone offer any help?

Thanks.

---

### Post by SeijiSensei on 2012-02-01
If you're trying to play 720p/1080p video encoded with H.264, your hardware is probably unable to decode the stream fast enough.  The simplest and cheapest solution is to replace that ATI video card with an [NVIDIA card]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Order=PRICE&PageSize=20") that supports "VDPAU," NVIDIA's method for decoding H.264 in hardware.  mplayer has a driver for VDPAU; I use **smplayer** to wrap mplayer in a nice GUI.

---

### Post by Randy Flagg on 2012-02-01
I have have seen that as one resolution but I would like to try and get this working with the ATI card.  I came to the realization that I am not using hardware acceleration and that is the issue.

So, I installed VAAPI this morning and try it with VLC but it just shuts down VLC when I try and play a video.  I haven't even tried it in XBMC yet.

---

