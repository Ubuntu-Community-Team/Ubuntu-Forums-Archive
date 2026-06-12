---
title: "distortion/line across screen - atv - .22-fixes - ubuntu 9.04"
date: 2009-11-01
forum: Mythbuntu
---

### Post by iitywygms on 2009-11-01
Hey all.
I am using an apple tv running ubuntu 9.04 with the latest .22-fixes build.
Since the last few updates, not sure when it changed, I get a thin line of blinking white dots across the whole screen when watching live tv or recordings.  It does not appear on the main menu screens.
I have to run standard xvmc for playback as the apple tv is low powered.  If I change the playback profile decoders to other modes, the blinking dots do not appear, but of course playback stutters.
Anyone have any idea what this might be, or how I can go about hunting down the problem?

---

### Post by yonkiman on 2009-11-02
> **iitywygms said:**
> I get a thin line of blinking white dots across the whole screen when watching live tv or recordings.

Well I think I know what it is - it's the closed captioning and other data transmitted at the top of the video.  In the old days this wasn't visible because all analog TVs had overscan, so there was always a bit of extra video above the top, below the bottom, and beyond the sides of the TV screen.

Nowadays, particularly with fixed-resolution displays like LCDs and plasmas, there is no overscan, so these lines show up.  I just ignore them, but I think there are a few ways to get rid of them.  The best way would probably be to increase the "zoom" of the display by one notch.  This would increase the size of the image so the top and bottom would essentially be overscanned again, clipping the white lines.  If this is a 4:3 show being shown on a 16:9 display, then it will also make the image proportionally wider, using up more of the 16:9 screen without distorting the aspect ratio.

There may be other good solutions as well...

---

### Post by iitywygms on 2009-11-02
Yeah, I know what you are talking about.  The little white dots at the top of the tv screen.  I have seen those.
This is not the issue I am having.  The dots are a little smaller, and in the very middle of the screen.
Also, they disappear if I use a different profile. They are only visible if I use xvmc. 
Thanks for the suggestion thou.
I will get a screen shot and post it.

---

### Post by iitywygms on 2009-11-02
Here is a screen shot.  The dots going across the middle of the screen.  I have sort of pointed to them.
Kind of hard to see in this pic.  It actually is more apparent than this in person.
[IMG]http://i193.photobucket.com/albums/z161/dabears_rule/editScreenshotofmythbed.png[/IMG]

---

### Post by iitywygms on 2009-11-03
Solved by downgrading nvidia driver to 96.

---

