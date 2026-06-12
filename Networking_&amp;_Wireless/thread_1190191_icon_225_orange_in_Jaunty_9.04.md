---
title: "icon 225 orange in Jaunty 9.04"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by IsraeliHawk on 2009-06-17
hi all,

i installed a friend of mine a fresh 9.04 with EXT4 system. 

She has a icon 255 orange netstick, and although its supposed to work "out of the box" something doesn't work..

any ideas how to configure it? i have a feeling it works just fine (it recognized it and all..), only the config. needs to be fixed..

i would enjoy all the help i could get.. 

thanks in advance.. 

Uri

---

### Post by IsraeliHawk on 2009-06-17
solved.

all you need to do is this (Israel configuration.. but it's quite global, to be exact..)

go to 'edit connections' in the wireless menu. in it insert these options:
number: *99#
username: orange
pass: orange
APN: uinternet (depending your country's config.!! ask your provider..)
network: **empty/blank**
PIN: (ask your provider)
PUK: **empty**

good luck :)

---

### Post by cariboo on 2009-06-17
Could you post the output of:

```
sudo lshw -C network
```

in your next post.

---

### Post by mathamor on 2009-06-21
~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:91:3a:6a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:dd:41:f8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=10.0.1.14 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:ac:d7:b2:ae:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by koketso Mabuse on 2009-09-07
Above is the Solution Guys, Had that issue a week ago and did excatly that. 

Find it on Network Manger
Enter Fake user name and password.. APN = according to your Service Provider...

---

### Post by AryehDen on 2009-12-17
What is Orange Israel's APN?  is it uinternet as you have written on the thread?  Or is there more I need to do.

Thanks,

Aryeh

---

### Post by alexfish on 2009-12-17
> **AryehDen said:**
> What is Orange Israel's APN?  is it uinternet as you have written on the thread?  Or is there more I need to do.

Thanks,

Aryeh

Hi should look like this

---

### Post by AryehDen on 2009-12-18
I could kiss you!
Thanks for the help

> **IsraeliHawk said:**
> solved.

all you need to do is this (Israel configuration.. but it's quite global, to be exact..)

go to 'edit connections' in the wireless menu. in it insert these options:
number: *99#
username: orange
pass: orange
APN: uinternet (depending your country's config.!! ask your provider..)
network: **empty/blank**
PIN: (ask your provider)
PUK: **empty**

good luck :)

---

### Post by alexfish on 2009-12-18
> **AryehDen said:**
> I could kiss you!
Thanks for the help

[COLOR="Navy"]The [SIZE="3"]Ubuntu[/SIZE] [SIZE="2"]Wizard Has IT ALL[/SIZE][/COLOR]

[COLOR="Navy"][SIZE="2"]Thanks Wizard[/SIZE][/COLOR]

---

