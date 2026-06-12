---
title: "GeForce Ti 4200"
date: 2008-05-12
forum: Multimedia Software
---

### Post by thestenz on 2008-05-12
Hi. I am trying to use a GeForce Ti 4200 (128 mb) video card with Ubuntu 8.04. I want use the TV and acceleration so I am trying to use the Nvidia drivers. I have tired all three versions (new, regular, legacy) none seem to recognize my card and they only leave very low resolution options avilable to me. I want to know which is the right driver (the plain nvidia-glx?) and get the proper resolutions. Thanks!

---

### Post by nick_h on 2008-05-14
The nvidia-glx is the correct driver.  I enabled mine through System->Administration->Hardware Drivers and it works with Visual Effects in Hardy.

I don't use the TV out.

---

### Post by Lucky LIX on 2008-05-14
I'm using the Geforce Ti4200 without problems, worked out of the box with correct settings and now running nvidia-glx
For TV out I use Nvtv TV OUT, which worked in 7.10 but I haven't tested it in 8.04 yet.

---

### Post by thestenz on 2008-05-14
If it helps (and my bet it won't), I am using an old Dell (I hate Dell but it was free) Optiplex GX260. The is built in video, but all video seems to be coming through the GeForce card. The nvidia-glx driver just won't work once I turn it on in the Hardware Drivers. The machine also can't seem to identify the monitor, and the card name doesn't show up in the xorg.conf file. I have also tried 7.10 and had similar issues. I might try 7.04 or even 6.10 just to see if it works for reference. I have read an older Nvidia driver series (80.x.x) works. I need to track those down. Any ideas would be greatly appreciated. I have been googling up a storm an found very little.
I have a homebrew a GeForce 6200 that used the nvidia-glx-new driver without a problem.

---

### Post by nick_h on 2008-05-15
Check which card you have with by typing:
```
lspci -nn | grep -i nvidia
```

Lookup the required driver in the list of legacy drivers [here](http://www.nvidia.com/object/IO_32667.html).  Use the PCI ID to get an exact match.

I think you will need 1.0-9639 which is probably what you have installed.  You could always try downloading it from the [nvidia site](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html).

---

### Post by thestenz on 2008-05-15
Thanks Nick. I'd like to say things worked out well. Your post gave me a ray of hope. But the package would get an error at 100% and say a module could not be made. I meant to port the result of the grep, but I got so fed up with dealing with this for days, I formatted the machine. I can tell you it was (as I thought) a GeForce Ti 4200 with AGP 8X (r1) there was no apparent hex number (PCI ID) just "(300)" which doesn't match the card's number on the site. I'm trying 7.04 now to see if it makes a difference, but 7.10 didn't work either. I'm losing hope quickly. The goal was eventually to make this a mythbox.

Progress update: I installed Ubuntu 7.04 and the Nvidia drivers work just great. In fact it is the version you suggested. Now the next thing is how to get it to work in 8.04...

---

### Post by nick_h on 2008-05-16
I just noticed that nvidia-glx installs 96.43.05 in Hardy.  The GeForce Ti 4200 is not on the supported list for that version - but it works for me.

Try installing 1.0-9639 on Hardy.  As far as I can remember it will compile a kernel module so make sure you install the *build-essential* package first.  You will also need to stop the X server before installation.

---

### Post by thestenz on 2008-05-16
Hello Nick and all. As I said above I got fustrated and formatted the machine.

The result of the grep was 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] [10de:0281] (rev a1).

When I tried the 1.0-9639 package (in 8.04 before the format) it got to 100% and said there was an error and the module failed.

I installed Ubuntu 7.04, which as it turns out, uses 1.0-9639 as the accerlated Nvidia Driver. It worked fine. So I took my chances and ugraded to 7.10. It left the nvidia driver alond and still works with the acceleration on. I'm not sure whether or not to press my luck and upgrade it again to 8.04.

---

