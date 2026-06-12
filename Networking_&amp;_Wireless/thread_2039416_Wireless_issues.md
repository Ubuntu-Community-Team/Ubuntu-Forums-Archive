---
title: "Wireless issues"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by mysteron75 on 2012-08-08
I am having issues with my wireless connection. Whenever i boot or reboot. I am having to go under network settings and reestablish my wireless connection. I have connect automatically check and make available to all users checked. This just started happening. I had been having issues getting diablo 3 running under wireless and i add:

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

I dont know if this is causing the issue. Please help

---

### Post by Hadaka on 2012-08-09
Hi, try this
click the antenna symbol...top right corner...
then click EDIT CONNECTIONS
then click WIRELESS
then click your SSID..your wifi
then click EDIT...same box as your SSID
then click WIRELESS SECURITY
enter YOUR WIFI PASSCODE and click SAVE
good luck.

---

### Post by Bucky Ball on 2012-08-09
> **mysteron75 said:**
> 

echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope



... should be:

```
echo 0 |sudo tee /proc/sys/kernel/yama/ptrace_scope
```

There needs to be a space after 'echo 0'.

---

### Post by mysteron75 on 2012-08-09
Hi, try this
click the antenna symbol...top right corner...
then click EDIT CONNECTIONS
then click WIRELESS
then click your SSID..your wifi
then click EDIT...same box as your SSID
then click WIRELESS SECURITY
enter YOUR WIFI PASSCODE and click SAVE
good luck.

Didnt work. I dont have issues connecting. My computer just wont stay connected after a reboot and i have to manually connect to my wifi every time i use my laptop.

---

### Post by andox on 2012-08-09
I just switched from Ubuntu to Xubuntu. I'm having the same problem on Xubuntu, and I had the same problem on Ubuntu.

The only difference between you and I are that I didn't do anything network related to both OS. I'm just assuming that the linux drivers are just not good enough.

---

### Post by Bucky Ball on 2012-08-09
> **andox said:**
>  I'm just assuming that the linux drivers are just not good enough.

Extremely doubtful (there possibly isn't a Linux driver for your card, though, if very new) and not sure what's made you come to that conclusion. If you have issues please post a new thread as hijacking with another issue makes things v confusing for helpers and is unfair to original poster. ;)


Anyhow, please post the output of this command from a terminal:

```
sudo lshw -C network
```There is the possibility that the drivers/firmware are not installed properly. This will tell us something about that. The other possibility is it needs a little gentle persuasion.

That command will also tell us the card you are using which would help a lot!

---

### Post by mysteron75 on 2012-08-09
I ran the command and this is what I got:


*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e8:39:df:14:c0:23
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic firmware=N/A ip=192.168.2.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fc400000-fc40ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:a5:9c:66
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fc500000-fc503fff ioport:4000(size=256)

---

### Post by Bucky Ball on 2012-08-10
driver=ath9k driverversion=3.2.0-27-generic

As it should be. You might try using Mad Wifi instead of Network manager. That is specifically for Atheros cards (which yours is).

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by mysteron75 on 2012-08-10
Thanks it looks like ubuntu is seeing my wireless as hidden and its not. I will give madwifi a shot.

---

