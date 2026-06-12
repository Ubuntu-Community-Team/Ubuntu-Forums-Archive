---
title: "nvidia.ko not found at boot"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Mblackwell on 2007-02-08
For some reason whenever I boot I have to run

sudo apt-get --reinstall install nvidia-glx linux-restricted-modules-2.6.17-10-generic

or I cannot start X. It gives me an error that it can't find nvidia.ko. I'm forced to do that and start gdm manully every time I restart, which fortunately isn't often. I've done everything I can think of, redone the configs, added "nvidia" to /etc/modules... does anyone else have any ideas?

---

### Post by emperorcezar on 2007-02-09
What exactly is the error message?

---

### Post by Mblackwell on 2007-02-09
```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

(pasted from Xorg.0.log.old)

---

### Post by sstakes1 on 2007-02-10
I got the same error and it has happened after I autoupdated this morning. Last update was done about 2 days ago.:confused:

---

### Post by david_2001 on 2007-02-10
Silly question: Are you installing the correct version of linux-restricted-modules for the running kernel, so the output of 
```
uname -a
```
includes
> 2.6.17-10-generic
and not, for example
> 2.6.17-11-generic

---

### Post by Mblackwell on 2007-02-10
As of this morning I changed it to -11, just to note (because of the kernel update).

Still the same problems though. At least so far. Haven't booted again since this morning.

---

### Post by david_2001 on 2007-02-10
> **sstakes1 said:**
> I got the same error and it has happened after I autoupdated this morning. Last update was done about 2 days ago.:confused:
If you have any custom kernel modules installed, in this case probably the "latest" nvidia driver from the nvidia website, then they have to be reinstalled following a kernel update.  Each version of the kernel has it's own set of modules, stored in /lib/modules/<kernel_version>.

---

### Post by jinho326 on 2007-02-10
I've also been getting the same problems as Mblackwell, where the nvidia.ko file is missing, and so X doesnt start. Funny thing is, this problem is also came up when I tried booting from Sabayon Linux Live CD, and I also got the message that it cant find the nvidia.ko file either...So in both my ubuntu installation and the Sabayon live cd start, kdm doesnt work... What can I do about this?

Thanks

---

### Post by neighborlee on 2007-02-10
> **jinho326 said:**
> I've also been getting the same problems as Mblackwell, where the nvidia.ko file is missing, and so X doesnt start. Funny thing is, this problem is also came up when I tried booting from Sabayon Linux Live CD, and I also got the message that it cant find the nvidia.ko file either...So in both my ubuntu installation and the Sabayon live cd start, kdm doesnt work... What can I do about this?

Thanks

same problem here..nvidia wont boot from fresh install of nvidia-gx and sudo nvidia-xconfig

waz up I can't wait long as I despeately need 3d ;)

this usallly 'just works' here ;)

cheers
nl

---

### Post by david_2001 on 2007-02-11
> **jinho326 said:**
> I've also been getting the same problems as Mblackwell, where the nvidia.ko file is missing, and so X doesnt start. Funny thing is, this problem is also came up when I tried booting from Sabayon Linux Live CD, and I also got the message that it cant find the nvidia.ko file either...So in both my ubuntu installation and the Sabayon live cd start, kdm doesnt work... What can I do about this?

Thanks
A live CD is reporting that it cannot find a file that should be on the CD?  I'm sorry but that's just weird.  Either that or it's the world's most unlikely coincidence :shock:

---

### Post by david_2001 on 2007-02-11
> **neighborlee said:**
> same problem here..nvidia wont boot from fresh install of nvidia-gx and sudo nvidia-xconfig

waz up I can't wait long as I despeately need 3d ;)

this usallly 'just works' here ;)

cheers
nl
If you had the Ubuntu linux-restricted-modules and nvidia-glx packages installed before the kernel update then they would both have got updated at the same time as the kernel.  All the updates came from the same respository, so if you get one then you ought to get the rest.  That's what happened here - I had beryl working nicely before the upgrade and again after rebooting after the upgrade.

One possible cause that comes to mind from looking over some of the related posts elsewhere is version mis-match and the easiest way to make this happen would be to **not** uninstall both the Ubuntu linux-restricted-modules package and the nvidia-glx package before installing the "latest" nvidia drivers from the nvidia website.  If linux-restricted-modules gets updated subsequently but nvidia-glx does not, for example, then this will wreak version havoc.

EDIT: Due to the update, though the previous kernel is left installed it won't boot with the nvidia driver.  This is because the nvidia-glx package will have been set up for the latest kernel, only.

---

### Post by sstakes1 on 2007-02-11
I did not notice the kernel upgrade. Getting the appropriate linux-restricted-modules fixed it for me

---

### Post by neighborlee on 2007-02-11
> **david_2001 said:**
> If you had the Ubuntu linux-restricted-modules and nvidia-glx packages installed before the kernel update then they would both have got updated at the same time as the kernel.  All the updates came from the same respository, so if you get one then you ought to get the rest.  That's what happened here - I had beryl working nicely before the upgrade and again after rebooting after the upgrade.

One possible cause that comes to mind from looking over some of the related posts elsewhere is version mis-match and the easiest way to make this happen would be to **not** uninstall both the Ubuntu linux-restricted-modules package and the nvidia-glx package before installing the "latest" nvidia drivers from the nvidia website.  If linux-restricted-modules gets updated subsequently but nvidia-glx does not, for example, then this will wreak version havoc.

EDIT: Due to the update, though the previous kernel is left installed it won't boot with the nvidia driver.  This is because the nvidia-glx package will have been set up for the latest kernel, only.

yeah I gave up..I tried the removing all and adding a new repo that had the fix supposedly..and adding nvidia-glx again, but no go..there was no right combo of  restric, module and nvidia-glx..uname -r showed 2.6.17-11 yet rest showed 2.6.17-7...so I threw in the towel and went to using 'envy'..even that was causing a weird black screen with flashing cursor upper left corner of screen, until I found another post that said I had to ctrl-alt-F1 first..then it worked flawlessly (once I again removed nvidia-glx) and 3d came right up..

whew...I hope this mess never happens again ;)

cheers
nl

---

