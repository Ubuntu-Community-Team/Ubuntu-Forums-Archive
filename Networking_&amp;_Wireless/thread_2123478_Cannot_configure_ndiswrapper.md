---
title: "Cannot configure ndiswrapper"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by lucaghera on 2013-03-08
Hi all,

I wanted to install a USB-to-WIFI adapter on a pc.

I followed the instructions reported here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
However I'm stuck at the point 3.4

```
#sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

I tried to install from sources as Tom suggested here: [http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found) 
However when I type "make" it returns the following error:

```
# make
make -C utils
make[1]: Entering directory `/tmp/ndiswrapper-1.58/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/tmp/ndiswrapper-1.58/driver'
Makefile:41: *** Please run 'make modules_prepare' in /root/. Stop.
make[1]: Leaving directory `/tmp/ndiswrapper-1.58/driver'
make: *** [driver] Error 2


```

How can I fix this problem?
I have ubuntu 10.04 patched with xenomai:

```
# uname -a
Linux rh2c 2.6.34.5-pal-m3d-rt #3 SMP Thu Aug 2 14:36:05 CEST 2012 i686 GNU/Linux
```

```
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
```

---

### Post by Old_Grey_Wolf on 2013-03-08
Are you doing this on a desktop or server version of Ubuntu?

If a desktop version, after you installed ndisgtk from Ubuntu Software Center did you enter gksudo ndisgtk and navigate to where you had the driver stored?

---

### Post by Bucky Ball on 2013-03-08
*Thread moved to **Networking & Wireless***


Do you know what wireless chip the USB adapter is using and that you actually need ndiswrapper for it??? Ndiswrapper is largely superseded and can prevent any other drivers working when installed. Generally avoid and last resort.

Did you try just plugging the adapter in before going this route? Did you plug it in and do an update, for instance?

With the adapter plugged in, could you post the result of this command:

lsusb

Thanks.

---

### Post by lucaghera on 2013-03-08
Thanks all,

I have a version without graphical interface because it is an industrial pc.

I pluged in the adapter and executed an sudo apt-get update and upgrade.

However ifconfing doesn't list it.

This is the result of the lsusb command.

```
root@rh2c:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by lucaghera on 2013-03-12
If it could be easier for you I also have a Asus USB-N13 Wi-Fi Adapter.

This is the result of the lsusb command with that Adapter plugged in

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Bucky Ball on 2013-03-12
Bus 001 Device 002: ID 0baf:0118 U.S. _**Robotics U5 802.11g Adapter**_

That's the adapter. Clearly shown in the output of the first lsusb.

I suggest doing a search for the Robotics U5 and seeing if you can discover what wireless chipset it uses. Here's a start ...

Try post 26 here and follow the process from 'I removed ndiswrapper ...'

[http://ubuntuforums.org/showthread.php?t=1838434&page=3](http://ubuntuforums.org/showthread.php?t=1838434&page=3)

In other words, ndiswrapper is not required but it appears Prism is. I have no experience with Prism. 

As for the ASUSTek adapter, plug it in and do an update. See what happens. That might work out of the box, who knows. Again, do some googling for the device that is shown in the lsusb output. Good luck.

---

