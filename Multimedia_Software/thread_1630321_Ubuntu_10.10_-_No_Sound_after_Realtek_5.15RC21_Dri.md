---
title: "Ubuntu 10.10 - No Sound after Realtek 5.15RC21 Driver"
date: 2010-11-25
forum: Multimedia Software
---

### Post by doomedforever on 2010-11-25
Hi Boardies,

well, this is my 1st thread here...and i got a problem. ;)

About myself, i am using Ubuntu Linux since 10.04, and Linux in generall since the early
90's, my 1st Linux was Suse Linux 4.x, and i bought Suse 5.3 Distro with KDE 1.0 final
in 1998, have used MandrakeSoft Linux 5.3, and also Debian at that time, too...between
the years, i always have had linux on a spare machine, while using Windows
 (mostly NT4, later 2000, XP - today 7) as my primary OS, but since Ubuntu 10.04, 
i'm very rarely booting Windows, only for working with Photoshop from time to time...)

So, the trouble is, that i thought to myself, it could be nice to use the realtek driver
and using the realtek audio rack gui, which was really a bad idea - then since i today
this morning installed the 5.15 RC21 driver, i have no sound at all after rebooting
my -otherwise- perfect running Maverick...*sigh* 

Hardware Specs: Gigabyte P35-DS3, 4 Gig PC2-800 A-Data Vistesta Extreme
onboard Realtek ALC889a Codec (which sounds great with default 10.10 driver before)
Nvidia 8600 GT/512 MB with latest nVidia Driver 260.21, 1TB Samsung HD103SJ HDD,
16x LG H62N DVD Toaster. 

I hope someone could help me fix that issue - i won't like to re-install my customized
Maverick - thank you much!

Greetings
Marc

---

### Post by Raze7 on 2010-11-29
Yea, i got the same problem

---

### Post by Lord Paladin on 2011-01-06
Same problem, I think because the driver is alsa based after deleting your current sound driver it then tries to install the new one in Asound which does not exist. I have no idea how to fix it though

---

### Post by Lord Paladin on 2011-01-07
Opened Synaptic searched ALSA did a complete removal on pretty much everything libraries and all - overkill I know but I didn't want to miss anything then reinstalled them and rebooted. Just going to use the generic driver screw the genuine one too much hassle, works a treat

---

### Post by lidex on 2011-01-07
To reset alsa to ubuntu default.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by Flos Headford on 2011-02-05
Can someone remind me - what was the thinking behind the idea of releasing an OS with the sound facilities MUTED by default? Somehow the brilliance of the concept has escaped my meagre mental faculties. I would have thought this might be a bit of a turn-off for people we've just persuaded to try Linux. Or am I the only one who thinks that?
Phil

---

### Post by lidex on 2011-02-09
> **Flos Headford said:**
>  Or am I the only one who thinks that?
Phil

Yep. :wink:

Probably has to do with not blaring out loud audio that would at least startle, perhaps damage speakers?

---

### Post by Araxis on 2011-02-21
Hello everyone, I am new to Ubuntu but I recently had to deal with this no sound business since installing Ubuntu 64bit.

I built a new rig and ran Ubuntu 32bit with no issue, but when I reinstalled 64 my sound stopped working. It detected all the hardware and pretty much acted as if there was nothing wrong, although I do believe alsa was slightly confused on my drivers.

ANYWAYS, long story short, I updated/upgraded everything, then installed a newer kernel than what came with the regular updates. Im using 2.6.35.25 and my sound works great!


Hope this helps someone.

---

### Post by Araxis on 2011-02-21
I should also mention my driver was Realtek ALC888B  :)

---

### Post by the.lost.one on 2011-05-29
> **Lord Paladin said:**
> Opened Synaptic searched ALSA did a complete removal on pretty much everything libraries and all - overkill I know but I didn't want to miss anything then reinstalled them and rebooted. Just going to use the generic driver screw the genuine one too much hassle, works a treat

I just reinstalled them, but still no sound. Please tell me if I choose the "complete removal" option, would the packages be removed from synaptic? 

How did you reinstall after complete removal? Using the same search for ALSA?

__
I have got 64 bit Natty kernel 2.6.38-8

---

### Post by lidex on 2011-05-29
Try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by the.lost.one on 2011-05-29
> **lidex said:**
> Try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```
omg! it worked like a charm! you're a life saver, lidex. i cannot tell you how much time and headache you saved me :D

it would have worked with your earlier post, but i didnt have aptitude installed and when it didn't work i presumed you meant apt-get

---

### Post by neycho on 2012-02-05
> **lidex said:**
> To reset alsa to ubuntu default.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```**Reboot.** 10x a lot man! :) It works great for me. I have sounds again! :) :)

---

