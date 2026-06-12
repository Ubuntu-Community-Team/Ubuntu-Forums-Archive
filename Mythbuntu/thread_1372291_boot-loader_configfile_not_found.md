---
title: "boot-loader configfile not found"
date: 2010-01-04
forum: Mythbuntu
---

### Post by smartias on 2010-01-04
Hi,
I'm using an out-of-the-box 9.04-Mythbuntu, which is running pretty well. Today I've been looking around in Synaptic Package Manager and found that grub is installed as the boot-loader. Due to the fact that I'm running my Mythbuntu-Box in combination with a HDMI-TV, I don't see anything until the system is started up. That's why I wanted to have a look at the menu.lst-file. But I didn't find this file. The only menu.lst I found is in /usr1/share/doc/grub/examples/menu.lst which is for sure not the one starting up my system.
I don't even have /boot/grub. All I see in /boot is:
```
drwxr-xr-x  2 root root    4096 2010-01-04 11:09 .
drwxr-xr-x 24 root root    4096 2010-01-04 15:32 ..
-rw-r--r--  1 root root  525592 2009-04-17 05:34 abi-2.6.28-11-generic
-rw-r--r--  1 root root  524846 2009-12-02 00:03 abi-2.6.28-17-generic
-rw-r--r--  1 root root   90584 2009-04-17 05:34 config-2.6.28-11-generic
-rw-r--r--  1 root root   90655 2009-12-02 00:03 config-2.6.28-17-generic
-rw-r--r--  1 root root 8009374 2009-05-30 12:41 initrd.img-2.6.28-11-generic
-rw-r--r--  1 root root 8022006 2009-12-05 06:47 initrd.img-2.6.28-17-generic
-rw-r--r--  1 root root  128796 2009-03-27 21:12 memtest86+.bin
-rw-r--r--  1 root root 1871601 2009-04-17 05:34 System.map-2.6.28-11-generic
-rw-r--r--  1 root root 1864864 2009-12-02 00:03 System.map-2.6.28-17-generic
-rw-r--r--  1 root root    1170 2009-04-17 05:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r--  1 root root    1170 2009-12-02 00:07 vmcoreinfo-2.6.28-17-generic
-rw-r--r--  1 root root 3522336 2009-04-17 05:34 vmlinuz-2.6.28-11-generic
-rw-r--r--  1 root root 3513280 2009-12-02 00:03 vmlinuz-2.6.28-17-generic

```

Can anyone please tell what I'm missing and where my config-file is?

---

