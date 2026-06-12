---
title: "wired/wireless connection problems"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by josemcruz on 2012-11-27
I'm running xubuntu 12.10 quetzal. My wired connection doesn't connect to the internet at all, and my wireless connection only connects after the computer boots up, but disconnects after a few minutes of use. The wireless repeats the same behavior after reboot with the wired connection still not working. This is actually a rather recent development, and I'm not sure what happened.

Here's the output from inputting ```
sudo lshw -C network
``` in terminal:

```
*-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 5c:ac:4c:b9:ba:dc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.5.0-18-generic firmware=N/A ip=10.251.214.43 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:f0904000-f0904fff memory:f0900000-f0903fff memory:f0920000-f093ffff
```

Any help would be much appreciated.

---

### Post by ahallubuntu on 2012-11-27
You have a Realtek wireless card.  The 8192 built-in driver in the kernel is known to have issues even in 12.10.  You can try building the latest driver from Realtek's website from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

There are several variations of the 8192.  Ubuntu used the rtl8192se driver for yours, so I'd probably look for that one on Realtek's website and build it.  It involves running some command line/terminal stuff, though.

Can's say about your wired card, except that it's a RTL8111/8168B card.  Google for info on that + Ubuntu.

---

### Post by NikTh on 2012-11-27
Hi , 

Please , open a terminal and try this command 

```
echo 'options rtl8192se swenc=1' | sudo tee /etc/modprobe.d/rtl8129.conf
``` 

Reboot the PC and see if wireless stability improved. 

Thanks

---

### Post by varunendra on 2012-11-29
For wireless connection, please follow what *NikTh* suggested above. If it doesn't seem to help, you may try what *ahallubuntu* suggested, but if you need to go that way, make sure you have "build-essential" and "linux-headers" installed to be able to build the driver -
```
apt-get install build-essential linux-headers-generic
```


As for the wired connection -
> **josemcruz said:**
> ```

  *-network **[COLOR="Red"]UNCLAIMED[/COLOR]**
       description: Ethernet controller
       product: **[COLOR="Red"]RTL8111/8168B[/COLOR]** PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
```
I am surprised to see that no driver loaded for that Ethernet adapter. Usually the default kernel driver r8169 is loaded for that chip, and works fine for most people. What happens if you try -
```
sudo modprobe -v r8169
```
Does it return any errors? Does the wired connection gets enabled?

If it doesn't help or returns any errors, please post -
```
locate r8169.ko
ls /lib/firmware/rtl_nic
dmesg | grep -ie r81 -e rtl81
```

.

---

