---
title: "Activate ati's framebuffer???"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by Bombermath on 2007-06-10
Hello all,

I would like to use Mplayer on a framebuffer console (my final goal would be to use tweaked low res modline in fb.modes and display directly in 320x240@60 on my RGB tv) but I really don't know how to proceed!
until now, here's what I did :

- I was able to use vesafb just by adding vga=xxx in the grub menu.lst, the /dev/fb0 was automatically created,  the console displays in 1024x768 but I couldn't change resolution etc... with fbset.

-So I wanted to use a framebuffer especially developed for my video card (ATI Rage Mobility P/M (rev64) ) I think it's ati128fb. so I added "video=ati128fb:mode:1024x768" to the menu.lst but nothing happened.

- also tried to do "mknod /dev/fb1 c 29 32" to create a new framebuffer device but it was not recognized by fbset.

- also tried to modprobe ati128fb, ok but then what do I need to do to assign this with my fb1?
ps= I removed the framebuffer from the blacklist

Sorry if all this questions look unclear or stupid but I'm quite new to linux world and I sometime do things I don't completely understand myself.

Thank you

Summary of my config:
Compaq Armada laptop
Ubuntu 6.10
Ati Rage Mobility P/M AGP 2x (rev64)
Directfb library installed

---

### Post by Hibbelharry on 2007-06-26
you should include the framebuffer module in the initial ramdisk by editing /etc/initramfs-tools/modules , add it there. Then rebuild your initial ramdisk by update-initramfs -u -k all. After that append the correct parameters to your kernel command line, something like video=ati128fb:XRESxYRES.

I'm not sure whether ati128fb is right, i always thought that one was made especially for rage128 chips and yours seems to be a mach64 derivate...

Good Luck
Hibbelharry

---

