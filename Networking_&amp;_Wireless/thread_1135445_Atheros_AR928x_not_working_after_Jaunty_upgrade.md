---
title: "Atheros AR928x not working after Jaunty upgrade"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by zozoman on 2009-04-24
Hello everyone, I was hoping to solve my problem through searching, but every post I've read so far has not helped. Hopefully making my own thread will help.

This is what I got from lspci | grep Wireless

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network 

This is what I have from sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:52:b4:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:72:31:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.199 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:d5:20:f7:e6:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
alonzo@Lappy:/etc/lib/wireless/madwifi-0.9.4$ home lshw -C network
bash: home: command not found
alonzo@Lappy:/etc/lib/wireless/madwifi-0.9.4$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:52:b4:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:72:31:67
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.199 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:d5:20:f7:e6:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Before I did the upgrade to Jaunty yesterday everything was working fine. After the upgrade I can no longer find or connect to wireless networks. I have to use an ethernet cable to access the Internet.

I am relatively new to Ubuntu and Linux alike, but from what I know I do have madwifi tools installed. I have tried to install the latest madwifi from [www.madwifi-project.org](www.madwifi-project.org) but when I 'make' the files I end up getting the following error:

```
alonzo@Lappy:/etc/lib/wireless/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/etc/lib/wireless/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /etc/lib/wireless/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /etc/lib/wireless/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /etc/lib/wireless/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_power.o
/etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/etc/lib/wireless/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/etc/lib/wireless/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/etc/lib/wireless/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```
I am not sure if I even need this package from madwifi, but I figured it couldn't hurt. Since I get those errors I don't know if it would actually fix my problems.


Thanks in advance for any help that is given.

-Alonzo

---

### Post by zozoman on 2009-04-24
Bump.

***Edit***
I got it to work! After more searching I came across a post by Volanin and it worked like a charm!
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

Just untar the file. After you untar the file go to the directory you extracted it to and type "./FILENAME" and it will create a deb file for you. After it makes the deb file just run it and your wireless will automagicly work. Only if you are using an ath9k wireless card, obviously.

---

