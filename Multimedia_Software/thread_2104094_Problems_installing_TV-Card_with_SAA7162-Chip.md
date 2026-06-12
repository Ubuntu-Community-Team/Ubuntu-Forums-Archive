---
title: "Problems installing TV-Card with SAA7162-Chip"
date: 2013-01-12
forum: Multimedia Software
---

### Post by whocares02 on 2013-01-12
I try to install the TV-Tuner-card Pinnacle PCTV 7010ix Hybrid in Ubuntu 12.04 and have several problems:


[LIST=1]
[*]A driver seems hard to get. Finally I think I found one [here]("http://linuxtv.org/hg/~endriss/media_build_experimental").
[*]The compiled kernel-modules get placed in the wrong folder:
[/LIST]

> /lib/modules/3.2.0-**29**-generic/kernel/drivers/media/pci/saa716x/But my kernel version is : 3.2.0-**35**-generic

Output of lspci | grep SAA:
> 04:00.0 Multimedia controller: Philips Semiconductors SAA7162 (rev 01)dmesg doesn't output anything useful regarding to DVB at all.
Typing ```
modprobe  saa716x_ff
```  is giving me this: 
> FATAL: Module saa716x_ff not found.Do I have to apply special settings when compiling the driver? I don't understand why the modules are placed in the wrong folder.

**Edit:** I tried softlinking the subfolder of the wrong kernel-directory. After running > depmod -a, I tried inserting the module again. This time it says: > FATAL: Error inserting saa716x_ff (/lib/modules/3.2.0-35-generic/kernel/drivers/media/pci/saa716x/saa716x_ff.ko): Invalid module format


---

