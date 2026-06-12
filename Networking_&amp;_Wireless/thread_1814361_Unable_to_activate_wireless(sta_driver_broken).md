---
title: "Unable to activate wireless(sta driver broken?)"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by Mexi on 2011-07-29
[SIZE=2]Hello,
for over at week i have been trying to get my wireless card to work now.

If i open Additional drivers, the non proprietary driver seems to be working and active.[/SIZE]
[SIZE=2]If i deactivate that and use the STA driver instead, it says active, but currently not in use.

When i use the non proprietary driver, i can check mark on 'activate wireless', but nothing happens.

When i use the STA driver there are no wireless options.

I'm not sure if its important, but when i do "sudo lshw -C network" when the STA driver is active but not in use, the network status changes from 'disabled' to 'unclaimed'.
[/SIZE]
[SIZE=2]When i came here, i tried to install[/SIZE] "firmware-b43-lpphy-installer" [SIZE=2]as the sticky said i should, but the installation fails.
It says my card is not supported: "Not supported card here (PCI id 14e4:4727)!"[/SIZE]

[SIZE=2]Before i came here i have tried:[/SIZE]

getting driver(or is it firmware?(or is that the same?)) from here([http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09))
Result: i put the files in /lib/firmware/brcm but don't know where to go from here, nothing shows up in additional drivers that wasn't there already.


Installing the STA proprietary driver, i also tried removing it and installing it again.
Result: Active, but currently not in use(even after reboot)


Using synaptic package manager i installed "linux-backports-modules-cw-2.6.39-natty-generic"
Result: no change of anything as far as i can tell


[SIZE=2]In the guide to post about wireless it said to post a lot of information so here it is:[/SIZE]

Commands in bold

Lenovo b560

Ubuntu 11.04

**lspci:**

Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

[B]iwconfig:
[/B]
wlan0 IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=off
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn

**lsmod:**

zak@zak-Lenovo-B560:~$ lsmod | grep "brcmsmac"
brcmsmac 590330 0
mac80211 259567 1 brcmsmac
cfg80211 155552 2 brcmsmac,mac80211

[B]
dmesg:[/B]

zak@zak-Lenovo-B560:~$ dmesg | grep "brcmsmac"
[ 563.726360] brcmsmac 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 563.726371] brcmsmac 0000:04:00.0: setting latency timer to 64
[ 563.899990] brcmsmac 0000:04:00.0: PCI INT A disabled
[ 563.900288] brcmsmac 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 563.900304] brcmsmac 0000:04:00.0: setting latency timer to 64


**sudo lshw -C network:**

*-network DISABLED
description: Wireless interface
product: BCM4313 802.11b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wlan0
version: 01
serial: ac:81:12:49:64:ec
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=brcmsmac driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:f2500000-f2503fff


**iwlist scan:**

zak@zak-Lenovo-B560:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wlan0 Failed to read scan data : Network is down

**uname -mr:**

zak@zak-Lenovo-B560:~$ uname -mr
2.6.38-10-generic i686

**sudo /etc/init.d/networking restart:**

zak@zak-Lenovo-B560:~$ sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.

[SIZE=3]
Any help would be greatly appreciated :)[/SIZE]

---

### Post by wildmanne39 on 2011-07-29
Hi, the drivers you need can be installed through synaptic, so remove the ones you downloaded from the outside source.

Then look at the link and install the ones you need for your system.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
If you need more help post back here.
Thank you

---

