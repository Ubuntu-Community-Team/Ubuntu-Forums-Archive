---
title: "Wireless Connection Issue UA600ex Realtek RTL8188SU"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by Wolfx128 on 2012-02-02
Hello, 
The issue I am having is trying to gain access to the network which my wireless adapter is able to see. I am currently using a Realtek Amped Wireless UA600ex wireless USB adapter and I can view all the networks which I am able to normally view on my windows partition though I am not able to connect properly to them, even if they are unprotected networks.

Other cards such as the LinksysWUSB600N work natively and connect just fine and have left me at a loss on what possible could be going wrong. I would tend to believe something is wrong with the drivers, though I am not sure at this point. Thank you very much for your assistance.

lspci & lsusb
```

$ lspci | grep 'Realtek'
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

$lsubs | grep 'Realtek'
Bus 002 Device 008: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

```ifconfg & iwconfig
```

$ ifconfg wlan0
wlan0     Link encap:Ethernet  HWaddr f8:78:8c:00:85:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig wlan0
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```lsmod
```

$ lsmod | grep 'rt'
parport_pc             36962  0 
rt2800usb              22590  0 
rt2800lib              54538  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20830  1 rt2800usb
rt2x00lib              50365  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              462092  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              199630  2 rt2x00lib,mac80211
parport                46562  3 parport_pc,ppdev,lp

```lshw -C network
```

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:2c:5f:56
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:d800(size=256) memory:fbeff000-fbefffff memory:cfff0000-cfffffff memory:fbec0000-fbedffff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlan0
       serial: f8:78:8c:00:85:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@2:3
       logical name: wlan1
       serial: 00:1e:e5:e1:46:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-15-generic firmware=0.29 ip=192.168.1.112 link=yes multicast=yes wireless=IEEE 802.11abgn

```iwscan (modded for desired network)
```

wlan0     Scan completed :
          Cell 02 - Address: 00:23:69:EA:D9:2E
                    ESSID:"AG"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A00011010440001021041000100103B000103104700102369EAD92C002369EAD92C069C2034001021001C4C696E6B7379732C2041204469766973696F6E206F6620436973636F102300075752543631304E1024000876312E30302E30331042000234321054000800060050F2040001101100075752543631304E100800020084103C000103
                    Signal level=72/100  

```lsb_release
```

Description:    Ubuntu 11.10

```uname -mr
```

3.0.0-15-generic x86_64

```

---

### Post by Wolfx128 on 2012-02-02
Ok... Just to keep information rolling into this to hopefully narrow down the problem.
I have installed new firmware as directed by this guide to try and add missing pieces.

 Guide:
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

I am also working on creating the driver provided by the distributer, but am running into the following error on compilation, I am using 'build-essentials' to compile

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.0.0-15-generic/build M=/RTL8188_USB/driver/rtl8188usb_driver  modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-15-generic'
  CC [M]  /RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.o
In file included from /RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.c:23:0:
/RTL8188_USB/driver/rtl8188usb_driver/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/RTL8188_USB/driver/rtl8188usb_driver/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
In file included from /RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_ht.h:25:0,
                 from /RTL8188_USB/driver/rtl8188usb_driver/include/drv_types.h:67,
                 from /RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.c:24:
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h: In function &#8216;get_da&#8217;:
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:350:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:350:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:353:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:353:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:356:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:356:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:359:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:359:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h: In function &#8216;get_sa&#8217;:
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:374:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:374:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:377:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:377:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:380:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:380:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:383:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:383:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:397:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:397:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:400:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:400:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:403:9: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/wifi.h:403:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /RTL8188_USB/driver/rtl8188usb_driver/include/drv_types.h:73:0,
                 from /RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.c:24:
/RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_recv.h:434:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_recv.h:434:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
In file included from /RTL8188_USB/driver/rtl8188usb_driver/include/drv_types.h:77:0,
                 from /RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.c:24:
/RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_io.h: At top level:
/RTL8188_USB/driver/rtl8188usb_driver/include/rtl871x_io.h:35:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/RTL8188_USB/driver/rtl8188usb_driver/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/RTL8188_USB/driver/rtl8188usb_driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
make: *** [modules] Error 2

```

Though I do code, I am not excellent at C or C++ and am not sure how to approach this problem presented

---

