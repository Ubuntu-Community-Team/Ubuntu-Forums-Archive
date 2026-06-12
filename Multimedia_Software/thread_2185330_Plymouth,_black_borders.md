---
title: "Plymouth, black borders"
date: 2013-11-02
forum: Multimedia Software
---

### Post by han2 on 2013-11-02
Hello,

After installing nVidia propietary drivers, I recovered Plymouth, but now it has a black border around:

[IMG]http://i39.tinypic.com/f2zrc.jpg[/IMG]

I've tried with different resolutions, but it always show the black border, even with resolutions as low as 1024x768. It's as if Plymouth is now not detecting well the monitor's size. The monitor's native resolution is 1920x1080, and before installing the nVidia propietary drivers (and recovering Plymouth) the Xubuntu logo was showing fine, fitting to the screen.

This is what I did to recover Plymouth:

```
1. sudo apt-get install v86d

2. sudo mousepad /etc/default/grub

Replace:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

With:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap"

Replace:

#GRUB_GFXMODE=640x480

With:

GRUB_GFXMODE=1024x768

3. sudo mousepad /etc/initramfs-tools/modules

Add the following line at the end of the file:

uvesafb mode_option=1920x1080-32 mtrr=3 scroll=ywrap

4. echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

5. sudo update-grub2

6. sudo update-initramfs -u

7. Restart.
```

Any ideas?

Regards.

---

### Post by lah7 on 2013-11-02
I have an nVidia graphics card with the proprietary drivers and I have a similar (if not, exact) situation with a black border during start-up. It doesn't bother me though.

My monitor states it is 22" but is 21.5" viewable, everything before the login screen is displayed in a border regardless of it's resolution. It's connection is DVI. As soon as the login screen appears, everything is in its native size. The same goes if I was to plug in a Raspberry Pi (small linux computer) via HDMI into this monitor, even though the system is outputting 1920x1080, my monitor displays it in a border.

From my knowledge of the above situations, it's possibly how the graphic card is outputting the signal and how the monitor retrieves this signal. Already, we've discovered that installing the nVidia proprietary drivers causes the resolution of Plymouth to reduce to 640x480 and create an uglier text splash screen.

All I can ask and suggest is, what connection is from your nVidia card to your monitor? And using the buttons on your monitor, can you find any details about it's signal status (Hz, resolution?)

Alternately, I know that Plymouth is quite picky with resolutions as 1920x1080 didn't work for me. I did pick 1280x720 instead and it now displays the graphical logo, you may wish to try a different resolution to test.

Sorry it's not a solution, but all I know is that it's something to do with nVidia's driver and how its sends the signal.

---

### Post by han2 on 2013-11-03
Thanks for your response, lah7.

I have the same problem: before the login screen everything has the black borders, but from that point on everything is in its native size. I'm using the HDMI connection, and using the buttons unfortunately makes no difference.

Anyway, after some days using it this way I'm getting accustomed to it, so it's  not a big problem. As you say, it has to be related to the nVidia  propietary drivers. Maybe they solve it in future versions (fingers crossed).

Regards.

---

