---
title: "After Wubi install Grub only shows Windows as boot option"
date: 2010-08-08
forum: Mythbuntu
---

### Post by Henk Poley on 2010-08-08
So I installed Mythbuntu using Wubi on a Win2k3 test system (doing nothing important). After the reboot I go through Mythbuntu setup, again it reboots. On the Windows bootloader I choose Mythbuntu, then grub shows up with only the Windows chainloader.

What do I need to enter on the grub console to boot my wubi install, to run `grub-pc`?

---

### Post by Henk Poley on 2010-08-08
I will need to adapt this code. What are the versions used on a fresh Mythbuntu 10.04 install? Or does it update everything on first boot (so I can check my ubuntu versions)?

```
sh:grub> linux /boot/vmlinuz-(Your version of the kernel) root=/dev/(Your Windows partition) loop=/ubuntu/disks/root.disk ro

sh:grub> initrd /boot/initrd.img-(Your version of the kernel)


sh:grub> boot
```

Source: [http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/](http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/)

Edit, for me it was:

```
sh:grub> linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

sh:grub> initrd /boot/initrd.img-2.6.32-21-generic


sh:grub> boot
```

---

### Post by Henk Poley on 2010-08-08
From my Ubuntu install's /boot:

```
initrd.img-2.6.31-21-generic
initrd.img-2.6.32-21-generic
initrd.img-2.6.32-22-generic
initrd.img-2.6.32-23-generic
vmlinuz-2.6.31-21-generic
vmlinuz-2.6.32-21-generic
vmlinuz-2.6.32-22-generic
vmlinuz-2.6.32-23-generic
```

Edit: 2.6.32-21-generic seems to work.
Edit2: Ah gosh, tab completion works in grub
Edit3: and for root= you can supply /dev/sda1 on most windows PATA systems

---

