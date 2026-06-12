---
title: "No sound through external speakers/headphones"
date: 2009-05-26
forum: Multimedia Software
---

### Post by spetstnelis on 2009-05-26
**UPDATE: This solution no longer works, for some reason. Previously working solution is in post #8.**

Hi all,

I am currently running Ubuntu 9.04 on a **Gateway M-6850FX laptop**.  I get sound from my laptop speakers, but when I try to plug in external speakers or headphones, the sound disappears.  Sound does not come from either the speakers/headphones or the laptop speakers.  This is apparently a common problem, but trying the previously posted solutions did not work.  

One of the solutions was to mute "external amplifier" or disable it in alsamixer, but I cannot find that switch.

So far, it looks like this laptop is running **SigmaTel STAC9205** and **LSI ID 1040** (I do not know what this is).

It also detects 2 sound cards when I type **aplay -l** into terminal: **Intel [HDA Intel]** and **HDMI [HDA ATI HDMI]**

And I am sure there is no hardware issue with the external port itself, because I am able to use it in Windows Vista, when I plug in my headphones or external speakers.  Does anyone have any suggestions to get the sound to come out from the external port?  Thanks in advance

---

### Post by spetstnelis on 2009-05-27
Does anyone have any ideas?  I should mention that I am a complete newb in Ubuntu! :D

---

### Post by redenex on 2009-05-27
I wish I could help you but I have the same problem with my HP TX1005 AU. :popcorn:

---

### Post by jimbo99 on 2009-05-27
In the sound mixer properties you have the digital option turned on?  Turn it off.  I don't know which screen only that the digital option being set on can trump sound output.

---

### Post by spetstnelis on 2009-05-27
I don't see anything regarding digital options.  I see "Digital Input Source" under volume control, but that doesn't seem to be anything significant...

---

### Post by lswartz on 2009-05-27
Go to your terminal & type in 
```
alsamixer
```

It gives you a nice color box in your terminal so you can adjust your audio settings.

OOPS! Now I see you have already tried that.

---

### Post by PaulReaver on 2009-05-27
try turning up alsa mixer Front Speaker in the volume control

---

### Post by spetstnelis on 2009-05-27
I figured out the solution!  It turned out to be a common problem among laptops with **SigmaTel STAC9205 codec**.

The bug is discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

I first followed this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/34)

>            Hi guys!
 I've made my headphones work :). I've found the solution in this thread:
  [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
  Download the script and run with the options "-di"
    sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di
  Then reboot, and everything works !!
  Basically the script, download the last version of alsa (1.0.20) and then compile it.
  I can cofirm that this bug is solved with that version of alsa, and is working in:
  Gateway T-1625
  Ubuntu 9.04 - 64 bit
 Cheers and I hope this work for you! :)
 P.S: I wondering why ubuntu not update the alsa version to 1.0.20 ?

        
Then I followed this extra step: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/39](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/39)

>            As a correction to my previous post, this -does- work on the T-6828. The issue with mine was that it required a line to be appended to /etc/modprobe.d/alsa-base.conf, and the computer restarted:
 options snd-hda-intel enable_msi=0 model=eapd
 O happy day!

        
Cheers :)

---

### Post by jimbo99 on 2009-05-27
I have never recommended that anyone compile from source in Linux.  You update your kernel and oh well, off to do it again.  If you do that with too many features you end up with something that's bound to slip by.

As far as the "digital" piece I was talking about.  I'm not a guru on sound.  I do have about 8 installs of K/Ubuntu at my shop and I have had lots of issues with sound and invariably in the mixer there's an option for digital output and unchecking that generally solves my sound woes.  It doesn't always do so, and sometimes there's a need for more changes, but in the vast majority of cases I have turned off digital and it worked.

This isn't to say that the bug you discuss isn't for real.  It probably is.  It isn't to say that fixing it by compiling from scratch didn't solve your problem.  I just warn everyone about compiling from source for anything, absolutely everything, as I consider it an absolute no no, even if it solves your problem.  I generally find another solution somewhere down the line or I find a better program/answer to my problem, but never ever compile, period, no matter what anyone tells you.

---

### Post by Mishna on 2009-11-10
> **spetstnelis said:**
> I figured out the solution!  It turned out to be a common problem among laptops with **SigmaTel STAC9205 codec**.

The bug is discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

I first followed this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/34)

Then I followed this extra step: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/39](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755/comments/39)

Cheers :)

This corrected the issue I for me as well until recently. The fix is still in place, but I recently installed Juk and Amarok. I am not certain if the issue began before or after I installed these, but it appears to be after I installed them. I'm going to uninstall them and reboot and see what happens.

edit: This does not appear to have corrected the issue. Not sure what to do at this point. I'm going to check some other resources and check back.

---

