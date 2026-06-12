---
title: "Huawei TI ETS2288 modem"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by Yuva Raj on 2012-08-04
Im Using Huawei TI ETS2288 Modem & ubuntu 11.04 OS

I Cant able to Use "Internet".

Please help me out..im newbie to Opensource :(

My System architecture is i686.

---

### Post by praseodym on 2012-08-04
Hi there.

Please open a terminal with CTRL+ALT+T and show the outputs of the commands:

```
lsusb
lsmod
usb-devices
```

---

### Post by gordintoronto on 2012-08-04
Perhaps this will help:
[http://ubuntuforums.org/archive/index.php/t-1196837.html](http://ubuntuforums.org/archive/index.php/t-1196837.html) 

I Googled: Huawei TI ETS2288 linux
to find it.

---

### Post by Yuva Raj on 2012-08-04
Hi, thanks...

thats works fine & now i needed "how to install packages like Synaptic Package Manager,Wvdial & Gnome"

{I manually downloaded & tried bcz i dont have Internet until i install Wvdial}

When i type sudo apt-get install packagename.deb
It shows the following error 

$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

---

### Post by Yuva Raj on 2012-08-04
> **gordintoronto said:**
> Perhaps this will help:
[http://ubuntuforums.org/archive/index.php/t-1196837.html](http://ubuntuforums.org/archive/index.php/t-1196837.html) 

I Googled: Huawei TI ETS2288 linux
to find it.

Thanks :D

It worked till 7th step.

But when i execute this command,
**sudo wvdial bsnl **
Wvdial command not found it says.

---

### Post by praseodym on 2012-08-04
Did you create the file in step 7?

> gksu gedit /etc/wvdial.conf
Insert the text and change to _your_ username and password there.

---

### Post by Yuva Raj on 2012-08-05
> **praseodym said:**
> Did you create the file in step 7?


Insert the text and change to _your_ username and password there.

Yeah !! 

But i dont have Wvdial Package.
I downloaded But it has dependecies.

How to resolve that?
I have 4 Files for to install Wvdial

1.libconfig
2.libbase
3.libextras
4.Wvdial.

---

### Post by praseodym on 2012-08-05
You will find all packages on [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Yuva Raj on 2012-08-05
> **praseodym said:**
> You will find all packages on [http://packages.ubuntu.com](http://packages.ubuntu.com)

I Downloaded it.
It has Multi-files..How should i install via Terminal apt-get Command simulatenously.
It is a dependency file.

---

### Post by praseodym on 2012-08-05
Save the files in "Downloads" and install via:

> sudo dpkg -i ~/Downloads/*.deb
If there are still missing dependecies download them and try it again

---

### Post by Yuva Raj on 2012-08-05
> **praseodym said:**
> Hi there.

Please open a terminal with CTRL+ALT+T and show the outputs of the commands:

```
lsusb
lsmod
usb-devices
```

root@yuva-desktop:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 002 Device 004: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter

---

### Post by Yuva Raj on 2012-08-05
> **praseodym said:**
> Did you create the file in step 7?


Insert the text and change to _your_ username and password there.

root@yuva-desktop:~# sudo wvdial dialup
sudo: wvdial: command not found

Wvdial Package is not in my Ubuntu 11.10.

But i downloaded that Package & Copied into var/caches/apt/archives

& tried this Command : sudo apt-get install packagename.deb

It shows,

root@yuva-desktop:~# apt-get install wvdial
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package wvdial

---

### Post by praseodym on 2012-08-05
Install the .deb Packages vie double click

---

