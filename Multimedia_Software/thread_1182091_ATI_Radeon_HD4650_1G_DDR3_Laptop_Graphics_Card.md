---
title: "ATI Radeon HD4650 1G DDR3 Laptop Graphics Card"
date: 2009-06-08
forum: Multimedia Software
---

### Post by linux4life88 on 2009-06-08
I know ATI is notoriously bad at supporting Linux but I was wondering how well this card works under Ubuntu. Does it support 3D rendering?

---

### Post by linux4life88 on 2009-06-08
I forgot to say that the laptop that I have running this graphics card is an Asus N81Vp-C1. As I said before I want to know if direct rendering works and if Ubuntu supports the maximum resolution of 1366x768. Any help would be much appreciated.

---

### Post by edu77pose on 2009-06-08
Hi,

I've got a HD4570 laptop video card & I've got it working (3D compiz fusion) by downloading the drivers from the AMD website. I'm pretty sure it'll work for you.  Good thing is they have 32 & 64 bit drivers (4600 series via the radeon.

Go to
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

You'll need to download the installer instructions and basically use this command
sh ./ati-driver-installer-9-5-x86.x86_64.run

Make sure you have a read of the instructions too.  

It worked for me so it should work for you.

---

### Post by linux4life88 on 2009-06-09
> **edu77pose said:**
> Hi,

I've got a HD4570 laptop video card & I've got it working (3D compiz fusion) by downloading the drivers from the AMD website. I'm pretty sure it'll work for you.  Good thing is they have 32 & 64 bit drivers (4600 series via the radeon.

Go to
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

You'll need to download the installer instructions and basically use this command
sh ./ati-driver-installer-9-5-x86.x86_64.run

Make sure you have a read of the instructions too.  

It worked for me so it should work for you.

Thank you so much for the help. I went into restricted drivers and there Ubuntu would allow me to download a driver from there. Is this the same driver or would I be better off to do as you said and get the one straight of of ATI's website. Thanks again for the help. I will let you know how my experience turns out.

---

### Post by edu77pose on 2009-06-10
> **linux4life88 said:**
> Thank you so much for the help. I went into restricted drivers and there Ubuntu would allow me to download a driver from there. Is this the same driver or would I be better off to do as you said and get the one straight of of ATI's website. Thanks again for the help. I will let you know how my experience turns out.

The beauty of getting the drivers from ATI is that they update them regularly, so they get rid of the bugs a lot quicker than what ubuntu can do.  In saying this the updates can change things a bit.  In my short experience the benefits outweigh the adversities. 

ATI have come a long way, since they joined with AMD the support for the linux community is great!

---

### Post by Innova on 2009-07-17
> **linux4life88 said:**
> I forgot to say that the laptop that I have running this graphics card is an Asus N81Vp-C1. As I said before I want to know if direct rendering works and if Ubuntu supports the maximum resolution of 1366x768. Any help would be much appreciated.

How is this laptop working out for you?  Any other driver issues with Ubuntu?

I am very close to buying the D1 version (just a T9600 instead of T9550), and will be running Ubuntu as my primary OS.

Are things going well?

---

### Post by jcMike on 2009-07-17
> **Innova said:**
> How is this laptop working out for you?  Any other driver issues with Ubuntu?
 
I am very close to buying the D1 version (just a T9600 instead of T9550), and will be running Ubuntu as my primary OS.
 
Are things going well?
 
As for me, the best laptops from dell or samsung. :)

---

### Post by nickleus on 2009-10-30
here's what i did to get desktop effects and 3d games working in karmic amd64 with my ATI Radeon HD 4650:
 [http://nickhumphrey.net/showthread.php?p=3345](http://nickhumphrey.net/showthread.php?p=3345)

---

### Post by Vermifugo on 2009-11-03
I just installed karmic and cant get direct rendering with this card.

I instaled the driver from ati home

when i look in glxinfo i get

direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

I tried to change the enviroment variable, but it always reset to 1 when i reboot.

Does anyone solved this by now?

---

### Post by nickleus on 2009-11-04
here's my xorg.conf
```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 1200 0
    Screen         "amdcccle-Screen[1]-1" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "0-LCD"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "right"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "intel"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LCD" "0-LCD"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by adityab88 on 2010-02-08
Hi, i am using Hd 4650 + karmic koala also, and i followed your installation instructions [http://nickhumphrey.net/showthread.php?p=3345](http://nickhumphrey.net/showthread.php?p=3345)

i still cant seem to run compiz fusion. how would i do that? i am new to ubuntu, so any help would be much appreciated :D

---

