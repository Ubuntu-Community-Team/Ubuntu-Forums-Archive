---
title: "wifi hotspot/accesspoint setup : driver problem : help"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by xachu4u on 2012-11-07
aim:
 to setup a wifi accesspoint for my wifi enabled android device to connect to.

Tried:
Tried a lot....i read about hostapd being able to setup wifi AP, but i couldn't get it to work. I found the problem was with my driver.

Please check this out:

**lemontree@lemontree-Inspiron-N5010:~$** lspci -k | grep -A 3 'Network'
12:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

**lemontree@lemontree-Inspiron-N5010:~$ **iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off[B]        

root@lemontree-Inspiron-N5010:/home/lemontree# [/B]iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

**lemontree@lemontree-Inspiron-N5010:~$** iw list
*
*
*
    Supported interface modes:
         * IBSS
         * managed
         * monitor
*
*
*
_[see no master mode.....:(]_


**root@lemontree-Inspiron-N5010:/home/lemontree#** rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
**root@lemontree-Inspiron-N5010:/home/lemontree# **lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:5d:c1:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:fbd00000-fbd01fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: 78:2b:cb:f4:91:b4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:d000(size=256) memory:d0c10000-d0c10fff memory:d0c00000-d0c0ffff memory:fb300000-fb31ffff


................................................................................................................................................................
so..the problem as i found on many sites is that intel driver(iwlwifi or iwlagn) doesnt support AP..:(
[B]
root@lemontree-Inspiron-N5010:/home/lemontree# [/B]modinfo iwlagn |grep depends
depends:        mac80211,cfg80211


I still have some hope, becoz iwlagn depends on mac80211..and hostapd is said to run on such systems.

So my this is my query:

Is there some way to setup a wifi hotspot (not ad-hoc) using my Intel Corporation Centrino Wireless-N 1000 adapter.....?

Can i replace iwlagn with some other driver that supports AP mode..if so, how?

Note:
I m using a fresh installation of ubuntu 11.10 and haven't run apt-get upgrade yet(slow connection). I tried connectify and mhotspot in windows 7 for this, and it works. But i want a solution in linux. Should i try another distro? Should i buy an external wifi adapter....:(?:confused:

---

### Post by chili555 on 2012-11-07
> Is there some way to setup a wifi hotspot (not ad-hoc) using my Intel Corporation Centrino Wireless-N 1000 adapter.....?
No.> Can i replace iwlagn with some other driver that supports AP mode..if so, how?None that I know of.> Should i buy an external wifi adapter..Yes. Google its chipset and 'master' carefully before you buy it. And, before you ask, no I don't know of one.

---

