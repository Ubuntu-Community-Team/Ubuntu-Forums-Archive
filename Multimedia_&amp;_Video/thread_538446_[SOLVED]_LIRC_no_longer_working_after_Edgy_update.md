---
title: "[SOLVED] LIRC no longer working after Edgy update"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by Dertiger on 2007-08-30
I had MythTV 0.20 working well on Edgy.  I updated myth to .20.2 to support the new TV guide service and decided to update the entire system, which included a new kernel.  Now the remote control isn't working (LIRC and Hauppage 150).  I've read about /dev/lirc being created at /dev/lirc0 or /dev/lirc/0, but I don't have any of these devices.

The output of 

```
ls -l /dev/licd*
```

gives this

```
srw-rw-rw- 1 root root 0 Aug 29 21:48 /dev/lircd
```

Why isn't my device being created?  Everything worked yesterday before the update.

dmesg | lirc shows this:

```
[17179616.612000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179616.612000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
```

and /var/log/syslog shows this:
```

Aug 29 21:05:02 localhost lircd-0.8.2-CVS[6371]: lircd(userspace) ready
Aug 29 21:05:06 localhost lircd-0.8.2-CVS[6371]: accepted new client on /dev/lir
cd
Aug 29 21:05:06 localhost lircd-0.8.2-CVS[6371]: could not get file information 
for /dev/lirc
```

Any suggestions would be appreciated!

---

### Post by Dertiger on 2007-08-30
I just found this thread:

[http://ubuntuforums.org/showthread.php?t=487674&referrerid=87672](http://ubuntuforums.org/showthread.php?t=487674&referrerid=87672)

but I can't accept that mine is a hardware issue since the problem occurred after updating the kernel.  Just to be sure, I reseated the IR connector and rebooted with no success.

---

### Post by morgwon on 2007-08-31
You need to rebuild the lirc modules if you updated the kernel. Once you do that you should be good. If you followed [this guide]("https://help.ubuntu.com/community/Install_Lirc_Edgy") then 

Rebuild Modules

If you ever need to rebuild your lirc modules for a new kernel version, here are the correct steps to follow:

    *

      sudo rm /usr/src/lirc*deb
      sudo m-a clean lirc
      sudo m-a update,prepare
      sudo m-a a-i lirc
      sudo depmod -a

You probably want to restart the lirc service afterwards:

    *

      sudo /etc/init.d/lirc restart

---

### Post by Dertiger on 2007-09-01
Problem solved.  I was embarassed to discover that the capture card was not detected, either.  Once I rebuilt the IVTV drivers, the card worked and the IR device was discovered.  All is fine again.  This whole experience is a good reminder not to upgrade unless necessary (or bored!)

---

