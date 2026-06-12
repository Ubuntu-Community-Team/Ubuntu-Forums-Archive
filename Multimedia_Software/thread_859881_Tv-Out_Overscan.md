---
title: "Tv-Out Overscan"
date: 2008-07-15
forum: Multimedia Software
---

### Post by yousillygoose on 2008-07-15
I have made a few posts about configuring svideo+tvout to output to the tv.  This worked flawlessly with nvidia-settings in Gutsy and is a wreck in hardy.  I used twinview in Gutsy and it configured itself nicely.  In hardy I am forced to configure the xorg so that it outputs to the tv.  The only way that I have gotten this to work is to run it through separate x sessions (figured out out last night).  The problem now with the output is that the full image is not being shown on the tv (I believe this is due to overscan).  I am trying the "Option   "TvOverScan" option but it does not make any change to the picture.  I am using a Geforce 8600M Gt.  Is there any way to make the full picture show or to run it through twinview?  Thank you

---

### Post by yousillygoose on 2008-07-15
I also do not have any LCD tv to try this on.

---

### Post by yousillygoose on 2008-07-15
bump

---

### Post by Zeotronic on 2008-07-15
Its been a while since I tv outed, and I no longer have a TV with which to try this with... but I'm pretty sure I used NVidia TV-Out (NVTV in synaptic), so I'd advise you to check that out. As for twinview, I've never heard of it, and don't see it in the repository... but NVidia TV-Out may meet your needs.

---

### Post by yousillygoose on 2008-07-16
Twinview is an option in nvidia-settings to play on both screens connected by the same X session.  I'll try the other program out.  From what I have read, though, the overscan is a common problem people have that they can't resolve.

---

### Post by Jean__ on 2008-07-16
Many (modern) tv's have an option not to overscan, on mine it's called 'scan only'.

---

### Post by yousillygoose on 2008-07-16
I looked through my tv's options and it doesn't have that option.  It seems that the solution should be through my laptops settings and not the tv's considering I don't always watch movies from the same tv (often do it from my girlfriends).  I know it isn't the cable or the hardware being that I used the cable yesterday from another computer that runs xp and I ran it with mine perfectly when I ran Gutsy.  If I had to guess the reasoning behind the overscanning issue I would say that Nvidia isn't supporting the option with some of their cards (and I unluckily have one card that is not supported).  I feel this way because some people's nvidia-settings has the overscan option and others do not (mine doesn't).  That being said I think that the overscan option in the xorg only works if it would be found in nvidia-settings.  Now, for the sake of wonderful movie watch, SOMEONE PROVE ME WRONG!

---

### Post by yousillygoose on 2008-07-16
nvtv is giving me Fatal: No supported video card found.  I guess that program hates me too?

---

### Post by Zeotronic on 2008-07-16
While I suspect you do, I've got to ask, you DO have the restricted hardware driver for your card installed right? You probably do, I cant imagine how you could have not done it, but its the only thing that I can think of (not that I'm at all an expert on the subject). You may try installing it with Envy, I had to do that a version or so ago because the synaptic install didn't work right (and as I understand it that was true that version for a lot of people). I wouldn't do it however, unless you can confirm that the problems you are having are related to that.

---

### Post by yousillygoose on 2008-07-16
I have the newest version of the driver installed (I installed it actually through Nvidia's side as Envy didn't have the up to date driver).  Envy now, though, was updated and has the newest driver.

---

### Post by Jean__ on 2008-07-17
This will not be helpfull to you but since I did quite some searching on overscan, here goes.
Every tv does overscan, it's an issue from way back when tv boradcasting begun and the techs had trouble with the picture quality at the sides of the screen. So they decided to just cut that out. Hence, overscan. If you could see that area, you could sometimes see things like a microphone being there.
So when you connect a tv as a pc monitor, it also cuts the sides away. So it is not so much an issue of the video card allthough a card could of course compensate.

> **yousillygoose said:**
> It seems that the solution should be through my laptops settings and not the tv's 

---

### Post by yousillygoose on 2008-07-17
In great annoyance I just purchased a vga to rca cable.  I was using a svideo to rca cable.  I am hoping that the changing the type of cable I use will make my problems go away (but who knows).  Any more clues are always helpful!

---

### Post by yousillygoose on 2008-07-17
> **Jean__ said:**
> 
So when you connect a tv as a pc monitor, it also cuts the sides away. So it is not so much an issue of the video card allthough a card could of course compensate.

I see your point but have a question back to you: when you output Svideo in windows there is no (or I haven't experienced with the same hardware) overscan.  Being that windows software [and GUTSY] can eliminate overscan and make the tv fit correctly it says to me that it is possible to do in Hardy but may have not been accomplished yet.  There is also a chance that it has been accomplished but people don't really know how (but I doubt that).

---

### Post by Jean__ on 2008-07-17
I understand your frustration, I'm sorry I can't help.

> **yousillygoose said:**
> There is also a chance that it has been accomplished but people don't really know how (but I doubt that).

---

### Post by yousillygoose on 2008-07-17
No worries, I'm just glad you're hear and trying  :)

---

### Post by xc3RnbFO8P on 2008-07-17
Check this:
[http://ubuntuforums.org/showthread.php?t=859680]("http://ubuntuforums.org/showthread.php?t=859680")

---

### Post by yousillygoose on 2008-07-17
The TVOverScan option does not affect my picture at all.  When I change the value the picture looks the same.

---

### Post by xc3RnbFO8P on 2008-07-17
Just watch the thread,
they are still working at it.

---

### Post by yousillygoose on 2008-07-17
Thank you very much.  If anyone solves it let me know and I'll watch both threads

---

### Post by SBFC on 2008-07-18
> **yousillygoose said:**
> I have made a few posts about configuring svideo+tvout to output to the tv.  This worked flawlessly with nvidia-settings in Gutsy and is a wreck in hardy.  I used twinview in Gutsy and it configured itself nicely.  In hardy I am forced to configure the xorg so that it outputs to the tv.  The only way that I have gotten this to work is to run it through separate x sessions (figured out out last night).  The problem now with the output is that the full image is not being shown on the tv (I believe this is due to overscan).  I am trying the "Option   "TvOverScan" option but it does not make any change to the picture.  I am using a Geforce 8600M Gt.  Is there any way to make the full picture show or to run it through twinview?  Thank you

How did you get tv-out to work with gutsy? I'm still using Gutsy and I see no option in nvidia-settings (I'm using TwinView) to output video to my tv. Am I blind?

I am assuming you meant you had video being routed to your television...which is what I'm inquiring about. Thought I may have been a little unclear.

---

