---
title: "I have lost my advance graphics..."
date: 2010-03-27
forum: Multimedia Software
---

### Post by Nexeh on 2010-03-27
I'm a new guy to Ubuntu/Linux but IMO am pretty decent with computers. I'm a Java Programmer so i'm pretty familiar with my way around. Decided to try ubuntu to learn more about other OS. So far I'm loving it and i have come through many issues including other graphics problems but this ones got me stuck.

I had Compiz working great on Ubuntu 9.10. I had the full desktop effect, Desktop Cube, and all the fancy fun stuff. I was working on something completely unrelated and my desk top ended up freezing. I was still able to get to the terminal through ctrl-alt-F2 which i eventually rebooted the machine through. When the machine came back up it was in no effects mode and would not enable any desktop effects now.

I have since tried many thing found in forums and feel that i'm worst off now than i was before. I started by following a guide for installing the proprietary ATI drivers for my Video card. When i downloaded ati-driver-installer-9-3-x86.x86_64.run and went to package it for 9.10 it only supported up to 9.04. So being desperate i went for it.

It didn't work :P. So i followed a guide for removing the driver and everything went exactly as the guide said but now when i restart the computer i get a ubuntu popup box that says "failed to load fglrx module" This must mean there is some remnace of the setting to use the driver.I have tried so many things to fix this and can't. Here's some more misc information

jeremy@jeremy-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.1.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

jeremy@jeremy-desktop:~$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

jeremy@jeremy-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
fglrxinfo: command not found

jeremy@jeremy-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Projec

jeremy@jeremy-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

I also did the sudo dpkg-reconfigure -phigh xserver-xorg once but never got the walk through everyone talks about

---

### Post by Nexeh on 2010-03-27
Thought it might be usefull to know the tutorials i was using..

install
 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

remove
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Nexeh on 2010-03-27
Update:

I no longer get the low graphics warning when i start Ubuntu. This is after starting in recovery mode and running Xorg -reconfig and copying /root/xorg.config. to /etc/X11/xorg.config However I still can not enable effects. Halfway there now!

---

### Post by Nexeh on 2010-03-27
RESOLVED

I had to black list an nvidia module that was getting loaded that was interfereing with the correct drivers.

---

