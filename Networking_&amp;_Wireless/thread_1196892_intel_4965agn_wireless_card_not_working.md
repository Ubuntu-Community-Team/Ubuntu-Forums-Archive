---
title: "intel 4965agn wireless card not working"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by chacha_nehru on 2009-06-25
I've been trying to get my wireless card to work and have tried most of the solutions suggested in similar threads, but nothing seems to work. 
I have an HP dv6000 laptop, with the Intel PRO/Wireless 4965 AG or AGN. Iam running Hardy 8.04.

A few more details:

```
 lshw -C network


 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:74:7b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:bf:7f:8f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.4 latency=0 module=r8169 multicast=yes

``````
 
 iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```Any and all help appreciated...

---

### Post by Metaljaz on 2009-06-25
try installing linux-backports-modules-hardy package by typing the below in a terminal window. Then restart computer and see if its working.

sudo apt-get install linux-backports-modules-hardy

---

### Post by chacha_nehru on 2009-06-25
nope, its still not working...

---

### Post by Metaljaz on 2009-06-25
Looks like Ubuntu recognizes the card maybe a driver issue:

[http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

---

### Post by chacha_nehru on 2009-06-25
i followed the instructions there and installed the mac80211 subsystem . However, while installing the iwlwifi driver for the 4965agn card, several errors popped up while building the iwlwifi.ko module.. 
here are a few of the errors:

```
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8211: error: ‘IEEE80211_CHAN_W_IBSS’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8213: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8217: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8217: error: ‘IEEE80211_CHAN_W_ACTIVE_SCAN’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8220: error: ‘MODE_IEEE80211A’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8222: error: dereferencing pointer to incomplete type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8223: error: dereferencing pointer to incomplete type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8234: error: ‘struct ieee80211_channel’ has no member named ‘chan’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8235: error: ‘struct ieee80211_channel’ has no member named ‘power_level’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8237: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8239: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8241: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8245: error: ‘struct ieee80211_channel’ has no member named ‘flag’
/iwlwifi-1.2.25/compatible/iwl3945-base.c: At top level:
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8440: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8441: error: unknown field ‘open’ specified in initializer
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8442: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8445: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8446: error: unknown field ‘config_interface’ specified in initializer
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8446: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8447: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8450: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8453: error: unknown field ‘beacon_update’ specified in initializer
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8453: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8455: warning: initialization from incompatible pointer type
/iwlwifi-1.2.25/compatible/iwl3945-base.c: In function ‘iwl3945_pci_probe’:
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8511: error: ‘struct ieee80211_hw’ has no member named ‘max_rssi’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8512: error: ‘struct ieee80211_hw’ has no member named ‘max_noise’
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8516: error: ‘IEEE80211_HW_WEP_INCLUDE_IV’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8517: error: ‘IEEE80211_HW_HOST_GEN_BEACON_TEMPLATE’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8583: error: ‘IEEE80211_IF_TYPE_STA’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8628: error: ‘MODE_IEEE80211G’ undeclared (first use in this function)
/iwlwifi-1.2.25/compatible/iwl3945-base.c:8665: warning: too few arguments for format
make[3]: *** [/iwlwifi-1.2.25/compatible/iwl3945-base.o] Error 1
make[2]: *** [_module_/iwlwifi-1.2.25/compatible] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/tkudari/wireless-testing'
make: *** [modules] Error 2
root@tkudari-laptop:/iwlwifi-1.2.25# 

```:confused:

---

### Post by Metaljaz on 2009-06-25
Read these links for additional information (try reading them in the order they are in first): Hopefully the one that helps is here:

[http://www.linlap.com/wiki/configuring+the+iwl4965+driver+for+the+intel+4965agn+wireless+controller](http://www.linlap.com/wiki/configuring+the+iwl4965+driver+for+the+intel+4965agn+wireless+controller)

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

[http://ubuntuforums.org/showthread.php?t=396204](http://ubuntuforums.org/showthread.php?t=396204)

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by chacha_nehru on 2009-06-26
thank you for those links.. i'd visited these links before, all except the first one. But I noticed that most of the solutions that work on those threads are for older kernel versions. ( especially 7.04 ). Anyway, I read somewhere that the compile error I have been getting may be because an external build of the drivers is not allowed, since they have already been built into the kernel. 

Another thing I noticed after installing the mac80211 subsystem yesterday is that under:

System > Administration > Hardware Drivers, I can see that the 'Intel Wireless WiFi Link AGN Driver for Linux' is enabled and in use. Also ,running:

```

sudo modprobe iwl4965

```returns nothing.. so iam guessing that the drivers are up and running? 

But on running :
```

# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:74:7b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:bf:7f:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s

```so the wireless network is still disabled .. What's happening here??

---

### Post by chacha_nehru on 2009-06-26
Also, dmesg keeps saying:

```

[ 5672.029725] iwlagn 0000:02:00.0: Could not read microcode: -2
[ 5676.084634] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[ 5676.088527] iwlagn 0000:02:00.0: iwlwifi-4965-2.ucode firmware file req failed: -2

```

---

### Post by Metaljaz on 2009-06-26
I think its looking for the ucode file so make sure its in the right directory.  Put the uncompressed iwlwifi-4965-1.ucode file in /lib/firmware/

In your case i guess its the 4965-2.ucode file

---

### Post by chacha_nehru on 2009-06-26
Nope, i'd tried doing that beg=fore, it hadn't worked ... :(

---

### Post by chacha_nehru on 2009-06-26
Yes !, it worked.. !  this time is, I extracted the ucode file directly to the firmware directory and its not showing that in dmesg anymore ! can't understand why that would happen, though. 
now, lshw shows this :

```

tkudari@tkudari-laptop:~/Desktop$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:74:7b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:bf:7f:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s

```however, dmesg shows:
```

 ADDRCONF(NETDEV_UP): wlan0: link is not ready

```also, the wireless LED is not turning on..

---

