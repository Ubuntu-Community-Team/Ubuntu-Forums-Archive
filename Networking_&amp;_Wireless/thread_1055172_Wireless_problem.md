---
title: "Wireless problem"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by joker31174 on 2009-01-30
Hey guys,

I have an Acer Aspire 5515 laptop with an internal wireless card. (802.11abg)

When I boot up in Vista, I can connect to my network automatically.

When I boot up in Ubuntu, I can't access the wireless capabilities.

How do I connect to a wireless network?

---

### Post by utnubuuser on 2009-01-30
Have you tried going to:> System>>Administration>>Hardware Drivers and checking if there are proprieatary drivers, and if so, enabling them?

---

### Post by joker31174 on 2009-01-30
Did what you said, and it came up with this:

Component                                       Enabled   Status
Atheros Hardware Access Layer (HAL)            (enabled)  In use
Support for Atheros 802.11 wireless LAN cards  (enabled)  In use

I have already tried ndiswrapper and it didn't work.



???

---

### Post by undegaussable on 2009-01-30
I am having the exact same issue with the Acer Aspire 5515.  What's really puzzling is that Acer doesn't have this computer listed at all on their Support site!  I suspect that is because this is a brand-new model Acer just put out a couple weeks ago -- everything posted about the Aspire 5515 on the Internet is from the last 7-10 days.

Here's my output for various commands

lspci:
```
(...)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
lsusb:
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
ifconfig:
```
eth0      (ethernet...)

lo        (...)

```
iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

lsmod and dmesg both contain no information about wireless.  This is clearly a driver issue but I have no idea how to solve it.  Anyone got an idea?  I am going to open a bug for this.

---

### Post by Crafty Kisses on 2009-01-30
What are the results of this command?
```
lshw -C network
```

---

### Post by undegaussable on 2009-01-30
I am DELIGHTED to report a solution to this problem.

First I installed the backported ath5k drivers.  To do this, do the following (from [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014"))
> 1) System->admin->"Software Sources"
2) On "Updates" tab check "Unsupported updates (intrepid-backports)"
3) When prompted click "Reload" to update the indexes
4) System->admin->"Synaptic..."
5) Find and mark for installation "linux-backports-modules-intrepid"
6) Click "Apply"
7) optionally from Terminal type "modprobe -l | grep ath5k" and you should see the location of the driver displayed to confirm it is there.
At this point if you reboot, your wireless may work.  Mine didn't, so I had to open /etc/modprobe.d/madwifi and comment out the line "blacklist ath5k".

If this doesn't work for you, read the whole ath5k instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros").  But this worked for me. :D

---

