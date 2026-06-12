---
title: "Intel Pro network card not found (10.04 64bit)"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by margus21 on 2011-04-28
hi,

just installed ubuntu server 10.04 on my new pc, but it didn't configured network card automatically (I'm quite new in linux, so help needed)

Network: integrated NIC on Intel DQ67SW ([http://www.intel.com/Products/Desktop/Motherboards/db-dq67sw/DQ67SW-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/db-dq67sw/DQ67SW-overview.htm))

output of lspci | grep -i ethernet:
Ethernet controller: Intel Corporation Device 1502 (rev 04)

I didn't find any linux drivers for that board/NIC, is there any chance to get it working or do I have to add new network card?

thanks,
Margus

---

### Post by Sergei_K on 2011-04-28
does it show up in ```
ifconfig -a
```?

---

### Post by Bucky Ball on 2011-04-28
Welcome.

Have you plugged in an ethernet cable and gotten the updates? That could well pick up the card and offer appropriate software/firmware. Many cards won't work without getting online with an ethernet cable first. Catch 22. ;)

---

### Post by margus21 on 2011-04-28
ifconfig -a shows only lo device, no eth0, etc.

yes, the cable is connected and green light is blinking.

btw, I did find the driver, or at least something: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng)

followed the instructions to p.6, but can't set the IP as there is no device ethx (eth0 or eth1, etc)

thanks,
margus

---

### Post by chili555 on 2011-04-28
> output of lspci | grep -i ethernet:
Ethernet controller: Intel Corporation Device 1502 (rev 04)It's a rare Intel network card that doesn't have a built-in driver. Please show us:```
lspci -nn | grep -i ethernet
```Thanks.

---

### Post by margus21 on 2011-04-28
> **chili555 said:**
> It's a rare Intel network card that doesn't have a built-in driver. Please show us:```
lspci -nn | grep -i ethernet
```Thanks.

Output:
Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)


---
from Intel board manual I have found:
Gigabit (10/100/1000 Mbs/s) LAN subsystem using the Intel® 82579LM Gigabit Ethernet Controller

---

### Post by chili555 on 2011-04-28
This is supposed to work with the ubiquitous module *e1000e*. If it isn't working, something else is wrong. Let's insert it and see if there are any interesting messages:```
sudo modprobe e1000e
dmesg | grep e100
```Thanks.

---

### Post by margus21 on 2011-04-28
> **chili555 said:**
> This is supposed to work with the ubiquitous module *e1000e*. If it isn't working, something else is wrong. Let's insert it and see if there are any interesting messages:```
sudo modprobe e1000e
dmesg | grep e100
```Thanks.


Output:
BIOS-e820: 00000000bcad9000 - 00000000bcae1000 (usable)
BIOS-e820: 00000000bcae1000 - 00000000bcde6000 (reserved)
modified: 00000000bcad9000 - 00000000bcae1000 (usable)
modified: 00000000bcae1000 - 00000000bcde6000 (reserved)
PM: Registered nosave memory: 00000000bcae1000 - 00000000bcde6000
e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
e1000e: Copyright (c) 1999-2008 Intel Corporation

btw, should modprobe create a log for that command? in the screen it doesn't say anything. (successful or not, no error message as well)

---

### Post by chili555 on 2011-04-28
> btw, should modprobe create a log for that command?These lines in dmesg are an abbreviated log:> e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
e1000e: Copyright (c) 1999-2008 Intel CorporationI would have thought it would be a bit more extensive, like this:```
[    1.539530] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.539534] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.539567] e1000e 0000:02:00.0: Disabling ASPM  L1
[    1.539585] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.539610] e1000e 0000:02:00.0: setting latency timer to 64
[    1.539824] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.540277] e1000e 0000:02:00.0: Disabling ASPM L0s 
[    1.668935] e1000e 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:41:e6:cb:ef
[    1.668941] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.669018] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: 005301-003
[   13.000353] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
[   13.056166] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
etc., etc.
```You will probably find a bit more in /var/log/syslog.```
sudo cat /var/log/syslog | grep -e eth -e e100
```What is the bus number for the device; you know, the part you omitted? For example:```
lspci -nn | grep -i ether
[COLOR="Red"]**02:00.0**[/COLOR] Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]

```You might check dmesg for your bus number as well.

