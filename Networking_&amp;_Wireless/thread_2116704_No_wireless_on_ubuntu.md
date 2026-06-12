---
title: "No wireless on ubuntu"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by Farxodor on 2013-02-16
Hi, I recently Installed Ubuntu on my HP Pavilion dv6 laptop. The laptop has a wi-fi on/off switch on the keyboard (as an alternate function for the f12 key), which starts off and will not turn on while I am running Ubuntu.  I don't have a wired connection, and my only access to the internet is through windows 7 on the same laptop, which works fine.

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by Farxodor on 2013-02-16
Here you are:

sudo lshw -C network:
```
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:ae:91:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-29-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:d4500000-d4501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: a0:b3:cc:45:55:85
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff


```iwconfig: 
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


```

---

### Post by Farxodor on 2013-02-17
Anyone?

---

### Post by ZippyUbu on 2013-02-17
> 0: phy0: Wireless LAN     Soft blocked: no     [COLOR=Red]Hard blocked: yes[/COLOR]
Try: ```
sudo rfkill unblock all
```I've seen a few issues like this, try resetting your BIOS. After resetting, log back into Ubuntu and try:

```
sudo rfkill list
``` see if any of the Wireless LAN options are blocked. 

Post your findings..

--
Zu

---

### Post by Farxodor on 2013-02-17
> **ZippyUbu said:**
> Try: ```
sudo rfkill unblock all
```
This seemed to be all that's required, as I'm now posting this from Ubuntu. Thanks.

---

### Post by ZippyUbu on 2013-02-17
Great, help others; don't forget to mark as solved ;-)

---

