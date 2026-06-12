---
title: "alsa 1.0.15 deb package"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by btboudreaux on 2007-11-25
I have the dreaded MCP51 Nvidia High Definition Audio Chipset and I can't seem to find a working solution. 

I've read that alsa 1.0.15 fixes this issue. Anyone know where I can get a .deb package or repo from? Medibuntu repos don't seem to have it.

---

### Post by btboudreaux on 2007-12-05
After unsuccessfully trying to install this from source for a week... I think I'll bump this up.

---

### Post by Jeff250 on 2007-12-05
This is far from trivial, since, aside from alsa libraries, there are also alsa drivers built into the kernel, so you would need a newer kernel package too.  Your best bet is to compile and install the newer alsa kernel modules into your kernel and then install the newer alsa libraries from source.  Since you report issues doing trying to do this, perhaps we can help you out with them.

Another option is using an alpha version of Hardy Heron, but this isn't a real solution if you need a dependable machine.

---

### Post by btboudreaux on 2007-12-08
> **Jeff250 said:**
> This is far from trivial, since, aside from alsa libraries, there are also alsa drivers built into the kernel, so you would need a newer kernel package too.  Your best bet is to compile and install the newer alsa kernel modules into your kernel and then install the newer alsa libraries from source.  Since you report issues doing trying to do this, perhaps we can help you out with them.

Another option is using an alpha version of Hardy Heron, but this isn't a real solution if you need a dependable machine.

I've followed directions on how to install these three packages.

alsa-driver-1.0.15
alsa-lib-1.0.15
alsa-utils-1.0.15

Basically I did ./configure, then make, then sudo make install for all three but when I rebooted, I got an error when I clicked on the volume applet.

Any ideas or guides on installing the kernel modules into the kernel? Or what I'm doing wrong.

---

### Post by Jeff250 on 2007-12-12
Sorry for the late response.  Hmm, that looks right, so I'm not sure what the problem could be.  What error message are you getting?  Also, try running gnome-volume-control from the terminal, and see if there is any useful output there.

---

### Post by btboudreaux on 2007-12-13
It gives an error about no device. I give up. The one thing I despise about linux is the whole "Lets make installing drivers so complicated and trivial you want to blow out your brains" thing.

---

### Post by fenian on 2007-12-13
Did you follow[ these instructions]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")?

---

### Post by btboudreaux on 2007-12-14
> **fenian said:**
> Did you follow[ these instructions]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")?

I followed something that was pretty much the same. But there are one or two things different. I'll try again when I have time.

---

### Post by steeef on 2007-12-14
I have the same card, and after following those instructions, I have the same missing device issue. What it looks like is that I have two different versions of the module. The Ubuntu-supplied one:
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
and the one installed from source 1.0.15:
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

I'm just not positive on how to reconcile these two.

---

### Post by syxbit on 2007-12-14
try my guide here
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by steeef on 2007-12-14
Yup, I found that after searching a bit more. Thanks for the awesome scripts!

---

### Post by btboudreaux on 2007-12-15
> **syxbit said:**
> try my guide here
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

Thanks for the script. It seems to have installed correctly, although I'm still not getting any sound. Maybe I have a different revision of the chipset? I think I'm SOL.

---

