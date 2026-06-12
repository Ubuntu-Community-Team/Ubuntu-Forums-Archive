---
title: "Atheros AR9285 on HP ProBook 4530s (Mint14/Ubuntu12.10)"
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by GyroTech on 2013-01-21
I have an Atheros AR9285 and I cannot get it to work.

Having spent a day going through these forums and the Ubuntu bug tracker trying the related fixes I still havn't gotten any closer to a working wireless connection.

It seems that there is a hardware block somewhere:
```
$sudo rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

But pressing the physical button on the front of the laptop only turns everything off:
```
$sudo rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
```

I have installed the backport drivers:
```
$ sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-cw-3.6-quantal-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I have also tried resetting my BIOS to factory default settings, but that did not help.

I have tried adding various modules to the blacklist:
```
blacklist ath_pci
blacklist ath_hal
blacklist ath9k
blacklist hp-wmi
blacklist ath3k
```
All of these at once, individually, and in combinations, but nothing gave me a useable wifi connection.

Can someone suggest more tricks for me to try before I go completely mad??

---

### Post by gordintoronto on 2013-01-21
Have you succesfully set up a wireless connection in Ubuntu or Mint?  Does a network manager icon appear, near the speaker icon?

You've blacklisted ath9k, which is the driver your wireless card should be using, according to this:
[http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10](http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10)

Atheros has the reputation of just working, and my AR2413 has worked with all 40 distros or versions I have fooled around with.

---

### Post by GyroTech on 2013-01-22
I have connected quite a few different machines (Mint, Ubuntu, Debian) to the target network, but none of those had the AR9285 chip.

The network icon shows up just fine (I'm currently using a wired connection on the same machine), but with the wireless slider in the "Off" posistion. If I click it to turn it on, the menu just closes. when you open it again, the Wireless slider is still in the "Off" posistion. Interestingly, when you open up the Network Settings, the "Airplane mode" slider is set to "On", and this one you can turn on and off normally, though it doesn seem to affect anything (Bluetooth is always functional for example).

I'm sorry I wasn't clear about the blacklist, but none of those options currently exist in my */etc/modprobe.d/blacklist.conf* file, they are just ones I've tried in desperation. For instance the ath9k module is currently loaded on my system:

```
$ sudo lsmod | grep ath9k
ath9k                 145576  0 
mac80211              549341  1 ath9k
ath9k_common           14056  1 ath9k
ath9k_hw              408948  2 ath9k,ath9k_common
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
cfg80211              211134  3 ath9k,mac80211,ath
compat                 14950  9 rfcomm,bnep,ath9k,mac80211,ath9k_common,ath9k_hw,btusb,cfg80211,bluetooth

```

but the wifi is still listed as DISABLED
```
$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:78:5b:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d4700000-d470ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: 64:31:50:90:c2:67
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=172.16.24.167 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
```

and the physical wireless LAN is still listed as hard-blocked:
```
$ sudo rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by GyroTech on 2013-01-22
I have also tried disabling the hardware encryption for the card as it helped some users of the ath5k driver:

```
sudo echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```

But it didn't change anything after a reboot:
```
$ sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

---

### Post by GyroTech on 2013-01-24
Turns out having an ethernet cable connected acts as a hardware block to the wifi, as soon as I physically disconnected the ethernet, my wifi connection sprang into life...

Damn I feel dumb from this one :D

---

