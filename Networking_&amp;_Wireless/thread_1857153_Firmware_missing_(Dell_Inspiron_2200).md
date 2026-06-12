---
title: "Firmware missing (Dell Inspiron 2200)"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by walcott.erci on 2011-10-09
I just installed Ubuntu 11.04 on my old Inspiron 2200, and it won't connect to wireless internet.  It says "device not ready (firmware missing)"

I ran the command lspci -vvnn | grep 14e4 for details on my device and it showed 

Network Controlloer [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 8.02.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)


PLEASE HELP ME!

---

### Post by praseodym on 2011-10-09
Hi,

install the firmware via cable connection:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by walcott.erci on 2011-10-09
> **praseodym said:**
> Hi,

install the firmware via cable connection:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

That worked great.  The device is working, however I still can't find any networks, even though on my other computer I'm connected wirelessly.  Idea?

---

### Post by praseodym on 2011-10-10
Check your router settings (firmware up-to-date? MAC-Filter off).

Post the following:

```
dmesg | grep b43
iwconfig
rfkill list
sudo iwlist scan
lsmod
```

---

### Post by angelsoto on 2013-01-09
thanks a lot praseodym!

where did you get the firmware command from?

---

### Post by praseodym on 2013-01-09
"apt-get" is the terminal command for the software-center or the synaptic package manager.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

