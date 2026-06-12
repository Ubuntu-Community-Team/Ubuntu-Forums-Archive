---
title: "wireless problems: Natty, Ralink RT2860"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by eltonw on 2011-04-30
Machine: Asus EEE 1000 PC netbook running Natty Narwhal / Ubuntu 11.04
Modem: Siemens Speed Stream 4200 ADSL
Router: Linksys Wireless-N Home Router WRT120N-CA

I did a clean install of the GA release of 11.04 on my Asus EEE netbook on the release date 28 April. No updates available / applied since then. 

As of yesterday, April 29, I am having problems connecting. Natty keeps trying then asks for the password, again ... and again ... and again.
The machine itself is barely 5 feet  / 3 m away from the router! 

:([COLOR="Red"][FONT="Georgia"]This is precisely the **same problem** that we had when Karmic Kola was released a year ago[/FONT][/COLOR]:(

 ... and I am typing this on a Macbook (OSX 10.6.7) that is further away from said router.

Are there newer drivers for the Ralink card? 

... or a fix for this?

TIA for any pointers to a solution. 

(Of course, I guess I can connect the netbook to the router via a network cable, but this does not solve the Wifi problem... :(   ... nor is a convenient "solution")

---

### Post by garvinrick4 on 2011-04-30
To locate what type of card exactly and if a driver and what is installed:
```
rick@rick-HP:~$ sudo lshw -C network
[sudo] password for rick: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:48:8f:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 ip=192.xxx.xxx latency=0 link=yes multicast=yes 
```** See near the bottom where it says driver iwlagn:
```
rick@rick-HP:~$ locate iwlagn
/etc/modprobe.d/iwlagn.conf
/lib/modules/2.6.38-6-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.38-7-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-2.6.38-8-generic/include/config/iwlagn.h


```

---

### Post by eltonw on 2011-04-30
Thank you, garvinrick4!

I have to do a 'sneakernet' to copy from the Asus netbook to my Macbook: copy-paste text save to USB then copy over to mac..

Here are the results of the commands:

*-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:ed:c8:c3
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:00:5e:7b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fbef0000-fbefffff
===================================================================
locate rt2800pci
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
/usr/src/linux-headers-2.6.38-8-generic/include/config/rt2800pci
/usr/src/linux-headers-2.6.38-8-generic/include/config/rt2800pci.h
/usr/src/linux-headers-2.6.38-8-generic/include/config/rt2800pci/rt33xx.h
/usr/src/linux-headers-2.6.38-8-generic/include/config/rt2800pci/rt35xx.h

---

### Post by eltonw on 2011-04-30
**[COLOR="Red"]ADDENDUM[/COLOR]**: I have been doing some further research, and came across newer firmware for the network card:rt2680.bin dated 2010-01-27. I am positive that I have NOT done any firmware updates to this card since the machine was purchased (2008-12-28). 

_Downloaded from the Ralinktech linux section_

I am inclined to believe that this firmware might improve things, but I must confess ignorance on HOWTO do a firmware update in linux.

---

### Post by estevez on 2011-04-30
Hi,

 I am using eeepc 901, with the same wifi chip (ralink 2860), but my driver is RT2860 not rt2800pci.

I had a few issues with wifi in natty, now is everything working ok. 

You can try:

different driver - blacklist other rt28xx modules as suggested here - [http://ubuntuforums.org/showthread.php?t=1617290](http://ubuntuforums.org/showthread.php?t=1617290)

or

compile new driver, its little bit tricky, if you arent familiar with terminal, but  complete directions are here - [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

or

 if wireless works on boot, and is unable to connect only after resume from suspend, or if your laptop is running on battery then maybe just this trick will help you. You have to disable power saving script for wireless and/or pcie_aspm which is easy. just create empty files in /etc/pm/power.d/

You can see details here - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773018](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773018)

Combination of first and third workaround solved my problems with wireless in natty.

Wish you a luck and happy wireless browsing.

---

### Post by eltonw on 2011-04-30
Muchísimas gracias, estevez. 
I tried your first suggestion and edited the blacklist file as recommended:
 [http://ubuntuforums.org/showthread.php?t=1617290]("http://ubuntuforums.org/showthread.php?t=1617290")

If this is not asking too much, I would appreciate directions on how to do the firmware update as I mentioned in my [COLOR="Red"]**ADDENDUM **[/COLOR]to the post.

---

### Post by jawilljr on 2011-04-30
> **eltonw said:**
> Muchísimas gracias, estevez. 
I tried your first suggestion and edited the blacklist file as recommended:
 [http://ubuntuforums.org/showthread.php?t=1617290]("http://ubuntuforums.org/showthread.php?t=1617290")

If this is not asking too much, I would appreciate directions on how to do the firmware update as I mentioned in my [COLOR="Red"]**ADDENDUM **[/COLOR]to the post.

All you have to do is copy the rt2860.bin file to /lib/firmware as follows:

First just in case save the old one:

```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bin.old
```

Next copy the your downloaded firmware:

```
sudo cp /path/to/new/firmware/2860.bin /lib/firmware/2860.bin
```

Of course change the path the the new firmware.

Jerry

---

### Post by paped on 2011-05-01
Thanks you for the advice, step 1 of post 5 worked for me. Found this post due to the wireless on my EEEPC 901 being broken/unstable after an upgrade to 11.04 from 10.10, would work slowly for a couple of minutes then fail completely and need a reboot to work again. It is now stable and showing as using the correct rt2860 rather than the rt2800pci driver as it did after the upgrade.

---

### Post by eltonw on 2011-05-01
> **jawilljr said:**
> All you have to do is copy the rt2860.bin file to /lib/firmware as follows:

First just in case save the old one:

```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bin.old
```

Next copy the your downloaded firmware:

```
sudo cp /path/to/new/firmware/2860.bin /lib/firmware/2860.bin
```

Of course change the path the the new firmware.

Jerry

Thank you. It was a good (and welcome) bit of practice of using console commands.:grin:

---

### Post by sgerrand on 2011-05-17
i would strongly recommend not performing a custom compile of the drivers for the rt2680 network card. the serialmonkey crew do a great job of creating solid and tested drivers for the rt2x00 series of nics.

instead, i would recommend following the blacklist technique. adding the following to **/etc/modprobe.d/blacklist.conf** was enough for me:
```

blacklist rt2800pci
blacklist rt2x00pci

```

this was enough to get my wlan interface back to normal - i.e. it now resumes from sleep/connection interruptions and has no issue connecting to networks with different encryption (wep/wpa/etc).

hope that helps!

---