Off to lunch with Mrs. Chili; see you a bit later.

---

### Post by margus21 on 2011-04-28
> **chili555 said:**
> What is the bus number for the device; you know, the part you omitted? 

00:19.0 Ethernet controller [0200]: Intel ... etc.

---

### Post by margus21 on 2011-04-28
any more ideas or have to buy new network card :( ?

---

### Post by margus21 on 2011-04-28
> **chili555 said:**
> You might check dmesg for your bus number as well.

$ dmesg | grep 00:19

pci 0000:00:19.0 reg 10 32bit mmio: [0xfe600000-0xfe61ffff]
pci 0000:00:19.0 reg 14 32bit mmio: [0xfe628000-0xfe628fff]
pci 0000:00:19.0 PME# supported from D0 D3hot D3cold
pci 0000:00:19.0 PME# disabled

---

### Post by chili555 on 2011-04-28
I see no visible signs of life from the Intel. I'd go shopping.

---

### Post by jawilljr on 2011-04-28
Download and install the latest e1000e drivers from [here]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/")

[This is the latest stable e1000e drivers]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/1.3.10a/e1000e-1.3.10a.tar.gz/download")

Jerry

---

### Post by margus21 on 2011-04-29
> **jawilljr said:**
> Download and install the latest e1000e drivers from [here]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/")

[This is the latest stable e1000e drivers]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/1.3.10a/e1000e-1.3.10a.tar.gz/download")

Jerry

just tired with that driver (but it was the same, I tried yesterday as well)
no luck :(

@Chili555 - does it means hw failure or just no proper driver for that device? As I just bought that MB and if it's hw failure, I will go and ask to replace it. If it's driver issue with Ubuntu, then I will go to buy extra NIC.

thanks,

---

### Post by Bucky Ball on 2011-04-29
As mentioned, most that Intel card should be working, as most Intel cards do, out of the box. If it isn't quite possibly HW problem. I would attempt swapping the MB first before, as yourself and Chilli suggest, going shopping.

---

### Post by chili555 on 2011-04-29
The bus doesn't recognize the hardware and the hardware doesn't grab and activate the driver. The proper driver is in the kernel already:> Ethernet controller [0200]: Intel Corporation Device [[COLOR="Red"]8086:1502[/COLOR]] (rev 04)```
$ modinfo e1000e
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/e1000e/e1000e.ko
version:        1.2.20-k2
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     566D897FE2181A99FA51235
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]1502[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
--- snip ---
```My guess is defective hardware, but further testing would be required to confirm it. Have you checked in the BIOS to be sure  the NIC isn't disabled?

---

### Post by jawilljr on 2011-04-29
Chili,

Margus is running Lucid, and his NIC drivers is not in his kernel. 

Here is the output of my Lucid install:

```
kjawhtpc@kjawhtpc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
kjawhtpc@kjawhtpc:~$ uname -a
Linux kjawhtpc 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux
kjawhtpc@kjawhtpc:~$ sudo modinfo e1000e |grep 1502
kjawhtpc@kjawhtpc:~$
```

I tried "modinfo |grep 1502" on my Maverick box and it came back with this:

```
jawilljr@jawilljr:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
jawilljr@jawilljr:~$ modinfo e1000e |grep 1502
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
jawilljr@jawilljr:~$ 
```

So he needs to either upgrade his kernel or upgrade the distro. I do not know why the latest stable e1000e drivers did not work.

Jerry

---

### Post by margus21 on 2011-05-03
> **jawilljr said:**
> So he needs to either upgrade his kernel or upgrade the distro. I do not know why the latest stable e1000e drivers did not work.

Jerry

So, it might work with latest Ubuntu 11.04?
anyway I'll give a try, as my screen resolution is also awful (800x600).

I will let you know about the outcome.

thanks

---

### Post by fnerdwq on 2011-05-06
> **margus21 said:**
> So, it might work with latest Ubuntu 11.04?


Try the maverick backport kernel in 'lucid-updates', called 'linux-image-generic-lts-backport-maverick'. This has a sliglty newer Version 1.0.2-k4 of the e1000e and is working here.

---

### Post by comlong on 2011-06-23
I have the same problem with same netcard. 10.04 LTS, 64 bit
Dell atitude E6420.
I update the "linux-image-generic-lts-backport-maverick", then the wired internet works, it is fine. But, I can not restart the system. That is a new issue.
Firstly, I installed 11.04, 64 bit, I have wired internet but can not restart; then I switched to 10.04 LTS 64 bit, I can restart but I lost my wired internet.
For both situation, wireless internet works well.
How to fix it?

---

### Post by fnerdwq on 2011-06-23
> **comlong said:**
> I have the same problem with same netcard. 10.04 LTS, 64 bit
Dell atitude E6420.
I update the "linux-image-generic-lts-backport-maverick", then the wired internet works, it is fine. But, I can not restart the system. That is a new issue.
Firstly, I installed 11.04, 64 bit, I have wired internet but can not restart; then I switched to 10.04 LTS 64 bit, I can restart but I lost my wired internet.
For both situation, wireless internet works well.
How to fix it?

An alternative to the maverick-backport kernel is using the normal lucid kernel and building yourself a DKMS Package for the current version of the e1000e module.

It's realy simple:
1. Download the current e1000e module from
[http://sourceforge.net/projects/e1000/files/](http://sourceforge.net/projects/e1000/files/)
2. build the DKMS Package, following this instruction:
[https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging](https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging)

Then you're (hopefully) done...

good luck

---

### Post by comlong on 2011-06-23
Thanks for your idea. But I am totally new to ubuntu, could you give a simple solution?
It looks a common problem, ubuntu should have a fixed version

---

### Post by fnerdwq on 2011-06-23
> **comlong said:**
> Thanks for your idea. But I am totally new to ubuntu, could you give a simple solution?
It looks a common problem, ubuntu should have a fixed version

sorry, i don't have a simple(r) solution. Ubuntu is not an Enterprise linux in the way they would patch the LTS version with new drivers.

But natty it not an option (or not working for you)?  I supose they have "full Sandy bridge support"?

Best solution it building the DKMS Modules. It's really not that difficult, try

Im principle you just need the dkms.conf, like
PACKAGE_NAME="e1000e"
PACKAGE_VERSION="1.3.10a"    * <---- Fill in the downloaded version*
CLEAN="make clean"
MAKE="make BUILD_KERNEL=$kernelver"
BUILT_MODULE_NAME[0]="e1000e"
DEST_MODULE_LOCATION[0]="/updates"
AUTOINSTALL="yes"

This should give you a head start... Rest in the artikle.
Nice thing about DKMS: it will build the module for each new installed kernel update (in contrast to doing a make/make isntall)

---

### Post by srocrown on 2011-10-01
I wanted to spell out the steps I took for those newbies who are already confused by being 
caught in the catch-22 of how to apt-get without a working nix card, and installed the base from a usb, like me.

I share, knowing full well that there are probably more elegant or official ways to do it.  But if you are new to linux, not being able to use the Ethernet card on the brand-new machine that you just bought is VERY frustrating.  I followed the steps already given in this forum, they are just spelled out with a bit more detail.

Here is what I did:

Step 1. Capture all of the debs I will need.  I am going to copy everything to a usb - /media/disk

```
sudo apt-get clean
sudo apt-get -y install dkms build-essential make linux-headers-generic linux-headers-server --reinstall
sudo apt-get -y install gcc g++ gcc-4.4 g++-4.4 xz-utils binutils liblzma1 --reinstall
sudo apt-get -y install libc6-dev libc6 libc-dev-bin linux-libc-dev dpkg-dev --reinstall
sudo apt-get -y install libgomp1 libstdc++6 libstdc++6-4.4-dev --reinstall
sudo mkdir -p /media/disk/intel
sudo cp /var/cache/apt/archives/*.deb /media/disk/intel
wget http://tenet.dl.sourceforge.net/project/e1000/e1000e%20stable/1.6.2/e1000e-1.6.2.tar.gz
cp e1000e*.gz /media/disk/intel
```

Step 2. Create dkms.conf.  I always have trouble with double quotes, so they all now become single apostrophe.

```
nano /media/disk/intel/dkms.conf
```

```
PACKAGE_NAME='e1000e'
PACKAGE_VERSION='1.6.2'
CLEAN='make -C src/ clean'
MAKE='make -C src/ BUILD_KERNEL=$kernelver KERNELDIR=/lib/modules/${kernelver}/build'
BUILT_MODULE_NAME[0]='e1000e'
BUILT_MODULE_LOCATION=src/
DEST_MODULE_LOCATION[0]='/updates'
AUTOINSTALL='yes'
REMAKE_INITRD=yes
```


Step 3. Install utils.  Now I take my usb drive to the server without a working nix.

```
sudo dpkg -i liblzma1*.deb xz-utils*.deb binutils*.deb dpkg-dev*.deb
sudo dpkg -i libc*.deb linux-libc*.deb libg*.deb make*.deb
sudo dpkg -i gcc*.deb g++*.deb libs*.deb build-e*.deb 
sudo dpkg -i dkms*.deb linux-h*.deb 
```

Step 4. Create the module.

```
sudo cp e1000e*.gz /usr/src
sudo cp dkms.conf /usr/src/e1000e-dkms.conf
cd /usr/src
sudo tar xzvf e1000e-1.6.2.tar.gz
cd e1000e-1.6.2
sudo mv ../e1000e-dkms.conf dkms.conf
sudo dkms add -m e1000e -v 1.6.2
sudo dkms build -m e1000e -v 1.6.2
sudo dkms install -m e1000e -v 1.6.2
echo "Now restart computer."
```

Step 5.  Restart the computer.
```

sudo shutdown -r now
```

Step 6.  Assign the card.

```
sudo ifconfig eth0 192.168.1.100
sudo ifconfig eth0 up
```

Yeah!! It works.

---

### Post by Jws0001 on 2011-11-08
> **fnerdwq said:**
> An alternative to the maverick-backport kernel is using the normal lucid kernel and building yourself a DKMS Package for the current version of the e1000e module.

It's realy simple:
1. Download the current e1000e module from
[http://sourceforge.net/projects/e1000/files/](http://sourceforge.net/projects/e1000/files/)
2. build the DKMS Package, following this instruction:
[https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging](https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging)

Then you're (hopefully) done...

good luck

This worked so easily for me.  I went to sourceforge and downloaded the latest stable version, then followed the instruction in the README after I unzipped the archive.  Literally all I had to do was:

tar -xvf e1000e-1.6.3.tar.gz
cd e1000e-1.6.3/src/
sudo make install
sudo modprobe e1000e
sudo dhclient eth0

Done.  Thanks for the help.

---

### Post by Bucky Ball on 2011-11-08
Comlong, please mark this thread as solved if it is. This helps others. ;)

---

### Post by Jws0001 on 2011-11-08
I do have another semi-related question though.  I did some system updates and I think the kernel got updated and this fix got erased.  I did it again and it still worked but is there a .deb or some more permanent solution?

---

### Post by Bucky Ball on 2011-11-11
This thread is very old (and very dead). You might do better posting a new thread with a descriptive thread title and as much info as you can give. ;)

---

