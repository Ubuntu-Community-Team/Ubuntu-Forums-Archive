---
title: "[SOLVED] Can't use usb wireless with ar5523 chipset"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by sambarluc on 2008-12-16
Hi,
I see there's lot of discussion on this subject, but I couldn't find a solution working for me.
I just bought a USB wireless card with Atheros chipset, but can't use it with 8.10.
lsusb shows:
```
Bus 001 Device 002: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)
```
I tried with ndiswrapper, but could not make it work following any thread I have found. I have also read that an older version of ndiswrapper could have a utility to load the firmware, but could not compile it.
I have also read that ath5k driver should work, but I can not find the package in intrepid backports!
Any suggestion?
Thank you!

---

### Post by nixscripter on 2008-12-16
It's for a different card with the same chipset, but try these instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper))

---

### Post by sambarluc on 2008-12-17
It works!
Great, thank you! Just a comment, if you have a second wirless card you can't use wicd, but with (k)network manager it works just fine.

---

### Post by logari81 on 2010-05-27
For anyone who comes across this thread, please its time to stop spreading the nd_s_ra_per spam, there is a native driver for this device (0cf3:0002). In lucid run:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-generic module-assistant

```

download and install the following package:
[https://launchpad.net/~logari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0~lucid1_all.deb](https://launchpad.net/~logari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0~lucid1_all.deb)

run

```
sudo m-a a-i ar5523-source
wget http://verein.lst.de/~hch/ar5523.tgz
tar xf ar5523.tgz ar5523/uath-ar5523.bin --strip 1
sudo mv uath-ar5523.bin /lib/firmware

```

Connect the stick, you are ready.

---

### Post by harrykar on 2010-06-14
> **logari81 said:**
> For anyone who comes across this thread, please its time to stop spreading the nd_s_ra_per spam, there is a native driver for this device (0cf3:0002). In lucid run:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-generic module-assistant

```download and install the following package:
[https://launchpad.net/~logari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0~lucid1_all.deb]("https://launchpad.net/%7Elogari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0%7Elucid1_all.deb")

run

```
sudo m-a a-i ar5523-source
wget http://verein.lst.de/~hch/ar5523.tgz
tar xf ar5523.tgz ar5523/uath-ar5523.bin --strip 1
sudo mv uath-ar5523.bin /lib/firmware

```Connect the stick, you are ready.

Im in Lucid amd 64. I had followed a similar guide ([http://wiki.debian.org/ar5523](http://wiki.debian.org/ar5523)) then i installed ndiswrapper + win drivers and finally your guide(the difference respect debian guide(no problem with build install-loading driver) is  /lib/firmware dir instead/usr/local/lib/firmware) without uninstall ndiswrapper + win drivers but actually dongle not work(foremost no wlan0 interface)

PS: i open a thread about(lang it) :[http://forum.ubuntu-it.org/index.php/topic,391516.0.html](http://forum.ubuntu-it.org/index.php/topic,391516.0.html)

---

### Post by dc46and2 on 2010-06-23
Thanks logari81.  I have a D-Link DWL-G132 and was looking for a way to use it with 64-bit linux.  There are no 64-bit XP drivers, so ndiswrapper does't work.  Your instructions worked for me.

Lucid wanted to load the ndiswrapper module, so to make it work I issued:

```
modprobe -r ndiswrapper
modprobe ar5523
```It's a little slow, and signal strength is not reported, but it works.

---

### Post by dc46and2 on 2010-06-23
Oh yeah... and if you unplug the dongle or remove the ar5523 module, it locks the system.  This native driver looks promising, but still needs some work before it's ready for general use I think.  Looks like I'm going back to 32-bit and ndiswrapper for now.

---

### Post by sambarluc on 2010-07-22
> **logari81 said:**
> For anyone who comes across this thread, please its time to stop spreading the nd_s_ra_per spam, there is a native driver for this device (0cf3:0002). In lucid run:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential linux-headers-generic module-assistant

```

download and install the following package:
[https://launchpad.net/~logari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0~lucid1_all.deb](https://launchpad.net/~logari81/+archive/ppa/+files/ar5523-source_0-0ubuntu0~lucid1_all.deb)

run

```
sudo m-a a-i ar5523-source
wget http://verein.lst.de/~hch/ar5523.tgz
tar xf ar5523.tgz ar5523/uath-ar5523.bin --strip 1
sudo mv uath-ar5523.bin /lib/firmware

```

Connect the stick, you are ready.

Sounds great, but how does it work, on 32 bit? I want to be sure before I change, I need the network.
Thanks

---

### Post by sambarluc on 2010-08-02
I could test it on a machine, and actually the native driver works great, much better than with ndiswrapper. Unfortunately, it makes the kernel very unstable. In particular, disconnecting from a network or unplugging the device caused crashes (of the kernel). After a while the machine simply became unsuable, so I had to completely remove the drivers.
I think it's a good start, but needs a lot of improvement!
Now, I'm simply going for a natively supported card.

---

### Post by foodbaby on 2011-02-26
On Kubuntu 10.10 maverick 2.6.35-24-generic 64bit I tried the native driver by following instructions here: [http://wiki.debian.org/ar5523](http://wiki.debian.org/ar5523)

except for step 3 did the following to get the driver to work with kernel 2.6.35-24:

 3. Build and install a driver source package:

```

$ cd ar5523
$ patch < debian/patches/kcompat-2.6.35.patch 
$ dpkg-buildpackage -us -uc
$ su
# dpkg -i ../ar5523-source*deb

```and for step 5 it's slightly different on ubuntu:

5. Install the device firmware
```

 # mv ../uath-ar5523.bin /lib/firmware

```got the driver loaded but was somewhat unstable - caused some complete system hangs so gave up on it.

---

### Post by jarl on 2011-03-08
It seems like
[http://verein.lst.de/~hch/ar5523.tgz]("http://verein.lst.de/~hch/ar5523.tgz")
is gone, anybody knows where to find it?

Jarl

---

### Post by jarl on 2011-03-08
It seems like [http://verein.lst.de/~hch/ar5523.tgz]("http://verein.lst.de/~hch/ar5523.tgz") is gone. Anybody who knows where to find it?

---

### Post by jarl on 2011-03-08
> **jarl said:**
> It seems like [http://verein.lst.de/~hch/ar5523.tgz]("http://verein.lst.de/~hch/ar5523.tgz") is gone. Anybody who knows where to find it?

I found it on [http://damien.bergamini.free.fr/packages/openbsd/uath-firmware-1.0p0.tgz]("http://damien.bergamini.free.fr/packages/openbsd/uath-firmware-1.0p0.tgz")

The md5sum should be 3b976a7f9319289ab6c5891bc103a431

---

