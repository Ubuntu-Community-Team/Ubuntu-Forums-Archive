---
title: "Ralink WIFI modem not working"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by shahan on 2010-04-19
I cannt get connection of my WIFI modem on UBUNTU 9.10(new installed)
but it works on ubuntu 9.04(installed through WUBI.exe) without any driver.

below is my** lsusb **report on UBUNTU 9.10
[PHP]    shahan@shahan-desktop:~$ lsusb
  Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  shahan@shahan-desktop:~$ 
  [/PHP]

---

### Post by shahan on 2010-04-19
wow...
got the solution

  	 	 	 	 	 	  Fixed with:
Step1: add "blacklist rt2800usb" to:
sudo gedit /etc/modprobe.d/blacklist.conf
Step2: Force the removal of the wrongly loaded module "sudo modprobe -r rt2800usb".
 
Now its working.....

---

