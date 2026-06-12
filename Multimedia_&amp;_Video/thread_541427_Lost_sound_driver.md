---
title: "Lost sound driver"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by p110011 on 2007-09-02
After the Linux header update last night, my sound quit. It's an on-board ECS Mother board AC97 sound.

I was following this thread [http://ubuntuforums.org/showthread.php?t=540296&page=2](http://ubuntuforums.org/showthread.php?t=540296&page=2) and when I try to install the lib I get a message that says "missing file operand"

I was in a hurry or something and I accidentally installed the driver before the lib, I don't know if that caused my problem or if I need to uninstall it somehow?

Anyway I don't have sound now. Maybe someone can help.

---

### Post by linuxwizard on 2007-09-03
Try booting your computer using the  2.6.20-15 kernel and see if you get back your sound.

---

### Post by Tribble on 2007-09-03
I'm having the same problems, so I just tried that...now everything acts like it's working, i.e. volume control and alsamixer, but I don't hear anything. :confused:

---

### Post by p110011 on 2007-09-03
Grub only lists 2.6.20-16

---

### Post by linuxwizard on 2007-09-03
Tribble
Check over your sound card settings something may have been reset or disabled.





p110011
Did you uninstall the kernel or remove 2.6.20-15 from grub ?

---

### Post by p110011 on 2007-09-03
p110011
Did you uninstall the kernel or remove 2.6.20-15 from grub ?[/quote]


No, I thought that was kind of strange too because I normally wait till everything works before I remove an old Kernel.  I see 2.6.20-15 in Synaptic Package Manager.

I see other people resolving their lost drivers by reinstalling the Alsa but I can't even do that.

---

### Post by linuxwizard on 2007-09-03
p110011> I see 2.6.20-15 in Synaptic Package Manager.

Is it installed ? If so try this
If you need to get into the grub menu, to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts. By default you have to press 'ESC' very quickly. After pressing 'ESC' you will be presented with a list of kernels and operating systems that you can boot. See if  2.6.20-generic-15 kernel shows up that way.

---

### Post by p110011 on 2007-09-03
That didn't work.I had to reinstall the older kernel, but it still doesn't show up in Grub.

---

### Post by linuxwizard on 2007-09-03
in terminal > sudo update-grub

---

### Post by p110011 on 2007-09-03
Ok I can't seem to get the 2.6.20-15 kernel installed.

~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by mtb-cliff on 2007-09-03
I am having a similar problem on one of my two machines. It also happened overnight.

followed the comprehensive sound guide - and I also run in to compilation issues. This is on an integrated audio Intel8x0. I have the exact same system  - both running ubuntu. Only one of them stopped working last night.

The sound card is detected as Intel 82801EB/ER by alsaconf and lspci.

I can provide a lot of debug output from the compiler - most of which indicates a missing file in the malloc.

thanks - my kids are driving me nuts to get their sound working again..... Cliff.

---

