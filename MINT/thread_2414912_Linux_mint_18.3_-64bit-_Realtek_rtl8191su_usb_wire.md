---
title: "Linux mint 18.3 -64bit- Realtek rtl8191su usb wireless poor?"
date: 2019-03-17
forum: MINT
---

### Post by rayxoxo on 2019-03-17
New to posting - Hope all ends well...

Here is the results of:
 sudo apt install hwinfo & lsusb


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libhd21 libx86emu1
The following NEW packages will be installed:
  hwinfo libhd21 libx86emu1
0 upgraded, 3 newly installed, 0 to remove and 20 not upgraded.
Need to get 727 kB of archives.
After this operation, 3,138 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://mirror.math.ucdavis.edu/ubuntu](http://mirror.math.ucdavis.edu/ubuntu) xenial/universe amd64 libx86emu1 amd64 1.5-1 [47.5 kB]
Get:2 [http://mirror.math.ucdavis.edu/ubuntu](http://mirror.math.ucdavis.edu/ubuntu) xenial/universe amd64 libhd21 amd64 21.23-1 [663 kB]
Get:3 [http://mirror.math.ucdavis.edu/ubuntu](http://mirror.math.ucdavis.edu/ubuntu) xenial/universe amd64 hwinfo amd64 21.23-1 [16.8 kB]
Fetched 727 kB in 0s (1,101 kB/s) 
Selecting previously unselected package libx86emu1:amd64.
(Reading database ... 282440 files and directories currently installed.)
Preparing to unpack .../libx86emu1_1.5-1_amd64.deb ...
Unpacking libx86emu1:amd64 (1.5-1) ...
Selecting previously unselected package libhd21:amd64.
Preparing to unpack .../libhd21_21.23-1_amd64.deb ...
Unpacking libhd21:amd64 (21.23-1) ...
Selecting previously unselected package hwinfo.
Preparing to unpack .../hwinfo_21.23-1_amd64.deb ...
Unpacking hwinfo (21.23-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libx86emu1:amd64 (1.5-1) ...
Setting up libhd21:amd64 (21.23-1) ...
Setting up hwinfo (21.23-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
ray@r18 ~ $ lsusb
Bus 002 Device 013: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 002 Device 012: ID 0bda:818b Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 276d:1160  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by coffeecat on 2019-03-18
*Thread moved to **MINT** sub-forum.*

Please have a look at this sticky: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Post the contents of the wireless-info.txt that you get from running the script. This will provide the information for forum members to be able to help you.

---

### Post by praseodym on 2019-03-19
[https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)

Should be this one

```
sudo apt-get install git linux-headers-generic build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0
```
Reboot. Check the other remarks there as well

---

