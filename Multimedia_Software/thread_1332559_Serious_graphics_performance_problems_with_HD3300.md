---
title: "Serious graphics performance problems with HD3300"
date: 2009-11-20
forum: Multimedia Software
---

### Post by bgenc on 2009-11-20
I have an  onboard HD3300 graphics card. I know 
that this card is not a top-notch high tech device, 
but I roughly get 100fps in glxgears!! Compiz is 
totally sluggish, flash lags, videos stutter. My 10 
year old graphics card could do much better than 
this. I am using ATI's proprietary drivers and I 
can't believe these drivers are this bad. There must 
be something else which is wrong. Please give me a 
hint on fixing this thing.

---

### Post by xzero1 on 2009-11-20
I have used the 3300IGP with _Jaunty_ with little issues. Check my post for ideas.
[URL="http://ubuntuforums.org/showthread.php?t=1224509"]
http://ubuntuforums.org/showthread.php?t=1224509[/URL]

---

### Post by bgenc on 2009-11-21
> **xzero1 said:**
> I have used the 3300IGP with _Jaunty_ with little issues. Check my post for ideas.
[URL="http://ubuntuforums.org/showthread.php?t=1224509"]
http://ubuntuforums.org/showthread.php?t=1224509[/URL]

Thank you, this helped a bit. Compiz benchmark still 
gives me around 22 fps, glxgears is about 300 fps now. 
The changes mostly helped with full screen video 
performance. Flash is still slow. Screensavers are 
still horrible.

---

### Post by SR_ELPIRATA on 2009-11-23
My onboard HD3300 works great! and I'm just using the default Restricted Driver for 9.04. I havent made any FPS tests with this card (not sure how to) but had it working with Compiz and worked great.

Video performance is top notch even with hi-def files up to 1080p. Flash also works great on this end. I dont like screensavers so I havent tested this either. The only reason I use 9.04 instead of 9.10 (which also worked great video wise) is that I was having bad audio noises with the onboard audio whereas audio works great in both 8.10 and 9.04 (well, with 720p/1080p HD stuff... I get a noise every 10secs but other than that is all well here).

ELP

---

### Post by bgenc on 2009-11-24
> **SR_ELPIRATA said:**
> My onboard HD3300 works great! and I'm just using the default Restricted Driver for 9.04. I havent made any FPS tests with this card (not sure how to) but had it working with Compiz and worked great.

Video performance is top notch even with hi-def files up to 1080p. Flash also works great on this end. I dont like screensavers so I havent tested this either. The only reason I use 9.04 instead of 9.10 (which also worked great video wise) is that I was having bad audio noises with the onboard audio whereas audio works great in both 8.10 and 9.04 (well, with 720p/1080p HD stuff... I get a noise every 10secs but other than that is all well here).

ELP

Do your motherboard has a sideport memory for the chip? I have 128mb onboard memory dedicated to the video card. I am starting to suspect that this may be the source of the problem. Maybe the driver doesn't know how to handle the sideport memory properly.

---

### Post by SR_ELPIRATA on 2009-11-24
Yes, it has sideport. I have it configured to use the 128MB sideport plus 256mb shared, so if you're using just the 128... and you have more memory available... consider adding some ram like I did.

BTW, did the glxgears test and.... 1000fps :D

As I said before, all my MP4 1080p demos run great, no frames lost.

Ah, and about the noise I was having every 10 secs, it was an issue with VLC. I installed XBMC Media Center and it played all my HD files without audio problems. I would really recommend geting it, its working great.

---

