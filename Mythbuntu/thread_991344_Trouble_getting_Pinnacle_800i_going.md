---
title: "Trouble getting Pinnacle 800i going"
date: 2008-11-23
forum: Mythbuntu
---

### Post by bigmike626 on 2008-11-23
I've extracted and copied the firmware and I've downloaded the latest v4l-dvb-tree and built the module per instructions from [http://www.mythtv.org/wiki/index.php/Pinnacle_800i](http://www.mythtv.org/wiki/index.php/Pinnacle_800i). When I go to myth setup the card isn't found. I've tried rebooting and that did not help. Going through dmesg I found this entry

[   42.568621] cx8800: disagrees about version of symbol v4l_compat_ioctl32
[   42.568624] cx8800: Unknown symbol v4l_compat_ioctl32

Could this be why myth doesn't recognize the card? Any help/nudge in the right direction  would be greatly appreciated.

Thanks

---

### Post by lionsnob on 2008-11-23
Are you using 8.10?  If so, the card is recognized as long as you put the firmware in /lib/firmware.

---

### Post by bigmike626 on 2008-11-23
No I'm using 8.04

---

### Post by Burnasty on 2009-01-22
I downloaded the driver but I don't understand how to extract and install.  I have the zip file and the extract.sh file, I just don't know what to do now.  Any help is greatly appreciated.

---

### Post by bigmike626 on 2009-01-23
Open a terminal and to go to the folder where you downloaded the firmware (which if you haven't changed anything it should be the Desktop). From there all you need to do is run the command sh extract.sh and that will extract the file you need. From there you need to copy the file that was extracted (dvb-fe-xc5000-1.1.fw) to /lib/firmware/2.6.**-*-generic (where you see the *'s replace with whatever your latest kernal version)

HTH

---

### Post by Burnasty on 2009-01-24
It says permission denied

edit:  I added sudo and now it says command not found

---

### Post by Burnasty on 2009-01-24
I am extremely green with this process.  I am sorry if the questions I ask are simple.  I am just struggling with this a little.  I have read a few tutorials and one tells of navigating to the download destination via command line.  I don't know how to do that.  Any help is much appreciated.

---

