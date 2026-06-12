---
title: "Muting the speakers when headphones are plugged in (Intel HDA)"
date: 2011-03-09
forum: Multimedia Software
---

### Post by PercentSevenC on 2011-03-09
So, I've been bashing my head against this problem for weeks now. The problem is that my external speakers are not being muted when I plug in headphones. I get sound through both the speakers and the headphones at the same time. This is happening on every Linux distro I've tried so far on this box, but in Windows everything behaves as expected. I've tried every option I have in both alsamixer and the Gnome sound preferences, to no avail. Curiously, if I mute any one of the audio channels or toggle the headphone switch in alsamixer, all sound output is muted, to both the speakers and headphones.

The audio chipset is a Realtek ALC888, on a Gigabyte GA-770TA-UD3 motherboard (6 jacks, optical and coaxial S/PDIF out). I must've tried a dozen different models in /etc/modprobe.d/alsa-base.conf, and none of them seem to make any difference at all.

Halp?

---

### Post by PercentSevenC on 2011-03-11
Anybody have any insight on this?

---

### Post by PercentSevenC on 2011-04-09
Hate to bump this again, but I'm still struggling with this problem.

---

### Post by lidex on 2011-04-10
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by PercentSevenC on 2011-04-10
[http://www.alsa-project.org/db/?f=958ea2b5552bf479c141f0ff0fc04d381c657548](http://www.alsa-project.org/db/?f=958ea2b5552bf479c141f0ff0fc04d381c657548)

---

### Post by lidex on 2011-04-13
> **PercentSevenC said:**
> [http://www.alsa-project.org/db/?f=958ea2b5552bf479c141f0ff0fc04d381c657548](http://www.alsa-project.org/db/?f=958ea2b5552bf479c141f0ff0fc04d381c657548)

Go ahead and remove the auto model line from alsa-base.conf then 
reboot. Which other have you tried already? How about 6stack-dig?

If you're up to it you can try an alsa upgrade - the link in my sig.

---

### Post by PercentSevenC on 2011-04-13
I don't remember all the ones I've tried anymore. I did try 6stack-dig, as well as 6stack-dig-demo, 6stack-digout, 6stack, and several random manufacturer-specific ones like 6stack-dell. I started going through the list one by one, but it didn't seem to be getting me anywhere, so I gave up. If you have any other recommendations, I'll gladly give them a shot. I'm just not sure what else to try.

I may attempt an ALSA upgrade later tonight, but I'm not hopeful, since Natty Beta 1 exhibited the same symptoms on this machine.

---

