---
title: "VLC/Movie Player fullscreen issue - black bar on right hand side of monitor"
date: 2010-11-29
forum: Multimedia Software
---

### Post by webbber on 2010-11-29
Hi all - a new problem for me - I am using a laptop with a monitor attached to it. When I watch a movie (xvid) in Movie Player or VLC fullscreen on my attached monitor, a vertical black bar appears on the right hand side of the screen and blocks part of the picture. 

I don't think its to do with settings, because it happens in both players, and no black bar appears when I fullscreen flashplayer from a web page in google chrome. Weirdly, the black bar also appears when I drag the corner of the vlc window to make it bigger (not fullscreen). It fills about 1/8 of the screen on the right hand side. Fullscreen works on my laptop screen, just not on the external monitor. 

My setup: I have no desktop effects enabled (actually, the problem goes away if I enable effects, but performance is really bad - it's a fairly old laptop - Compaq nx6325 running Ubuntu 10.10. My desktop extends over both the laptop and external monitor.

I tried looking on fora for help, but I can only find information about black bars top and bottom (letterbox).

Any tips on this point much appreciated :) 

Leigh

---

### Post by Sotiri on 2010-11-29
Try to reinstall VLC player! see then what happens to the right bar on you're right bar.

I thiss is not helping at all try to refresh you're nvidia settings by choosing a new resolution.

---

### Post by webbber on 2010-11-29
> **Sotiri said:**
> Try to reinstall VLC player! see then what happens to the right bar on you're right bar.

I thiss is not helping at all try to refresh you're nvidia settings by choosing a new resolution.

Hey - thanks for trying to assist! 

I tried re-installing VLC - it didn't help - and may I add that Movie Player acts the same. 

A new development - when I switch to a lower resolution, it works fine - it's just at 1920x1080 when the effect happens.

---

### Post by akand074 on 2010-11-29
Do you have your proprietary drivers for your graphics card installed? System > Administration > Additional drivers. That seems to be an odd bug though. Works if you enable effects and if you bring down the resolution.. peculiar.

---

### Post by webbber on 2010-11-29
> **akand074 said:**
> Do you have your proprietary drivers for your graphics card installed? System > Administration > Additional drivers. That seems to be an odd bug though. Works if you enable effects and if you bring down the resolution.. peculiar.

No - I don't. You think I should try some?

---

### Post by akand074 on 2010-11-29
> **webbber said:**
> No - I don't. You think I should try some?

Yes definitely. Install your graphics driver.

---

### Post by johnmay on 2010-12-04
I was having a similar problem, and found a solution here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and used the  xrandr --addmode VGA-2  command to fix the resolution. 

Now, I am using the nVidia card with the default driver and the system is rockin!



The thread I started was:  two screen widths from same monitor on web page would be really interested in knowing how you solve the problem.


Yeehaw

---

