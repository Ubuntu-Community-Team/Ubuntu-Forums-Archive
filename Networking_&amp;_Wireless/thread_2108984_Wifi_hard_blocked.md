---
title: "Wifi hard blocked"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by spencer1501 on 2013-01-26
Hi, i'm new to ubuntu and can't get the network running as it appears to be hardware blocked. could some please give me some assistance in getting this running. The wired LAN works fine. Thanks

---

### Post by mörgæs on 2013-01-26
Hi, welcome to the fora.

Please run the command 

```
sudo lshw -c network
```and post the result in CODE tags.

---

### Post by bkratz on 2013-01-26
Another good one to see would be 


rfkill list all

---

### Post by spencer1501 on 2013-01-26
Hi, thanks for the fast response. The results are as follows

```
   *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:0f:e9:db
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.107 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0f2c000-f0f2cfff memory:f0f18000-f0f1bfff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:25:2c:17:90:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-36-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f0100000-f0103fff

```and from rfkill list all

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```Regards Spencer

---

### Post by prodigy_ on 2013-01-26
"Hard blocked: yes" generally means your WiFi is disabled by a hardware switch or in BIOS. On my particular laptop (HP 6510b) I had to reset BIOS settings to default.

---

### Post by Hadaka on 2013-01-26
Hi, Dell "usually" is able to toggle the wireless on/off
with the Fn/F2 key combination...so   press the Fn key and
the F2 together ONE time ,,,then

```
rfkil list all
```

see if that clears some of your hard blocks.

---

### Post by spencer1501 on 2013-01-27
Hi Guys,

I tried both of these options and the bios reset seems to have done the job. Stranage as all the bios settings looked fine. Thanks so much for your help.

Regards

Spencer

---

### Post by mörgæs on 2013-01-27
Good, then please mark the thread 'solved'.

---

