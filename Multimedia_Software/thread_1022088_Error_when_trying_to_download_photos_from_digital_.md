---
title: "Error when trying to download photos from digital Camera"
date: 2008-12-26
forum: Multimedia Software
---

### Post by ilovelinux on 2008-12-26
Please help!  My husband got me an AWESOME camera for Christmas and when I plug the camera into my computer to import the photos I get this message:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device"

The camera is a KODAK HD EasyShare Z1285

I have tried to import photos using gtkam this also does not work.

I have a FUGI camera that I have had for years, an icon will pop up on the desktop to click into to manually copy and paste photos but I am not even getting an icon with this Kodak camera....please help!!

I am also wondering if the problem is this is an HD camera?

---

### Post by xc3RnbFO8P on 2008-12-26
Read this:
[http://ubuntuforums.org/showthread.php?t=346840]("http://ubuntuforums.org/showthread.php?t=346840")

---

### Post by ilovelinux on 2008-12-26
?

---

### Post by ilovelinux on 2008-12-26
Thank you, I still need some assistance though.....I am stuck on Step 2

In step 1 I get this

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 13ee:0003
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 040a:0402 Kodak Co.
Bus 001 Device 001: ID 0000:0000

So for Step 2 I typed 040a:0402

and I get

bash: 040a:0402: command not found

Am I missing something?

---

### Post by xc3RnbFO8P on 2008-12-26
Bus 001 Device 006: ID 040a:0402 Kodak Co.

In Terminal: 
> sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
add this line 
> SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0402", MODE="0660", GROUP="plugdev"
save the file
then in Terminal:
> sudo /etc/init.d/udev restart
and connect the camera again.

---

### Post by ilovelinux on 2008-12-26
I get it now :)  Thank you very much.  Happy Holidays and Happy New Year from Canada!!

---

### Post by RJARRRPCGP on 2008-12-26
When using F-Spot with my Kodak EasyShare M753, I find that if I get an error, I have to turn off the camera then turn the camera back on and sometimes, unplug the camera and plug the camera back in. 

Usually the error I get is the one claiming it couldn't lock the device. 

Seems more likely to give that error message if I launch F-Spot with the Kodak EasyShare M753 turned on. 

Seems like it's a conflict with the auto-mount and detection feature of Ubuntu and Gnome.

---

