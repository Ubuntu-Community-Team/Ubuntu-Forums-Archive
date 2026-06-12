---
title: "No sound in HP dv7 series laptop"
date: 2009-06-10
forum: Multimedia Software
---

### Post by GilbertEvanG on 2009-06-10
Hello,
I recently purchased a HP dv7 series laptop and am dual booting windows vista with Ubuntu 9.04 64bit.

I am getting no sound out of my laptop when I boot with Ubuntu (it works fine for vista, so the hardware isn't bad).

My audio devices is the following: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I have tried following the Comprehensive Sound Problems Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) but on step 3 I get stuck because my sound card does not appear to be in the matrix (I don't see the ICH9 series listed under Intel [[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)]).

I also found these instructions which looked promising: [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

After following those instructions, I still do not get sound out of Ubuntu, but, when I shut down my laptop I get a garbled sound out of the speakers for about a second. That is the only sound Ubuntu produces for me, and its only on shutdown.

I have also tried adding options to my /etc/modprobe.d/alsa-base.conf file as suggested here ([http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)). I currently have added the following options suggested in that thread to no avail:

options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1


I am pretty new to linux, so any assistance would be greatly appreciated.
Thank you.

---

### Post by Yellow Pasque on 2009-06-10
> dv7t-2000
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-**Upgrade ALSA to 1.0.19**

You need to upgrade ALSA. The version included with Ubuntu 9.04 is too old. [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by GilbertEvanG on 2009-06-10
Thank you.
That just about did the trick. Now I have sound on start up and during normal use, but I still get the weird loud static sound when the computer shuts off from Ubuntu. Any ideas on how to fix that?

---

