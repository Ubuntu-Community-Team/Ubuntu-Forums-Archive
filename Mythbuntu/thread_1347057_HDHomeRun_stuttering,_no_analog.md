---
title: "HDHomeRun stuttering, no analog?"
date: 2009-12-05
forum: Mythbuntu
---

### Post by fosheezy on 2009-12-05
I just purchased an HDHomeRun to use with my new mythtv setup. My box has the following hardware:

-AMD 2.8 GHz quad core
-gigabyte MB
-ATI 4350 video card
-4GB DDR3 RAM
-7200 RPM HDD
-Gigabit switch, cat6 or cat5e cable

I got the HDHomeRun setup and I can see the OTA HD channels. If I turn on PIP or PBP I get a bunch of stuttering. I know the network can handle it because I used eyeTV on my laptop and was able to watch two HD channels at once and they both looked beautiful. I have TOP running on my laptop (over ssh) while the linux box is playing tv and I usually have over 50% idle (of total cores) even with the two streams in PIP. xorg is using about 55% and myth is using 100-150%.

When I view them on the linux box the quality isn't up to par and I cannot get the video card to go full HD (1920x1080) on my full HD tv.

I also am not getting any of the regular NTSC channels (1-112). I was under the impression that mythtv picked these up, am I wrong? I get my OTA HD channels (113-115) fine.

Any suggestions?

---

### Post by seeker5528 on 2009-12-05
I'm not using my HDHomerun for OTA stuff so don't know how that differs from cable in the way it shows up, but it should be showing all your digital channels whether they are HD or not.

In my area all the local affiliates do HD, so ABC, NBC, CBS, FOX, WB, MyQ2, plus a couple others and a couple PBS networks, some of them broadcast more than one HD stream, so not sure exactly what you mean when you say:

> I also am not getting any of the regular NTSC channels (1-112). I was under the impression that mythtv picked these up, am I wrong? I get my OTA HD channels (113-115) fine.

It just doesn't fit with what I see in my area (in the vicinity of Seattle, WA).

There are different options for what kind of system you are connected to, 8-VSB (ATSC over-the-air digital HDTV), QAM64/256 (unencrypted digital cable TV), I think after Comcast reshuffled their stuff when they switched everything over channel 30 to digital I had to scan with 8-VSB in Windows, but I am pretty sure I used one of the QAM options in MythTV and I never changed it, just scanned for the new channels. Even thought they say 8-VSB is for OTA stuff and QAM is for Cable, you might try changing it anyway just to see if it makes a difference.

Later, Seeker

---

### Post by fosheezy on 2009-12-05
So I won't get the standard def channels if they are not digital?

I get the digital unencrypted HD stuff, but nothing else.

I am on a college campus, I think they have a directv signal that they distribute (I've seen the 'searching for signal' when it was raining a few days ago) so I doubt they have anything digital but the HD stuff.

I'd just like to know why it is stuttering when I watch two at once. I'd like to be able to record two shows at once and not worry about stuttering on both of them. Could it be a video card issue?

---

### Post by matt06 on 2009-12-05
> **fosheezy said:**
> So I won't get the standard def channels if they are not digital?
It is my understanding that the HDHomeRun is a *digital only* receiver, and if that's correct, you will not get any non-digital (analog) channels, whether they are SD or HD.

---

