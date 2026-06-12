---
title: "ATI/HDMI Over/Under Scan In Lucid"
date: 2010-05-09
forum: Multimedia Software
---

### Post by smuggly on 2010-05-09
Is There A Way Yet To Fix The Black All The Way Aroung The Screen With HDMI.Its Really Just A Digital Issue I Think!.It Works Through VGA Fine But The Audio Xtra Wire Thing Is A Drag.It Would Be Nice To Get Catalyst Working ( The Overscan Underscan Tab Like Windows) But Xorg.conf Would Be OK I Guess.
       Thanks For Viewing.

On Another Note I Really Love Lucid Its A Windows Rival For Sure.Especially If We Can Get Stuff Like This Fixed.

                                 Thanks Smuggly

---

### Post by xc3RnbFO8P on 2010-05-09
If it is TV, you should be able to fix this in TV setup (Scale, Format).

---

### Post by efflandt on 2010-05-10
Look through your /var/log/Xorg.0.log to see if anything jumps out at you.  Which Ubuntu version, and are you using default or proprietary drivers, with or without xorg.conf?

I have an older ATI X1300 connected DVI to HDMI to a 1080p HDTV, and default drivers in Ubuntu 9.10 or 10.04 LTS automatically worked 1920x1080 full screen.  Although, the default driver in 10.04 breaks my suspend and hibernate, so I use radeon.modeset=0 to use the user mode driver, instead of kernel mode 10.04 uses by default. I have my HDTV set to "just scan", so it matches itself full screen to the video signal if it is close.

In WinXP it was under scanned all the way around, but after I updated its drivers (which I think just updated Catalyst), I found an under scan slider and adjusted that to zero to get full screen.

---

### Post by smuggly on 2010-05-14
Im Running Lucid 64 bit On A Gigabyte Board With Integrated Ati 4200hd.I Havent Checked Xorg.conf yet.And Yea I Have CCC Installed In Lucid But The Slider Isnt There.Im Running The Restricted Drivers.

---

### Post by pricinosus on 2010-09-19
This problem will never be solved by ATI... never.. never... I am tired to hope this will work ever. 

This misery is perpetuated since middle nineties, from Windows 95 times when ati was overwhelmed by releasing a good driver in time.

Fortunately/Unfortunately linux driver is maintained by community.
Ironically is the same ATI attitude.    

In previous release of driver there was a slider like in windows where you could adjust the over/under scan the image.

This slider was gone.... don't ask me why... 

This is beyond everything

If here is somebody, thinking I'm wrong please correct me, and teach me how to solve this problem in Lucid.

---

### Post by tedrogers on 2010-10-13
I have this very same problem, and I find it difficult to believe this cannot be fixed through drivers.

Like many suggest, it is, in my case at least, not the TV settings. This seems to be a driver issue.

Windows has overscan / underscan and Ubuntu does not.

I am very disappointed and am still looking for a solution.

I hope to find one soon, but I have been looking on and off now for over a year. :(

---

