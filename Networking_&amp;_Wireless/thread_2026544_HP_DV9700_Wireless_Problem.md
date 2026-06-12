---
title: "HP DV9700 Wireless Problem"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by BondFF on 2012-07-15
Hey guys/gals,

Brand new to the forum and to Ubuntu as well.  I've recently installed 12.04 on my HP DV9700 laptop, and I really like it so far.

My wired connection works just fine, but I'm having some difficulty getting wireless to work.  

I ran lshw -C network and here are the results:

*-network
description: Ethernet inferface
product:  MCP65 Ethernet
vendor: NVIDIA Corporation
physical id: 6
bus info: pci@0000:00:06.0
logical name: eth0
version: a3
serial: 00:1e:68:71:f0:ac
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotation

*network DISABLED
description: Wireless Interface
product:  BCM4321 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth1
version: 03
serial:  00:21:00:18:5c:ce
width: 64 bits
clock:  33MHz
capabilities: bus_master cap_list ethernet physical wireless
config: boradcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff

When I right-click on my connections is shows: Wireless is disabled by hardware switch.  The physical switch on the front of the laptop is on.  

Not sure where to go from here - any help would be greatly appreciated!

---

### Post by chili555 on 2012-07-15
Please let us see:```
rfkill list all
lsmod | grep hp
```Thanks.

---

### Post by BondFF on 2012-07-15
> **chili555 said:**
> Please let us see:```
rfkill list all
lsmod | grep hp
```Thanks.

0:  brcmwl -0: Wireless LAN
Soft blocked: no
Hard blocked: yes
1:  hp:wifi:  Wireless LAN
Soft blocked: no
Hard blocked: yes
2: hp-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: yes
_______________________________________

hp_wmi                 13652     0
sparse_keymap    13658     1  hp_wmi
wmi                       18744     1  hp_wmi

---

### Post by chili555 on 2012-07-15
Now, please try:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Is it working now? If so, we'll need to amend one file and make it persistent.

---

### Post by BondFF on 2012-07-15
> **chili555 said:**
> Now, please try:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Is it working now? If so, we'll need to amend one file and make it persistent.

Hey Chili,

This is what I got after typing in those commands:

WARNING:  All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Then I input unblock all.  Then rkfill list all.

It showed me:

0: brcmwl -0: Wireless LAN
Soft Blocked: no
Hard Blocked: yes

I did a reboot and now and I still get the same "Wireless is disabled by hardware switch" message.

---

### Post by chili555 on 2012-07-15
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Oops! Let's figure this out first. Please let me see:```
cat /etc/modprobe.d/blacklist
```We'll place the contents in a proper file first.> Then I input unblock all. Then rkfill list all.

It showed me:

0: brcmwl -0: Wireless LAN
Soft Blocked: no
Hard Blocked: yes

I did a reboot and now and I still get the same "Wireless is disabled by hardware switch" message.It doesn't do much good to reboot and wipe out what we're trying to accomplish. Please stop until we figure out and implement the fix.

Please see attached. Open a terminal and do:```
rfkill list all
```Now move the switch #4 and run again:```
rfkill list all
```Is there any change? If not, do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Move the switch again.```
rfkill list all
```Is there *any* point where the wireless is not hard blocked?

Please do not reboot until we find the fix.

---

### Post by Kirk Schnable on 2012-07-15
Hard blocking usually indicates the wireless switch is off.  If this laptop has a hardware wireless switch, please make sure it's flipped to On.  If it has a hotkey like Function+F5, please try that a few times and see if you can get the hard block removed.

Kirk

---

### Post by BondFF on 2012-07-15
So when I flip the wireless switch off I get this:

0: brcmwl -0: Wireless LAN
Soft blocked: no
Hard blocked: yes

1: hp-wifi: Wireless LAN
Soft blocked : no
Hard blocked: no

It also takes the block off bluetooth, which works when the wireless switch is OFF, but the bluetooth shuts down when I turned the wireless switch on.

---

### Post by BondFF on 2012-07-15
Ok, so I turned the wireless switch off - and bluetooth was connected.  I manually dc'ed the bluetooth, right clicked on my connections, and I was able to connect to wireless!

So:

Switch Off = Wireless but no bluetooth
Switch On = Bluetooth but no wireless

Very strange - but I have a connection now.  I really appreciate the help!

---

### Post by chili555 on 2012-07-15
Would you please use thread tools at the top to mark Solved?

Glad it's working!

---

### Post by BondFF on 2012-07-15
Thanks again for the help!  I'm really digging Ubuntu so far, and I came from W7.  :D

---

### Post by Kirk Schnable on 2012-07-15
> **BondFF said:**
> Thanks again for the help!  I'm really digging Ubuntu so far, and I came from W7.  :D

Glad you're enjoying it! :)  You might be able to "fix" the Bluetooth issue by booting into Windows with the wireless switch off, then turning the wireless switch on.

You could also try pulling the CMOS battery.  When our wireless settings got funky on Lenovo netbooks at work, that was the "fix" we came up with to get everything working right again.

As always feel free to stop back by the forums if you have other questions!

Kirk

---

