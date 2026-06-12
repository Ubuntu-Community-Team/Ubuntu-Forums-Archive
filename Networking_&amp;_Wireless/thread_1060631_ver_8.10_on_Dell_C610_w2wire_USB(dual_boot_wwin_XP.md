---
title: "ver 8.10 on Dell C610 w/2wire USB(dual boot w/win XP)"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by zapme on 2009-02-04
2wire usb wireless adapter works fine on winXP. WD external drive works fine attached to same usb hub as the 2wire. Unbuntu 8.10 install didn't pick up any wireless adapter.Laptop is Dell C610 with dual boot of ubuntu 8.10 and winXP which also works fine.
 Have run these terminal commands with 
the results shown (abbreviated).
dmesg   shows usb hub and usb mass storage device found
iwconfig shows no wireless extensions on l0,eth0 and pan0.
sudo lshw -C network  shows info only for eth0.
ifconfig  shows L0 loopback and eth0  ethernet
ping 127.0.0.1  shows 100% response to ping
lspci -v|less  shows much data but specific to usb it says;
               usb controller:Intel Corp 82801cm/cam usb controller  #1(rev2)
lsusb  shows;
          Bus 001 Device 004:ID 1630:0005
          Bus 001 Device 003:ID 1058:0910 Western DigitalTech                                       
          Bus 001 Device 002:ID 05e3:0608 Genesys Logic Usb 2.0Port Hub
          Bus 001 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
I understand(I think) that I need an Orinoco CS driver instead of
the win  Wlan0.sys driver windoze uses but how can I get started if Ubuntu 8.10 can't even find the hardware? 
  I am a relative newbie in Linux but like the philosophy of it but have no ethernet connection ability so wireless must be made to work, somehow.:confused::confused::confused:

---

