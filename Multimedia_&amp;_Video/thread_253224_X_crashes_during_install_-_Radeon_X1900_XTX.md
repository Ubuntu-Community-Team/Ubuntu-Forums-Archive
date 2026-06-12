---
title: "X crashes during install - Radeon X1900 XTX"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by a5an0 on 2006-09-08
Hey all, heres the deal. I'm trying to get a friend of mine into this beautiful operating system of ours. He is running a AMD dual core 64-bit processor, 2 Gig ram, and a Radeon X1900 XTX (monitor can support 1280x720 -- its a widescreen lcd). 

Whenever I boot from the 6.06 desktop cd, the x server crashes, and we get the blue screen, etc, etc, etc. 

Itried changing the driver in the xorg.config to vga and vesa, but it still craps out. has anyoe been able to make this work?

Thanks!

---

### Post by ShinjiLeery on 2006-09-08
> **a5an0 said:**
> Hey all, heres the deal. I'm trying to get a friend of mine into this beautiful operating system of ours. He is running a AMD dual core 64-bit processor, 2 Gig ram, and a Radeon X1900 XTX (monitor can support 1280x720 -- its a widescreen lcd). 

Whenever I boot from the 6.06 desktop cd, the x server crashes, and we get the blue screen, etc, etc, etc. 

Itried changing the driver in the xorg.config to vga and vesa, but it still craps out. has anyoe been able to make this work?

Thanks!

Try to post the xorg error log, so we can help you ;)

---

### Post by tseliot on 2006-09-08
First of all I suggest you to use Ubuntu 32bit.

Please, follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by Inhumane on 2006-09-08
I've had this problem, read the log closely and check what it says your radeon X1900's AGP is, should look like AGP: X : X : X, paste it in the AGP section after you select the drivers and it should work

---

### Post by FireStorm82 on 2007-12-17
i have this same problem and pretty much same hardwrae x1900 vid card 2 gigs of ram and athlon 64 bit processor 

installing 32 bit version, tryed all the install options on the cd, normal mode, safe graphics mode, tryed noapic in the boot options basically i cant install because the live cd wont boot, because in safe graphics mode i get message the graphics server restarted 6 times in 90 seconds its possible something is going wrong, will try again in 2 minutes, and it never works,   in normal mode i just get an black or red screen and nothing happens
is there a way to install with text mode using the live cd or something?

---

