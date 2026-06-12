---
title: "Broadcom 4311 wifi card not working with Ubuntu"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by cselinux on 2012-12-13
First forum, please go easy :) 

I just installed Ubuntu 12.10 on my Dell Inspiron E1705 and everything works great except the wifi is not working. I am currently using a wifi usb that is allowing me to use the internet. 

Still looking around for some help through other threads, but not necessarily confident with any of them. 

Help would be greatly appreciated! I love ubuntu and don't want to switch back to Windows because of the wifi issue. 

Happy threading! :)

---

### Post by Abhinav Kumar on 2012-12-13
Hi cselinux,
you may find the following thread useful 
[http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)

Regards,
Abhinav

---

### Post by TBABill on 2012-12-13
Have you tried to, while connected via ethernet or USB ```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` And once completed ```
sudo modprobe b43
``` Then try to connect?

---

### Post by cselinux on 2012-12-13
This is what I recieved after the sudo apt-get

sudo apt-get install b43-fwcutter firmware-b43-installer
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by BicyclerBoy on 2012-12-13
That usually means you have synaptic or update manager open at the same time.
Those 2 apps & apt-get all require exclusive access to same files.

I have this written down from BCM4312 wifi issues kernel 3.5 & *buntu12.04:
The first 6 lines is debugging stuff to help you & others..

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod

http://lkubuntu.wordpress.com/2011/09/08/how-to-fix-broadcom-43xx/

If your card number is: BCM4312, then type in a Terminal window:

sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*

sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*

Then reboot
```

My BCM4312 is using wl driver (modified source code 2 lines)

---

### Post by irv on 2012-12-13
OK, make sure you have software center and the package manager closed and follow these steps.

make sure you have dkms installed first.
In a terminal type:
```
sudo apt-get install dkms
```
Here what to do next. 
1. uninstall “bcmwl-kernel-source” package,
```
sudo apt-get remove bcmwl-kernel-source
```
2. install “firmware-b43-installer” package
```
sudo apt-get install firmware-b43-installer
```
3. install “b43-fwcutter” packager
```
sudo apt-get install b43-fwcutter
```
4. type into the terminal:
 ```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```
This was the out put:
Quote:
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

At this point you may have to restart your computer.

---

