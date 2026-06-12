---
title: "Restart fails after partial upgrade on VMWare Virtual Box"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-07-15
I just did a Maverick Meerkat Partial upgrade and restarted. On restart I was asked in GRUB 1.9.8 to choose a kernel type and if I prefer to use recovery mode or not. All choices lead to black screens. It seems Ubuntu gets stuck or can no longer handle a GUI. Neither can I seem to be able to get Maverick running in recovery mode. What to do besides deleting this VmWare Fusion virtual box and starting from scratch?

---

### Post by Stoneface on 2010-07-15
I suddenly managed to enter Ubuntu with the latest kernel in the list: 2.6.34-5. Will see if I can fix all that went wrong.

---

### Post by Stoneface on 2010-07-15
Nah, after restart same issue.

---

### Post by andrewthomas on 2010-07-15
**Update Manager Offers a "Partial Upgrade"? Read This.**
[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

---

### Post by Stoneface on 2010-07-16
> **andrewthomas said:**
> **Update Manager Offers a "Partial Upgrade"? Read This.**
[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

Reading it. I think the issue was either caused by a bad (partial ) upgrade or VMWare VMWare Tools not to play nice with the 2.6.35 kernel in gui mode.
How could I get the latest kernel going again is the question. Only 2.6.34 runs. Reinstalling VMWare Tools failed somehow and I'd say that is causing 2.6.35 to start up and fail with a black screen. I never tinkered much with Grub, but I sort of remembered I could try a non GUI startup.. How again? Pressing I e to edit the latest kernel startup details works, but what to add or remove?

Anyways I can restart using 2.6.34 and run MAverick Meerkat. Only Got an error:
The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet". and if I wanted to remove it. It did not delete it for now.

---

### Post by andrewthomas on 2010-07-16
You might want to check out this thread:

 [http://ubuntuforums.org/showpost.php?p=9592609&postcount=36](http://ubuntuforums.org/showpost.php?p=9592609&postcount=36)

Here is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614)

---

### Post by Stoneface on 2010-07-18
Thanks andrewthomas! ```
set gfxpayload=text
``` from thread [http://ubuntuforums.org/showpost.php?p=9592609&postcount=36](http://ubuntuforums.org/showpost.php?p=9592609&postcount=36) in the GRUB menu config for teh latest kernel worked to log on. I am reading the bug reports and possible fixes for the 2.6.35 gui startup issue probably caused by VMWare Fusion problem VMWare Tools not working properly with 2.6.35/Maverick Meerkat. I will probably adjust GRUB to make this permanently until a proper solution has been found.

---

### Post by Stoneface on 2010-07-18
Well, I added ```
 GRUB_GFXPAYLOAD_LINUX=text
``` to /etc/default/grub and did a ```
sudo update-grub
```. The I restarted. Saw a _ or cursor for a bit, then a black screen and then Ubuntu restarted properly using the latest 2.6.35.8 kernel and all worked. So not as fast a reboot as always, but it works :)

Reading [https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/598542](https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/598542) now. Normally I use VMWare's own tools but if Open Tools work with 2.6.35 quicker I might move.

---

### Post by Stoneface on 2010-07-23
Just tried to reinstall VMWare Tools after the latest upgrade via the update-manager. Still errors: ```
make: Entering directory `/tmp/vmware-root/modules/vsock-only'
make -C /lib/modules/2.6.35-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-10-generic'
  CC [M]  /tmp/vmware-root/modules/vsock-only/linux/af_vsock.o
/tmp/vmware-root/modules/vsock-only/linux/af_vsock.c:312: warning: initialization from incompatible pointer type
/tmp/vmware-root/modules/vsock-only/linux/af_vsock.c:359: warning: initialization from incompatible pointer type
/tmp/vmware-root/modules/vsock-only/linux/af_vsock.c: In function &#8216;VSockVmciStreamConnect&#8217;:
/tmp/vmware-root/modules/vsock-only/linux/af_vsock.c:3224: error: &#8216;struct sock&#8217; has no member named &#8216;sk_sleep&#8217;
```

Might try this patch [http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10](http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10)

---

### Post by Stoneface on 2010-07-23
Well, patch backfired:
```

me@ubuntu:~/Desktop/vmware-7.1-ubuntu10.10-patch$ sudo ./apply_patch.sh
[sudo] password for jasper: 
cp: cannot stat `/usr/lib/vmware/modules/source/vsock.tar': No such file or directory
tar: /usr/lib/vmware/modules/source/vsock.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
./apply_patch.sh: line 13: cd: vsock-only: No such file or directory
./apply_patch.sh: line 14: ../vsock-2.6.35.diff: No such file or directory
Failed to apply patch

```

---

### Post by Stoneface on 2010-08-15
Did the last partial upgrade of Maverick Meerkat. All seems to work well, except rebooting as VMWare's Fusion's bootup using VMWare Tools fails to built. I tried to install VMWare tools but it fails. Even after I got the last VMWare Fusion update (running Version 3.1.1 (282344) now) yesterday. I guess they still have not added 2.6.35 support to the mix yet.

---

### Post by Stoneface on 2010-08-23
Will run Maverick Meerkat using VirtualBox for now until VMWare Fusion catches up again.

---

