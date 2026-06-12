---
title: "Do Big Screens demand more from Graphics Cards?"
date: 2009-03-06
forum: Multimedia Software
---

### Post by bilijoe on 2009-03-06
I have been having minor, but irritating troubles with my display for some time now. I'm running Ubuntu 8.10 on a DELL Optiplex GX270 with a 2.88GHz Hyper threading Pentium 4, 4Gb RAM (only 3.5Gb of which is recognised by the P4). At times, when scrolling through a long document, web page, folder with lots of files, etc., the response to any method of scrolling is very sluggish. Sometimes, the scroll will actually stop altogether for a second or 3. 

The peoblem seems to be a little more pronounced when using the mouse wheel than it is when using the scroll bar. I've had this problem under 7.10, 8.04, and now 8.10. It's worse if I turn on the System>Preferences>Appearance>Visual Effects, but occurs even when those are turned off. I had been running with the on-board video untill recently, when I came by a used NVIDA GeForce FX5500 D 256M (from a friend who was upgrading, so I know the card hasn't ben abused). I rather expected the new card to solve the problem, but it made almost no difference.

So now, I come around to wondering about the only item left in the chain--the Monitor. I have an HP w2408, 24" flat, widescreen monitor; a beautiful, bright, crisp, huge screen. 

So my question, for whatever guru[s] out there understand these things much better than I, is "Do Big monitors put more of a load on the video card than 'average sized' monitors?" In other words, in order to get Compiz to work (it works now, but is extremely sluggish, and often turns the screen Black and White, and stalls for up to 15 or 20 seconds), and to get away from the frustration of sometimes having to watch a screen scroll line, by line, by line... do I need yet a heftier video card? Can anyone recommend a good one--one they've used with a big screen and found to work well? Or is there something else in the system that may be causing this problem that I am not considering?

Any help, suggestions, pointers to salient articles or other postings, etc., will be greatly appreciated.

---

### Post by yther on 2009-03-06
It's not the physical size of the screen that counts, but the resolution.  640×480 is going to stress your video card (and system memory, etc.) a lot less than 1600×1200, for example, because (just multiply it to prove) there are lots more dots involved.  If you're running your big screen at a high resolution, it could be that your graphics card doesn't have enough memory to do it well.

Have you tried lower resolutions or color depths to see if the problem gets better or goes away?  Also you might try changing to/from the proprietary graphics drivers and see what happens.

---

### Post by Jubward on 2009-03-06
I don't think it could be your monitor, I've never heard of a computer being sluggish from how big its screen is. Have you tried turning off everything possible that has anything to do with effects/animations and see if it solves the problem?

---

### Post by bilijoe on 2009-03-06
> **yther said:**
> It's not the physical size of the screen that counts, but the resolution.  640×480 is going to stress your video card (and system memory, etc.) a lot less than 1600×1200, for example, because (just multiply it to prove) there are lots more dots involved.  If you're running your big screen at a high resolution, it could be that your graphics card doesn't have enough memory to do it well.

Have you tried lower resolutions or color depths to see if the problem gets better or goes away?  Also you might try changing to/from the proprietary graphics drivers and see what happens.
Ive been running at 1920 x 1200. according to my figures, that's about 2,250Mpix, at a color depth of 24 bits per pixel (I only sort of--barely know what I'm doing here, so please bear with me, as my math may be stupid). According to my calculations (?) this results in 54Mb per screen, which means the 256Mb of memory on the graphics card can hold just 4.75 frames, which, at 60 fps, resolves to only about .08 seconds. Am I right in how I figured this out? And, am I right in thinking that, with 3-D graphics, etc., .08 seconds of "lead time" is not nearly enough?

To run this screen at the current resolution and color depth, how much video memory would you recommend? I have 4Gb RAM installed, but the P4 I am running is only a 32-bit chip, and so only recognizes about 3.5Gb. Is there any way to use that dangling half-Gig of memory for the Video processor?

Many thanks for your previous response. It made sense and helped me understand better, what might be going on here.:popcorn:

---

### Post by questioning on 2009-03-06
> **bilijoe said:**
> Ive been running at 1920 x 1200. according to my figures, that's about 2,250Mpix, at a color depth of 24 bits per pixel (I only sort of--barely know what I'm doing here, so please bear with me, as my math may be stupid). According to my calculations (?) this results in 54Mb per screen, which means the 256Mb of memory on the graphics card can hold just 4.75 frames, which, at 60 fps, resolves to only about .08 seconds. Am I right in how I figured this out?



no you are not right, 256mb ram are plenty enough, also with effects turned on.. gaming at 1920x1200 on the other hand would seriously suck ;)

you got a problem with your driver, thats all. try some of the newer nvidia beta drivers.

---

