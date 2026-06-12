---
title: "No wired internet connection - Atheros AR8162"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by wildonion on 2013-03-07
Hi-I'm trying to do a new install of ubuntu 12.10, but I have no wired internet access, only wireless. I've been trying to follow the steps found in post # 4 of this link: [HTML]ubuntuforums.org/showthread.php?p=12206393A[/HTML] but I running into some errors. The terminal commands I'm inputting seem to be going well until I input sudo make install, and I get the following error: 

```
ubuntu@ubuntu:~/compat-wireless-3.5.1-1-snpc$ sudo make install
Updating Ubuntu's initramfs for 3.5.0-17-generic under /boot/ ...
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Will now run update-grub to ensure grub will find the new initramfs ...
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
make: *** [uninstall] Error 1
```


I'm not really sure what to do from here.

---

### Post by wildonion on 2013-03-08
I'm actually trying to run the fix that the user chili555 lists while using linux from the live cd. In other words, I'm trying to fix the ethernet problem before I install ubuntu, so I'm wondering if just running ubuntu from the live cd is keeping me from fixing the problem.

---

