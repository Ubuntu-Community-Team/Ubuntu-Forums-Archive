---
title: "Toshiba Satellite L35-S1054 No Headphone Sound"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by Innuendo108 on 2008-03-17
Hello
I've viewed ALL topics and didn't find the solution of my problem.

Toshiba Satellite L35-S1054
Intel HDA Realtek ALC861VD
UbuntuStudio 7.10 kernel 2.6.22-14-rt
ALSA 1.0.16

I have sound in my laptop dynamics, but I have no sound in my headphones.
I've tried all that read:
1) Compiled the latest ALSA
2) Tried "options snd-hda-intel model=3stack" and "options snd-hda-intel model=toshiba" and "options snd-hda-intel model=auto" in alsa-base file
3)Tried this code:
```

sudo mv -v /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel{,_orig}.ko
sudo cp -v /lib/modules/2.6.22-12-generic/{kernel/sound/pci/hda,ubuntu/media/snd-hda-intel}/snd-hda-intel.ko
sudo depmod -a
sudo modprobe snd_hda_intel

```
after what i've got new options in ALSA mixer but there is still no sound in headphones.

Here are screenshots of my ALSA mixer (sorry for russian labels, but I think you you'll understand by images-labels)


Hope we'll find the solution!
Sincerely yours, Evgheny

---

### Post by fedex1993 on 2008-03-17
i have the same problem on my toshiba laptop and i still havnt fixed it

---

### Post by Innuendo108 on 2008-03-17
it's a pity.
Have you tried Hardy Heron? I want to try only for fixing this buy, but if you tried - i wouldn't install alpha =)

---

### Post by Anthem on 2008-04-25
> **Innuendo108 said:**
> Have you tried Hardy Heron?
This is still broken in Hardy... same problem on a fresh install on a Satellite A135.

Here's somebody else with the same problem:

[http://ubuntuforums.org/showthread.php?t=604741](http://ubuntuforums.org/showthread.php?t=604741)

EDIT:  Hmm, promising.  I'll try this:

[https://answers.launchpad.net/ubuntu/+question/24989](https://answers.launchpad.net/ubuntu/+question/24989)

---

### Post by natetheinfamous on 2008-05-05
Fixed, I had the same problem but found the solution here:
[http://www.backports.ubuntuforums.org/showthread.php?t=473425](http://www.backports.ubuntuforums.org/showthread.php?t=473425)

---

