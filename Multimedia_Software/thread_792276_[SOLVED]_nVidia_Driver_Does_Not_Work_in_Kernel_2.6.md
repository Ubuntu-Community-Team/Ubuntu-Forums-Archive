---
title: "[SOLVED] nVidia Driver Does Not Work in Kernel 2.6.24-16"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Zer0Nin3r on 2008-05-12
After upgrading recently to 8.04 display would kick into safe mode.  Tried upgrading to nVidia driver [169.12]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") and reverted back to my backed up xorg.conf as I was still having problems displaying on my HDTV.  This is with kernel 2.6.24-16

New driver also proved incompatible with the old kernel (2.6.22-14) so I reverted back to the the old driver that had been working for me before the upgrade ([100.14.19]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html")).  I am able to get a normal display when running 8.04 under the 2.6.22-14 kernel with the old driver.

How do I get the the display to work correctly in the newer kernel (2.6.24-16)?

My xorg.conf is displayed below

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GS]"
    Driver         "nvidia"
    Busid	   "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "TVStandard" "HD480i"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```


**Update**
nVidia keeps an archive of Linux drivers [here]("http://www.nvidia.com/object/linux_display_archive.html").

---

### Post by Zer0Nin3r on 2008-05-20
Alright, an update.

So I managed to get the nvidia driver (169.12) to work with the current kernel that installs with 8.04.  I used the tty method and stopping the gdm rather than booting into recovery mode terminal.  Everything works fine until I reboot and then it boots back into safe mode.  If I reinstall the driver again the display and driver start working again.  I am still using the xorg.conf from my last post.  Also, I uninstalled the *nvidia-glx-new* which was conflicting with the driver from nVidia.

**Update**
Solved the problem via this [post]("http://ubuntuforums.org/showthread.php?p=4970051#post4970051").

---

### Post by WunSick on 2008-05-20
I also have this issue with my 8800GT card on my desktop.  All routes seem to give me no help at all.

---

### Post by Zer0Nin3r on 2008-05-21
Have you tried the following before your install of the nVidia driver?

```
sudo apt-get install build-essential
```

Try that and if already installed try the '--reinstall' operator with it too.

---

### Post by fsckedagain on 2008-05-21
try this;

load the driver so you can get it running properly in x. Then open nvidia-settings in x so you can get the EDID (select your display on the left and there will be a button that says "acquire EDID"). Save the edid.bin file to a place you can remember.

Edit your xorg.conf file and find the Device section add this to it;

Option         "CustomEDID" "DFP-0:/home/mike/edid.bin"

My Device section looks like so;

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "CustomEDID" "DFP-0:/home/mike/edid.bin"
EndSection


Worked great for me, I was having all kinds of issues. White screen black stripe, wrong kernel module loading, etc.

This solved them all. If you need more help, PM me.

fyi I am running a Dell Precision M4300 with an NVidia Quadro 360M 512MB card.

gl

---

