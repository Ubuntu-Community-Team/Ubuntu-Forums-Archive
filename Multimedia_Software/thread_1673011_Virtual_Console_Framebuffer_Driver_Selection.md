---
title: "Virtual Console Framebuffer Driver Selection"
date: 2011-01-21
forum: Multimedia Software
---

### Post by polytopal on 2011-01-21
Hello, I registered a while back but haven't really had a nasty stumper till now fortunately, so here goes and thank you in advance for any help at all.

I installed Ubuntu 10.04.1 as that is the newest version listed under the CUDA devdriver download page as the supported version for CUDA development.  Until recently I had done all my CUDA development on version 9.04 which has recently reached its end-of-life.  Upon attempting to install the devdriver I was notified that the open-source Nouveau driver was active, and the proprietary nVidia driver was incompatible.  After performing a cursory, then thorough search I discovered that though GDM was disabled, I was operating in an enhanced graphical console mode, such that a special framebuffer driver was still loaded in memory, tripping off nVidia's checks and stalling the install of the driver package.  I proceeded to uninstall the Nouveau xorg driver package, blacklisted it from loading by appending "blacklist nouveau" and "options nouveau modeset=0" as separate lines into "/etc/modprobe.d/blacklist.conf."  Though this step that follows may have been unnecessary, I rebuilt the initial ramdisk after backing up the old one using the following command "mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`," after which I also included "vga=normal nomodeset" into the "GRUB_CMDLINE_LINUX_DEFAULT=" line in the "/etc/default/grub" file to restore proper virtual console functionality.  Now while all of this allowed me to properly install the developer CUDA enabled driver, it disabled the possibility of running enhanced framebuffer modes, whenever I tried by swapping "vga=791" into the "GRUB_CMDLINE_LINUX_DEFAULT=" line, all Virtual consoles accessible via ctrl-F1-6 key combinations are garbled and unreadable, and would sometimes cause lockups.  From what I understand I've gotten rid of the virtual console framebuffer driver, without properly selecting an alternative, I would greatly appreciate any hints on setting up/selecting a new console framebuffer driver.

An extra twist, I ran the following command "grep -Ri nouveau *" from /etc binary files: ld.so.cache and /usr/bin/Xorg (from symbolic link /etc/X11/X) matched it, I don't understand why the Xorg binary would have references to Nouveau built directly into it... does/should this affect the approach I might take to solve this problem...

Thanks again!

---

