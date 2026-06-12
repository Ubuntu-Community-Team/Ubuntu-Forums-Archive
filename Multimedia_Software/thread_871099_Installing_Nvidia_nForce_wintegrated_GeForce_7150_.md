---
title: "Installing Nvidia nForce w/integrated GeForce 7150 as root"
date: 2008-07-26
forum: Multimedia Software
---

### Post by oobsniper2000 on 2008-07-26
I'm still new to Linux so please forgive such a basic question.  I searched the forums and didn't see anything specific to this...

I'm trying to install the nVidia drivers found here:

    [nVidia Linux driver]("http://http://www.nvidia.com/object/linux_display_ia32_173.14.05.html")

Following the instructions listed on the page:

    "sh NVIDIA-Linux-x86-173.14.05-pkg1.run"

I get an error saying it must installed as root.  How do I do that?

I'm running Ubuntu Server 8.04.1 with the Ubuntu Desktop installed on top.

---

### Post by sistoviejo on 2008-07-26
Actually those drivers can be installed easier if you go to:
System>Administration>Hardware Drivers
Then simply enable the Nvidia driver.
You don't need to download it from nvidia's website. Ubuntu does it for you.

---

### Post by oobsniper2000 on 2008-07-26
> **sistoviejo said:**
> Actually those drivers can be installed easier if you go to:
System>Administration>Hardware Drivers
Then simply enable the Nvidia driver.
You don't need to download it from nvidia's website. Ubuntu does it for you.

That brings up the "Hardware Drivers" dialog which says "No proprietary drivers are in use on this system.", the "Component, "Enabled", "Status" columns are all blank, and there are only "Help" and "Cancel" buttons.  Do I need to place the .run file in a specific place?

---

### Post by oobsniper2000 on 2008-07-26
So, I also tried Envy.  It seems to have installed the driver but when it reboots I get some dialogs to choose the monitor & graphics driver and I can't 1.  get the monitor to test properly and 2. get it to select a driver for my hardware.

Basically, all I really want to do is set my display from 800/600 to 1280.  It is proving quite frustrating to do something that should be so simple...

---

### Post by sistoviejo on 2008-07-26
To run a command as root on the console you type sudo before the command.
For example to run ls as root, type sudo ls and hit enter.

If you don't want to deal with the command line you can hit alt+f2 and a dialog will come up. On this dialog you can type gksudo <command> to run command as root.

---

### Post by xc3RnbFO8P on 2008-07-26
Did you try
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

### Post by oobsniper2000 on 2008-07-26
> **Ringi said:**
> Did you try
atl+f2

Choose Generic
and resolution that your monitor supports

Yes, but none of the resolutions seem to pass the test.  I always get the dialog asking to keep the settings but the rest of the screen is hashed black& white so I just choose "no".

I can select the proper monitor resolution of 1440x900 but only 60Hz refresh and the monitor specifies standard resolutions with both 60Hz & 75Hz.

Hardware details:

Monitor:
[HyundaiiIT X93W]("http://www.hyundaiit.com/Eng/product/GoodsView.asp?GoodsCode=134&BigCode=B101&MiddleCode=M102&SmallCode=")
WXGA 1440x900@75Hz
Horizontal Freq 30-81kHz

Graphics:
[MSI P6NGM-F1H]("http://www.msicomputer.com/product/p_spec.asp?model=P6NGM-FIH&class=mb")
 mobo w/integrated nVidia nForce MCP73 with GeForce 7150.  It only has a standard analog VGA connector so I'm not using the DVI on the monitor.

Is the GeForce 7150 part of the "GeForce 7" series when selecting drivers?

---

### Post by xc3RnbFO8P on 2008-07-26
I think 1024x768 is the highest  resolution that will work.
> It only has a standard analog VGA connector

---

### Post by oobsniper2000 on 2008-07-26
> **Ringi said:**
> I think 1024x768 is the highest  resolution that will work.

I tried that as well and get the same results as all other resolutions.

---

### Post by oobsniper2000 on 2008-07-28
I'm been futzing with this and still can't get it to work.  This is the kind of thing that has always driven me away from Linux systems but this time I am determined to get it working.  It's simply way to frustrating for something that should be simple, though.

---

### Post by ErroneousBosch on 2008-08-18
I had a very similar problem on my 7150 when I first got it, and it drove me nuts. Envy does not solve the problem. The issue seems is at least partially that HAL does not have the 7150 in it's list of hardware.

In any case, I was able to solve by editing my xorg.conf thusly:
```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Horizsync 28-72
Vertrefresh 43-60
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```


performance is not great for 3d (not sure if that is the card or my solution)
There is also a bug report that seems related to this:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/242527]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/242527")
I will likely try this solution when I get a chance

---

