---
title: "Cannot share wlan internet through ethernet"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by Helios747 on 2012-03-22
Hello,

For hours I've been attempting to share my laptop's wireless internet connection to my desktop connected through ethernet.

I've tried several methods to no avail.

KDE's NetworkManager GUI

commandline fu with IPTables and ip_forwarding

firestarter's internet connection sharing wizard

All of these I've tried with opendns and standard DNS

wlan (laptop) = dhcp

ethernet (laptop) = 192.168.1.3

ethernet (desktop, win7) = 192.168.1.2

The computers can see each other, but the desktop can't route through the laptop or ping the outside world.

I'm running Oneric KDE on the laptop.


HELP!

---

### Post by Insomn1a on 2012-03-22
> **Helios747 said:**
> Hello,

For hours I've been attempting to share my laptop's wireless internet connection to my desktop connected through ethernet.

I've tried several methods to no avail.

KDE's NetworkManager GUI

commandline fu with IPTables and ip_forwarding

firestarter's internet connection sharing wizard

All of these I've tried with opendns and standard DNS

wlan (laptop) = dhcp

ethernet (laptop) = 192.168.1.3

ethernet (desktop, win7) = 192.168.1.2

The computers can see each other, but the desktop can't route through the laptop or ping the outside world.

I'm running Oneric KDE on the laptop.


HELP!

can you run ifconfig in terminal and show me the configuration of the NIC on the desktop?

---

### Post by SeijiSensei on 2012-03-22
Have you enabled IP forwarding in /etc/sysctl.conf?  Edit the file as root with sudo and set

```
net.ipv4.ip_forward=1
```

then reboot. Forwarding packets across interfaces is disabled by default in Ubuntu for security reasons.

---

### Post by Helios747 on 2012-03-22
I solved this by hosting SSH on the laptop, and connecting the Windows 7 desktop with a socksv5 tunnel.

Not the solution I originally intended, but I guess there's several ways to solve a problem. ;)

Marking as solved.

---

