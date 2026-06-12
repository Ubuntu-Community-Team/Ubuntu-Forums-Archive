---
title: "need help with mac80211 and rtl8185"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by pozer69 on 2009-01-10
joseph@ubuntu-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
joseph@ubuntu-laptop:~$ sudo lshw -C network
[sudo] password for joseph: 
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:f4:92:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:a6:98:69:93:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
joseph@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:48:f9:7c  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe48:f97c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165131819 (165.1 MB)  TX bytes:5699097 (5.6 MB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3680 (3.6 KB)  TX bytes:3680 (3.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f4:92:c7  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:c0:a8:f4:92:c7  
          inet addr:169.254.11.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-F4-92-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joseph@ubuntu-laptop:~$

---

### Post by pozer69 on 2009-01-10
root@ubuntu-laptop:~/rtl-mac80211-20070729# make && make install
make -C /lib/modules/2.6.27-9-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/joseph/rtl-mac80211-20070729/rtl8187_dev.o
In file included from /home/joseph/rtl-mac80211-20070729/rtl8187.h:18,
                 from /home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:25:
/home/joseph/rtl-mac80211-20070729/rtl818x.h:157: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:158: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:159: error: ‘IEEE80211_RATE_CCK’ undeclared here (not in a function)
/home/joseph/rtl-mac80211-20070729/rtl818x.h:160: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:161: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:163: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:164: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:166: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:167: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:169: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:170: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:171: error: ‘IEEE80211_RATE_OFDM’ undeclared here (not in a function)
/home/joseph/rtl-mac80211-20070729/rtl818x.h:172: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:173: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:175: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:176: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:178: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:179: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:181: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:182: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:184: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:185: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:187: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:188: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:190: error: unknown field ‘rate’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:191: error: unknown field ‘val’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:196: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:197: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:198: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:199: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:200: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:201: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:202: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:203: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:204: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:205: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:206: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:207: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:208: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:209: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:210: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:211: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:212: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:213: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:214: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:215: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:216: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:217: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:218: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:219: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:220: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:221: error: unknown field ‘freq’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:222: error: unknown field ‘chan’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl818x.h:223: error: unknown field ‘freq’ specified in initializer
In file included from /home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:25:
/home/joseph/rtl-mac80211-20070729/rtl8187.h:74: error: array type has incomplete element type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_tx_cb’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: error: variable ‘status’ has initializer but incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: error: extra brace group at end of initializer
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: error: (near initialization for ‘status’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: warning: excess elements in struct initializer
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: warning: (near initialization for ‘status’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: error: storage size of ‘status’ isn’t known
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: error: request for member ‘control’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: error: request for member ‘control’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: error: request for member ‘control’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: warning: passing argument 3 of ‘__constant_memcpy’ makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: error: request for member ‘control’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: error: request for member ‘control’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:67: warning: passing argument 3 of ‘__memcpy’ makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:70: error: request for member ‘flags’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:70: error: ‘IEEE80211_TX_STATUS_ACK’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:70: error: (Each undeclared identifier is reported only once
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:70: error: for each function it appears in.)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:70: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:71: error: too many arguments to function ‘ieee80211_tx_status_irqsafe’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:61: warning: unused variable ‘status’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_tx’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:92: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:92: error: request for member ‘rts_cts_rate’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:92: error: invalid operands to binary << (have ‘const struct ieee80211_rate *’ and ‘int’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:92: error: invalid operands to binary | (have ‘u32’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:92: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:93: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:93: error: request for member ‘tx_rate’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:93: error: invalid operands to binary << (have ‘const struct ieee80211_rate *’ and ‘int’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:93: error: invalid operands to binary | (have ‘u32’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:93: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:94: error: implicit declaration of function ‘ieee80211_get_morefrag’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:96: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:96: error: request for member ‘flags’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:96: error: ‘IEEE80211_TXCTL_USE_RTS_CTS’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:96: error: invalid operands to binary & (have ‘const struct ieee80211_rate *’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:99: warning: passing argument 2 of ‘ieee80211_rts_duration’ makes pointer from integer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:99: warning: passing argument 3 of ‘ieee80211_rts_duration’ makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:99: error: too few arguments to function ‘ieee80211_rts_duration’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:99: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:101: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:101: error: request for member ‘flags’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:101: error: ‘IEEE80211_TXCTL_USE_CTS_PROTECT’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:101: error: invalid operands to binary & (have ‘const struct ieee80211_rate *’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:105: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:105: error: request for member ‘retry_limit’ in something not a structure or union
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:105: error: invalid operands to binary << (have ‘const struct ieee80211_rate *’ and ‘int’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:105: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:109: error: dereferencing pointer to incomplete type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:109: warning: passing argument 2 of ‘kmemdup’ makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_rx_cb’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:166: error: ‘struct ieee80211_rx_status’ has no member named ‘ssi’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:166: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:167: error: ‘struct ieee80211_rx_status’ has no member named ‘rate’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:167: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:168: error: ‘struct ieee80211_conf’ has no member named ‘freq’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:168: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:169: error: ‘struct ieee80211_rx_status’ has no member named ‘channel’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:169: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:170: error: ‘struct ieee80211_rx_status’ has no member named ‘phymode’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:170: error: ‘struct ieee80211_conf’ has no member named ‘phymode’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:170: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_add_interface’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:457: error: ‘IEEE80211_IF_TYPE_MGMT’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:457: warning: comparison between pointer and integer
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_remove_interface’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:478: error: ‘IEEE80211_IF_TYPE_MGMT’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:478: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_config’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:484: warning: passing argument 2 of ‘rtl8187_set_channel’ makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: At top level:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:525: warning: initialization from incompatible pointer type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:526: error: unknown field ‘open’ specified in initializer
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:527: warning: initialization from incompatible pointer type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:531: warning: initialization from incompatible pointer type
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c: In function ‘rtl8187_probe’:
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:594: error: ‘const struct ieee80211_rate’ has no member named ‘mode’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:594: error: ‘MODE_IEEE80211G’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:594: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:595: error: ‘const struct ieee80211_rate’ has no member named ‘num_rates’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:595: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:596: error: ‘const struct ieee80211_rate’ has no member named ‘rates’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:596: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:597: error: ‘const struct ieee80211_rate’ has no member named ‘num_channels’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:597: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:598: error: ‘const struct ieee80211_rate’ has no member named ‘channels’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:598: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:599: error: ‘const struct ieee80211_rate’ has no member named ‘mode’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:599: error: ‘MODE_IEEE80211B’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:599: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:600: error: ‘const struct ieee80211_rate’ has no member named ‘num_rates’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:600: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:601: error: ‘const struct ieee80211_rate’ has no member named ‘rates’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:601: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:602: error: ‘const struct ieee80211_rate’ has no member named ‘num_channels’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:602: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:603: error: ‘const struct ieee80211_rate’ has no member named ‘channels’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:603: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:604: error: ‘IEEE80211_IF_TYPE_MGMT’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:604: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:607: error: ‘IEEE80211_HW_WEP_INCLUDE_IV’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:607: error: invalid operands to binary | (have ‘int’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:608: error: ‘IEEE80211_HW_DATA_NULLFUNC_ACK’ undeclared (first use in this function)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:608: error: invalid operands to binary | (have ‘const struct ieee80211_rate *’ and ‘const struct ieee80211_rate *’)
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:608: warning: assignment makes integer from pointer without a cast
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:611: error: ‘struct ieee80211_hw’ has no member named ‘max_rssi’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:611: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:615: error: implicit declaration of function ‘ieee80211_register_hwmode’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:641: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:641: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:642: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:642: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:647: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:647: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:648: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:648: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:653: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:653: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:654: error: ‘struct ieee80211_channel’ has no member named ‘val’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:654: warning: statement with no effect
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:685: error: implicit declaration of function ‘MAC_ARG’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:687: warning: format ‘%02x’ expects type ‘unsigned int’, but argument 5 has type ‘char * const’
/home/joseph/rtl-mac80211-20070729/rtl8187_dev.c:687: warning: too few arguments for format
make[2]: *** [/home/joseph/rtl-mac80211-20070729/rtl8187_dev.o] Error 1
make[1]: *** [_module_/home/joseph/rtl-mac80211-20070729] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
root@ubuntu-laptop:~/rtl-mac80211-20070729#

---

