---
title: "Web cam not detected"
date: 2012-01-21
forum: Multimedia Software
---

### Post by Popper06 on 2012-01-21
I have a problem concerning web cam in my laptop. After installing Ubuntu 11.10 everything is working like a charm after having made a few tweaks, apart from the built in web cam. The cam is not detected by either Cheese, Camorama or Skype. 
My lspci is:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

Any suggestions???

---

### Post by sudodus on 2012-01-21
Welcome to the Ubuntu Forums,

Look for the webcam using
```
gksudo lshw | less
```

or install and use the GUI program ***hardinfo***
```
sudo apt-get install hardinfo
```

*Edit: by the way, are you new to linux? Has the webcam worked in another version or distro of linux?*

---

### Post by Popper06 on 2012-01-21
The web cam worked flawlessly i Win7. 
I switched to Ubuntu 11.10 and I have not tried any other distros since Ubuntu fully suits my needs.
I would categorize myself as "semi-noobish" concerning Linux but eager to learn!

When using hardinfo, the cam does not appear in the list :-(

---

### Post by sudodus on 2012-01-21
> **Popper06 said:**
> The web cam worked flawlessly i Win7. 
I switched to Ubuntu 11.10 and I have not tried any other distros since Ubuntu fully suits my needs.
I would categorize myself as "semi-noobish" concerning Linux but eager to learn!

When using hardinfo, the cam does not appear in the list :-(
That shows that Ubuntu does not recognize it as a hardware to deal with. It is a general problem, that those who make hardware forget to make drivers for linux. Gradually volunteers manage to make or tweak drivers to manage hardware, but new or unusual equipment may lack support.

One obvious solution is dual booting. Another and more convenient solution is to run Windows in a virtual machine (for example VirtualBox) in order to run hardware, that is not (yet) supported by linux.

---

### Post by Popper06 on 2012-01-21
Ok.
I will try to go with the Virtualbox solution.
Kind of sad though - are there really no appropriate proprietary drivers for web cams to try?

---

### Post by sudodus on 2012-01-21
> **Popper06 said:**
> Ok.
I will try to go with the Virtualbox solution.
Kind of sad though - are there really no appropriate proprietary drivers for web cams to try?
Some manufacturers make linux drivers, for example Brother and nVidia. Some webcams are made with such generic interfaces, that they work with any operating system (at least if it is fairly modern).

Browse the internet for your particular webcam! There might be a driver or some report of success with linux. It is worth trying and maybe get a positive surprise :-)

---

### Post by Popper06 on 2012-01-22
Well, VirtualBox is not really doing the trick for me. I would really like to have a 100 % Ubuntu solution to my webcam problem.
Doing a bit of searching I came by:

[http://www.ideasonboard.org/uvc/#downloadhe](http://www.ideasonboard.org/uvc/#downloadhe) 

About 60% down the list is the webcam in my Acer 5745G notebook. It seems to be manufactured by SuYin.
But I need a driver for it and there is no file to download. Is this because it is already included in the distro?
Sorry to say so, but I am a little bewildered.

Suggestions what to do?

---

### Post by sudodus on 2012-01-22
> **Popper06 said:**
> Well, VirtualBox is not really doing the trick for me. I would really like to have a 100 % Ubuntu solution to my webcam problem.
Doing a bit of searching I came by:

[http://www.ideasonboard.org/uvc/#downloadhe](http://www.ideasonboard.org/uvc/#downloadhe) 

About 60% down the list is the webcam in my Acer 5745G notebook. It seems to be manufactured by SuYin.
But I need a driver for it and there is no file to download. Is this because it is already included in the distro?
Sorry to say so, but I am a little bewildered.

Suggestions what to do?

Yes it is ticked green (working) in that list. I think it means that it should work out of the box with the built-in driver package in the linux kernel (with new kernels). Have you tried if it works with some software (for example Cheese or Skype)? (I understand you have browsed to the manufacturer's site and searched for linux drivers.)

---

### Post by Popper06 on 2012-01-22
I have tried Cheese, Skype and Camorama and neither of them are able to detect the camera :confused:

---

### Post by sudodus on 2012-01-22
> **Popper06 said:**
> I have tried Cheese, Skype and Camorama and neither of them are able to detect the camera :confused: Sorry, I have no more ideas now. Let us hope someone else will help you further...

---

### Post by Popper06 on 2012-01-22
Thank you for your effort, anyway!

---

