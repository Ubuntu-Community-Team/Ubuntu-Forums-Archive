---
title: "Oh Crap!  nVidia setup?"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by yerdon on 2007-02-21
Hi everyone,

I'm running Edgy and I just bought a nVidia GeForce FX5200 card and plopped it in the slot.  I restarted the computer and now I get:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

If I say Yes, it doesn't help and if I say no, it tells me "The X server is now disabled.  Restart GDM when it is configured correctly."

Question:  How do I configure the "X server" or "GDM"?  I remember doing this some time in the past, but I don't know how to get to it now.

Can you tell I'm new to Linux?  But loving it!

Thank you!

Joseph

---

### Post by Jovec on 2007-02-21
> **yerdon said:**
> Question:  How do I configure the "X server" or "GDM"?  I remember doing this some time in the past, but I don't know how to get to it now.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by yerdon on 2007-02-22
Thank you!  That was it.  Saved!

---

### Post by yerdon on 2007-06-04
After installing some updates the same thing happened again!  This time, doing the reconfigure doesn't work.  I go through the whole thing, but when I try to restart the GDM, it fails.

I thought that I could just reinstall the NVIDIA driver by doing the following command (I downloaded it previously):

```
sudo sh NVIDIA*
``` 

However, when I do that, it takes me through the steps and prompts me that it will need to "compile a kernel interface for my kernel" (same as always).  I press OK and then it gives me an error I've never seen before:

ERROR: Unable to find the kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your kernel and that they are properly configure; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.

I am pretty new to Linux and I have no idea what this means...  HELP!

Thanks,

JD

---

### Post by Nythain on 2007-06-04
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

that should get you everything you need to completely compile the drivers manually...

---

### Post by yerdon on 2007-06-04
Thanks, but when I do that I get an error that says: 

Couldn't find build.  If I type in only the first part, it seems to work fine.  But even doing "sudo build ..." doesn't work.

Thanks!

Joseph

---

### Post by yerdon on 2007-06-04
And why have I never needed it before?  It seems that something may have gone really wrong with those updates...

Any help would be really appreciated!

Thanks,

Joseph

---

### Post by yerdon on 2007-06-04
You know what, the first part was all that was needed.  I just tried it again, and this time it worked!

Thank you!  I am logged back in.

Without this support Ubuntu would not be ready for big time - but you guys are always so helpful!

JD

---

