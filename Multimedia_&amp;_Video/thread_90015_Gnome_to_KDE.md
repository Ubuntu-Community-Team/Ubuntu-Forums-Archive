---
title: "Gnome to KDE"
date: 2005-11-14
forum: Multimedia &amp; Video
---

### Post by gazruss on 2005-11-14
Hi folks, first post from this very new "newbie"
just finished installing UBUNTU, on my Sony Vaio. Had a problem with getting the correct resolution for my graphics card. After some searching on here i found a fix, but now, when i boot up, the start screen where i would choose either Gnome or KDE is split across my screen. And the part where i would "PICK" is hidden......i can go into Gnome with no problem. but can't get to KDE

Any suggestions :confused:

---

### Post by aysiu on 2005-11-14
I think alt-s lets you select the session type. I could be wrong.

---

### Post by gazruss on 2005-11-14
Thanks for the response, but ALT s does brin up a new window, but the new window is still hidden. It's hard to describe, but there is a black band right in the middle of the screen. The boot screen is on the extreme left side. half in view, half hidden. The hidden half is where the login is....

---

### Post by aysiu on 2005-11-14
Well, you said your normal screen resolution is fine, just not the login screen? Is your normal screen resolution at least 1024 x 768? If so, there may be a fix.

In the terminal (Can you get to a terminal? If not, press Control-Alt-F1 at the login screen), type ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` This makes a backup copy of your Grub menu configuration file.

Then type in ```
sudo nano /boot/grub/menu.lst
``` This allows you to edit the Grub menu config.

Find the entry for Ubuntu. For example, my entry looks like this ```
title           Ubuntu Linux
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
``` Notice how there are some parameters after the kernel part? ro and quiet? We're going to add another one called *vga=791*. So if your entry looked like mine, it would now look like ```
title           Ubuntu Linux
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet vga=791
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
``` Then, to save (control-x), confirm changes (y), and exit nano (enter).

Reboot. Any difference? If not, we can change it back.

---

### Post by gazruss on 2005-11-15
Hi there,
Tried your suggestion, apart from the boot up text changing size, the main Ubuntu boot screen is the same.....I can't post a pic of it cuz now i can't even log on

---

