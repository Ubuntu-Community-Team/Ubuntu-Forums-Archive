---
title: "Iwp5300 master mode?"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by zdog291 on 2010-07-21
Hi I have a Fujitsu T5010 laptop running Ubuntu and I am trying to see if it is possible to enable master mode with built in Intel 5300 AGN wireless adapter.

I followed through the instructions on:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

```
sudo iwconfig wlan0 mode master

```

I get
```

Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.

```

but in the same article it says that it is possible to enable master mode with the iwlwifi drivers 

My Card
```
 
lspci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
18:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
38:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)

```


```

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:23:26:61:4b:a2
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-3 ip=128.236.131.163 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:f2700000-f271ffff memory:f2725000-f2725fff ioport:1840(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:55:4d:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f2500000-f2501fff

```

---

### Post by chili555 on 2010-07-21
> *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       product: PRO/Wireless 5300 AGNWhy is it disabled? Please let us see:```
rfkill list all
dmesg | grep iwlagn
```Thanks.

---

### Post by zdog291 on 2010-07-21
Here are the results of the code


```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
zachary@zachary-laptop:~$ dmesg | grep iwlagn
[   14.347971] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   14.347974] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   14.348030] iwlagn 0000:18:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.348038] iwlagn 0000:18:00.0: setting latency timer to 64
[   14.348071] iwlagn 0000:18:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   14.383217] iwlagn 0000:18:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.383767] iwlagn 0000:18:00.0: irq 30 for MSI/MSI-X

```

---

### Post by chili555 on 2010-07-22
> 0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]
That typically means the wireless switch on your laptop is switched to 'Off.' Can you please switch it on?

---

