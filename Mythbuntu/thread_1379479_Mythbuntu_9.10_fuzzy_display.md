---
title: "Mythbuntu 9.10 fuzzy display"
date: 2010-01-12
forum: Mythbuntu
---

### Post by gwagchunks on 2010-01-12
Hi

Just testing 9.10 on my laptop, an IBM Thinkpad R51 with intel chipset. Video is all fuzzy / pixelized when watching via video manager. If I play externally with VLC, video is perfect. Any ideas on how to make the internal mythfrontend video better?

Many thanks

---

### Post by SiHa on 2010-01-13
Playback profiles?? Maybe it's defaulted to something that's not suited to your hardware.

---

### Post by gwagchunks on 2010-01-13
> **SiHa said:**
> Playback profiles?? Maybe it's defaulted to something that's not suited to your hardware.
Thanks for the reply SiHa (are you enjoying the snow?! - It's p**ing me off now!)

I tried every profile but no joy, I also went into backend setup and changed all the TV options (for PAL, PAL-I, PAL-M etc...) no luck there either. It's strange, it works fine on 9.04, and it does work like I say in 9.10 with VLC externally, so the hardware should be Ok? I was just playing with 9.10 really. I did try it on a spare HDD on my main system but had similar issues. I'll wait until the next version of mythbuntu has come out and has bedded in a bit. 

Thanks

---

### Post by SiHa on 2010-01-13
> Thanks for the reply SiHa (are you enjoying the snow?! - It's p**ing me off now!)
Had enough now, looking foward to some rain!

I just thought the profiles might be trying to do something your mobo doesn't like. If you try using some acceleration that's not supported it will generally fall back to something really bad. Maybe it's worth just setting up a new profile that works for all resolutions, then work through the available decoders.

Does the frontend log give any clues, like 'method not supported' or anything?

10.04 LTS & 0.23 is due out soon I guess.

---

### Post by gwagchunks on 2010-01-15
I tried copying the xorg.conf from my 9.04 config, but this did not work. I found this in the frontendlog:

```

2010-01-15 21:56:42.303 VideoOutputXv Error: Could not find suitable XVideo surface.
2010-01-15 21:56:42.303 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2010-01-15 21:56:42.303 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xa5037f0) visual(0xa4f6fd0) 
                        depth(24) WxH(1024x768) bpl(3072)
2010-01-15 21:56:42.305 VideoOutputXv Error: Could not find suitable XVideo surface.
2010-01-15 21:56:42.306 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***
2010-01-15 21:56:42.339 OSD Theme Dimensions W: 1280 H: 720
2010-01-15 21:56:43.291 Failed to approve 'bobdeint' deinterlacer as a software deinterlacer
2010-01-15 21:56:43.292 Couldn't load deinterlace filter 

```

I've searched around and there seems to be some results that are a bit old and go nowhere. 

Not to worry, I'll stick with 9.04 and wait to try the next release.

---

