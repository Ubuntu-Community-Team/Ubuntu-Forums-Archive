---
title: "Intel HDA - no sound on Breezy amd64"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by outox on 2005-11-07
Hi
I am new with Ubuntu Linux. I've installed it two days ago. Everything is working very nice,  except Intel HDA sound. My souncard has been detected during installation. I can see it in gnome-volume-control, gnome-alsamixer, alsamixer etc.  I've unmuted all channels (PCM etc. but don't have "main" channel in alsamixers) and still have no sound! I have a second card (SB Live 5.1) and when i switch to SBLive, sound is working perfectly. So the question is: why i have no sound with my HDA when i have it in all my alsamixers and have all channel unmuted, and what can i do to fix it??
Plz help me :)

---

### Post by Kallewoof on 2005-11-10
I think this is the same issue described here: [http://ubuntuforums.org/showthread.php?t=86481](http://ubuntuforums.org/showthread.php?t=86481)

I have the exact same problem, for what it's worth.

-Kalle.

---

### Post by Kallewoof on 2005-11-17
Okay, since I didn't see any responses to all the Intel HDA questions, I'll poke into it and puke out what I find here.

This page: [http://spide.blogspot.com/2005/08/softwarerec-install-ubuntu-on-acer.html](http://spide.blogspot.com/2005/08/softwarerec-install-ubuntu-on-acer.html)

It talks about setting up a model that I'm not personally using, but he does describe the Intel HDA. The relevant quote is:
> 
4. Sound Card

To bring up the Intel HDA sound card, we need to repair the broken apic support in kernel.
I am using linux-image-2.6.12-6-686, and assume all following steps are executed on linux-source-2.6.12:
a. Download io_apic.c and mpparse.c to /usr/src/linux-source-2.6.12/arch/i386/kernel/
b. compile kernel (make menuconfig; make; make_modules_install; cp System.map /boot/System.map-xxx; cp arch/i386/boot/bzImage /boot/xxxx; mkinitrd -o /boot/initrd.img-xxxx; etc.
(for ubuntu 5.10, kernel 2.6.12-9-386, need change the line: #define WORKING_SET 1024 in scripts/kallsyms.c to: #define WORKING_SET 65536 )
then apic support is repaired, after this, you can delete acpi=off parameters from your grub menu.list. After grabing latest alsa and install, the sound card can be detected and run.


I'm not sure if the kernel in Ubuntu is fixed at this point, but the post was made yesterday.

Does anyone know if the latest alsa drivers are available from some repository compatible with Ubuntu? Has anyone tried installing them? Did it make a difference? Does anyone know if/when Ubuntu plans to put these drivers into the main distribution, presuming they did make a difference?

Inquisitive today, aren't I? :) Anyway, I'll try to poke at this later today, but I've had so bloody little time to do so that I thought I'd ask if someone else had gone through the trouble already.

-Kalle.

---

