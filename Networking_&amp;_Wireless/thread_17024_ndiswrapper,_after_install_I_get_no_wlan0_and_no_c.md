---
title: "ndiswrapper, after install I get no wlan0 and no connection"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by berzerker on 2005-02-25
This is driving me insane, I've almost every distro out there to try and get my SMC2802W card to work. After some time I found out that I had v2 which means it isn't supported by prism54.. 
So, off to ndiswrapper... 
I followed this guide:
[http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)

Now, I've searched this site and read other threads about ndiswrapper problems, and they kinda seem more logical than mine, because ndiswrapper installs just fine, no complaints or anything. This is a fresh install, only thing I've added to it is openssh server to transer the driver files to the machine I'm installing on. I installed ndiswrapper by using synaptics like recommended, and I ran the appropriate commands, like recommended, and I didn't get a single error message.
ndiswrapper -l reports that 2802w is installed, hardware present. However, when running iwconfig, no wlan0 shows up. It shows eth1 as being wireless and it says NOT READY! 
Anyway, I run "modprobe ndiswrapper", and then "dmesg". The last one shows "ndiswrapper version 0.10 loaded (preemtp=yes,smp=no)
ndiswrapper: driver 2802w.sys (smc, 04/29/2004, 2.0.11.1) added"

Still no wlan0 however. Running "ndiswrapper -m" applies wlan0 to the modprobe conf file, but still doesn't show up, it's still eth1.

I open the network configuration tool and press "Add" and "Wireless connection", I can at this point only choose to configure eth1. I then enter the required info, press forward and "Apply". At this point, the config tool freezes for a while, and when coming back to itself again, the wireless card is inactive. Pressing active and it will be checked for a few seconds before going down again.
Interestingly, running "iwconfig" now, it is not registered as a wireless connection any longer... it says that eth1 has no wireless extensions anymore ..

What the hell is going on? Is there something in the install procedure I'm missing?

Very grateful for any help, it's really really bugging me...

---

### Post by acascianelli on 2005-02-25
try doing an 'insmod ndiswrapper'

---

### Post by berzerker on 2005-02-25
"insmod: can't read 'ndiswrapper': No such file or directory"

:shock:

 ](*,)

---

### Post by bm009 on 2005-06-10
I have a wireless card on my pc and i can't make it to work with linux. 
The card is smc2802w and i found out that is a v2.

I've tried ndiswrapper but it doesn't work. What can i do to make it work??

can someone help me?

---

### Post by blu.gecko on 2005-06-18
its been ahwile since I have spoken up but, when I did my ndiswrapper install I did it in this exact order.


ndisiswrapper-installed
ndiswrapper - i /media/cdroom0/folder/
ndiswrapper -l hardware present hardware found
modprobe ndiswrapper

then I went to the network and had to activate wlan0, and on the eth0 comment you may have to gedit the "ndiswraspper" file to eth0 to wlan0 :roll: I never used a "sys" file I used a "inf" file.....

if you dont activate the hardware it will disapear. 

hope that helps somewhat...... :roll:

---

