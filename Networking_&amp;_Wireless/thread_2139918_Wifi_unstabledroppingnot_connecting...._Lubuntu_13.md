---
title: "Wifi unstable/dropping/not connecting.... Lubuntu 13.04?"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2013-04-28
I know there have been several posts on wifi problems, but just wanted to say that my workaround for my ASUS X401A is to change the security mode on the router.

I've had similar problems (years ago) when wifi dongles would work with WEP but apparently not with WPA.
Now I'm certainly not suggesting you run unprotected or run with WEP (which is not very secure) but its a useful area to explore.

It seems with my ASUS I get a stable connection with the wifi router set to WPA only, but not with WPA2 or with WPA+WPA2. 

I notice another thread indicates changing the b,g,n mode fixes their problem. This may be a related solution, but my router does not directly support this option.

---

### Post by praseodym on 2013-04-28
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
```

---

### Post by SteveDee on 2013-04-30
> **praseodym said:**
> Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
```

Many thanks for taking an interest in this problem.

```

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Foxconn International, Inc. Device [105b:e054]
	Kernel driver in use: rt2800pci
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
	Subsystem: ASUSTeK Computer Inc. Device [1043:14f7]
	Kernel driver in use: r8169

```

...others in attached files:-

---

### Post by praseodym on 2013-05-01
Change to WPA2 only and deactivate the PM:
```

sudo iwconfig wlan0 power off
```

---

### Post by SteveDee on 2013-05-01
> **praseodym said:**
> Change to WPA2 only and deactivate the PM...


Many thanks, I will test for a few days with WPA2 only and Power Management turned off.

Why do you think this will work?

---

### Post by praseodym on 2013-05-01
WPA2 is more stable with the network-manager. The PM decreases the power of the wireless card if the battery goes less charged.

---

