---
title: "TV problems (freeze, black pic)"
date: 2008-05-26
forum: Mythbuntu
---

### Post by ~~MAINFRAIME²~~ on 2008-05-26
I have the following problems with the TV function
-not playing smoothly
-picture freezes
-black screens
-channel switching also slow

I have the "ATI accelerated graphics driver" installed.
Decoder: XvMC
Renderer: XvMC-blit
OSD: chromakey

How can I fix that?


In mythtv-setup 6. Storage directories > create live group
I can't add a directory let's say I want to add "/mnt/live/" and exit the setup tells me that it has no write access to "/mnt/live//.test"
What is the problem here?
How can I add a directory?

System:
Mythbuntu 8.04 X64
GA-MA69G-S3H (AMD690G)
AMD Sempron 64 le 1150
ATI Radeon X1250 (IGP)
2GB RAM DDR2-800
KWorld DVB-S 100
more than enough for some SDTV

I'm using a CRT monitor [1024x768] for all the testing after everything is running I want to use my PAL TV.

---

### Post by zoiks on 2008-05-27
> **~~MAINFRAIME²~~ said:**
> I have the following problems with the TV function
-not playing smoothly
-picture freezes
-black screens
-channel switching also slow

I have the "ATI accelerated graphics driver" installed.
Decoder: XvMC
Renderer: XvMC-blit
OSD: chromakey

How can I fix that?


In mythtv-setup 6. Storage directories > create live group
I can't add a directory let's say I want to add "/mnt/live/" and exit the setup tells me that it has no write access to "/mnt/live//.test"
What is the problem here?
How can I add a directory?

System:
Mythbuntu 8.04 X64
GA-MA69G-S3H (AMD690G)
AMD Sempron 64 le 1150
ATI Radeon X1250 (IGP)
2GB RAM DDR2-800
KWorld DVB-S 100
more than enough for some SDTV

I'm using a CRT monitor [1024x768] for all the testing after everything is running I want to use my PAL TV.

1) I don't know why your video is slow and choppy. WAGs: Could it be the ATI driver is clunky? Me personally I wouldn't trust a driver *from* ATI yet. CPU-intensive delinterlacing? XVMC? You shouldn't need XVMC for SD.

2) As far as your directories go, remember that the user "mythtv" needs write access to whatever directories you choose. Could make things tricky since mythtv is a non-normal user in mythbuntu. Mythtv-setup appears to check for write access when you are exiting. (I get this all the time. Just try making /mnt/live world-writable or adding mythtv to the appropriate group, etc.)

---

### Post by ~~MAINFRAIME²~~ on 2008-05-27
> 
2) As far as your directories go, remember that the user "mythtv" needs write access to whatever directories you choose. Could make things tricky since mythtv is a non-normal user in mythbuntu. Mythtv-setup appears to check for write access when you are exiting. (I get this all the time. Just try making /mnt/live world-writable or adding mythtv to the appropriate group, etc.)

With "chmod 777" it works.


> 
1) I don't know why your video is slow and choppy.

And that's the best case, normally the playback freezes or I just get a black screen and the OSD also does not disappear in most cases.

> 
WAGs: Could it be the ATI driver is clunky? Me personally I wouldn't trust a driver *from* ATI yet.

I have now disabled the ATI driver and now I only get a black screen when trying to watch TV.
Also only this driver supports 2D/3D acceleration or am I wrong?

> 
CPU-intensive delinterlacing? XVMC? You shouldn't need XVMC for SD.

I don't have any deinterlace filter selected.
What renderer would be best?
Now I have tried most of the renderer's but with no success.

I have now tried to play some avi and mkv files also not working with mythfrontend same with DVD but mplayer plays everything avi(DivX), mkv(x264), DVD and the live recordings.

The only working renderer's with mplayer are x11, gl and gl2,
the others(xv, xvidix & xvmc) throw some error(Error opening/initializing the selected video_out (-vo) device.).
Same without the ATI driver and also the gl and gl2 renderer are somewhat slow then.

---

### Post by zoiks on 2008-05-29
> **~~MAINFRAIME²~~ said:**
> I have now tried to play some avi and mkv files also not working with mythfrontend same with DVD but mplayer plays everything avi(DivX), mkv(x264), DVD and the live recordings.

The only working renderer's with mplayer are x11, gl and gl2,
the others(xv, xvidix & xvmc) throw some error(Error opening/initializing the selected video_out (-vo) device.).
Same without the ATI driver and also the gl and gl2 renderer are somewhat slow then.

Boy, I wish I could help you here, hopefully someone else can. My limited experience with the ATI proprietary driver was that it completely broke my x.org, so I dumped it. But I would have expected xv to work even with the OS drivers. I personally have only played around with xvmc (on nvidia) and decided it wasn't for me (black & white OSD, only works with mpeg2, etc). I would focus on why xvideo isn't working - that should be a default fallback AFAIK.

That probably doesn't help much, but good luck!

---

