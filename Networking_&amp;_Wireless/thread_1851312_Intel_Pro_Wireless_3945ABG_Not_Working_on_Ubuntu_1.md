---
title: "Intel Pro /Wireless 3945ABG Not Working on Ubuntu 11.04&#8207;"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by shian_god_0 on 2011-09-28
I have recently installed Ubuntu 11.04 on my Acer Aspire 5633WLMi. However, the wireless function is not working.
I have read several post from this forum but I could not find any solutions.
Here are some of the information from my laptop:

**sudo rfkill list all**
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

**dmesg | grep iwl**
[   14.637153] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.637157] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   14.637229] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.637245] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.691625] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.691631] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.699786] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   14.897849] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.931258] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   19.940136] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.
[   21.988067] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.
[  142.272094] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.

**sudo lshw -C network**
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:75:cd:a3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-11-generic-pae firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d0100000-d0100fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:cd:36:fe
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:d0000000-d0001fff

Hope anyone can help me with this, thank you.

Regards,
Mika

---

### Post by chili555 on 2011-09-28
Please check here: [http://ubuntuforums.org/showthread.php?t=1837729&highlight=iwl3945](http://ubuntuforums.org/showthread.php?t=1837729&highlight=iwl3945)

---

### Post by shian_god_0 on 2011-09-28
Hi Chili555,

Thanks for the reply.
I have installed linux-backports-modules-cw-2.6.39-natty-generic. The wireless still do not work.
When I checked on my installed software, I found these has been installed too:
linux-backporrts-modules-cw-2.6.39-natty-generic-pae
linux-backporrts-modules-cw-2.6.39-2.6.38-10-generic
linux-backporrts-modules-cw-2.6.39-2.6.38-11-generic
linux-backporrts-modules-cw-2.6.39-2.6.38-11-generic-pae
Not sure whether these will affect the 1st package.

Thank you.

---

### Post by chili555 on 2011-09-28
> The wireless still do not work.Is the dmesg still the same?> [ 17.931258] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[ 19.940136] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.
[ 21.988067] iwl3945 0000:05:00.0: [COLOR="Red"]Wait for START_ALIVE timeout after 2000ms[/COLOR].I have been Googling this and have no answers yet.

Does the card work correctly in any other Linux live CD or USB versions or Windows?

---

### Post by shian_god_0 on 2011-09-28
Hi Chili555,

This is my old laptop and the wireless works well with Windows Vista.
As for the **dmesg | grep iwl**
Here is the new message I got:

[   13.886925] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.886929] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   13.887010] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.887026] iwl3945 0000:05:00.0: setting latency timer to 64
[   13.944067] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.944072] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.944231] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   14.244825] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.736129] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   16.777261] iwl3945 0000:05:00.0: Hardware error detected.  Restarting.
[   16.777271] iwl3945 0000:05:00.0: Loaded firmware version: 15.32.2.9
[   16.777277] iwl3945 0000:05:00.0: Not valid error log pointer 0x00000000
[   16.777283] iwl3945 0000:05:00.0: Invalid event log pointer 0x00000000
[   18.744031] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.
[   18.816650] iwl3945 0000:05:00.0: Hardware error detected.  Restarting.
[   18.816660] iwl3945 0000:05:00.0: Loaded firmware version: 15.32.2.9
[   18.816667] iwl3945 0000:05:00.0: Not valid error log pointer 0x00000000
[   18.816672] iwl3945 0000:05:00.0: Invalid event log pointer 0x00000000
[   20.784058] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.

It shown that it has hardware error. 
I had been googled on 'START_ALIVE' too but did not find any useful information.
:?

---

### Post by chili555 on 2011-09-28
> [ 16.777277] iwl3945 0000:05:00.0: Not valid error log pointer 0x00000000
[ 16.777283] iwl3945 0000:05:00.0: Invalid event log pointer 0x00000000
[ 18.744031] iwl3945 0000:05:00.0: Wait for START_ALIVE timeout after 2000ms.
[ 18.816650] iwl3945 0000:05:00.0: Hardware error detected. Restarting.I have been Googling these errors to no avail. I suggest you download a live CD .iso from another distro, Fedora or PCLinuxOS, for example and run the live CD to see if the card works. Check dmesg for errors or warnings.

You might also file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

My 3945ABG works perfectly in 11.04 (and in 11.10 daily build on a live USB key) so I don't really think it's a driver or kernel error.

I'm sorry I could not be of more help.

---

### Post by shian_god_0 on 2011-09-29
Hey Chili555,

Thanks for your help and information.
I will try the solution that you provided to test my wireless hardware.
You have helped me a lot in this and I appreciate every reply from you.
Thank you once again and wish you have a nice day.

---

