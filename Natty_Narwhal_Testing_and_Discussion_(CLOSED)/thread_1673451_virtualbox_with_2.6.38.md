---
title: "virtualbox with 2.6.38"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2011-01-22
VirtualBox needs some patching to get the kernel drivers to build on mainline 2.6.38.

You need to change <linux/autoconf.h> to <generated/autoconf.h> in the following files:

/usr/share/virtualbox/src/vboxhost/vboxdrv/SUPDrvInternal.h
/usr/share/virtualbox/src/vboxhost/vboxdrv/include/internal/iprt.h
/usr/share/virtualbox/src/vboxhost/vboxdrv/include/iprt/types.h
/usr/share/virtualbox/src/vboxhost/vboxdrv/r0drv/linux/the-linux-kernel.h

/usr/share/virtualbox/src/vboxhost/vboxnetadp/include/iprt/types.h
/usr/share/virtualbox/src/vboxhost/vboxnetadp/r0drv/linux/the-linux-kernel.h

/usr/share/virtualbox/src/vboxhost/vboxnetflt/include/iprt/types.h
/usr/share/virtualbox/src/vboxhost/vboxnetflt/r0drv/linux/the-linux-kernel.h

---

### Post by dino99 on 2011-01-22
many thanks,

this kind of usefull info need to be known by all the hedgers around, might be on other subforums like: tutorials &tips, virtualization

---

### Post by grubdude on 2011-01-28
This might seem like a dumb question but why can't I find this path?
 
/usr/share/virtualbox/src/vboxhost/vboxdrv
 
All I can find is /usr/share/vboxGuestAdditions

---

### Post by cariboo on 2011-01-28
Try /etc/init.d/vboxdrv

---

### Post by grubdude on 2011-01-28
Thank you sir! :-)

---

### Post by grubdude on 2011-01-28
All I get there is vboxadd and vboxadd-service
 
Beats me. I cannot find the path.

---

### Post by SevenMachines on 2011-01-28
Packages install module src for dkms to /usr/src/virtualbox-ose-3.2.12/ for me

---

### Post by grubdude on 2011-01-28
All I see is usr/src/vboxguest-3.2.12
 
Sure would like to fix this..very annoying without guest additions. :-)

---

### Post by cariboo on 2011-01-28
There is a new vesion of vbox available 4.0.2, it installs with the latest generic kernel with no problems.

@grubdude, it looks like your vbox install is broken, so might just as well install the newer version from [virtualbox.org]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by grubdude on 2011-01-28
Thanks for the update. I was just about to upgrade to 4.02.... :-)
 
Sure hope it is backward compatible with existing vms....

---

### Post by areteichi on 2011-01-29
> **jfernyhough said:**
> VirtualBox needs some patching to get the kernel drivers to build on mainline 2.6.38.

Thank you so much for this!:KS
After spending a good few hours looking for a solution, I was about to give up trying to fix this problem before I saw this thread. Now that your tip fixed it, I'm well and happy again!!!:mrgreen:

---

### Post by dino99 on 2011-01-29
well i've made the changes indicated into post #1, but it seem not enough, i get:

localhost dkms_autoinstaller: vboxhost (4.0.2): Installing module on kernel 2.6.38-1-generic-pae.
localhost dkms_autoinstaller: (bad exit status: 10)
localhost dkms_autoinstaller:   Build failed.  Installation skipped.

so we still need an update or some more tweaks

---

### Post by SevenMachines on 2011-01-29
If anyones sticking with ose like me, attached is the diff i'm using with current natty version which should get it working for the moment
```
$ cd /usr/src/virtualbox-ose-3.2.12
$ sudo patch -p1 < /path/to/file/autoconf-include-fix.diff
$ sudo dpkg-reconfigure virtualbox-ose-dkms
```

---

### Post by Peter Besenbruch on 2011-04-19
I found a simpler way of fixing the issue. You create a link from the /usr/src/linux-headers-2.6.38-generic/include/generated/autoconf.h to /usr/src/linux-headers-2.6.38-generic/include/linux/autoconf.h. It accomplishes what the original poster wrote, but also maintains backwards compatibility. It's also much less work. In other words:

ln --symbolic /usr/src/linux-headers-2.6.38-8-generic/include/generated/autoconf.h /usr/src/linux-headers-2.6.38-8-generic/include/linux/autoconf.h

Adjust as needed for your kernel type and version.  This worked for me.

---

### Post by recluce on 2011-04-19
I am really not sure what this thread is all about. Older versions of virtualbox (4.01 and earlier, IF memory serves) did not work with kernel 2.6.38 - and were not intended to (visit the virtualbox forum about this, if you like).

I am currently running virtualbox 4.04 on kernel 2.6.38-8 (generic) withount any tricks, smoke or mirrors. Maybe important, even though I doubt it: I run the backported kernel from Natty on a Lucid base (64 bit).

---

