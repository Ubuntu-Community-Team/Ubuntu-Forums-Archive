---
title: "Ubuntu 10.04 Belkin Wireless N USB found but won't connect"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by dmlmidi on 2010-05-04
**_Solved thanks to clorinekid_**.  Read on for symptoms and final solution

I have been trying to get my Belkin FD8233-4v3 wireless-n usb adapter to work in Ubuntu since 8.04.  It has worked with ndiswrapper under 32-bit (never the 64-bit) versions in the past, but has never been able to be configured directly.  It uses the Ralink RT2870 chipset, but cannot seem to be configured using the drivers from the Ralink website.

With Ubuntu 10.04 64-Bit, everything has changed.  I have high hopes that this adapter may finally work correctly and without ndiswrapper.  As soon as I first booted 10.04, for the first time ever, Ubuntu recognized the IF automatically, reported my wireless router, allowed me to enter my 128-bit WEP hex code and tried to connect up.  It is failing miserably, but it is making a valiant effort.

So, next I tried the following in terminal:

$ sudo lshw -C network
The system returns the following profile for the Belkin USB IF:
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:2f:de:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

I then tried the following progression to get the network to connect:
  $ sudo ifconfig wlan0 down
  $ sudo dhclient -r wlan0
  $ sudo ifconfig wlan0 up
  $ sudo iwconfig wlan0 essid "MY_ESSID"
  $ sudo iwconfig wlan0 key MY_WEP_KEY
  $ sudo iwconfig wlan0 mode Managed
  $ sudo dhclient wlan0

With the results:
  Listening on LPF/wlan0/00:1c:df:2f:de:9b
  Sending on   LPF/wlan0/00:1c:df:2f:de:9b
  Sending on   Socket/fallback
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

I have also tried inserting the command line:
  $ sudo iwconfig wlan0 key open
but I still get the same results:
  Yada, Yada, Yada
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

Any ideas how to get the network connected with this IF?  Any help will be much appreciated.

---

### Post by dmlmidi on 2010-05-04
I have tried some additional variations:
1. I have tried to connect with and without WEP.
Result:  No success connecting with or without WEP security enabled.

2.I have tried using WEP key indexes 1,2,3 and 4.
Result: No success connecting using an alternate WEP key index.

---

### Post by chlorinekid on 2010-05-04
looks like your problem relates to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

ubuntu is loading two sets of drivers when it should only be loading one set. you need to blacklist the following and then restart system forcing it to load only one set of drivers.

open a terminal and enter:
> gksudo gedit /etc/modprobe.d/blacklist.conf

add the following to the end of the file:
> blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

restart system and see if that works.

problem relates to ralink drivers which is what you have..

---

### Post by dmlmidi on 2010-05-04
Thank you chlorinekid.  That was the solution.

I didn't have a chance to mention it, but I was also trying some blacklisting, however based upon my research in posts, of the RT2500 drivers.  That didn't solve it either.

I deleted my RT2500 blacklistings and copied and pasted yours into the blacklist. I am now running with great connection strength and throughput speed using WEP key index 1.

Again, thank you so much for your research and willingness to share.  I really appreciate it!

:guitar:

---

### Post by biocyberman on 2010-05-12
> **chlorinekid said:**
> 
ubuntu is loading two sets of drivers when it should only be loading one set.
Well, thanks for your information. I had problem with my Netgear WNR2000 after upgrading to Lucid. Switching from "WPA-PSK [TKIP] + WPA2-PSK [AES]" (mixed mode) to WPA2-PSK [AES] solved my problem. Nothing else like kernel updating has to be done.

---

