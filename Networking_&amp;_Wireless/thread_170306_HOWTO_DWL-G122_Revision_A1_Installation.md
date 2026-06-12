---
title: "HOWTO: DWL-G122 Revision A1 Installation"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by cscott300 on 2006-05-04
For those who don't know, not all D-Link DWL-G122 are made equal. For those unlucky people such as myself, I got the A1 version, which is based on a different chipset than the majority of these units. A1 is based on the Intersil Prisma chipset, and not Ralink rt2570.

To make it work (at least it did for me...):
[LIST=1]
[*]Make sure you got what you need
```
sudo apt-get install ndiswrapper-utils
```
this will require network access (chicken, meet egg.) Otherwise, you need the ubuntu install media, and you can install it from there (check /etc/apt/sources.list to be sure it is installing from the CD or DVD.)
[*]Get Drivers
I got the drivers I needed [here.]("http://support.dlink.ca/ProductView.asp?ProdID=353#firmware")
[*]Install via ndiswrapper
Unpack the driver zip file; it doesn't matter where, so I put in ~/Desktop ('cause I'm lazy.)
```
cd ~/Desktop
sudo ndiswrapper -i PRISMA02.inf
sudo modprobe ndiswrapper

```
Now, if you enter ```
sudo ndiswrapper -l
``` you should see ```
prisma02   driver present, hardware present
```
If you don't, it didn't work... :-x 
If it did, Great! :p 
[*]Reboot, and configure the device.
from the terminal, sudo modprobe ndiswrapper
This might need to be done each time you boot (I don't know yet, haven't rebooted...)
Then, in System > Administration > Networking, configure the new device (for me, it appears as wlan0.)
[/LIST]

---

### Post by cscott300 on 2007-08-28
I've since updated to Feisty, and with that some changes to the guide. From the way it looks, I'm the only one to use this guide...but at least it helped my install on Feisty, so at least 1 person needed me 8-[

Again, to make it work (at least it did for me...):
[LIST=1]
[*]Make sure you got what you need
```
sudo aptitude install ndisgtk ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```
this will require network access (chicken, meet egg.) Otherwise, you need the ubuntu install media, and you can install it from there (check /etc/apt/sources.list to be sure it is installing from the CD or DVD.)
[*]Get Drivers
I got the drivers I needed [here.]("http://support.dlink.com/products/view.asp?productid=DWL%2DG122#") By default, firefox saves things on the Desktop, which is where my download ended up.
[*]Install via ndiswrapper
Unpack the driver zip file; it doesn't matter where, so I put it under ~/Desktop as well (since I'm lazy.)
```
cd ~/Desktop/
unzip dwlg122_driver_113.zip
cd D-Link AirPlus G Utility(V3.2.0.40308) with G122-1.0.13
sudo ndiswrapper -i PRISMA02.inf
sudo modprobe ndiswrapper

```
Now, if you enter ```
sudo ndiswrapper -l
``` you should see ```
prisma02 : driver installed
        device (2001:3703) present (alternate driver: prism54usb)
```
If you don't, it didn't work... :-x  (sorry, my help ends here.)
If it did, Great! :p 
[*]Reboot
[*]Once you've logged back in, configure the device.
from the terminal, ```
sudo ndisgtk
```
[/LIST]

---

