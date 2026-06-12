---
title: "wireless usb Belkin N600 not working"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by Kitabalibar on 2011-10-16
Hi everyone,

I've been trying to make my belkin n600 usb wireless adapter working, but I still have some problems. After some readings, I successfully installed the proper drivers with ndiswrapper, but my key is still not recognised ! The light does not show up, and I really don't see what I should do now. 

here's some info :

ndiswrapper -l returns 

bcmwlhigh5 : driver installed
    device (050D:615A) present

iwconfig :

lo        no wireless extensions.

eth0      no wireless extensions.

lsusb  : 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:615a Belkin Components 
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub

Thanks for your time, and help

---

### Post by bwackwat on 2011-10-16
Hello,

Although I don't have a solution by any means, I am in nearly the same situation.

I have a desktop upstairs using a Belkin n600 USB Wireless Adapter. 

I have been successfully receiving wireless packets under Windows 7 with the WUSB.

I have recently installed CentOS 6 and with ndiswrapper have successfully installed the same driver.

lsusb shows my WUSB, ndiswrapper -l shows my driver and device loaded.

However I still have no signs of wlan0 or any wireless extensions.

Thank you!

~Bwackwat

---

### Post by bwackwat on 2011-10-16
Update!

CentOS now recognizes my WUSB as a wireless network card and can successfully search for access points.

I used:
ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

However I am still having a couple issues. When I restart, the connection goes away until I use modprobe again. Also, I cannot actually connect to any networks. My hunch on the lack of connection is due to the lack of automatically found DHCP and MAC addresses.

Any thoughts?

~Bwackwat

---

### Post by Bmonsterboy on 2011-10-16
Oh man, I spent a few hours trying to make one work. It is possible, so preserve! I'll try and find some of the threads that helped :)

---

