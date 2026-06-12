---
title: "CANNOT get this to work SO FRUSTRATING"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by mamtambam on 2009-01-01
So i've gone through a ton of different rt2860 windows drivers and couldnt get any of them for 64 bit, each time i would run 
 dmesg | grep -e ndis -e wlan
and get that the drivers are not 64 bit. SO then i tried going with the linux drivers following these instructions [http://ubuntuforums.org/showthread.php?t=1022733&highlight=rt2860](http://ubuntuforums.org/showthread.php?t=1022733&highlight=rt2860)        and when i ran "cd 2008_0918_RT2860_Linux_STA_v1.8.0.0"  i get bash: cd: 2008_0918_RT2860_Linux_STA_v1.8.0.0: No such file or directory


sooo, anybody that knows where to get the correct 64bit windows drivers for the RaLink rt2860 wireless card please speak up, ive gone through correctly patching and compiling ndiswrapper so that shouldnt be the problem. 
when i run iwconfig wlan0  i get wlan0 no such device. 
 
when i run lshw -c network i get "network unclaimed"
when i run lsmod | grep ndis  i get: 
ndiswrapper           253696  0 
usbcore               175376  7 ndiswrapper,btusb,usb_storage,libusual,ehci_hcd,uhci_hcd

after doing this, again i run dmesg | grep -e ndis -e wlan  i get that the drivers arent 64bit and that they can't be loaded, BUT, I REMOVED THOSE DRIVERS USING system-administration-windows wirless drivers, so wtf
any help plese

---

