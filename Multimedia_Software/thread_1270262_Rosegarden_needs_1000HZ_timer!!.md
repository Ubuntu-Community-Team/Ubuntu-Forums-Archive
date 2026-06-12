---
title: "Rosegarden needs 1000HZ timer!!"
date: 2009-09-19
forum: Multimedia Software
---

### Post by Qbeta on 2009-09-19
I have struggled with Rosegarden for months and have concluded that the only thing needed to get it working is to switch to a 1000HZ timer resolution instead of the 250HZ setting that is the default in the current kernels.  Is there some reason the developers can't make this simple change?  The kernel config help says that 1000HZ is what you want for desktops and the main Ubuntu distro is supposedly for desktops.  I would build my own kernel but don't have time to look into what appears to be a complicated process (I need third party drivers to work and don't know how the initrd system works).  I've tried make-kpkg but it bails out with some error about how it can't find a kernel I don't even have in the control file.  I don't know about control files and don't have time to research that.  Is there any particular reason for this 250HZ timer setting that someone can explain to me?

---

### Post by Bucky Ball on 2009-09-19
You need to run the rt (real time) kernel that comes with Ubuntu Studio for really good results. I'm pretty sure you can just install the kernel though. I have Studio apps and kernel running on a Xubuntu install and have a choice of the rt kernel at boot.

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video **linux-rt**

```... installs all Studio apps but you could just use:

```
sudo apt-get install linux-rt
```... and I imagine that would work. Be aware that the rt kernel will break the install if you are running nvidia graphics drivers. There is a long winded way around this though (something to do with changing the date in the BIOS). It may have been fixed by now as haven't tried both together for awhile.

---

### Post by Qbeta on 2009-09-19
Tried that.  That was the first thing I tried in fact.  My graphics card didn't work with the rt kernel.  Something about the nvidia driver's interaction with the rt kernel or maybe the driver wasn't even found, I forget which.  Of course when I installed the rt image all those issues should have been taken care of like for any other kernel image but they weren't apparently.

EDIT: Ah, I just read the last bit of your message.  So yes, nvidia and linux-rt don't like each other.  Lovely, now back to my original question, WTF does a desktop machine need a 250HZ timer resolution anyway.  Sorry if I sound peeved but I am.

---

### Post by Bucky Ball on 2009-09-19
Rosegarden is not part of the Ubuntu package. It is part of UStudio. Rosegarden aims to be a high-end digital audio application. It is not exactly Open Office Writer (which if course doesn't require the same specs).

If you are recording 1, 2, 3 things at the same time at high sample rates and are aiming for 'pro' quality, obviously the linux-rt is going to be required. If you are just looking to record yourself on guitar, I would stick to one of the less involved apps.

---

### Post by raboofje on 2009-09-20
> **Bucky Ball said:**
> Rosegarden is not part of the Ubuntu package. It is part of UStudio.

Uh, rosegarden is [definitely](http://packages.ubuntu.com/search?keywords=rosegarden) part of ubuntu. 

> Rosegarden aims to be a high-end digital audio application. If you are recording 1, 2, 3 things at the same time at high sample rates and are aiming for 'pro' quality, obviously the linux-rt is going to be required. If you are just looking to record yourself on guitar, I would stick to one of the less involved apps.

Still, OP correctly points out it would make sense for the 'default' kernel to be configured to run at 1000hz. 

I just checked linux-image-2.6.31-10-generic_2.6.31-10.34_i386.deb from karmic and that's still configured for 250HZ. We should open a launchpad item requesting this to be changed to 1000HZ.

---

### Post by raboofje on 2009-09-20
Added it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433505)

---

### Post by Bucky Ball on 2009-09-20
> **raboofje said:**
> Uh, rosegarden is [definitely]("http://packages.ubuntu.com/search?keywords=rosegarden") part of ubuntu. 

Last I heard you installed it yourself, wasn't part of the Ubuntu install but maybe that has changed in newer releases than 8.04 LTS. It is part of a Ubuntu Studio install.

I am not saying it is not supported by Ubuntu, I am saying it is not included in the apps on the Ubuntu install CD (unless things have changed).

---

### Post by Qbeta on 2009-09-20
> **Bucky Ball said:**
> Rosegarden is not part of the Ubuntu package. It is part of UStudio. Rosegarden aims to be a high-end digital audio application. It is not exactly Open Office Writer (which if course doesn't require the same specs).

If you are recording 1, 2, 3 things at the same time at high sample rates and are aiming for 'pro' quality, obviously the linux-rt is going to be required. If you are just looking to record yourself on guitar, I would stick to one of the less involved apps.

Um no, I don't use Rosegarden for recording but composing and I want to hear the midi playback.  I can't play 5 instruments at once, in fact I'm only a rank amateur on one (guitar).  Some of the weirder stuff I compose can't even BE played as far as I know (chords with 10 notes, etc...).  Only Rosegarden or something like it will do.

As for linux-rt, see my above comments.  I just doesn't work - no graphics so no nothing.

---

### Post by Qbeta on 2009-09-20
> **raboofje said:**
> Added it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433505)

Thank you!!:guitar:

---

