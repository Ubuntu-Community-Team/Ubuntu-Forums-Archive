---
title: "Realtek RTL8188SU 802.11n WLAN Adapter"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by bensewell on 2011-03-11
Hi just swapping all my computers over to linux as it far far better than anything i've used before.  Have the above driver as identified in lsusb.

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true)

Downloaded the linux driver but dont know what to do from here.  Tried doing it the windows inf file way but that didnt work.  Or more like i couldnt get it working.

Any pointers?

---

### Post by chili555 on 2011-03-11
> Have the above driver as identified in lsusb.Could you please post it?```
lsusb
```

---

### Post by bensewell on 2011-03-11
Yes of course here it is:)

---

### Post by chili555 on 2011-03-11
Please post:```
sudo modprobe r8192s_usb
iwconfig
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by bensewell on 2011-03-12
Hi thanks for the reply.

Here are the screenshots with the commands from the terminal.

---

### Post by chili555 on 2011-03-12
You have the classic firmware problem. It's pretty easily fixed. Remove the device. Get a wired ethernet connection temporarily and do:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Reinsert the device and you should be working.

I notice that ndiswrapper is still active and you'll probably have a more efficient system if, after you verify the native driver is working, do:```
sudo apt-get remove --purge ndiswrap*
sudo rm /etc/modprobe.d/blacklist
```Post back if you get stuck.

---

### Post by bensewell on 2011-03-12
Ok will do.  Will have to move the PC upstairs for the router connection and do some tinkering then all should be OK i think :)

Could i do this with another machine and then copy the files over with a usb stick?

---

### Post by chili555 on 2011-03-12
> Could i do this with another machine and then copy the files over with a usb stick?Certainly. Drag and drop the firmware file to your desktop and then:```
sudo mkdir /lib/firmware/RTL8192SU
cd Desktop
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Post back if you get stuck.

---

### Post by bensewell on 2011-03-13
worked a treat Thanks :)

---

### Post by appleworm on 2011-04-11
God bless you for this tutorial !!

I´m sorry for rebirthing this old thread, but I´m so happy! Thanks for this tutorial - I´ve tried everything (hours and hours of googling and trying lots of non-working tutorials) and it didn´t worked - everything but THIS ! 

Thank you very much ;)

---

### Post by nik_nah on 2011-05-13
This isn't working for me on x64 ubuntu 11.04
I've tried...
* ndiswrapper with WinX64 driver: NULL pointer crash
* r8712 driver from realtek: "iwlist wlan0 scan" returns "no scan results"

I am not getting any firmware messages in dmesg.

---

