---
title: "wireless fails obtaining ip/verifying access point"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by wallofsleep on 2011-07-26
Hi, I'm running Ubuntu 10.10. My wired connection is functional and other wireless connections in the house are operating. WEP is currently disabled.

I have tried using Wicd and Wifi Radar with similar outcomes. Wicd fails to obtain an ip and when a static ip is assigned, it fails to verify an access point. 

I am unable to get to network manager because the replacement screen I installed has removed a small amount from the right side. Also, somehow the nm icon was removed before the screen was replaced. My wireless connects to the previously set-up internet connection from my old house, but no new points.

I will need a walkthrough if using the terminal.

Thanks.

---

### Post by thefasterblueone on 2011-07-26
Right click the top panel and select 'add to panel' then choose 'Indicator Applet' then click 'Add'. Now you should have a network icon.

If you still need help with the other problems let us know.

---

### Post by doclawson on 2011-07-26
New to the forum and ubuntu.
Just installed Ubuntu 11.04 on my Dell Latitude D620 all seems fine except I am clueless as to how to setup my wireless. I have a Netgear WNR 1000 setup in home. Any help would be appreciated by this new novice.

---

### Post by garvinrick4 on 2011-07-26
> **doclawson said:**
> New to the forum and ubuntu.
Just installed Ubuntu 11.04 on my Dell Latitude D620 all seems fine except I am clueless as to how to setup my wireless. I have a Netgear WNR 1000 setup in home. Any help would be appreciated by this new novice.
Start your own Thread in same "Network and Wireless" and include the output of:
Open a terminal: ctrl/alt/t
```
sudo lshw -C network
```                      
```
 lspci -nnk | grep -iA2 network 
```

---

### Post by wallofsleep on 2011-07-26
> **thefasterblueone said:**
> If you still need help with the other problems let us know.
There is no network icon in my indicator applet. I haven't been able to find anything resembling nm in the add to panel menu.

```
sudo lshw -C network
```[SIZE=1]  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:02:25:7c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5751-v3.29a ip=192.168.0.199 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:55:2e:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfbff000-dfbfffff
[/SIZE]

```
 lspci -nnk | grep -iA2 network 
```[SIZE=1]03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200[/SIZE]

---

### Post by wallofsleep on 2011-07-27
still stuck

---

### Post by thefasterblueone on 2011-07-27
Try using only WICD. Network-Manager never seems to work right for me.
If you want to uninstall Network-Manager run this in Terminal.
Be sure you have WICD installed first.

```
sudo apt-get remove --purge network-manager
```

when setting up your wireless encryption don't use WPA/WPA2 together. Use one or the other for best results.

---

### Post by wallofsleep on 2011-07-27
NM uninstalled.

I don't believe we're using wpa/wpa2 together. I am attempting to connect to an unsecured wireless.

---

### Post by wallofsleep on 2011-07-27
Would it be easier if I was just instructed on connecting the wireless through the terminal?

---

### Post by thefasterblueone on 2011-07-27
No.
[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by wildmanne39 on 2011-07-27
Hi, please run these commands and post the results.
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep ipw
```
this is to make sure nothing else is going on since you last connected at your old house.

---

### Post by wallofsleep on 2011-07-28
Killing NM must have done the trick. After I restored all my defaults, I connected without an issue. Many thanks!

---

