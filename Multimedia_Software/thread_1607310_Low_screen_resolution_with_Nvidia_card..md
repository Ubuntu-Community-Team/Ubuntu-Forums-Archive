---
title: "Low screen resolution with Nvidia card."
date: 2010-10-27
forum: Multimedia Software
---

### Post by DaSaint on 2010-10-27
**Problem:**
Installed Ubuntu 10.10 on my computer whose mainboard had just been changed (into an msi 785GM-E51). Processor had also been upgraded (to an Athlon II XII 250 3.0 GHz) and new graphics card had been installed (Nvidia GT 220). 
After installation it turned out I could not get a decent screen resolution.
After installing the nvidia drivers I could still not change the resolution.

I got a pop-up that said:
X Server does not support size requested

I also got popped into low graphics mode but then I did have my full 2048x1152 resolution strangely enough.

Maximum resolution I could get was 640x480,

**Attempts to resolve the problem:**
Installing and uninstalling the drivers trough the “restricted drivers manager”.
Messing around with the xorg.conf file.
At first I did not even have one so I tried creating one.
I also tried letting the nvidia program create one.

**Solution:**
Eventually I found out about a new Nvidia driver included in Ubuntu called “Nouveau”.
And it seemed that one was causing my problems. 
I ended up de-installing “xserver-xorg-video-nouveau” and also “nvidia-common”
So I ended up with no nvidia drivers and no xorg.conf file.

Reboot, ... Problem solved..
I'm now looking at an 2048x1152 resolution Samsung Syncmaster 2343NW on a Nvidia GT220 card.

Too bad this nouveau driver is installed by default if it can completely render a system useless. It seems to me there is still some work on this driver.

I don't play any games or don't do any heavy graphical stuff but maybe for other people it's quite a problem to not have the nvidia drivers installed.
For me, I don't need the hassle right now so I'll just leave them uninstalled.
Hopefully one day these drivers will work better.

---

### Post by DaSaint on 2010-10-27
I just found this page:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture) 

Which could also be providing a solution to peoples graphics problems. It could even be a solution for me. I guess I'll have to give it a try.
Maybe that way I can run the nvidia driver and have full nvidia performance without the trouble.

---

### Post by gtardini on 2010-10-29
I also got "Low graphics mode" on 10.04. The desktop does not give signs of poor resolution, though. That's anyway a lot better than 10.10, where the X-server was not found at all (or it crashed). I tried a few things from the forum, like gdm restart or some xorg- commands, but none did the job. Until I tried 10.04, and there I can work more than reasonably with low graphics mode. What capability does it restrict? As I said, the resolution looks quite nice.

---

### Post by DaSaint on 2010-10-29
I had this "low graphics mode" thing pop up on my laptop. But it would only pop up after 10 minutes or so.
Conclusion would be that I would be working on something that was not yet saved and BOOM. Ubuntu would log off and then back on again in low graphics mode but my work would be gone.

So that was quite annoying. I had that on my laptop with 10.04 but not with 10.10.
But my laptop doesn't have an nvidia card. It has intel.

Strange things...

---

