---
title: "Wireless problem compaq laptop"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by tchambers14 on 2009-04-08
I have just installed ubuntu on an old laptop and everything is working well with the exception of the wireless connection. 

Ubuntu recognises the card and i have installed the broadcom b43 driver however the computer will not pick up any networks the output from  ```
lshw -C network
``` looks like this: -
```

 *-network:0             [D^[[D^[[D^[[D^[[A^[[B
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:7e:c3:fc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=129.67.161.83 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:a9:99:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:ca:b7:93:6c:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Can anyone help me?

Tom

---

### Post by pytheas22 on 2009-04-08
You need to install firmware before the b43 driver will fully work.  A box should have popped up informing you of this when you first logged into the desktop, but I guess not.  Unfortunately Ubuntu can't include the firmware by default because of potential legal issues with Broadcom.

To install the firmware, simply run these commands (provided you are connected to the Internet via ethernet):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

Then reboot and wireless should work.

If you have no way of plugging your computer into the Internet temporarily, let me know and I'll give instructions for an offline installation of the firmware.

---

### Post by tchambers14 on 2009-04-08
Thank you for your response however it does not seem to have worked, I know that I am in range of a wireless network yet when I click on the network manager icon on the taskbar it does not show any wireless networks, only the wired one. 

Is there anything else you could suggest i try?

Thanks again, 

Tom

---

### Post by lisati on 2009-04-08
Does your laptop have a switch to turn wireless on/off? My two laptops (both Toshiba) have one.

---

### Post by tchambers14 on 2009-04-08
Thank you so much, my laptop has a wireless button rather then a switch. When the laptop was running with windows this button would light up if the wireless was 'on'. It seems that with ubuntu the light is always on which caused some confusion!

Appreciate your help,

Tom

---

