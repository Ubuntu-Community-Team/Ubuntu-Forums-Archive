---
title: "Broadcom Wireless problems after kernel update"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by Pablo W on 2011-01-18
I have a HP Mini 5105 SSD netbook, runing Ubuntu 10.10 with 2Gb RAM. My wireless card is a Broadcom BCM43224 802.11a/b/g/n. Its driver is enabled and running. The wired network connection runs fine too.

The problem:
Wireless stopped working. When I right click on the network icon, the “enable network” option is clicked, but  the "enable wireless" option is listed in dark grey and cannot be clicked on. I have recently updated my kernel version to 2.6.35-24-generic.


What I have already tried:
Thanks to [this post]("http://ubuntuforums.org/showpost.php?p=10312711&postcount=5") and [this one too]("http://ubuntuforums.org/showthread.php?t=1653568&page=3") I got to know  there seems to be a problem with the 2.6.35-24-generic kernel. I have gone into the GRUB menu (it took some time to find out that you have to keep the Shift key pressed during startup for the GRUB menu to show), chosen the older kernel version (2.6.35-23-generic) and then removed the faulty one. Nevertheless, nothing has changed. I still cannot enable the wireless.

The outcome to lshw -C network is:
```
pablo@pablo-netbook:~$ lshw -C network
WARNING: you should run this program as super-user.
 *-network DISABLED      
      description: Wireless interface
      product: BCM43224 802.11a/b/g/n
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:08:00.0
      logical name: eth1
      version: 01
      serial: 00:26:82:38:d8:61
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
      resources: irq:16 memory:e8000000-e8003fff
 *-network
      description: Ethernet interface
      product: 88E8072 PCI-E Gigabit Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@0000:20:00.0
      logical name: eth0
      version: 10
      serial: 18:a9:05:93:3b:86
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list rom ethernet physical
      configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
      resources: irq:44 memory:e0000000-e0003fff ioport:2000(size=256) memory:7fc00000-7fc1ffff
pablo@pablo-netbook:~$
```


I’m sorry to say I am a newbie who can hardly understand other than plain language instructions. Any help will be appreciated.

---

### Post by Pablo W on 2011-01-19
Hello... is there anybody out there being able to provide some kind of help on this please?

---

### Post by Pablo W on 2011-01-19
While waiting for a kind expert soul able to help me, I have made some progress. Apparently Ubuntu 10.10 has an outdated driver for the Broadcom BCM43224 card (version 5.60.48.36). The updated driver is available from the Broadcom website here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) (by the time I'm posting this, the driver version there is version 5.100.82.38 ).

I have already downloaded the new 32 bit driver. So, my question now is: how do I replace the older driver with the new one?

Thanks.

---

### Post by Pablo W on 2011-01-19
This post was a duplicated of the previous one.

---

### Post by TBABill on 2011-01-19
Before installing the new driver, it's possible the old works just fine and an update borked its use temporarily. Can you post the output of ```
sudo rfkill list
``` and if you see either SOFT or HARD blocked maked as YES, then ```
sudo rfkill unblock all
``` This may not be your issue, but an easy check.

---

### Post by TBABill on 2011-01-19
Before installing the new driver, it's possible the old works just fine and an update borked its use temporarily. Can you post the output of ```
sudo rfkill list
``` and if you see either SOFT or HARD blocked maked as YES, then ```
sudo rfkill unblock all
``` This may not be your issue, but an easy check.

---

### Post by TBABill on 2011-01-19
Before installing the new driver, it's possible the old works just fine and an update borked its use temporarily. Can you post the output of ```
sudo rfkill list
``` and if you see either SOFT or HARD blocked maked as YES, then ```
sudo rfkill unblock all
``` This may not be your issue, but an easy check.

---

### Post by Pablo W on 2011-01-19
> **TBABill said:**
> Before installing the new driver, it's possible the old works just fine and an update borked its use temporarily. Can you post the output of ```
sudo rfkill list
``` and if you see either SOFT or HARD blocked maked as YES, then ```
sudo rfkill unblock all
``` This may not be your issue, but an easy check.

Thanks, TBABill.
Here is the outcome of the first one

```
pablo@pablo-netbook:~$ sudo rfkill list
[sudo] password for pablo: 
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
pablo@pablo-netbook:~$ 
```

When I type ```
sudo rfkill unblock all
``` nothing happens.

---

### Post by Pablo W on 2011-01-19
Hi again.
Just to say that, embarrassingly enough, just pulling from the wireless front switch brought wireless back. I should probably have tried that first.

Because of the design of the wireless button, it is almost impossible to accidentally switch wireless on (or off). I wonder whether the card was switched off by a software update.

I will keep reporting in case of new events. Thanks for your help.

---

