---
title: "Lost network connections"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by labman365 on 2013-07-19
Hi All,
I'm running 10.04 32 bit. All of a sudden I have lost my network connections. When I open system>preferences>network connections the wired interfaces are gone. Any ideas much appreciated.

---

### Post by praseodym on 2013-07-19
Hi,
please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
route -n
cat /etc/resolv.conf
```

---

### Post by labman365 on 2013-07-19
root@ub-server:~# uname -a
Linux ub-server 2.6.32-49-generic-pae #111-Ubuntu SMP Thu Jun 20 21:44:04 UTC 2013 i686 GNU/Linux
root@ub-server:~# lspci -nnk | grep -iA2 net
3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
    Kernel driver in use: tg3
    Kernel modules: tg3
root@ub-server:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 17ef:602d Lenovo 
Bus 002 Device 008: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 007: ID 050d:3201 Belkin Components F1DF102U/F1DG102U Flip KVM
Bus 002 Device 002: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ub-server:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ub-server:~# rfkill list
root@ub-server:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
root@ub-server:~# cat /etc/resolv.conf

---

### Post by praseodym on 2013-07-19
BIOS reset to default settings?

---

### Post by labman365 on 2013-07-19
> **praseodym said:**
> BIOS reset to default settings?

Ok, done that now but still the same

---

### Post by praseodym on 2013-07-19
Shut off the router currentless for 10 minutes. After that remove any networking profile and reboot

---

### Post by labman365 on 2013-07-19
> **praseodym said:**
> Shut off the router currentless for 10 minutes. After that remove any networking profile and reboot

Ok, shut down router and remove network profile from, Router or Computer? Sorry, not quite sure about it.

---

### Post by praseodym on 2013-07-19
From the computer (NetworkManager?).

---

### Post by Iowan on 2013-07-19
Also check **sudo lshw -C network **and **ifconfig**
Is this a server or workstation?
Should it have a static or DHCP address?

---

### Post by labman365 on 2013-07-19
Ok, that's sorted it. A big, big thank you for taking the time to help. :D

---

