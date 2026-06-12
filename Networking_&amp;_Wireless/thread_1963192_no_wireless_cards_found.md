---
title: "no wireless cards found?"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by ammon on 2012-04-22
iwconfig: lo and eth0 no wireless extensions(no wlan0 listed);

ndiswrapper -l return nothing;

dmesg | grep -e ndis -e wlan return only:

[14.093520] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[14.472949] usbcore: registered new interface driver ndiswrapper

but no any wlan(or other wireless cards) listed.

What meant by these messages?What should I do to fix it.Thanks a lot.

---

### Post by sanderj on 2012-04-22
What's the output of 

```
lspci | grep -i -e network -e wireless -e ether
lsusb
```

More specifically: is your wireless hardware seen?


Here's mine:

```
sander@R540:~$ lspci | grep -i -e network -e wireless -e ether
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
sander@R540:~$ 
```

---

### Post by ammon on 2012-04-22
Thank you Sander,

lspci | grep -i -e network -e wireless -e ether got:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

and lsusb:
Bus 002 Device 003: ID 17ef:4810 Lenovo Integrated Webcam [R5U877]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 17ef:6016 Lenovo 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I lost the wireless connection after a update for Ubuntu10.10.

---

### Post by ammon on 2012-04-22
ndiswrapper said:hardware exist:No

and I have a additional driver:Realtek RTL819 WiFi card(Already activated but not in using).

---

### Post by sanderj on 2012-04-22
So "Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)" is your wifi card. Good.

Oh, you have a second Wifi card? I would say that does not make it easier.

Anyway: can you try to live-boot from a Ubuntu 11.10 or 12.04 (=beta) CD/USB-stick, and see if it works? Maybe you need a wired connection temporarily to install a proprietary driver.

I would say (hope?) you don't need ndiswrapper: in my experience Realtek has native linux drivers.

---

