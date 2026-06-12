---
title: "ATI Radeon x1200 Motherboard intergration not getting detected"
date: 2011-05-20
forum: Multimedia Software
---

### Post by grandmasterhack on 2011-05-20
how to i get ubuntu to use my on board gfx card because it can't find it. games that run super fast in windows are bogged down(and proably rendering using the cpu) and it was enough for cube and cube 2.

any command i can use to scan for the mobo card or is it called something totally different than a VGA.

---

### Post by grandmasterhack on 2011-06-21
bump...

---

### Post by pme 72 on 2011-06-21
You could try sudo lshw -C video. That should return information on the enabled video device and driver in use.

---

### Post by grandmasterhack on 2011-06-21
command used: ```
sudo lshw -C video
```

output returned:

```
 *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:f0000000-f7ffffff memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff

```

how do i tell if I'm using the correct driver?

---

### Post by Blasphemist on 2011-06-21
It looks like you are using the open source driver, radeon. Look at this for what you may be able to do to test and tweak it. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you still can't get good enough performance, you could go to the closed source driver. This is the link on that. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Cristina Amazonas on 2011-06-21
I have exactly the same video card ... and it is not properly working as well.
I use Ubuntu 10.04 LTS and don't want to upgrade it, will it work ?
As I could reead they mention the Maverick 10.10 version ...
Thanks !

---

### Post by jocko on 2011-06-22
> **Blasphemist said:**
> If you still can't get good enough performance, you could go to the closed source driver. This is the link on that. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Amd/ATI have not made any driver for that card for years, so there is no way that link can help.

---

### Post by Yellow Pasque on 2011-06-22
The best thing you can do for 3D performance is use the xorg-edgers PPA, and make sure you disable SwapBuffersWait in xorg.conf: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Cristina Amazonas on 2011-06-22
I'm kind of lost :confused:

These instructions are not meant to be executed for beginners ... 
Any script or step-by-step using only terminal commands ?
:(

---

### Post by Yellow Pasque on 2011-06-22
First off, if you tried to install the proprietary ATI fglrx/Catalyst driver, see this: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```
Next, create an /etc/X11/xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
Copy,paste,save,exit,restart.
```

Section "Monitor"
    Identifier     "Monitor0"
EndSection

Section "Device"
    Identifier     "Device0"
    Option "SwapbuffersWait" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by grandmasterhack on 2011-06-28
well i dont know if the other guy tried it but it broke my display in zorin os 5(ubuntu based). the screen looks distorted. but if i use the profile that doesnt use 3d effects (guessing compiz) it works fine. how do i switch back to the open source driver? [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx")

apparently the open source driver is the best choice for me.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by tjones00 on 2011-06-30
Isn't the X1200 part of the RS600 family that was phased out of binary driver support? 

The only solution to using this chipset properly in modern linux is to use the open source driver, turn kms off, and create an xorg.conf to my knowledge.

---

### Post by grandmasterhack on 2011-07-01
> **tjones00 said:**
> Isn't the X1200 part of the RS600 family that was phased out of binary driver support? 

The only solution to using this chipset properly in modern linux is to use the open source driver, turn kms off, and create an xorg.conf to my knowledge.

[LIST]
[*]how do i turn kms off?
[*]Create a xorg.conf where? and what do i put in it?
[/LIST]

---

### Post by jocko on 2011-07-01
> **grandmasterhack said:**
> 
[LIST]
[*]how do i turn kms off?
[*]Create a xorg.conf where? and what do i put in it?
[/LIST]


To turn off kms, [see this post]("http://ubuntuforums.org/showpost.php?p=10960805&postcount=6").

You don't need any xorg.conf just to use the radeon driver. It will be used by default as long as you **don't** have a xorg.conf specifying another driver...

If you have tried to install the fglrx driver, make sure you remove any trace of it and reinstall the radeon driver and the mesa glx and dri modules. [See this link]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx").

---

### Post by superbatlife on 2011-10-24
Ubuntu 11.04 if you have x1270 card, lower your screen resolution as much as possible, 680x480. It stopped drag in mine while watching movies and gaming. As far as driver for that card I am thinking we are out of luck. I am glad my acer laptop works so well with 11.04, I have 0 hardware issues....just sayin...

---

### Post by edantes on 2012-11-23
AMD (née ATI) declared the x1200 "legacy" soon after I bought the motherboard 3 years ago!  There hasn't been Catalysis driver support since. :(

I have been using the xorg's radeon driver since then and has worked fine in a 2D windowing environment.  However, up to 12.04, it would NOT support Unity 3D.

But Surprise! I just installed Ubuntu 12.10 in this same machine and was happy to see that Unity 3D (with Compiz) works fine with the new version of the radeon driver. My luck, I only found that after buying an AMD HD 5450 card which brought no advantage whatsoever, at least not for the usual desktop applications I use.

---

