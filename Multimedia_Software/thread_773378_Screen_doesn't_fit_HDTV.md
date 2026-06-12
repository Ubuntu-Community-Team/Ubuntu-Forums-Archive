---
title: "Screen doesn't fit HDTV"
date: 2008-04-28
forum: Multimedia Software
---

### Post by fizban9 on 2008-04-28
I'm running off a fresh install of Hardy Heron and everything worked fine when it was hooked up to a monitor.  The problem happened when I switch to my HDTV, connected via a DVI to HDMI cable.  

Ubuntu sees the TV fine, even reports the correct name, and I can choose the correct resolution.  The problem is that the edge of the desktop goes off the edge of the TV.  

I had the same problem in Windows XP (It's a dual boot box) but the Nvidia drivers allowed me to scale the screen down to fit.

Is there any sort of Nvidia scaling in Ubuntu?  Or some other way to shrink the screen?

Thanks for the help.

---

### Post by fizban9 on 2008-05-01
is it bad if I bump my own thread.  I'm still hoping for a response.

---

### Post by x0d on 2008-05-01
I'd be curious on this too.  My mythbuntu setup has the same problem.

---

### Post by Elderon on 2008-05-01
I'm having the same issue with the start menu being pushed off the edge of my screen where I can't see it.  Changing resolutions does not help, it is always off the screen.

Though unlike you, hardy is not able to detect my hdtv.  Not sure if that's due to not using dvi/hdmi cables or not?  I'm using the video out on my video card nvidia 8800gt with component cables.

anyways, hope we can find a solution.

---

### Post by fizban9 on 2008-05-04
> **Elderon said:**
> I'm having the same issue with the start menu being pushed off the edge of my screen where I can't see it.  Changing resolutions does not help, it is always off the screen.

Though unlike you, hardy is not able to detect my hdtv.  Not sure if that's due to not using dvi/hdmi cables or not?  I'm using the video out on my video card nvidia 8800gt with component cables.

anyways, hope we can find a solution.

Yeah, I think it's not detecting your tv because you're using an analog connection.  

I mainly said that to bump the thread again.

There has to be some way to scale the image output from the nvidia card.  In windows the Nvidia driver actually has a scaler option.  

I hope someone comes up with something.

---

### Post by xc3RnbFO8P on 2008-05-05
Read this:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=96980]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=96980")
and this:
[http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html]("http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html")

---

### Post by odinb on 2008-05-05
In my experience there are 2 ways to solve this, where the first one is the easiest one.

1. UseEDID. the first link above has this reply that explains how to do that.
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=2651733&postcount=15](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=2651733&postcount=15)

2. If useEDID does not work (crappy firmware/hardware), you will have to figure out the Htimings and Vtimings manually using xvidtune.

See this link: [http://ubuntuforums.org/showthread.php?t=781972](http://ubuntuforums.org/showthread.php?t=781972)

Basically you add the following:
under
Section "Device"
add
Option "ModeValidation" "NoWidthAlignmentCheck"

and under
Section "Monitor"
you need the following (These are examples, you need the config specific to your monitor. Check your manual to have a starting point for xvidtune.)
HorizSync 31-70
VertRefresh 50-85
Mode "1360x768" # vfreq 59.815Hz, hfreq 47.553kHz
DotClock 85.500000
HTimings 1360 1494 1624 1798
VTimings 768 770 776 803
Flags "-HSync" "+VSync"

Good luck!

---

### Post by fizban9 on 2008-07-14
Just wondering if anyone else has fixed this yet.  Messing with my Htimings and Vtimings hasn't helped.

---

### Post by Fen_Star on 2008-07-14
> **fizban9 said:**
> Just wondering if anyone else has fixed this yet.  Messing with my Htimings and Vtimings hasn't helped.What is the native resolution of your TV?

---

### Post by markbuntu on 2008-07-14
There are a number of tvs that overscan by default and you have to get into their menus and tell them to stop it.

---

