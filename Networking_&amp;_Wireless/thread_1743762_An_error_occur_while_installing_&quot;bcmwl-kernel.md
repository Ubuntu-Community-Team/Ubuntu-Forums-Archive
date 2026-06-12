---
title: "An error occur while installing &quot;bcmwl-kernel-source&quot;"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by sualsalmi on 2011-04-29
Hi,

I am trying to install a wireless driver for my laptop (Dell inspiron 6400) which has Broadcom BCM4311 pci wirelees card.

One of the solutions that i have found is to  do 
```
sudo apt-get install bcmwl-kernel-source
```But unfortunately an error occurs during the installation!
the result is ....

```
user@user-MM061:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:170
14e4:4311)!
Use proper b43 or b43legacy firmware.
[COLOR=Red]Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```
Any provided support  will be appreciated!

---

### Post by josephmills on 2011-04-29
> **sualsalmi said:**
> Hi,

I am trying to install a wireless driver for my laptop (Dell inspiron 6400) which has Broadcom BCM4311 pci wirelees card.

One of the solutions that i have found is to  do 
```
sudo apt-get install bcmwl-kernel-source
```But unfortunately an error occurs during the installation!
the result is ....

```
user@user-MM061:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:170
14e4:4311)!
Use proper b43 or b43legacy firmware.
[COLOR=Red]Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 **firmware-b43-lpphy-installer**
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```
Any provided support  will be appreciated!

I dont thik that you need that could we see a 
```
lsmod | grep b43 
```
```
dmesg | grep b43 
```
thanks

---

