---
title: "Problems installing nVidia driver with a GeForce Go 7300"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by [knap] on 2006-12-03
I recently bought a Toshiba Satellite A100-498 laptop, specifications [here.](http://pt.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=PT&PRODUCT_ID=122825&toshibaShop=false)

Most of the stuff worked fine out of the box (I'm using Ubuntu 6.10 "Edgy"), but i couldn't get my screen resolution up from 1024x768 so i decided to install the nVidia proprietary drivers.

I downloaded [these drivers](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html) and installed them this way:

Installed linux-kernel-headers and build-essential packages
Ctrl-Alt-F1 to go to VT1
sudo /etc/init.d/gdm stop
sudo sh NVIDIA..blablabla.run

The installation started (compile from source), said that didn't find X.org SDK and development stuff but installed fine.

Then i did

sudo /etc/init.d/gdm start

and X worked fine, displayed the nVidia logo, i logged in and i had 3d acceleration but the resolution was still caped at 1024x768 so i added to the xorg.conf file the "1280x800" option for all depth and restart the computer but this time X didn't start at all. I did modprobe nvidia but still no luck. The server output states that 

"Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184 but this X module has the version 1.0-9629. Please make sure that the kernel module and all NVIDIA driver components have the same version.

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.

some more stuff and than

Fatal server error:
no screen found."

The detailed x server output states a lot of errors about fonts.

Any help would be appreciated.
--Luís Moreira

---

### Post by jarocooke on 2006-12-22
Hi there,

Double check that you don't have the restricted drivers installed or any other components of the packaged Nvidia drivers.  That is all I can think of for now.

---

### Post by tseliot on 2006-12-22
Try Envy, it will install the driver for you and solve your problem:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by venik212 on 2006-12-27
Bravo Alberto!  With the help of his ENVY script I finally have the full resolution of the Nvidia legacy card I have, and the resolution is just what I have in XP.
Now if only someone could create the same magic for my network card, or whatever it is that makes the internet connection under Ubuntu (using firefox, Swiftfox or Opera) so painfully slow, I could finally embrace Ubuntu and forget XP.... I am writing this under XP since I despaired of waiting for the web site to appear under UBUNTU.....

---

### Post by tseliot on 2006-12-27
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=323747&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=323747&highlight=ipv6)

---

### Post by [knap] on 2007-01-26
It's been a while since my first post but I'm with the same problem again, this time with the 97.46 driver.

I will try Envy (thanks tseliot) but i would like to know why the nVidia kernel module reverts to a previous version after a reboot. 

I have the same problem both in my desktop and my laptop, diferent graphic cards (both nVidia), cpus, etc.

Is this a Ubuntu problem? nVidia? Linux kernel?

Thanks.

---

### Post by [knap] on 2007-01-27
Envy did the trick, but i would like to know what Envy does that i manually don't do.

---

### Post by ripleyscat on 2007-01-27
I have a NVIDIA 6800 graphics card on a 865PE Neo2 (Intel) motherboard. I used ENVY available from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) no configuration was necessary. Everything runs exactly as expected.

---

### Post by venik212 on 2007-01-29
I believe that ENVY recompiles some of the restricted modules of the Linux kernel, among other things.

---

