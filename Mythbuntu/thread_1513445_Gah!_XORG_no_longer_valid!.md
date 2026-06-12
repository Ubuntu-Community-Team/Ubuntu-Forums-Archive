---
title: "Gah! XORG no longer valid!"
date: 2010-06-19
forum: Mythbuntu
---

### Post by dsbw on 2010-06-19
OK, so I'm trucking along with 10.04, got most of my kinks worked out, but low on disk space.

So I get another external drive (1.5TB) and plug it in. But now I get the dreaded "ubuntu is running in low-graphics mode". This may be unrelated, I realize. Probably is. I hadn't rebooted in quite some time.

But anyway, the Nvidia control panel ssys I'm not using the NVIDIA X driver, so run nvidia-xconfig and restart. I get warnings:

WARNING: No Layout specified, constructing implicit layout section using screen "Default Screen".
WARNING: Unable to find CorePointer in X configuration; attempting to add new CorePointer section.
WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device.
WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.
WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

Ohhhkay. That doesn't seem very promising. It doesn't change anything, so I revert to an xorg.conf I knew worked last week; that I had used for months. That error message is shorter (EE)No device found, but no more helpful.

So I go back and redo the nvidia xconfigure and take a closer look at the message:

(EE) date/time NVIDIA(0) Failed ot initialized the NVIDIA graphics device. Please check your system's kernel log for additional error messages and refer to Chapter 8: Common problems in the README for additional information.

Failed to initialize the NVIDIA graphics device! Screen(s) found, but non have a usable configuration.


```
Jun 19 11:06:09 castle kernel: [45601.023055] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:09 castle kernel: [45601.024391] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:09 castle kernel: [45601.024407] NVRM: rm_init_adapter(0) failed
Jun 19 11:06:09 castle kernel: [45601.312872] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:09 castle kernel: [45601.313494] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:09 castle kernel: [45601.313502] NVRM: rm_init_adapter(0) failed
Jun 19 11:06:09 castle kernel: [45601.615056] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:09 castle kernel: [45601.615681] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:09 castle kernel: [45601.615689] NVRM: rm_init_adapter(0) failed
Jun 19 11:06:10 castle kernel: [45601.911914] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:10 castle kernel: [45601.912538] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:10 castle kernel: [45601.912546] NVRM: rm_init_adapter(0) failed
Jun 19 11:06:10 castle kernel: [45602.189839] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:10 castle kernel: [45602.190450] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:10 castle kernel: [45602.190458] NVRM: rm_init_adapter(0) failed
Jun 19 11:06:10 castle kernel: [45602.446171] vmap allocation for size 16781312                                           failed: use vmalloc=<size> to increase size.
Jun 19 11:06:11 castle kernel: [45602.641347] NVRM: RmInitAdapter failed! (0x26:                                          0xffffffff:1076)
Jun 19 11:06:11 castle kernel: [45602.641364] NVRM: rm_init_adapter(0) failed

```

Well, that's sure a lot of additional error messages. I'm not sure about Chapter 8 (of what?) or README. 

Any clues?

---

### Post by ian dobson on 2010-06-19
Hi,

Maybe try uninstalling then reinstalling the NVidia driver.

I had a similar problem and reloading the driver fixed it.

Regards
Ian Dobson

---

### Post by dsbw on 2010-06-19
Well, as mysteriously as it appeared, it has now gone away.

---

### Post by dsbw on 2010-06-20
> **dsbw said:**
> Well, as mysteriously as it appeared, it has now gone away.

And now it's back. :confused:

---

### Post by dsbw on 2010-06-20
I've tried uninstalling and reinstalling. No joy.

I tried installing the 173 driver, which made it worse. I tried installing the one labeled "nvidia", which just plain didn't install. Then I switched it back to the default and am back where I was.

---

### Post by dsbw on 2010-06-24
Anyone? Normally I'd use Envy but its replacement is apparently built-in!

---

### Post by dsbw on 2010-06-27
> **dsbw said:**
> Anyone? Normally I'd use Envy but its replacement is apparently built-in!

Manually updated to the latest (June 22) drivers from NVIDIA.

That worked till I rebooted.

---

### Post by andree_b on 2010-06-28
Make sure to use the ubuntu tool (i think just called "restricted drivers" - at work now cant check) to select the wanted driver. It does some symlink magic that installing directly probably wont do.

You could also try to uninstall(if possible) or blacklist the noveau driver...

But if this error appears random you might also have a faulty/underpowered PSU

---

### Post by dsbw on 2010-06-30
> **andree_b said:**
> Make sure to use the ubuntu tool (i think just called "restricted drivers" - at work now cant check) to select the wanted driver. It does some symlink magic that installing directly probably wont do.

I was only using the restricted drivers dialog until I installed the latest. I can't use it with that (or if I can, I don't know how to).

> **andree_b said:**
> You could also try to uninstall(if possible) or blacklist the noveau driver...

The new driver doesn't seem to be the issue. It's behaving the same for all drivers.

> **andree_b said:**
> But if this error appears random you might also have a faulty/underpowered PSU

I don't really think it's random, though I suppose it could be the PSU. I've been using the same PSU for quite some time now and there aren't any other indications I can see that it has problems. 

I've plugged in some USB drives but they're all powered by wall warts. That's about it.

---

### Post by dsbw on 2010-07-02
Seem to have found my problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470)

Kernel bug.

Didn't notice the error message before. Changed kernels in grub and now it's working. Just have to figure out how to set the default in grub now...

---

