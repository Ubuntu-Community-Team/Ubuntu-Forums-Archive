---
title: "ATI drivers: Proprietary vs. Open-source"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by camilluk on 2006-11-23
I have an AMD-64bit 3200+ with an ATI All-In-Wonder X600Pro graphics card and a Samsung 32" LCD TV

A few months ago I started to try Ubuntu (64bit arch). It took me a while before I could figure out how to make a few things work. Meanwhile it was growing on me every day more. What took me longer to configure was my screen resolution (the tv's native res. is 1360x768 ](*,)

Eventually, the only way I could make it happen was by installing ATI proprietary's drivers, but I'm still not sure whether that's the only way. Truth is, I hardly know what I'm doing when I start editing Xorg & Co.:-k, and it might very well be that I didn't follow properly the how-to's, or perhaps that they didn't apply to my hardware.

A couple of days ago, happy enough that I can spend the rest of my days with (K)Ubuntu, I deleted every bit of NTFS from my HD and reinstalled Kubuntu (32bit arch, because 64bit is a pain in the neck, pls prove me wrong if you can...). Of course, the default resolution is 1024x768 (and as expected it won't give me an option for 1360x768.

Before I install the proprietary ATI drivers again, I would like to know:

1. Can I get 3D accel and a proper resolution with the default drivers shipped with Kubuntu 32bit? If so, how? Is there an ultimate, tested and blessed how-to for this?

2. If the answer to question 1 is 'yes', and therefore they can both handle 3D and proper resolution, are there other pros and cons of going with OS vs. Proprietary?

As soon as it's stable enough, I'd like to install Beryl, should this affect my drivers decision?

Thank you all!
Cam ;)

P.S. About Beryl: as soon as it's bug-free and the word spreads, I think a lot of Windows users will literally flock to Linux.

---

### Post by renzokuken on 2006-11-23
firstly always back up your xorg.conf before you do anything so if it does all go tits up you just copy the original back and can start again

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

apart from that, i would just go for it, im not sure which ones you mean by OS included and proprietary. i would give fglrx driver a go

look here

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

or

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

---

