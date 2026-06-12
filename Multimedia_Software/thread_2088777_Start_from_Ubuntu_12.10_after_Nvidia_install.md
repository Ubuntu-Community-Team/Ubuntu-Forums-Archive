---
title: "Start from Ubuntu 12.10 after Nvidia install"
date: 2012-11-27
forum: Multimedia Software
---

### Post by DrStrom on 2012-11-27
Hi Guys, It is not really a problem , but i like to know why Ubuntu 12.10 changed the size of letters from the start screen after i installed the new Nvidia driver 310 ? I installed freshly Ubuntu 12.10 and by that Ubuntu installed the vesa driver who brought a nice and need start screen and a bad desktop. So now i have a nice and need desktop but the start screen is bad! Because the letter size has changed to a big size. it looks like before it was for a high resolution and it is now changed vga standard.

maybe somebody knows how to change that.

thanks in advance

Christian

---

### Post by stinkeye on 2012-11-27
Don't know if this has been resolved yet but I had to download linux-headers-generic
before installing the nvidia driver.

```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by DrStrom on 2012-11-27
Thanks Stinkeye,

the nvidia driver is running perfectly

---

### Post by Bashing-om on 2012-11-27
DrStrom; Hi !

drs305's guide:
> 

[LIST]
[*]UUIDs for linux entries.
[*]**#GRUB_GFXMODE=640x480**
You can add this line and remove the # symbol to make it active. This  entry sets the resolution of the graphical menu (the menu text size). It  provides resolutions supported by the user's graphics card (e.g.  640x480, 800x600, 1280x1024, etc). The setting applies only to the boot  menu text.
[*]From the GRUB 2 menu you can display available resolutions by typing "c" and then at the "grub>" prompt type "vbeinfo"
[/LIST]



fot the complete text/guide:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[INDENT]just try'n to help <== BDQ

[/INDENT]

---

