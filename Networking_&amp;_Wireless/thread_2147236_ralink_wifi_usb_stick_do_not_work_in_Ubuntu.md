---
title: "ralink wifi usb stick do not work in Ubuntu"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by zhengtao on 2013-05-21
ralink wifi usb stick do not work in Ubuntu.

zhengtao@zhengtao-Y450:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: ideapad_wlan: Wireless LAN
Soft blocked: yes
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
3: phy1: Wireless LAN
Soft blocked: yes
Hard blocked: yes

---

### Post by Bucky Ball on 2013-05-21
Welcome to the forums. Plug it in and do an update. Check 'Additional Drivers'. Open a terminal and paste this in:

```
sudo lshw -C network
```

Hit return and post the result back here, please.

---

### Post by zhengtao on 2013-05-21
i only have a wireless connection and now it can not be used in Ubuntu, so i can't run update or check 'Additional Drivers'. But i have run the code.

*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:e0:1d:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-23-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f4100000-f4101fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:9e:61:44:76
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:50 memory:f4000000-f400ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlan1
       serial: 00:0f:13:42:12:64
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
zhengtao@zhengtao-Y450:~$

---

### Post by Bucky Ball on 2013-05-21
Not sure why you're using the USB when you have an Intel wireless card in the box that should work without doing anything. 

As for the Ralink situation; you may have the wrong driver installed (driver=rt2800usb) and may be missing firmware but might not need it (firmware=N/A). The Intel card:

```
configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-23-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
```

The Ralink card:

```
configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```

The cards appear to be up and running but not connected to any network. Maybe you need to switch on off as they both appear operational. When you say 'Can't connect' can you be more specific? Run us through exactly what is happening. What happens when you click the network icon? Do you see networks?

---

### Post by chili555 on 2013-05-21
@zhengtao--

I am here as you requested but my friend Bucky Ball is doing a great job, so I'll stand by while he fixes you up. He will also want to see:```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by zhengtao on 2013-05-21
my intel wireless card could not work neither in windows nor in Ubuntu one months ago, so i bought a ralink wifi usb stick.

i can only use a wireless internet connection, so i could not connect to internet as the wifi usb stick could not work in Ubuntu. When i click on the network icon, i can see two cards, but both of them are displayed "is diabled by hardware switch". but the wifi usb stick do not have a hardware switch obviously.

---

### Post by zhengtao on 2013-05-21
i have add a "blacklist ipw2200" to /etc/modprobe.d/blacklist.conf as you instructed in one former threads, but it did not work.

---

### Post by Bucky Ball on 2013-05-21
Fire away, chili. My knowledge of these things is miniscule in comparison. ;)

---

### Post by chili555 on 2013-05-21
> **zhengtao said:**
> i have add a "blacklist ipw2200" to /etc/modprobe.d/blacklist.conf as you instructed in one former threads, but it did not work.That's because the wireless driver for your card is iwlwifi, not ipw2200. Please change it, reboot and show us:```
rfkill list all
```I am starting to think the reason your wireless card won't work is that the wireless switch is defective and not the card.

What is the make and model of laptop?

@Bucky Ball--

Mrs. Chili and I are leaving in a few minutes so jump in as you can.

---

### Post by Bucky Ball on 2013-05-21
> **chili555 said:**
> 

@Bucky Ball--

Mrs. Chili and I are leaving in a few minutes so jump in as you can.

Will do. ;)

---

### Post by zhengtao on 2013-05-21
after changing "ipw2200" to "iwlwifi" and reboot, it worked!!!
now i am using ubuntu.
thanks sooooo much!!!
@chili555 @Bucky Ball

---

### Post by Bucky Ball on 2013-05-21
Great news! Please check the link in my signature to mark the thread as 'SOLVED' to help others. 

Enjoy the ride. ;)

---

### Post by chili555 on 2013-05-21
Awesome! Glad it's working. Have fun!

---

