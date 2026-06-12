---
title: "Blank screen during boot only."
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by jondale on 2007-06-11
Immediately after the grub menu the screen goes blank.  After a bit of time it comes back up with the gdm login screen and I can then log in and go about my business like nothing was wrong.   During the boot I can Ctrl+Alt+F1 and watch it go through it's bootup process just fine.

This is a fresh installation of Feisty 7.04 with nothing else on the drive.
I downloaded and burned the ISO to make the install CD.
I do not have this blank screen issue while booting from the install CD.
I didn't notice whether it happened after the initial reboot (after the installation).
I did all the updates (including the kernel) directly after installation and then rebooted (this is when I noticed it).

Dell GX270
P4 2.40 GHz
Intel 82865G Integrated Graphics Controller

My first thought is some graphics setting in the grub config but I am not sure what...
Any thoughts?

---

### Post by Nythain on 2007-06-11
in terminal type
gksudo gedit /boot/grub/menu.lst
find sections that look look like this
```

# defoptions=ro quiet splash

```
and this section
```

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.20-16-generic root=UUID=0f12560a-c71d-4c1f-bd19-ba9a6bf0a417 ro quiet splash
initrd        /initrd.img-2.6.20-16-generic
quiet
savedefault

```

first try adding 
```

vga=792

```
after the quiet splash (or splash quiet)
save the file and reboot

basically whats happening is grub is booting it out of your monitors refresh range, so its killing your monitor while its booting

if just adding vga=792 doesnt help then delete the quiet splash (or splash quiet)
you will lose your splash screen, but it will at least show you something :)

---

