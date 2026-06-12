---
title: "Need help getting D-Link DWA-160 to work in 8.10"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by bij33 on 2009-03-12
I downloaded and installed the Linux driver for DWA-160 rev.A1 Xtreme N USB wireless NIC from D-Link website but nothing seems to work.
The wireless card is not in the list when I issue ifconfig command. The hardware is OK because it works fine in XP. 

Any help would be immensely appreciated.


root@p670:/# lsusb
Bus 005 Device 004: ID 07d1:3c10 D-Link System 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 002 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@p670:/#

---

### Post by rickzoll on 2009-04-01
I'm working to get DWA-160 installed and working as well.  D-link now has their first release of a Linux driver. 
[http://www.dlink.com/products/support.asp?pid=656&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=656&sec=0#drivers)
Now I don't have this working yet but I'm working on it.  It's clear this is their first linux driver release because there's some typos and it is not very straight-forward.
rickzoll.

---

### Post by Spr0k3t on 2009-04-16
Looks like there are two revisions of this USB hardware.  From what I can tell, there are no drivers yet available for revB.

I haven't had much luck building the 64bit drivers just yet.  We'll see what happens soon.

---

### Post by Spr0k3t on 2009-04-18
I'm making some headway here.  I was able to compile the drivers (64bit) and even issue the command iwlist scan to see the available networks... I'll post up some more information here in a bit.

The DWA-160 REV:A1 does work with the latest OtusLinux drivers.  The drivers found on the D-Link site are buggy.

First of all, you will need a few tools to grab the latest revision of the driver.
```
sudo apt-get install linux-headers-generic git-core libssl-dev
```
Next, download the drivers for the tool-chain
```
cd /usr/src/
sudo git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git
```
Time to compile the source tree
```
make
sudo make install
```
Now you can test to see if it works or not
```
sudo modprobe arusb_lnx
iwconfig
```
You should see something like this
```
athX    IEEE 802.11-MIMO Nickname:"WAN"
        Frequency:2.422 GHz  Access Point: Not-Associated   Sensitivity=0
        Power Management:off
```
Okay, if you got this far, you are 90% of the way there... about where I am as well.  Time to turn on the wireless for this AP
```
sudo ifconfig athX up
```
At this point, the LED will start blinking and you should be able to scan the WAN for available networks.
```
iwlist athX scan
```

Congrats... you have a working DWA-160.  I'm still working with the WPA_Supplicant as well as how to get the modules loaded into the system at startup.  I'm totally newb at the whole compiling source trees from GIT.  Quite a bit of my information has been taken from an [Italian site detailing the Netgear WPN111v2](http://dnax.netsons.org/usare-ladattatore-usb-80211n-wn111v2-con-ubuntu), I was just able to hammer it out for my system is all.  If you are able to take this any further than what I have done so far, please post your results and how you achieved them.

Notes: Replace athX with the corresponding node you have.  It will be ath0 if you have no other Atheros network devices in your system.

---

### Post by n.lindberg on 2009-04-29
Hello! Excellent post! I followed it and Yes it is working...

No to the problem.. My network is using WPA and after do /etc/init.d/NetworkManager restart my network appears dsabled in the network list. THere is a network that is of using WEP which is enabled. I tried install the WPA suplicant driver but my knowledge is limited.

Any good advice?

I really want to learn this...

Thanks in advance,

Niclas Lindberg

---

### Post by equinoxweb on 2009-05-16
I have tried following Spr0k3t commands.  All is good until I get to sudo make install.

/usr/src/otus$ sudo make install
make -C OAL/Otus/Linux/ install
cd: 1: can't cd to /lib/modules/2.6.24-16-generic/build
make[1]: Entering directory `/usr/src/otus/OAL/Otus/Linux'
Makefile:17: *** /lib/modules/2.6.24-16-generic/build is missing, please set KERNEL_SOURCE.  Stop.
make[1]: Leaving directory `/usr/src/otus/OAL/Otus/Linux'
make: *** [install] Error 2
/usr/src/otus$

there is no /build dir in /lib/modules/2.6.24-16-generic

Any ideas?

---

### Post by CDrewing on 2009-10-31
Hey guys,

is your DWA-160 connecting with 54 MBit (802.11g) or 300 MBit (802.11n)? My Xtreme N capable D-Link DIR-655 tells me that the USB adapter is online with only 54 MBit. But I am still using the Ubuntu-brought drivers of the Jaunty distribution.

Will upgrading to your hand-made drivers help?

Thx
Chris

---

