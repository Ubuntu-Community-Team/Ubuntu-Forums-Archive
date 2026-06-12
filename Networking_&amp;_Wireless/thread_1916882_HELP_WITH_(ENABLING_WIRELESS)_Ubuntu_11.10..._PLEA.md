---
title: "HELP WITH (ENABLING WIRELESS) Ubuntu 11.10... PLEASE !re"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by hanaii on 2012-01-28
I downloaded Ubuntu 11.10 recently to my (Lenovo B575) system. Am in love with this operating system it is so much faster and smoother than windows 7, the only thing that is bothering me is that I can't seem to enable my wireless connection, every time I do so it goes on for a couple of seconds and it switches back off again in no time. If I can't get this problem solved Ubuntu is pretty much useless to me. SO please I need your help from higher perspective.

here are some information I collected from the terminal:
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:73:79:f1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s


and: 
*-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: cc:af:78:83:20:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-15-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:e0100000-e010ffff

note: (When I switch back to windows 7 my wireless connection works just fine)

---

### Post by carl4926 on 2012-01-28
Post result of

```
lspci -nnk | grep -iA2 net
```

---

### Post by hanaii on 2012-01-28
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Lenovo Device [17aa:f101]
    Kernel driver in use: rt2800pci

---

### Post by carl4926 on 2012-01-28
I have this device on my netbook
It works out of the box, no tinkering needed. Your driver is in place too

Install rfkill, if it's not already installed.

Then post the result of

```
rfkill list all
```

---

### Post by hanaii on 2012-01-28
here are my results:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by carl4926 on 2012-01-29
Have a look here
[http://lkubuntu.wordpress.com/2011/09/07/how-to-fix-rfkill-issues/](http://lkubuntu.wordpress.com/2011/09/07/how-to-fix-rfkill-issues/)

Please note though. I actually recommend you shutdown rather than re boot. And typically I avoid booting to windows (which I don't use any way) because windows seems to be the root of the problem, exactly how I'm not sure.

In some cases you may have to work at this....

---

### Post by carl4926 on 2012-01-29
Also. Please note.
Machines with not proper physical switch for the wireless, but that rely on some Fn combo to toggle it On/OFF, are typically problematic.

---

### Post by hanaii on 2012-01-29
Hello Carl,
Thanks for you assistant first of all, however I still keep getting the same problem even though I tried following the exacts steps but after rebooting I still end up with the same error.
My question is, If I remove windows 7, and keep ubuntu as  my primary operating system, do you think this would solve the problem ?

---

### Post by carl4926 on 2012-01-29
> **hanaii said:**
> Hello Carl,
Thanks for you assistant first of all, however I still keep getting the same problem even though I tried following the exacts steps but after rebooting I still end up with the same error.
My question is, If I remove windows 7, and keep ubuntu as  my primary operating system, do you think this would solve the problem ?

If you boot the Ubuntu live CD
Does the wireless work there

I find wherever I have had locks. If I boot a live CD it will work. Because it should.

What kind of wireless switch is it?

---

