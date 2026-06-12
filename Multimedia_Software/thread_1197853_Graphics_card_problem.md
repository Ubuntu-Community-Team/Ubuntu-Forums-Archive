---
title: "Graphics card problem"
date: 2009-06-26
forum: Multimedia Software
---

### Post by Jerlad on 2009-06-26
I have a Fujitsu laptop with a S3 Chrome 430 ULP graphics card. Downloaded the drivers from S3 graphics website but failed to install on Ubuntu 9.04. Is my graphics card supported?

---

### Post by tolotos on 2009-06-27
Since s3 is providing al linux-driver I am pretty sure that your card will work with ubuntu.
Such graphic-card related problems can be caused by a huge amount of origins. To determine what went wrong, it is very helpfull to know more about your system and the installation process.
It is for example of importance how you performed the installation of the s3 driver, whether you compiled from source or whether it was an installer, etc. 
Furthermore it is pivotal that you post the error messages with which the installation fails.
What ubuntu version are you using 32bit or 64bit?
This are the points I would start with.

---

### Post by Jerlad on 2009-06-27
Hi,

I am new to this so sorry for the lack of information.

I did exactly what was written in the readme document which came together with the tar file (s3g_Chrome4xx_5xx.14.02.08.tar.bz2). I unzipped the file using archive manager and did what's written there (Go into the directory and did a ./install.sh). After that, I restarted and it states failed and ubuntu have to go into low graphics mode.

Below is the install log:
S3 Graphics Linux Driver Install Log:
Installing/Uninstalling S3G Linux driver built on Linux 2.6.28-13-generic
Cannot find pre-build S3G kernel driver for kernel 2.6.28-13-generic
Found S3G S3 Graphics Chrome440/430 on your system.
[I]Begin installing driver
Install s3g_drv.so sucessfully.
Install libglx.so sucessfully.
Install libGL.so.1.2 sucessfully.
Install s3g_dri.so sucessfully.
Install libva.so.0.28.0 sucessfully
Install s3g_drv_video.so sucessfully.
[I]Begin building kernel modules
[I]End building kernel modules
Install s3g.ko sucessfully.
[I]End installing driver

Thanks in advance. I am using Ubuntu 9.04 32bits.:D

---

### Post by tolotos on 2009-06-27
Hello 

And welcome to the forum. During my first post I haven`t seen, that you just joined  ;-).
> I am new to this so sorry for the lack of information.Absolutly no problem, if you don`t know what information to post or where to find it, you will be asked for it. Thats absolutly ok.
As for your problem:
The installation seems to have completed successfully, so this is most likely not the cause of the problem. A possible cause for Ubuntu switching to low graphics mode is the wrong driver in your xorg.conf.
Open your xorg.conf (/etc/X11/xorg.conf) and search for something similar to the following paragraph:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"  
    VendorName     "NVIDIA Corporation"
EndSection

```While the attributes (nvidia, Device0, ...) may vary the important thing ist that you have the device section. Now change whatever value is set at "Driver" to s3g. 
After that perform a reboot. If further problems okkur just keep asking (and post your xorg.conf along with it ;-)).

tolotos

---

### Post by Jerlad on 2009-06-27
I still have the same problem.

Below is the details in my xorg.conf which will give me error msg:
#
# Sample /etc/X11/xorg.conf file for single card / single monitor configuration.
#

Section "ServerLayout"
    Identifier      "Simple Layout"
    Screen          "Screen1"
    InputDevice     "Mouse1" "CorePointer"
    InputDevice     "Keyboard1" "CoreKeyboard"
    Option          "AIGLX" "on"
EndSection

Section "Module"
    Load            "dbe"
    Load            "extmod"
    Load            "freetype"
    Load            "glx"
EndSection

Section "InputDevice"
    Identifier      "Keyboard1"
    Driver          "kbd"
    Option          "XkbLayout" "us"
    Option          "XkbModel" "pc102"
    Option          "XkbRules" "xorg"
EndSection

Section "InputDevice"
    Identifier      "Mouse1"
    Driver          "mouse"
    Option          "Protocol" "Auto"
    Option          "Device" "/dev/input/mice"
    Option          "ZAxisMapping"  "4 5 6 7"
EndSection

Section "Monitor"
    Identifier      "Monitor1"
    HorizSync       24 - 82
    VertRefresh     55 - 77
EndSection

Section "Device"
    Identifier      "VideoCard1"
    Driver          "s3g"
    VendorName      "S3 Graphics, Inc."
#   Option          "AccelMethod" "EXA"
EndSection

Section "Screen"
    DefaultDepth    24
    Identifier      "Screen1"
    Device          "VideoCard1"
    Monitor         "Monitor1"
    Subsection      "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection      "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
#
#   Display clockwise rotation support (90, 180, or 270 degree)
#   Option          "Rotate" "90"
#
EndSection

Section "Extensions"
    Option          "Composite" "Enable"
EndSection

Section "ServerFlags"
    Option          "IgnoreABI" "True"
EndSection

---

### Post by Jerlad on 2009-06-27
Below is the xorg file which didn't give me error:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Dev



Additional Info:

When my computer says it had to go to low graphics mode, the error is:
- Fail to load module "freetype" (module does not exist)
- Fail to load /usr/lib/xorg/modules/extensions//libglx.so
- Fail to load module "glx"
- Fail to load /usr/lib/xorg/modules/drivers//s3g_drv.so
-Fail to load module "s3g"
-No drivers available

---

### Post by tolotos on 2009-06-28
Your xorg.conf looks fine in my oppinion.

> - Fail to load /usr/lib/xorg/modules/drivers//s3g_drv.so
-Fail to load module "s3g"
Thats the pivotal part. If you compare it to the output of the installation script, you see that these modules have been build. I suppose that the installer copied them into a wrong directory. Search your harddrive for s3g_drv.so and paste a copy into /usr/lib/xorg/modules/drivers/. Hopfully that should do the trick.

---

### Post by Jerlad on 2009-06-29
I have double checked. s3g_drv.so is already in /usr/lib/xorg/modules/drivers.

---

### Post by tolotos on 2009-06-30
Well ok. hmm. I am quite out of ideas right now. The only thing that I could imagine is that the permissions of s3g_drv.so aren`t set correctly. To rule that out try:

sudo chmodd 777 s3g_drv.so (this is allowing absolutly anything. If this should work, you might consider tigther permissions).

You could also try:

sudo modprobe s3g

and see whether this provides a more detailed error message.

---

