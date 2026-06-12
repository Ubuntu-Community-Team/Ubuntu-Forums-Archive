---
title: "Will Jaunty (&amp; Karmic) support monitor and TV?"
date: 2009-10-17
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2009-10-17
I posted this in Absolute Beginner. I received 1 response, which, as a beginner to this aspect of the OS/Hardware I could make no sense of. I have posted that response, in red, at the end.

This is a Jaunty box.

I have an MSI Nvidia FX5600 graphics card. At the back are 3 ports. One is the VGA for the computer monitor. Another is an s-video (7 pins) and a third is a DVI+D. 

I know this is more an electronics question, yet, I've netsearched it and am too confused. I find lots of posts about 2 monitors with 2 video cards. Not enough info about 2 monitors and 1 video card. And those I do find are way-too-out-of-date. Yet, maybe I'm using the wrong keywords. Nomenclature is a problem.

I had posted this 

HOWTO: NVIDIA TV-OUT for Newbies
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

I read, as much of the above, as I could thought relevant to Jaunty, given that this How-To is well out of date. (very last post, #373, at page 31 from 2007)

My NVIDIA Driver Version is: 173.14.16

Can I run the TV set from the s-video output of the 'puter without burning the card? I have the NVIDIA X Server Settings/restricted driver enabled. The card is a 7-pin and the TV is a 4-pin s-video. Does it matter? That is, will 4-pin plug into 7-pin and run the TV?

Do Jaunty & Karmic support "dual monitors" with just one video card? Is that configurable from the NVIDIA X Server Settings app? I remember from decades ago, that video cards had only enough electrical power to run 1 device at a time. Running 2 would burn the card's parts up.

I'm trying to watch HULU (tv shows) on the TV set, rather than sitting at the computer. (Yes, I'm a couch potato!)

[COLOR="Red"]Karmic has mostly the same Nvidia stuff in it as Jaunty. The only difference is that Jaunty lacks the nvidia-glx-185 driver and Karmic lacks the nvidia-glx-71. So unless you're using the 71 driver you'll be fine.[/COLOR]

---

### Post by sohlside on 2009-11-02
Hopefully you got help on this by now.  If not, here's your answer. :)

You should be able to connect a 4-pin SVideo cable to your TV from your graphics card and still run your monitor without trouble.  The pins on a 7P (7 pin Svideo connector) won't mind that you aren't using all 7 pins.  Only the 4 that are present on both devices will be used and they're the only ones that you need for a simple connection.

---

