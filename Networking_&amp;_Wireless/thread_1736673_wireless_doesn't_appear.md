---
title: "wireless doesn't appear"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by Lovek on 2011-04-22
on start up yesterday suddenly the wireless option is not appearing together with the wired connection option as it used to do..

been using the netbook remix now for quite awhile - working fine - until a few days ago when not beeing able to log in anymore. after browsing around I finally solved it by getting rid of  gconfd/  (command: rm -rf .gconfd/ ) 
I got the message "Install problem! configuration defaults for GNOME power manager not correctly installed" - which apparently was not the real problem  and  was as I said solved by the above mentioned removal. 
 
could this have something to do with it? 

what should I look for? 
could I be missing drivers for the wifi? could they have disappeared together with the gconfd/ ??


would be very greatful for some tips here.. 

all the best, LoveK

---

### Post by josephmills on 2011-04-22
> **Lovek said:**
> on start up yesterday suddenly the wireless option is not appearing together with the wired connection option as it used to do..

been using the netbook remix now for quite awhile - working fine - until a few days ago when not beeing able to log in anymore. after browsing around I finally solved it by getting rid of  gconfd/  (command: rm -rf .gconfd/ ) 
I got the message "Install problem! configuration defaults for GNOME power manager not correctly installed" - which apparently was not the real problem  and  was as I said solved by the above mentioned removal. 
 
could this have something to do with it? 

what should I look for? 
could I be missing drivers for the wifi? could they have disappeared together with the gconfd/ ??


would be very greatful for some tips here.. 

all the best, LoveK
hi there could we please see a ```
rfkill list all 
```
and a ```
lshw -C network 
```  thanks

---

### Post by Lovek on 2011-04-23
> **josephmills said:**
> hi there could we please see a ```
rfkill list all 
```and a ```
lshw -C network 
```  thanks


yes sure, 
first: 
0: eeepc-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

second: 
WARNING: you should run this program as super-user.
^CI (sysfs)

---

### Post by josephmills on 2011-04-23
try ```
rfkill unblock all 
``` but do NOT reboot yet tell us what happens

---

### Post by Lovek on 2011-04-23
> **josephmills said:**
> try ```
rfkill unblock all 
``` but do NOT reboot yet tell us what happens


wow, dude that was fast. 

I got no answer in terminal but two sec later I was connected to my wifi.. :)

 thanks a mile!

L

---

### Post by josephmills on 2011-04-23
ok lets see you wireless card please post to us 
```

sudo lshw -C network

```
it takes a little while to load

---

### Post by Lovek on 2011-04-23
> **josephmills said:**
> ok lets see you wireless card please post to us 
```

sudo lshw -C network

```it takes a little while to load


answer to that:  PCI (sysfs)

---

### Post by josephmills on 2011-04-23
> **Lovek said:**
> answer to that:  PCI (sysfs)

you have to let it load or try 
```

lspci

```

---

### Post by Lovek on 2011-04-23
> **josephmills said:**
> you have to let it load or try 
```

lspci

```

ah sorry..  here it is:
*-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:22:15:88:40:30
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:ca:10:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic-pae firmware=N/A ip=192.168.0.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8000000-f800ffff


and:
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)


..but what exactly are we looking for here?

---

### Post by josephmills on 2011-04-23
all right lets see a 
```

lsmod | grep ath5k
```
```

and a [code]dmesg | grep ath5k
``` thanks

---

### Post by Lovek on 2011-04-23
> **josephmills said:**
> all right lets see a 
```

lsmod | grep ath5k
``````

and a [code]dmesg | grep ath5k
``` thanks

lsmod | grep ath5k
ath5k                 130403  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  2 ath5k,eeepc_laptop

and: 
dmesg | grep ath5k
[  335.482863] ath5k 0000:01:00.0: enabling device (0000 -> 0002)
[  335.482882] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  335.482902] ath5k 0000:01:00.0: setting latency timer to 64
[  335.482982] ath5k 0000:01:00.0: registered as 'phy0'
[  336.007123] Registered led device: ath5k-phy0::rx
[  336.007245] Registered led device: ath5k-phy0::tx
[  336.007253] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

---

### Post by josephmills on 2011-04-23
please do a 
```

sudo apt-get update 

```
then 
```

sudo apt-get upgrade

```
thanks that should send you on your way

---

### Post by Lovek on 2011-04-24
> **josephmills said:**
> please do a 
```

sudo apt-get update 

```then 
```

sudo apt-get upgrade

```thanks that should send you on your way


ok thanks, 

I fell asleep last night..  did the update/udgrade now . and everything seems to be working well.

---

