---
title: "Belkin Wireless USB"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by tonsoffun49 on 2011-01-03
I have a Belkin Wireless USB and I am not sure how to get it to work. Model: F7D1101v1

---

### Post by spiky001 on 2011-01-03
Have you just installed the system, if so I would plug in a network cable and update the system, Go to System/Administration/Update manager, make sure usb device is in

---

### Post by mail2345 on 2011-01-03
I have the exact same model, and these instructions worked for me:
[http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)
Only thing I changed was using gksudo gedit instead of sudo gedit.

---

### Post by bkratz on 2011-01-03
maybe you can find something useful here

[http://ubuntuforums.org/showpost.php?p=9665745&postcount=26](http://ubuntuforums.org/showpost.php?p=9665745&postcount=26)



for some reason that link in the post didn't work for me try this

[http://ubuntuforums.org/showthread.php?p=9539649](http://ubuntuforums.org/showthread.php?p=9539649)

---

### Post by tonsoffun49 on 2011-01-03
So I did all instruction but I am stuck at: 

2.) Then I obtained the firmware from here:
 	Quote:
 	 	 		 			 				[http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin") 			 		 	 	 
and copied it to /lib/firmware/RTL8192SU/ with these commands:

 	Quote:
 	 	 		 			 				wget [http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin")
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU

I downloaded the firmware but I am stuck on the last part with the commands.

---

