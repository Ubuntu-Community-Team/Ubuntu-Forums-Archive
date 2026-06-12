---
title: "Can't install wireless driver"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by sheds on 2011-05-02
I just upgraded ubuntu to 11.04 and I need to install the wireless driver again. I downloaded the driver and I am getting the following error when running make:

./kernelversion.c:13:30: fatal error: linux/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.

Here's what I already installed on my laptop trying to get it fixed.

gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)
2.6.38-8-generic

lrwxrwxrwx  1 root src    22 2011-05-01 22:16 linux -> linux-headers-2.6.38-8
drwxr-xr-x 24 root root 4096 2011-04-30 17:40 linux-headers-2.6.38-8
drwxr-xr-x  7 root root 4096 2011-04-30 17:40 linux-headers-2.6.38-8-generic
drwxr-xr-x  4 root root 4096 2011-05-01 22:10 linux-source-2.6.38
lrwxrwxrwx  1 root root   47 2011-05-01 22:10 linux-source-2.6.38.tar.bz2 -> linux-source-2.6.38/linux-source-2.6.38.tar.bz2
drwxr-xr-x 14 root root 4096 2007-10-17 22:27 madwifi-0.9.3.3
drwxr-xr-x 11 root root 4096 2011-04-30 17:43 virtualbox-ose-4.0.4

What am I missing?

Thanks.

---

### Post by northd_tech on 2011-05-02
First, let's make sure what kind of wireless interface you have.  Let's see the results when you run the following terminal commands:

```
lspci | grep work
sudo lshw -C network
```

---

### Post by sheds on 2011-05-02
Hi.

I managed to get the version for my kernel. But it won't load the module.

punisher@Aspire:~$ modinfo ath_pci
filename:       /lib/modules/2.6.38-8-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r4136 (branch madwifi-0.9.4)
description:    Support for Atheros 802.11 wireless LAN cards.


06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


*-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:ec:48:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d030ffff

---

### Post by chili555 on 2011-05-02
The driver is loaded:> *-network DISABLED
description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 01
serial: 78:e4:00:ec:48:4b
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=ath9k[/COLOR] driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:d0300000-d030ffff We wonder why it is DISABLED. Please post:```
dmesg | grep ath
rfkill list all
```Thanks.

---

### Post by sheds on 2011-05-02
Here you go.


punisher@Aspire:~/Downloads$ dmesg | grep ath
[    0.120795]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.120807]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    0.919278] device-mapper: multipath: version 1.2.0 loaded
[    0.919281] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.874928] ath_hal: module license 'Proprietary' taints kernel.
[   13.877139] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.970684] ath_pci: svn r4136 (branch madwifi-0.9.4)
[   16.334349] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.334362] ath9k 0000:06:00.0: setting latency timer to 64
[   16.776850] ath: EEPROM regdomain: 0x65
[   16.776854] ath: EEPROM indicates we should expect a direct regpair map
[   16.776858] ath: Country alpha2 being used: 00
[   16.776861] ath: Regpair used: 0x65
[   16.840077] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.841573] Registered led device: ath9k-phy0::radio
[   16.841648] Registered led device: ath9k-phy0::assoc
[   16.841718] Registered led device: ath9k-phy0::tx
[   16.841788] Registered led device: ath9k-phy0::rx
punisher@Aspire:~/Downloads$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by northd_tech on 2011-05-02
Well, according to "Decline-" about 12 hours ago, installing WICD will fix the problem for an Atheros AR928X wireless:

[http://ubuntuforums.org/showthread.php?t=1746861&highlight=atheros+ar928x](http://ubuntuforums.org/showthread.php?t=1746861&highlight=atheros+ar928x)

I prefer WICD to the Gnome Network Manager (but I've currently got both installed I believe under Ubuntu 10.04.2 LTS, and they seem to get along fairly well).

It might be a good idea for you to post the results of this terminal command:

```
lsmod | grep at 
```I'm not all that familiar with the Atheros wireless units, however.

If you want to try WICD, go into System > Administration > Synaptic Package Manager and select these with a right click to "Mark for installation" after typing "wicd" in the search box:

```
wicd

wicd-gtk

wicd-daemon
```

---

### Post by sheds on 2011-05-02
punisher@Aspire:/etc/modprobe.d$ lsmod | grep at
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
ath_pci                93370  0 
wlan                  201118  1 ath_pci
ath_hal               195796  1 ath_pci
atl1c                  36237  0 
pata_atiixp            12968  0

This doesn't look good does it? I installed wicd and it failed just after installation. Perhaps the module before is in it's way.

Processing triggers for python-support ...
Setting up python-wicd (1.7.0+ds1-6) ...
Setting up wicd-daemon (1.7.0+ds1-6) ...
 * Starting Network connection manager wicd                                                                         [fail] 
Setting up wicd-gtk (1.7.0+ds1-6) ...
Setting up wicd (1.7.0+ds1-6) ...
Processing triggers for python-support ...

---

### Post by chili555 on 2011-05-02
> 0: acer-wireless: Wireless LAN
[COLOR="Red"]Soft blocked: yes[/COLOR]
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noWicd is unlikely to fix this. Please do:```
sudo rfkill unblock all
rfkill list all
```Is it unblocked? If not, try:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Is your wireless working?

We can modify two files so this is fixed at boot.

---

### Post by sheds on 2011-05-02
This last 3 line block did the trick, it took out the acer wireless thing.

punisher@Aspire:~$ sudo rmmod -f acer-wmi
punisher@Aspire:~$ sudo rfkill unblock all
punisher@Aspire:~$ rfkill list all
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

I am now connected to the hidden SSID network.

What do I do to make this permanent over reboots?

And also, what was wrong?

---

### Post by northd_tech on 2011-05-02
> **sheds said:**
> 
This doesn't look good does it? I installed wicd and it failed just after installation. Perhaps the module before is in it's way.

Processing triggers for python-support ...
Setting up python-wicd (1.7.0+ds1-6) ...
Setting up wicd-daemon (1.7.0+ds1-6) ...
 * Starting Network connection manager wicd                                                                         [fail] 
Setting up wicd-gtk (1.7.0+ds1-6) ...
Setting up wicd (1.7.0+ds1-6) ...
Processing triggers for python-support ...
I recall that Wicd required me to uninstall the Gnome Network Manager applet under Ubuntu 9.04 using the Synaptic Package Manager.  I was actually quite surprised that Ubuntu 10.04 LTS allowed me to have both installed, but I currently have both Network Manager Applet 0.8 and Wicd running as I type this.

Ubuntu 11.xx might be a different situation though, or have different dependencies, conflicts, etc.

Do you still show the Network Manager applet on your desktop?

---

### Post by sheds on 2011-05-02
Yes, but it's now more full of options, or perhaps this is the WICD working now. I cannot tell by simply looking at the drop down when clicking the icon where the network manager used to be.

---

### Post by chili555 on 2011-05-02
Let's make it permanent:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprbe.d/blacklist.conf
gedit /etc/rc.local
```Add one line above Exit 0```
rfkill unblock all
```Proofread carefully, save and close.```
exit
```Laptops require drivers, often called wmi, to translate key presses, such as the wireless key, into commands the kernel recognizes. Not all wmis are perfectly implemented. In your case, acer-wmi *prevented* your wireless from working so we removed it. If it causes other anomalies, post back and we'll help.

---

### Post by sheds on 2011-05-02
You two guys know too much, are you part of the ubuntu team?

---

### Post by chili555 on 2011-05-02
> **sheds said:**
> You two guys know too much, are you part of the ubuntu team?I'm just a guy with a laptop and too much time. Thanks.

---

