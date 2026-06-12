---
title: "ATI Propietary Driver 9.6 on x1400 and Jaunty."
date: 2009-07-16
forum: Multimedia Software
---

### Post by xflyboy on 2009-07-16
Hi there.
I just installed Jaunty 9.04 on my Dell Inspiron 6400 with ATI Mobility x1400 video card. And went straight to install ATI Propietary Driver for Linux guide.
After some trials, and pices of information went to download v9.6 ATI driver that by [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start")
> Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.6. !!!SO BE CAREFUL!!!  does not support my card. (When i unpacked and prepared the installation, i didn't found that guide. It was after my second install that i found it).
BUT. v9.3 DOES support my card but it does not work with Jaunty X server.
So... For a moment i'm working with default installation and didn't went through any additional install of any kind of driver.
By lsmod i'm using radeon driver. No ATI driver's in "Hardware Drivers" ( i believe it's a restricted driver).
Any recomendation/suggestion of which driver should i install now?

Note: Almost none of the guides gives a clear howto to uninstall driver in case i need to use REPOSITORY driver instead of PROPIETARY one. Or vicereverse.

Regards.

---

### Post by xflyboy on 2009-07-16
[This]("http://forum.linuxmint.com/viewtopic.php?f=49&t=27870&start=0&st=0&sk=t&sd=a")
> to Insane1 (or others with the ATI Mobility Radeon x1400 graphics card) I'm running Mint 7 and my problems were solved by installing the "radeonhd" package.
This is what I did to install the right driver. WARNING - I have to warn everybody (see below) as you might damage your system!

Code: Select all
sudo apt-get install xserver-xorg-video-radeonhd

restart and it might work! (it did for me) More info: [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd) and cheers to them!!


---

### Post by markharding557 on 2009-07-16
unfortunatly you need to go back to intrepid to get a working driver

---

### Post by xflyboy on 2009-07-16
Thanks Mark.

For a time being i'm using [THIS]("http://ubuntuforums.org/showthread.php?t=1130582") solution.
Updated to Stable but Unsupported X Server ATI RADEON Drivers, and .30 kernel.
Regards.

---

### Post by jayhags on 2009-07-17
I guess it depends upon why you need the proprietary ATI driver.

I have the Mobility X1400 in my Acer Aspire 5670 running Jaunty.  The default install used the xorg radeon driver, but I have since installed the radeonhd you found above.  It has been working fine for me.

---

### Post by ale99 on 2009-07-17
RadeonHD DVI limitation:
I have a laptop with ATI x1450 card; You can't get video output on DVI (DVI-D_1). If you plan to connect your PC (i.e. laptop) to your TV via DVI, or S-Video output, the RadeaonHD drivers will not work. Use the Radeon (ATI) drivers. 

Ale99

---

### Post by melharty on 2009-11-02
@xflyboy: I have the same laptop as yours with the same x1400 card. I was really bugged to find out that this card is not supported anymore. Can you please tell/link me with the stable driver you found?

I'm actually on Ubuntu 9.10 now, but I think the Xorg versions are the same.


Nevermind I found your link

---

### Post by Surabaya on 2009-11-12
Hi melharty, 

I have also an X1400 Ati card on a Fujitsu Laptop and running Ubuntu 9.10.
The open source driver looks ok but my resolution stuck to 1280x80 (my laptop can reach up to 1650x1080).
Can you tell me what resolution did you reach?

Thank you!

GG

---

### Post by melharty on 2009-11-12
Haven't had the time to sort that out yet, but will let you know when I do.

---

### Post by TiPy on 2010-01-01
Does anyone experience video tearing with there ati card and opensource driver? if no could you post a solution to video tearing or your xorg.conf file?

thanks

---

### Post by flang3r on 2010-03-22
I have tried many things to get the fglrx driver to work. After installing radeonhd driver described in this forum my display works again and like a charm!
I'm using x1400 on Ubuntu 9.04 Jaunty Acer Aspirt 5670. 

Spread the word!


Thanks a lot guys !

---

### Post by flang3r on 2010-03-22
Or actually, if I type glrxinfo I get :
```
:~$ sudo fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault

```

So, I'm guessing I don't have full compatible driver for my x1400 yet

---

### Post by Yellow Pasque on 2010-03-22
You still have stuff left on your system from the proprietary driver. (specifically, libGL.so and libglx.so)
Remedy:
```
sudo /usr/share/ati/fglrx-uninstall.sh          # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
Log out to restart the X server.

---

### Post by flang3r on 2010-03-22
Ok, thanks again! I did everything and it seems like everything works !

---

### Post by Surabaya on 2010-03-22
> **flang3r said:**
> Ok, thanks again! I did everything and it seems like everything works !

Hi Flang3r, 

I am really interesting with your feedback. 
I am using an Ati Mobility Radeon on a Fujitsu Laptop. My problem is that my screen resolution stuck at 1280 x 800, but shoul be really higher.
Could you tell me what resolution you reach with your laptop? Did you make any special setup to reach it?
Thanks in advance for your help.

Regards, 

Surabaya.

---

