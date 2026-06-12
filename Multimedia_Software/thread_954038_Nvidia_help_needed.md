---
title: "Nvidia help needed"
date: 2008-10-20
forum: Multimedia Software
---

### Post by airjrdn on 2008-10-20
I just switched from Ubuntu 64bit to Ubuntu 32bit primarily because of compatibility issues.  Since switching, I've tried installing Nvidia drivers the same way I did before and can't get them working.  I've walked through the procedure probably 5 or 6 times now so I'm pretty sure it's not a typo here or there.

For reference, I am running a newly compiled kernel, which I had to do to get my Creative Labs X-Fi drivers working.  Note that I also did this under 64bit.  The link to how I did the sound drivers is here - [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

The link I've used for trying to install the Nvidia drivers is here - [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

I've also tried using the nvidia-glx-new stuff from the repository, but they don't work for me either.  In both cases, I get a black screen, a flash (repeat a few times), then a screen with a lot of jumbled up colors on the screen that doesn't go away.

I've removed the nvidia-glx stuff, and can do the commands to remove the propietary ones via the 2nd link above if necessary.

For reference, here's the hardware:
```

Monitor:Gateway FHD2400
Case:   Antec Nine Hundred
PSU:    OCZ GameXStream 700W Power Supply
MB:     EVGA 122-CK-NF68-A1 LGA 775 NVIDIA nForce 680i SLI ATX Intel Motherboard
CPU:    Intel Core 2 Quad Q6700 Kentsfield 2.66GHz LGA 775 Processor Model BX80562Q6700
HS/Fan: Arctic Cooling Freezer 7 Pro Cooler
Video:  2x EVGA 768-P2-N831-AR GeForce 8800GTX Superclocked 768MB 384-bit GDDR3 PCI Express x16 HDCP Ready SLI
RAM:    DDR2 2GB (2x1GB) PC6400C4, CL4-4-4-12, 800MHz, CorsairTWIN2X2048-6400C4
HD:     Seagate 500GB Serial ATA/300 16MB Buffer ST3500641AS-RK - Retail
        (?) 250G PATA
DVD:    Black NEC 18x DVD Multi Writer Burner AD-7170A, 18X DVD+/-R, 8X DVD+RW, 6X DVD-RW, OEM
Sound:  Creative X-Fi Xtreme Gamer

```

---

### Post by tuxxy on 2008-10-20
> **airjrdn said:**
> I just switched from Ubuntu 64bit to Ubuntu 32bit primarily because of compatibility issues.  Since switching, I've tried installing Nvidia drivers the same way I did before and can't get them working.  I've walked through the procedure probably 5 or 6 times now so I'm pretty sure it's not a typo here or there.


Out of curiosity what compatibility issues are these that you mention?

The 8800 cards should run fine, have you tried envyng to install the correct driver?

---

### Post by airjrdn on 2008-10-20
Thanks for replying, I haven't tried envy, I did run across instructions on removing drivers installed by envy.  Do you have a link to the latest suggested method of using envy to install them?  Also, do you know the difference between the drivers the different methods install?

As for the compatibility issues, Flash is flaky, but I understand that may not be a 64bit issue.  XBox Media Center did seem to be a 64bit issue though.  The other day I wanted to show the little ones Celestia (planets, etc.) and I installed each version in the repository, and only one had menus, and for whatever reason, it wouldn't show Sol (the sun).  Initially, it didn't show anything, but after closing it and opening it a couple of times, it would show earth.  There were other things the other copies showed, but it wouldn't.  The reason I wanted to use it was because of the menus it had.

I'm trying to remember other things people have suggested may be because I was running 64bit, but my mind is coming up blank. :)

---

### Post by airjrdn on 2008-10-20
Well, I installed envy, and used it to install the nvidia drivers.  Result?  Same.

When I boot up, I get a grayscale window allowing me to click configure, shutdown, or continue.  Continue gives me the inevitable black screen.  I've gone into configure and selected nvidia Geforce 8 series (for both cards), and selected generic 1920x1200 monitor because my Gateway model isn't listed.

Oh, and the really wonderful part?  The fact that it jacks my sound card drivers and I have to redo those everytime my video drivers mess up.

Wonderful

---

### Post by spkenny on 2008-10-21
I'm having compatibility issues with the accelerated graphics driver option.  To use compiz, I had to enable the accelerated driver.  This was done on 3 different nvidia cards, and with different results, but ultimately the same as in what air said was happening to his.  Sometimes it wouldnt even let ubuntu load until I would uninstall or disable the driver.  Oh and what is envy by the way?

---

### Post by airjrdn on 2008-10-21
[Envy]("http://albertomilone.com/nvidia_scripts1.html") seems to be an application that allows simplified installation of ATI and Nvidia drivers.

Given that the result was the same whether I installed them manually or w/Envy, I suspect the problem is with the drivers, Ubuntu, or both, and that when it works, I'll be able to more easily install them using Envy.

---

### Post by dredwerker on 2008-10-21
I have a 9800gt and I just installed the latest drivers from the Nvidia website by just downloading the '.run', going to a command line and 'sh' running their driver install.

It does something with a kernel module but runs fine thereafter. I am running at 1900*1200 quite happily with KDE4 effects on.

---

### Post by airjrdn on 2008-10-21
I don't know.  The fact that the ones via synaptic don't work, the ones from envy don't work, and the ones done manually don't work, and the fact that I've loaded the manual ones via that method a couple of times successfully suggest there's something else not right.

I did some searches and saw others having the same problem, which also suggests something is amiss.

---

### Post by RedRat on 2008-10-21
For information about Envy and the newer version EnvyNG see this link:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

