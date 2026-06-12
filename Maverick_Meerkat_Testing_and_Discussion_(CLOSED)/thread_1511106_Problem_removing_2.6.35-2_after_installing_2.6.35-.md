---
title: "Problem removing 2.6.35-2 after installing 2.6.35-3"
date: 2010-06-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-16
I get this:
```
E: linux-image-2.6.35-3-generic: subprocess installed post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
```

---

### Post by DougieFresh4U on 2010-06-16
I have the same issue on one of my installs. I removed .35.3 and still get error with .35.2. Same error message as you are getting.
My other installs do not seem to be affected.
Here is more of the terminal output:

```
[B]Running postinst hook script /usr/sbin/update-grub.
Invalid parameter, 2.6.35-2-generic
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.35-2-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.35-020635rc3-generic (2.6.35-020635rc3) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-020635rc3-generic
Running postinst hook script /usr/sbin/update-grub.
Invalid parameter, 2.6.35-020635rc3-generic
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.35-020635rc3-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.35-2-generic
 linux-image-2.6.35-020635rc3-generic
dougie@Maverick64bit:~$[/B]
```
If I install other kernels, the same error appears with the kernel numbers changing

---

### Post by arpanaut on 2010-06-16
I had that problem yesterday.
I believe it had to do with having the corresponding "linux-headers-*" installed/removed as the case may be.
After that update-grub ran correctly

I had other issues too so this may not apply to you but worth a try.

---

### Post by Yarui on 2010-06-16
This is a problem that started after you tried to delete an old kernel?  If so, you may have deleted something you shouldn't have.  Unless you are just really low on space you would probably be better off just keeping your older kernels.  Sometimes when you are having weird issues it is good to be able to boot into an old kernel to find out if it is a problem with the current kernel.  If you don't like having the extra kernels on your boot list there is an easy fix for that without deleting the old ones.

---

### Post by DougieFresh4U on 2010-06-16
I have rebooted and all boots good. Even with the errors showing for said kernel, it still boots into that kernel ok. So error says problem configuring kernel, but it reboots into that kernel with out any problem :confused:

---

### Post by Yarui on 2010-06-16
That's probably something you should still try to fix.  You want your kernel to be completely functional.  If you are getting errors but it is still booting, that probably just means some random part of the kernel isn't working. It could be something you don't need at all, but it could be something that a piece of your hardware or some random software you use relies on.  If you are able to operate your system without noticing any difference, though, you are probably fine.

---

### Post by DougieFresh4U on 2010-06-17
All appears to be 'normal' after update/upgrades this morning:pg
Using kernel **2.6.35.4**

---

### Post by aviramof on 2010-06-17
Really because i don't see it in the update manager yet i get partial update message and i'm using the main server for updates not my local one.

---

### Post by ranch hand on 2010-06-17
Quit using UM and a lot of your problems will go away.  This one won't because it is too late for it.  There will be an upgrade that will fix it if you just give it time.

During that time I think you could do your self a big favor by re-reading the stickies, particularly the testing FAC thread and the Partial update thread.

---

