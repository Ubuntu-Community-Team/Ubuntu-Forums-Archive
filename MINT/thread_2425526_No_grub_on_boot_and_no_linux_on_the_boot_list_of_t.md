---
title: "No grub on boot and no linux on the boot list of the bios"
date: 2019-08-26
forum: MINT
---

### Post by tackskull on 2019-08-26
Hi there,

I was looking to install Linux Mint in dual boot with windows 10 on my father's laptop. Once I did an install on the distro, once I reboot the pc the grub menu doesn't show (also by pressing esc or shift nothing happen). Even if I get on the boot menu on the pc bios, in the list I can only boot windows, there isn't any Linux distro to boot on.

If can be usefull, during the installation of the distro I clicked on "disable security boot". But once I turn on the pc and I get on the bios, on boot menu there is the voice "secure boot" on "enabled", but I can't get on with the cursor to change it on "disabled". It seems like the option of secure boot is like locked. That's very strange.

So basically the hard disk of this laptop is shared in two, a partition with windows10 working well, and the other with linux installed but not seen by the pc, can you guys help me?

---

### Post by jeremy31 on 2019-08-26
Moved to Mint.
What computer is this?

---

### Post by tackskull on 2019-08-26
Is a ACER Aspire ES 15

---

### Post by jeremy31 on 2019-08-26
Did the install freeze during the grub install?  [https://forums.linuxmint.com/viewtopic.php?f=46&t=300449](https://forums.linuxmint.com/viewtopic.php?f=46&t=300449)

---

### Post by tackskull on 2019-08-26
I remember that the installation was taking a lot of time to create the partitions, I saw the installation gone smooth and ok.

---

### Post by jeremy31 on 2019-08-26
From Live ISO post results for ```
sudo parted -l, efibootmgr
```

---

### Post by oldfred on 2019-08-26
You may need to turn on Secure Boot, set password & then enable "trust". Be sure not to lose UEFI password or reset to nothing when done.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)
Acer Travelmate B117 (success - after some UEFI boot troubles) Trust related
[https://forum.siduction.org/index.php?topic=6272.0](https://forum.siduction.org/index.php?topic=6272.0)

---

