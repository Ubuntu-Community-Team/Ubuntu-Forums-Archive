---
title: "Network doesn't work on every boot"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by NilPointer on 2013-01-18
Recently, I started to get problems with network. It gets fixed by reboot, but there must be a better solution.

I noticed, that when network doesn't work, interfaces are named eth0 and eth1_rename. After reboot, they're eth0 and eth1, and following messages show up in logs:

```
Jan 18 13:13:45 localhost kernel: [    9.980921] udev: renamed network interface eth0 to eth1
Jan 18 13:13:45 localhost kernel: [   10.025451] udev: renamed network interface eth1_rename to eth0

```

Also, that probably started around time, when I've removed wlan0 board. How can it be fixed?

---

### Post by c2tarun on 2013-01-18
> **NilPointer said:**
> Recently, I started to get problems with network. It gets fixed by reboot, but there must be a better solution.

I noticed, that when network doesn't work, interfaces are named eth0 and eth1_rename. After reboot, they're eth0 and eth1, and following messages show up in logs:

```
Jan 18 13:13:45 localhost kernel: [    9.980921] udev: renamed network interface eth0 to eth1
Jan 18 13:13:45 localhost kernel: [   10.025451] udev: renamed network interface eth1_rename to eth0

```

Also, that probably started around time, when I've removed wlan0 board. How can it be fixed?


I was also facing this problem in 10.04 and 10.10. But since I upgraded to 11.04 problem is fixed. Right now I am using 12.04 and I didn't face this problem. I think you should try upgrading to 12.04, it is also LTS.

---

### Post by imadovitsky on 2013-01-18
What's ur /etc/network/interfaces entrys ?

---

### Post by Cheesehead on 2013-01-18
> **c2tarun said:**
> Right now I am using 12.04 and I didn't face this problem. I think you should try upgrading to 12.04, it is also LTS.

There is no need to upgrade.

This kind of behavior is expected if you rely upon specific interface names
(for example, in /etc/network/interfaces) and change hardware (like a NIC) without updating your udev rules (/etc/udev/rules.d/*-persistent-net-rules) with the new MAC address.

Reinstalling (or the suggested upgrade) simply wipes the old udev rule with the old MAC address. It does work, but it's overkill for the rather simple fixes of either cleaning uneccessary lines from the interfaces file or deleting the old udev rule.

For example, here is my udev rule for laptop wireless. See the MAC address? And the assignment to wlan0? 
```
$ cat /etc/udev/rules.d/70-persistent-net.rules | grep wlan

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="03:24:2d:7c:2b:7a", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

TIP: use sudo or gksudo when editing this root-level file. And *always* make a backup of the file first.



imadovitsky is on the right track, asking first about the interfaces file.

---

### Post by NilPointer on 2013-01-18
Thanks for your replies!

Well, here are persistent net rules.

```
# PCI device 0x1106:0x3106 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:01:a2:ce:8d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:66:4e:64:b6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:0x8185 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:d1:50:ef:6b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0b05:0x1786 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:46:5d:ad:6b:cf", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
```

Third one is for removed wlan0 PCI card and fourth is for USB Wi-Fi dongle. Both are no longer needed. eth0 is installed, but unused (PCI Card). eth1 is integrated into MB and is only used NIC on system.

---

### Post by dpurgert on 2013-01-18
so, comment out 1, 3, and 4 and you should be good to go ...

---

### Post by NilPointer on 2013-01-19
Yes, I tried that, but problem is not yet solved. After commenting out 1, 3 and 4, first one ressurected as 5th entry and problem was still here. I eventually removed 3 and 4 completely (since I have no plans to use those NICs in future) and extracted eth0 card from PC. After that, it stopped to ressurect, but commenting out it's entry makes network not fixable even by reboot. Here is /etc/network/interfaces

```
auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables.rules
```

If I remember correctly, it was always that way and network was configured via Network Manager.

---

### Post by NilPointer on 2013-01-19
Hmm... Strange. 3rd reboot and network still works... It would seem that problem is solved!

Apparently, I fixed it somehow via trial-and-error editing of persistent net rules. Now file looks that way:

```
# PCI device 0x1106:0x3106 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:01:a2:ce:8d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:66:4e:64:b6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

---

