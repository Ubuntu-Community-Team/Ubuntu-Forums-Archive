---
title: "Diskless USB: Missing Operating System"
date: 2009-05-10
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-05-10
From 9.04, I prepared a newly FAT32-formatted 1.0 GB USB drive for diskless booting: build i386 image, prepare USB drive. The drive contains:

initrd.img
SYSLINUX.CFG
vmlinuz

Contents of SYSLINUX.CFG:
```
default diskless
timeout 3
prompt 1
label diskless
kernel vmlinuz
append initrd=initrd.img nbdroot=192.168.2.15  nbdport=2000 ip=dhcp quiet splash

```

On either of two PCs (ASUS M3N78-EM or P5WDG-2WS-Pro) when I boot from this drive I get "Missing operating system" and the suggestion to use a different boot drive.

The BIOS on each recognizes the USB drive and allows it to be promoted to the #1 spot in the boot priority and the drive light flashes, so I'm assuming that the systems are in fact trying to boot off the USB.

Nothing's blocking port 2000, but I don't think it even got that far.

---

### Post by DrJohn999 on 2009-05-10
Never try to do this stuff at 8 AM Sunday morning...

Of course, I made the USB drive bootable, and then it worked. What I really meant was, the documentation / prompts imply that a *bootable* drive image is being written. Obviously not the case here...

---

### Post by Verzweifler on 2009-07-01
I'd just like to add for completeness that "made the USB drive bootable" actually means issuing ```
sudo syslinux -sf /dev/your_device
```

Took me quite some time to look it up, so maybe this info is helpful for others and will hopefully save someone's eyes...

Note: I ran into trouble using this on my AMD64 Ubuntu 9.04 because I did not really want some 64-bit stuff on my stick. A chroot to the diskless image did not work either, so I therefore just issued the above command from my running diskless frontend (i386) and it worked like a charme.

---

