---
title: "Nvidia Gforce 5200 card"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by albertoramirez on 2006-02-01
Hello:

I've installed Ubuntu 64 on my AMD 64 computer.  It had an integrated Unichrome Pro graphics chip, and Ubuntu didn´t recognized it.  I've installed a Nvidia Gforce 5200 card, so...

Is there any driver or support for this card?  In case of an affirmative answer, What has to be done to make it work?  Is there a way, in case of no driver available, to get it work in a 1280 x 1024 resolution.  The system doesn't allows me to get a better resolution of 1024 x 768.

Thanks!

---

### Post by madmetal on 2006-02-01
nVidia provide drivers for ubuntu.
look at synaptic. its really easy to install them.

---

### Post by albertoramirez on 2006-02-02
Hello:

Well, I've done it, but got no difference, still can't get a 1280 x 1024 resolution.  

After installing the driver, what's next?

Thanks

---

### Post by madmetal on 2006-02-02
what's your monitor?
i got an LG1715s and only the supported resolutions and refresh rates are available.
i use 1280x1024 @75 which is the highest it can support.

---

### Post by albertoramirez on 2006-02-03
Well, I have a LCD Monitor Samsung Syncmaster 710n, and it supports 1280 x 1024 @ 60Hz.

---

### Post by madmetal on 2006-02-03
maybe you should try change /etc/X11/xorg.conf
but i am afraid i can't help more.. (i am a new user )

---

### Post by bikeboy on 2006-02-03
I think the nvidia drivers in synaptic are a bit outdated now. Try these links, I'm pretty sure this is a common question.

[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

Alternatively you could try this:
sudo dpkg-reconfigure xserver-xorg
But it's probably better to leave that a bit longer if you're new to linux and have not done a bit of reading in the other two links.

---

### Post by handy on 2006-02-03
An easy way is to install **Automatix** & let it do all the dirty work for you, it gives you quite a selection to choose from, including the latest nVidia (closed source) drivers.  Just tick the boxes for what you want to install & let her rip!

Here is where it begins:

**[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)**

All the best!
[B]
[EDIT:][/B]  I've installed it on both 32bit & 64bit Breezy 5.10, no problems!

---

### Post by POLO on 2006-02-03
The easiest way to get your correct LCD resolution is to select that resolution in installation.
Just hit "Enter", when it asks you to selestion screen resolutions: unselect with the spacebar the default (1024, 800, 600) and select 1280x1024 and you should be set.

Now looking into installing the offical nvidia drivers to speed up some things...

---

### Post by hashimoto on 2006-02-03
And if you don't want to do a reinstall you can also open a terminal and do:
```
sudo dpkg-reconfigure xserver-xorg
```
This will give you the chance to configure everything including the refresh rates of your monitor, so have your manuals at hand.

---

### Post by btnheazy03 on 2006-04-21
[QUOTE=albertoramirez]Hello:

I've installed Ubuntu 64 on my AMD 64 computer.  It had an integrated Unichrome Pro graphics chip, and Ubuntu didn´t recognized it.  I've installed a Nvidia Gforce 5200 card, so...

Is there any driver or support for this card?  In case of an affirmative answer, What has to be done to make it work?  Is there a way, in case of no driver available, to get it work in a 1280 x 1024 resolution.  The system doesn't allows me to get a better resolution of 1024 x 768.

Thanks![/QUOTE]

I think my setup shares some similarities with yours, so I hope I can help you out.

First of all, have you tried using the card under windows? If so, did you encounter any problems with it?

Next step for you is modifiyng your BIOS so that it appears there's only one card on your computer (the 5200). What happened with me is the BIOS initializes the integrated chipset before the PCI or AGP one, and of course you wouldn't want that. So disable your integrated graphics chipset using your BIOS config (if possible, don't even assign an IRQ to it, as what I did to my integrated Audio/Video chipsets) .. . you may have to modify your xorg.conf for this, otherwise you might be stuck at terminal

Hope this helps

---

### Post by xwindows2 on 2006-04-24
Hey can someone tell me easy way to install video driver for  dapper 6.06 beta,Its running on an amd 1300.. 512 ram.. pny gforce 5200 vid card.
the glx screen savers run really slow.  :confused:

---

