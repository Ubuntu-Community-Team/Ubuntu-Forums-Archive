---
title: "samung nc110 with intel centrino wireless-n 130 not finding wifi"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by ruairit on 2012-03-13
hello and greetings

I have a tad of a problem - five nc110 netbooks for my local national school that do not find the wireless card.  they are set to dual boot, windows7 and ubuntu 10.04 with edubuntu software added on. when i click on the network icon, only the wired connection is visible.

lspi gives:
```
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation Device [8086:0896] (rev 34)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```iwconfig gives\;
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```i have been to the intellinuxwireless.org site, downloaded various drivers but seem to be having a complete dutdut moment. its lasted three days so far.....

can anyone face helping?:confused:

many thanks
ruairi

---

### Post by flash63 on 2012-03-13
Hello,
you find complete instructions here 
[http://forum.ubuntuusers.de/post/2767012/](http://forum.ubuntuusers.de/post/2767012/)

Translation:
[http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F2767012%2F&act=url](http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F2767012%2F&act=url)

I set up for Ubuntu 10.04 revised driver package available on my homepage.

Follow the instructions ..

Download and install the latest firmware first (deb-Package):
[http://packages.ubuntu.com/oneiric/linux-firmware](http://packages.ubuntu.com/oneiric/linux-firmware)

Blacklist the old driver for safety
```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv iwlagn 
```
Build the new one:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install  
```
Load the driver and test the function:
```
sudo modprobe iwlwifi    
ifconfig
iwconfig
iwlist chan
sudo iwlist scan  
```

---

### Post by ruairit on 2012-03-14
Hi Flash63 

thank you for taking the time to reply and so quickly.

I followed the steps above, but i think i must have got it wrong along the way, as no driver appeared, and the machine was complaining about  bricked. i am now trying it again on a fresh install, fully updated but otherwise untouched machine. 

i shall report back n the morning on how this goes,thank you for your time.i am trying to get these machines into a local school so  your help is truly appreciated.

ruairit

---

### Post by flash63 on 2012-03-15
Otherwise there is the possibility to install a Backport Kernel from Ubuntu 11.10, which includes the necessary drivers already. The firmware must be updated as further described.

```
sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric
```
(Meta-Packages)

Direct download here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Select distribution lucid and search for the packages.

You need
linux-image-generic-lts-backport-oneiric
linux-image-3.0.0-16-generic
linux-headers-generic-lts-backport-oneiric
linux-headers-3.0.0-16-generic 

(note of the required system architecture 32/64bit!)

---

### Post by ruairit on 2012-03-17
thank you very much! I managed to get it working on two of the machines using the second option. it worked a treat, wireless networking is all up and running.
 
thanks you for your time and your help

---

### Post by jorsaave on 2012-09-09
Hi flash63, 

thanks a lot for your instructions (March 13th, 2012 06:23 PM), I  installed an Intel Centrino Wireless-N 130 card (in a Samsung Core I5  NP300E4A-S0HCL) with ubuntu 10.04.4 LTS.

There was just one problem, the driver link  ([http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz))  was removed, so I replaced for this one:

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.4/compat-wireless-3.4-rc3-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.4/compat-wireless-3.4-rc3-1.tar.bz2) 

that is, in fact, a new version.

Greetings
jorsaave

PS: the  replaced code is here

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.4/compat-wireless-3.4-rc3-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.4/compat-wireless-3.4-rc3-1.tar.bz2)
tar xvf compat-wireless-3.4-rc3-1.tar.bz2
cd compat-wireless-3.4-rc3-1
make sudo make install
```

---

