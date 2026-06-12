---
title: "upgraded to 1920x1080, VDPAU, speed issues"
date: 2009-12-07
forum: Mythbuntu
---

### Post by mathog on 2009-12-07
We bought a 1080P TV so the MythTV box was shifted from the previous analog component out to DVI out at 1920x1080.  Overall this works well but there are a few picture issues to deal with.  Configuration: ASUS EN8400GS 256 MB, Mythbuntu 8.10, jyavenard's 0.21 with vdpau, ECS AMD690GM-M2 motherboard, and Athlon 64 X2 4000+ "Brisbane".

1.  Deinterlacing was set at Temporal 2X.  That worked great at 640x480 but I turned it off after going to 1920x1080 because
at the new resolution it was causing very jerky playback on video with a lot of motion.  (There was some ice skating on, and with deinterlacing on the jumps were like watching a strobe light illuminated series of stills.)  Is Deinterlacing even needed now that the video output matches the TV resolution exactly?  With it off motion through MythTV is as good as through the TV's own tuner - no jerkiness.

2.  When MythTV starts up the stage where it is precalculating background images is now annoyingly long.   Is it possible to have MythTV precalculate those backgrounds once, and store them somewhere for the next time?  Or do a faster precalculation?

3.  The menu fades are ugly now.  Instead of doing a true fade it sort of flickers from one menu to the next.  I never much cared for the fade anyway.  Is there a setting that lets it just switch from one menu to the next in one frame and be done with it?


Thanks.

---

### Post by nickrout on 2009-12-07
> **mathog said:**
> We bought a 1080P TV so the MythTV box was shifted from the previous analog component out to DVI out at 1920x1080.  Overall this works well but there are a few picture issues to deal with.  Configuration: ASUS EN8400GS 256 MB, Mythbuntu 8.10, jyavenard's 0.21 with vdpau, ECS AMD690GM-M2 motherboard, and Athlon 64 X2 4000+ "Brisbane".

1.  Deinterlacing was set at Temporal 2X.  That worked great at 640x480 but I turned it off after going to 1920x1080 because
at the new resolution it was causing very jerky playback on video with a lot of motion.  (There was some ice skating on, and with deinterlacing on the jumps were like watching a strobe light illuminated series of stills.)  Is Deinterlacing even needed now that the video output matches the TV resolution exactly?  With it off motion through MythTV is as good as through the TV's own tuner - no jerkiness.


the 8400gs is probably unable to do temporal2x at that resolution, but vdpinfo (I think thats what its called) will tell you more.> 
2.  When MythTV starts up the stage where it is precalculating background images is now annoyingly long.   Is it possible to have MythTV precalculate those backgrounds once, and store them somewhere for the next time?  Or do a faster precalculation?

It is usually cached and should only take a long time the first time you run a particular theme.
> 
3.  The menu fades are ugly now.  Instead of doing a true fade it sort of flickers from one menu to the next.  I never much cared for the fade anyway.  Is there a setting that lets it just switch from one menu to the next in one frame and be done with it?


Thanks.

---

### Post by ian dobson on 2009-12-08
Hi,

I also imagine your graphic card is not upto 1080p with temporal2x.

There's an option in MythFrontend to set the maximum cache size, maybe it's abit too small on your system.

Regards
Ian Dobson

---

### Post by mathog on 2009-12-09
> **ian dobson said:**
> 
There's an option in MythFrontend to set the maximum cache size, maybe it's abit too small on your system.


Under setup, appearances, the theme cache was 1.  Changed it to 5 and now it actually caches things.  Odd that 1 wasn't enough since only a single theme was ever used.  Perhaps it had cached some previous theme and was not able to replace it with the current one.  One issue down.

Tried converting from OpenGL to QT render.  That fixed the fade slowness, since QT just switches instantly.  Unfortunately the EPG would lock up often with QT, so it is back to OpenGL for now.  I understand the OpenGL is hardcoded to fade, but surely there is a parameter somewhere that sets the speed of the transition???

The lack of deinterlace doesn't seem to be harming the image, at least, not that I have seen so far.

Thanks.

---

### Post by nickrout on 2009-12-09
your TV is probably doing the deinterlacing.

---

### Post by matt06 on 2009-12-09
> **mathog said:**
> I understand the OpenGL is hardcoded to fade
Is it?  I could have sworn there was a fade option, but I can't seem to find it anywhere now that I'm looking for it.

Just to clarify, are you referring to OSD fade while watching content or menu/screen fades?

---

### Post by mathog on 2009-12-10
> **matt06 said:**
> 
Just to clarify, are you referring to OSD fade while watching content or menu/screen fades?

Menu to Menu fades, for instance from the start menu ("watch TV" etc.) to the setup menu.  If I had the option nothing would fade, it would either be on or off instantly.  Note that not everything fades even now.  Once one drills down far enough into the setup menu, the transitions on a "next" or "back" click are instantaneous, instead of fading to the other menu screen.

---

### Post by matt06 on 2009-12-10
I understand which fades you mean now and you are probably correct that OpenGL is coded to do fades then with no option.  When you tried with QT did you play with the any of the guide shading/fill settings (I can't remember the wording and I'm not by my box) to see if that is causing the guide to lockup?  Somewhere to look maybe.

(Just for reference I was thinking of the OSD fade option in my previous post which is located somewhere under TV, Playback Profiles)

---

