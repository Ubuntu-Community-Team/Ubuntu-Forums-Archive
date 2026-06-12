---
title: "HDMI audio on Haswell based laptop"
date: 2013-11-21
forum: Multimedia Software
---

### Post by golfdiesel on 2013-11-21
I have a System76 laptop (Clevo based device) which has a Haswell Core i7 processor in it.
When I got the laptop there were loads of problems with the audio and video parts which were solved by either kernel updates and/or installing the latest Intel drivers from 01.org. This was all with Ubuntu 13.04.
The problem I am facing now is that after the 13.10 upgrade there is no audio anymore over the HDMI interface. I tried loads and loads of things including using the daily dkms packages from ubuntu audio dev but nothing seems to give me working audio over the HDMI interface.
When I plug in the HDMI cable that is connected to my TV all the devices show up and there is picture but no sound whatever I try.

Does anyone here have an idea on what there is left to try?

So far I have tried:
kernel update to the 3.12 series => no luck
back to kernel 3.11
removing and installing the ALSA parts => no luck
installing latest dkms packages => no luck

---

### Post by golfdiesel on 2013-11-21
Ok... did some more testing.
I did a clean install of Ubuntu 13.10 => no sound over HDMI
I then did something terrible ;) I installed Windows 7 to make sure that there isn't an hardware issue. After the installation the sound was up through the HDMI output, it worked perfectly.
I knew that I had sound before on 13.04 so I did a clean install of 13.04 and after a reboot sadly no sound over HDMI but then I installed the latest graphics stack from 01.org and after the reboot the sound was up through the HDMI interface! 
So it seems that 13.10 is not using an older graphics stack but the 01.org installer does not work on 13.10... So, does anyone have an idea other then sticking to 13.04?

---

### Post by howefield on 2013-11-21
Have you tried selecting HDMI from the Output tab of Sound Settings ?

---

### Post by golfdiesel on 2013-11-21
Yes I have done that. 
HDMI hotplugging is somewhat buggy as well in Ubuntu so you really need to reboot before the HDMI sound output is detected and you have to manually select the correct output to get sound out of it.
For some reason though it does not work with 13.10. I have read that the kernel in 13.10 has the latest intel graphics stack included but my experience tells me otherwise. It seems that the only way for me to get working sound is to stick with 13.04 for the moment with the 01.org graphics stack and when there is a new release from them I can try to upgrade to 13.10 hopefully.

---

### Post by golfdiesel on 2013-11-22
According to system76 it should be a hardware problem but I can't believe that since it works in 13.04 with the 01.org drivers and Windows 7 isn't having problems with it...

---

### Post by golfdiesel on 2013-12-01
Is there nobody who is able to help me with this?

---

### Post by RayDeCampo on 2013-12-01
I am experiencing the same issue with different hardware.  Sound was fine until the upgrade from 13.4 to 13.10.  I ended up filing a bug a report:  [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1256646](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1256646)

---

### Post by ddraper2 on 2013-12-02
I am having similar problems with System76 Gazelle Pro laptop, new in September, with Haswell i7. The sound was working fine 13.04, I updated to 31.10 and now there is no sound after a suspend. There are a few other threads about this problem and it is not isolated to System76 hardware. The HDMI sound output worked fine on 13.04 however I have tried it yet on 13.10 as I just updated 2 days ago.

---

### Post by p-acworth on 2014-02-08
I have a similar problem on a Haswell based intel NUC with intel 5000 HDMI.

I am running Ubuntu 13.10 with the latest drivers from 01.org (released 13 Jan).  

Weirdly enough, I get audio+video if HDMI is connected to my TV.  If HDMI is connected to my receiver (Pioneer Sc-79) I get no audio, no matter what I do.  Based on the above I will try reverting to 13.04.

---

