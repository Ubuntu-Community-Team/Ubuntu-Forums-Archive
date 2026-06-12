---
title: "Strange noise from internal speakers on laptop"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Aleksieff on 2010-01-23
Before I begin please excuse me if my English is not very good!

So my internal speakers on the laptop (MSI VR610X-022) are making some strange cracking sound from time to time. I don't think it's a hardware issue because they work fine with Windows. Currently I'm using Ubuntu 9.10, but I found that the problem also exists on 9.04. Please help 'cuz that's really annoying ...

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```
I'm pretty sure that my audio device is actually from Realtek (I use Realtek drivers on Windows), but this is what lspci said so ...

EDIT: There's noise even if i turn the sound off...

---

### Post by wit on 2010-01-31
I have got the same problem.
Even when I turn the sound off completely (volume 0%), the cracking sounds remain.

They happen when I open new windows (like a browser or Nautilus) or sometimes even when I move the mouse. This happens since 9.10. I have got a HP Pavilion dv6000

---

### Post by wit on 2010-01-31
ok, I have found a possible solution [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417302"):

> We can close this thread.
It is not a defect in alsa or anything else.
The main problem is the power-saving option in the intel hda module.
The sufficient fix is to modify the line in /etc/modprobe.d/alsa-base.conf containing something like
options snd-hda-intel power_save=X
Just remove the whole power_save=X option and that's it.
Restart is required than.

:popcorn:

---

### Post by mschering on 2010-05-18
This doesn't work for 10.04 lucid. Does anyone have an idea on how to fix it?

---

### Post by lidex on 2010-05-20
> **mschering said:**
> This doesn't work for 10.04 lucid. Does anyone have an idea on how to fix it?

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

