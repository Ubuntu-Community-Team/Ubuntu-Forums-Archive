---
title: "Ubuntu 10.10 x86-64 failing to boot in normal and rescue modes: monitor goes to sleep"
date: 2011-01-30
forum: Multimedia Software
---

### Post by maverick280857 on 2011-01-30
Hi,

I am running Ubuntu 10.10 Maverick Meerkat (64-bit) on my desktop, which has an Intel Core i7 920 CPU, 6 GB DDR3 SDRAM, HP 2309m monitor, and an NVIDIA GeForce GTX295 graphics card.

Everything was working fine until a few days ago, but I think an update of the nvidia kernel module (or possibly the system kernel too) crashed my X Windows. 

Right now, I cannot boot into Ubuntu at all. Grub shows two options - generic and rescue modes, but neither of them works. I see a cursor for a while after I select the generic mode, and then my screen blanks out and the monitor goes into "sleep" mode. The rescue mode boots up till X Windows starts, and I don't see any driver errors before it too forces my monitor to go into sleep mode.

I thought if I could get into the console mode somehow, I could fix the problem by removing the nvidia kernel module, but I am unable to figure out a way to do so. Can this be done through the LiveCD? If yes, how?

Thanks in advance.

---

### Post by maverick280857 on 2011-02-01
Any ideas anyone?

_**Summary**_:

Desktop has Ubuntu 10.10 64-bit installed.

When I boot into Ubuntu from Grub, the monitor goes to sleep. All I can do is press Ctrl+Alt+Del to reboot. Can't get to the console, even through rescue mode.

---

### Post by b0b138 on 2011-02-01
Can you boot to a previous kernel?

I have also had this problem with it updating the kernel and nvidia at the same time.  Since then I've always unchecked the video and done it last and by itself.

---

### Post by maverick280857 on 2011-02-01
> **b0b138 said:**
> Can you boot to a previous kernel?

I have also had this problem with it updating the kernel and nvidia at the same time.  Since then I've always unchecked the video and done it last and by itself.

Unfortunately, no :-(

---

### Post by b0b138 on 2011-02-01
You might be able to chroot from a live cd

```
sudo mount /dev/sdXX /mnt  (XX is where your install is, sda1 for example)
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```

Then remove and install the nvidia driver

```
sudo apt-get remove --purge nvidia-glx-xxx (xxx is 260 on mine)
sudo apt-get install nvidia-glx-xxx
```

Now unmount everything

```
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
```

And reboot (fingers crossed ;))

---

### Post by maverick280857 on 2011-02-02
Thanks b0b138, I tried this, but there seem to be no nvidia-glx-xxx drivers on my system to remove, so I only got "...package is not installed" messages. I uninstalled nvidia-* but it didn't help.

Any more ideas?

---

### Post by b0b138 on 2011-02-02
hmmm....after chrooting, do a sudo apt-get remove nvid <---stop there and hit tab a couple of times. It will autocomlete and show a listing of things installed that start with nvid.

Maybe try removing and install nvidia-current if its there.

---

### Post by maverick280857 on 2011-02-04
Autocomplete didn't work. But There was no nvidia-current installed, and in fact nothing of the form nvidia-*. I'm installing nvidia-current right now, will reboot and update.

---

### Post by maverick280857 on 2011-02-04
Thanks b0b138, re-installing nvidia-current and rebooting solved the problem! 

I have to figure out how to get the nvidia drivers working again (as I use NVIDIA CUDA and cannot work with the generic drivers). But thanks to your chain of commands, I know how to fix the system from the live cd if I screw up again.

Thank you very much!

---

### Post by angus.hendrick on 2011-06-27
I had this exact problem (Ubuntu 10.10 x86-64 with NVIDIA GTX295) after upgrading from an older ATI card. 

I resolved it by editing the grub boot command for the recovery boot option, adding "nomodeset" to the line containing "vmlinuz." This allowed me to boot to a command line.  From there I ran the installation script for the dev drivers for NVIDIA (I also use CUDA) which were previously downloaded.

Rebooting, I added "nomodeset" to the "vmlinuz" line, but this time in the normal graphical boot option.  After successfully booting into the graphical environment with the NVIDIA development driver, I edited /etc/default/grub from 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Finally I ran ```
sudo update-grub
```

It now boots fine.

---

