---
title: "Xorg not working on a fresh install (ati radeon x600)"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by germac on 2005-10-18
I've just installed the new version of ubuntu. Installation is ok but when I boot ubuntu, xorg fails, apparently my graphic card is not recognised. I'm running ubuntu on a Hp Pavilion zd8020ea, 17" WXGA 1440x900@60Hz, Ati radeon x600 128Mb. Ubuntu Hoary and the preview of Breezy worked great but this time it fails. Any solution yet?

---

### Post by mlomker on 2005-10-18
> Ubuntu Hoary and the preview of Breezy worked great but this time it fails.


32 or 64-bit?  You can run **sudo dpkg-reconfigure xserver-xorg** and select the ati or vesa drivers to get back to your desktop for now.

---

### Post by germac on 2005-10-18
[QUOTE=mlomker]32 or 64-bit?  You can run **sudo dpkg-reconfigure xserver-xorg** and select the ati or vesa drivers to get back to your desktop for now.[/QUOTE]

32-bit. I ll try vesa drivers in a moment. It's still a weird problem:???: 
My xorg log also points missing fonts problem. Maybe I need to download them during install to get it to work?

---

### Post by mlomker on 2005-10-18
> My xorg log also points missing fonts problem. 

You need to run the reconfigure.  The font directory changed in Breezy.

---

### Post by germac on 2005-10-18
I tried the reconfigure with vesa and ati drivers, same result : caught signal 4:???: 
xorg fails. I really don't get it
I also took a look at my xorg log and a line says direct rendering is not yet supported with ati radeon 9500 and newer cards... :confused:

---

### Post by jdarnel2 on 2005-10-18
Same issue here.  X600 with 256 megs of RAM.  Vesa get's me working again.

I'm on 64 bit.

---

### Post by germac on 2005-10-19
Using vesa or vga drivers gets me a Fatal server error : no screen found
        ati drivers gets me a Fatal server error : Caught signal 4
I tried to change resolution, hsync and vsync, not helping, I'm stuck.

---

### Post by mlomker on 2005-10-19
> Same issue here.  X600 with 256 megs of RAM.  Vesa get's me working again.


The fglrx drivers are currently broken in Breezy.  The Ubuntu maintainer, Septor, is working on it and has posts in a couple related threads.

---

### Post by germac on 2005-10-19
I hope this will be fixed soon. I was so waiting for breezy, kind of disappointed. Whatever, it's just a driver problem, could have been worse.

---

### Post by germac on 2005-10-19
Anyone could sent me his working xorg.conf with his ati radeon x600 so that I can try to fix me problem?
Thanks

---

### Post by germac on 2005-10-19
I downloaded the xorg-driver-fglrx from the console and install it, changed my xorg.conf with fglrx and it's working! Apparently glxgears is damn slow but I'll install ati's proprietary drivers to get a much more efficient glxgears.

Thanks for your help. :KS

---

### Post by MeijUbuntu on 2005-10-21
Had the same problems.

I got X server running by using the VESA driver. After that i dowmloaded the fglrx drivers and  created a xorg.conf file online. (seach for online fglrxconfig) !!

fglrx did not work with the default xorg.conf file.

Goodluck

---

### Post by hs2000 on 2005-10-21
I've managed to install Ubuntu 5.10 and make it work with my ATI X600 graphics cards. 
I had problems also. After installing Ubuntu, it freezed right before appearing the login username textbox.

After reading some post in the forums I've managed to find a working solution:

 1) I booted in safe mode

 2) Installed fglrx driver
        **Command:** sudo apt-get install xorg-driver-fglrx

 3) Installed retricted modules
        **Command:** sudo apt-get install linux-restricted-modules-$(uname -r)

 4) Made a backup of **/etc/X11/xorg.conf** configuration file
  
 5) Altered the **/etc/X11/xorg.conf**. Goto to the section "Device" and modify or add the following entries:
     Section "Device"
        Identifier "ATI"
        Driver     "fglrx"
        Option    "VideoOverlay"            "on"
        Option    "UserInternalAGPART"   "no"
     EndSection

For me this worked. No more freezes during boot.

---

### Post by ernie on 2005-10-29
i think i am haveing the same prblem only w/ a x850 pro video card.  i can do step 1-3 but 4 and 5 i dont know how to do can someone help

---

