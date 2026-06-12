---
title: "wireless not connecting: Realtek/Ubuntu 11.10/Toshiba Satellite L755-S5214"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Proudfoot58 on 2012-03-11
Need help getting my wireless working since upgrading from 10.04 to 11.10. I've looked at many threads about the issue but none have solved the problem for me. I know the router is fine since it connected before the upgrade and my wife's Windows 7 box still works. I am able to connect using a cable but not via wireless. It sees all the routers (including mine, PROUDFOOT) but no longer connects. It tries multiple times and eventually asks for the password again. I have verified the password and it is correct.

Any guidance would be appreciated


Suggested data capture below:

=========================================================
dmesg | grep w wlan0
=========================================================
[   13.467046] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.776310] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   17.780141] wlan0: authenticated
[   17.800522] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   17.812343] wlan0: RX AssocResp from 00:18:4d:50:60:52 (capab=0x431 status=0 aid=3)
[   17.812352] wlan0: associated
[   17.812837] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.217973] wlan0: deauthenticated from 00:18:4d:50:60:52 (Reason: 14)
[   18.350940] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=14)
[   28.417192] wlan0: no IPv6 routers present
[   42.361675] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   42.363506] wlan0: authenticated
[   42.363622] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   42.368281] wlan0: RX ReassocResp from 00:18:4d:50:60:52 (capab=0x431 status=12 aid=0)
[   42.368287] wlan0: 00:18:4d:50:60:52 denied association (code=12)
[   42.368681] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=3)
[   43.336807] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   43.339470] wlan0: authenticated
[   43.339864] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   43.343650] wlan0: RX AssocResp from 00:18:4d:50:60:52 (capab=0x431 status=12 aid=0)
[   43.343662] wlan0: 00:18:4d:50:60:52 denied association (code=12)
[   43.343750] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=3)
[   44.311818] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   44.316005] wlan0: authenticated
.
.  NOTE: manually trimmed the output. same lines duplicated many times
.
[   74.585897] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   74.587530] wlan0: authenticated
[   74.587821] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   74.590219] wlan0: RX AssocResp from 00:18:4d:50:60:52 (capab=0x431 status=12 aid=0)
[   74.590229] wlan0: 00:18:4d:50:60:52 denied association (code=12)
[   74.590304] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=3)
[   75.557007] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   75.558723] wlan0: authenticated
[   75.559087] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   75.561458] wlan0: RX AssocResp from 00:18:4d:50:60:52 (capab=0x431 status=12 aid=0)
[   75.561468] wlan0: 00:18:4d:50:60:52 denied association (code=12)
[   75.561561] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=3)
[   76.532129] wlan0: authenticate with 00:18:4d:50:60:52 (try 1)
[   76.535481] wlan0: authenticated
[   76.535778] wlan0: associate with 00:18:4d:50:60:52 (try 1)
[   76.538082] wlan0: RX AssocResp from 00:18:4d:50:60:52 (capab=0x431 status=12 aid=0)
[   76.538087] wlan0: 00:18:4d:50:60:52 denied association (code=12)
[   76.538133] wlan0: deauthenticating from 00:18:4d:50:60:52 by local choice (reason=3)


=========================================================
ifconfig
=========================================================
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:52:6a:53  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:fe52:6a53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2109 (2.1 KB)  TX bytes:7754 (7.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:1e:75:06  
          inet6 addr: fe80::d2df:9aff:fe1e:7506/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:474 (474.0 B)  TX bytes:1147 (1.1 KB)



=========================================================
iwconfig wlan0
=========================================================
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          


=========================================================
iwlist wlan0 scan "manually edited since option essid doesn't work"
=========================================================
          Cell 03 - Address: 00:18:4D:50:60:52
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"PROUDFOOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000117aae5c181
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000950524F5544464F4F54
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101000002A44000
                    IE: Unknown: DD1A00037F030100000000184D50605202184D50605264002C011D08


=========================================================
lshw -C network
=========================================================
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:1e:75:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-16-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:c0500000-c0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:52:6a:53
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:c0400000-c043ffff ioport:2000(size=128)


=========================================================
lsmod | grep -n realtek;lsmod | grep -n rtl
=========================================================
43:ums_realtek            13096  0 
44:usb_storage            44173  1 ums_realtek
14:rtl8192ce             127361  0 
19:rtlwifi               107538  1 rtl8192ce
31:mac80211              393421  2 rtl8192ce,rtlwifi
33:cfg80211              172427  2 rtlwifi,mac80211


=========================================================
/etc/init.d/networking restart
=========================================================
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.


=========================================================
lsb_release -d;uname -mr
=========================================================
Description:    Ubuntu 11.10
3.0.0-16-generic i686

---

### Post by praseodym on 2012-03-11
Try a new driver version: 0005.1230.2011 from the Realtek website

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722)

---

### Post by Proudfoot58 on 2012-03-11
I did already. that's what is currently installed

looking at some other posts, do I need to blacklist old drivers? Is there someway to find out what other rtl drivers are defined?

---

### Post by Proudfoot58 on 2012-03-11
SOLVED:

Changed the security setting on the router to WPA2-AES

Once change it connected without a problem. Not sure why WPA-TKIP became an issue but I'm back on-line.

---

### Post by Thewhistlingwind on 2012-03-11
> **Proudfoot58 said:**
> SOLVED:

Changed the security setting on the router to WPA2-AES

Once change it connected without a problem. Not sure why WPA-TKIP became an issue but I'm back on-line.

Great. Can you please change the category of the thread from [ubuntu] to [SOLVED]?

---

### Post by olinart on 2012-05-17
I have the same problem with 12.04 and a different wireless card: 
product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
In my university environment TKIP is standard. Changing the router setting is not a solution.

---

