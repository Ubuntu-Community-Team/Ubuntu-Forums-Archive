---
title: "[Solved] NVidia white screen of Death/Conflicting modules loading"
date: 2008-05-23
forum: Multimedia Software
---

### Post by fsckedagain on 2008-05-23
It was mentioned to me that I should maybe make a new thread with this information. I also would like to give credit where credit is due.

Here is the thread with the longer version of these instructions that I used to fix my issues.
[http://ubuntuforums.org/showpost.php?p=4531425&postcount=12](http://ubuntuforums.org/showpost.php?p=4531425&postcount=12)


try this;

load the driver so you can get it running properly in x. Then open nvidia-settings in x so you can get the EDID (select your display on the left and there will be a button that says "acquire EDID"). Save the edid.bin file to a place you can remember.

Edit your xorg.conf file and find the Device section add this to it;

Option "CustomEDID" "DFP-0:/home/mike/edid.bin"

My Device section looks like so;

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "CustomEDID" "DFP-0:/home/mike/edid.bin"
EndSection


Worked great for me, I was having all kinds of issues. White screen black stripe, wrong kernel module loading, etc.

This solved them all. If you need more help, PM me.

fyi I am running a Dell Precision M4300 with an NVidia Quadro 360M 512MB card.

gl

---

