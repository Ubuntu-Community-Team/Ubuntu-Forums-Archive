---
title: "Steinberg (Yamaha) UR22 on Ubuntu 13.04"
date: 2013-10-13
forum: Multimedia Software
---

### Post by 8rfAAn7 on 2013-10-13
Hi, I've recently bought an UR22 audio interface and I would like it to work on Linux (I use Ubuntu 13.04).  I have already looked on other forums on how to tweak things in the kernel and all that, but I'm not familiar enough with the architecture to make it work.  I've seen, for example, a comment and seemingly working solution posted by Clemens Ladisch ([http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html](http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html)), but I cannot find the file (/sound/usb/quirks-table.h) he recommends to tweak.

Also, I understand some people had a similar problem with the CL1 ([http://ubuntuforums.org/showthread.php?t=2150401&highlight=ur22](http://ubuntuforums.org/showthread.php?t=2150401&highlight=ur22)) and it supposedly works with Kernel 3.11.2 on ArchLinux.  Since Ubuntu 13.10 is supposed to be released soon, supported by kernel 3.11 if I'm right, I'm hoping it will solve my problem.

So, my questions are:

1- Do you thing kernel 3.11 (and/or Ubuntu 13.10) could make the UR22 work on Linux?
2- If not, what could I tweak (the Clemens Ladisch's solution seems so simple, if only I could find the file...) to make it work on Ubuntu?  I am not familiar with kernel tweaking/compiling and all that, so I would need a step-by-step tutorial for that matter.

Many thanks!

---

### Post by Bucky Ball on 2013-10-13
You are using the UR22. The last link suggesting 3.11 is in reference to the Ci1. That whole thread is in reference to that. 

The code they give as an example is already for your device, the UR22. You definitely don't have that file? Does typing:

```
cd /sound/usb
```

... get you anywhere or 'no such ...'? Either way, they give little idea about the details of what exactly they compiled the kernel with.

---

### Post by 8rfAAn7 on 2013-10-13
Hi Bucky Ball, thanks for the answer.  I have tried your code but the directory doesn't exist there. 

 I searched for the quirks-table.h file on my computer and I am 100% sure it doesn't exist.  So I have tried updating my kernel to version 3.11.0.  The good news is there was a blinking light on my UR22 device and now it is constantly lit, which means my computer recognizes the device.  That's a good start!  

The problem now is that I need Ubuntu to recognize my device, I need a driver or something like that.  I think that's what Clemens Ladisch did with the quirks-table.h file tweak.  But as you know, I can't find this file.  I even tried to create it (before updating my kernel) in the "/usr/src/linux-headers-3.8.0-31/sound/usb" directory, but it didn't work.  Any idea on how and where I could use Clemens Ladisch's code?  Or anything else?

Thanks again!

---

### Post by Bucky Ball on 2013-10-13
I posted a much lengthier reply last night but for some reason it didn't get here. Hmm.

Anyway, you do have /sound/usb/quirks-table.h. Do a search for exactly that:

locate /sound/usb/quirks-table.h

You'll find two or three. Matter of figuring out which to tweak. It is there in the regular 12.04 kernel also (I'm using it) so don't think there was any reason to install the newer one either. Who knows? Hope you have installed just the kernel rather than going from a stable release to one that isn't released yet (13.10). If you just installed the kernel, you should still be running 12.04 and the old kernel should still be selectable at boot.

---

