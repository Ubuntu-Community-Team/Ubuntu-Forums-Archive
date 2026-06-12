---
title: "ubuntu server 9.04 on board (MOBO) NIC, need help loading driver"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by eliatwork12345 on 2009-05-15
i am having problems with my on board NIC on ubuntu server 9.04. my NIC did not show up after i installed ubuntu server 9.04. i have the drivers for the NIC (intel 10-100) in a .tar. and i unarchived the .tar.gz. from my usb drive to the hard drive i am running ubuntu server 9.04 on. i have the folder e100-3.5.17 
 
my problem is in the readme file it tells me to run this command
"make install"
 
which then says 'make' is currently not installed. you can install it by typing: sudo apt-get install make
 
i can not apt-get install make since i do not have a working NIC to even get out to the internet. this is circular reasoning. 
 
the rest of the readme file goes like this
 
**4. Compile the driver module:**
**make install**
 
**The binary will be installed as below:**
**/lib/modules/<kernel_version>/kernel/drivers/net/e100/e100.[k]o**
**The install location listed above is the default locations. It may**
**not be correct for certain Linux distributions. For more information,**
**see the ldistrib.txt file included in the driver tar.**
 
**5. Install the module:**
**modprobe e100**
 
**6. Assign an IP address to the interface by entering the following, where**
**<x> is the interface number:**
**ifconfig eth<x> <IP_address>**
 
**7. Verify that the interface works. Enter the following, where <IP_address>**
**is the IP address for another machine on the same subnet as the interface**
**that is being tested:**
**ping <IP_address>**
 
anway i am just looking for some help so i can have my NIC up an running. is there another way to install the driver(s) without running the make install command?
 
Thanks

---

### Post by chili555 on 2009-05-15
I believe e100 already resides on your system. Please try:```
sudo modprobe e100
ifconfig
```Was an interface, eth0, hopefully, created?

---

