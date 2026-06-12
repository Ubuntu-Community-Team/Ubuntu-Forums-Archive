---
title: "mythbuntu frontend aspect ratio problems"
date: 2007-12-09
forum: Mythbuntu
---

### Post by d2tw4all on 2007-12-09
Hey guys, I've been using mythbuntu for a few weeks now and have everything working pretty well, a dedicated backend with multiple frontends, doing HDTV only using an HDHomerun.  I tried adding another frontend tonight which is connected to a DLP projector in my media room.  The projector's native resolution is 1024x768.  First of all, when I set the display type to LCD 1024x768 it doesn't give me that option as a resolution when I go to set it, the max is 800x600.  If I pick a higher resolution LCD display, or plug n play, I CAN set the resolution to 1024x768.  The problem is, when I'm in MythTV and play any HDTV content that's supposed to be 16:9, it's coming up full screen.  I'm not overriding the aspect ratio or anything funky so I'm not sure what it could be.  Using "w" to flip through aspect overrides merely stretches or skews the image, it still uses up the max top to bottom, where what I WANT/EXPECT is the correct aspect ratio with letterboxing at the top and bottom.  The video chipset is Intel and it's a 3ghz Pentium 4 HT with a gig of ram.  Oddly, if I set the resolution to 800x600, I DO get the correct letterboxing, the quality is just not great because of the low resolution.  Also, if I hook it up to a regular LCD monitor set to 1280x1024 it also looks correct with the letterboxing.  Anyone have any ideas, it's MADDENING!!!
Tom

---

### Post by d2tw4all on 2007-12-10
Anyone have any ideas?

---

### Post by ubnewbie2 on 2007-12-10
Is it possible that there is so much overscan that you never see the black bars, even when it's letterboxed?

---

### Post by d2tw4all on 2007-12-12
No, and actually I watched it closer and I'm not losing data top to bottom, it's stretching the widescreen all the way to the top and bottom.  I'm completely at a loss right now.
Tom

---

### Post by ubnewbie2 on 2007-12-12
All I can think of is that something is scaling the picture.  Either the video driver (I noticed some scaling options with nvidia - don't know about Intel) or the projector itself.  Since it looks correct on a normal LCD display, I'd look at the projector settings first.

---

### Post by Lester_Burnham on 2007-12-12
Hi,

Have you tried setting the aspect ratio in Mythfrontend Setup>Setup>Appearance to your TV ratio. I think that's where it  is.

Lester

---

