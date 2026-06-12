---
title: "Wireless won't resume in 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by NutmegCT on 2010-05-07
Good day all.

I've read many threads here on wireless problems in 10.04.  I've got it updated as of this morning.

Symptom:  wireless works perfectly - doesn't drop out and starts right up at boot.  But if computer (Dell Latitude D505) goes to sleep, wireless won't resume.  Network Manager shows wireless networking greyed out after waking.

Here's output that should be helpful:

xxx@xxx-laptop:~$ sudo lshw -C network
[sudo] password for xxx: 
  *-network:0             
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcffc000-fcffdfff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:0f:1f:a9:89:d5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:fcffe000-fcffefff ioport:ecc0(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:a9:e9:3e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.125 multicast=yes wireless=IEEE 802.11bg

I've read in several other threads here that blacklisting the wireless driver file(s) may resolve the problem. 

-  What driver file(s) on the computer do I blacklist?

Thanks.
Tom

---

### Post by chili555 on 2010-05-07
You have a Broadcom wireless device that seems to be working correctly; from a fresh boot you can get an IP address:> network
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:90:96:a9:e9:3e
capabilities: ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]ip=192.168.1.125[/COLOR]No blacklists are needed.

This works for some cards that won't wake up from suspend. Let's create a file:```
sudo gedit /etc/pm/config.d/config
```The text editor gedit will open a new file. Add one line:```
SUSPEND_MODULES="b43"
```Proofread carefully. Save and close gedit. Now does it work as expected?

Warning to the searchers: this depends on your wireless driver; if your driver isn't b43, substitute your driver here. Also, this seems to work with some, but not all wireless cards.

---

### Post by NutmegCT on 2010-05-07
Chili - it works!

I did as you said, saved the new config file with the single SUSPEND line, but then I rebooted.  Maybe I shouldn't have done that?

Anyway, after reboot, I saw wireless start up as usual.  Hit a few websites just to make sure.  Then put the laptop to sleep.  After a minute, I woke it up, and watched Network Manager spin the arrows as usual.  But this time the arrows stopped, the wireless "beam" icon appeared, and the message "network connected" appeared.  Back online.  First time that's happened since I moved from KK to LL a few weeks ago.

Sound good?

Tom

---

### Post by chili555 on 2010-05-07
Sounds perfect! A few searchers will like it, too. Enjoy!

---

### Post by diddyone on 2010-05-07
i have 10.04 lucid kernal 2.6.32-22 running on my toshiba laptop after update my wireless stopped working i have network-manager

sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-d800ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:10:d5:04
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:4000(size=256) memory:da000000-da000fff memory:d4000000-d401ffff(prefetchable)


is there any help

---

### Post by pdc on 2010-05-08
Hi diddyone

You need to start a new thread;

chili555 has helped someone with a broadcom card;

you have an atheros card;

post with your details in the title line

---

### Post by uutnubu on 2010-05-08
Chili555

Worked for me too!  Thanks!!!   ):P

---

### Post by NutmegCT on 2010-05-08
> **uutnubu said:**
> Chili555

Worked for me too!  Thanks!!!   ):P

We're all thanking the Ubuntu guys - and it sure helps when we share what we learned!

Tom

---

### Post by aeqel on 2010-05-09
Confirmed it works for me with the ath9k driver, sounds universal thanks Chilli555 - it was becoming a little bit of a nuisance. 

Though, I'll contribute a bit here for those who might have a bit of trouble.

**How to find your wireless driver:**
-Restart and connect to wireless. 
-Once connected right click the wireless icon and select connection information, now you can see what wireless driver you have.

Now you can follow Chilli555's instructions replacing "b43" (if your driver isn't b43) with your driver.

---

### Post by pedpie on 2010-05-19
Works great with my AR928X adapter.

---

### Post by Doctor T on 2010-06-13
> **aeqel said:**
> Confirmed it works for me with the ath9k driver, sounds universal thanks Chilli555 - it was becoming a little bit of a nuisance. 

Though, I'll contribute a bit here for those who might have a bit of trouble.

**How to find your wireless driver:**
-Restart and connect to wireless. 
-Once connected right click the wireless icon and select connection information, now you can see what wireless driver you have.

Now you can follow Chilli555's instructions replacing "b43" (if your driver isn't b43) with your driver.
This didn't work for me unfortunately, and I have an ath9k as well.  :(  I have the same symptoms as the original post i.e. lose wlan after waking up from sleep.  Is there an alternate fix I could try?  Should I start another thread?  (Lucid Lynx)

---

### Post by scur on 2010-10-17
> Originally Posted by aeqel 
How to find your wireless driver:
-Restart and connect to wireless. 
-Once connected right click the wireless icon and select connection information, now you can see what wireless driver you have.

Now you can follow Chilli555's instructions replacing "b43" (if your driver isn't b43) with your driver.

mine only has 'ndiswrapper' for the driver. do i just use this?

---

### Post by chili555 on 2010-10-17
> **scur said:**
> mine only has 'ndiswrapper' for the driver. do i just use this?Please do and then post back so the searchers will learn. Thanks.

---

### Post by scur on 2010-10-17
> Originally Posted by aeqel 
How to find your wireless driver:
-Restart and connect to wireless. 
-Once connected right click the wireless icon and select connection information, now you can see what wireless driver you have.

Now you can follow Chilli555's instructions replacing "b43" (if your driver isn't b43) with your driver.


scur: mine only has 'ndiswrapper' for the driver. do i just use this?\

chili555: Please do and then post back so the searchers will learn. Thanks.


nope, i still can't suspend or hibernate and come back up with wireless or a way to get it going without rebooting. i'd dig deeper, but still haven't gotten much of a handle on linux yet.

---

### Post by Sam Fallow on 2011-07-31
Just thought I'd update this thread for future searches. 

```
sudo gedit /etc/pm/config.d/config
``````
SUSPEND_MODULES="ndiswrapper"
```

This worked for me. Wifi using ndiswrapper now reappears after suspend. 
I'm using 10.04 with a realtek rtl8187b wifi card.

---

