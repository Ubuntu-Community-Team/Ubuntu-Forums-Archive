---
title: "WiFi - keeps saying my password is wrong"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by mike_pl on 2012-01-05
Hi!

I've recently installed Ubuntu. At first my wifi worked ok, but then it got disconnected and kept asking me for a password, saying it's wrong. After killing wpa_supplicant, NetworkManager and disabling and enabling the interface (a couple of times), my connection returned.But it still happens at least every other day. Moreover, when I reset my router the problem is sure to appear again.
Please help, it's driving me nuts.I've tried uninstalling gnome network manager and installing wicd, but still the same problem. What can I do? I've already searched the web. I've been fighting with it for the last three weeks. And I don't know what to do. I'm using WPA2. The connection works without any problem on Windows and my Android phone.
Below I post info as requested in the FAQ.


1) Machine Brand and Model (PC/Laptop):
Laptop: MSI Megabook M635

2 ) Wireless Brand, Model and Wireless Chipset:
02:09.0 Network controller: Ralink corp. RT2500 802.11g (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Unknown 802.11g mini-PCI Adapter
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fbffc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: rt2500pci
    Kernel modules: rt2500pci

3) check interface:
wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6e:16:50  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe6e:1650/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2181238 (2.1 MB)  TX bytes:647765 (647.7 KB)

wlan0     IEEE 802.11bg  ESSID:"tajemnicza_wyspa"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 30:46:9A:3B:08:BA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0

4) Modules:
lsmod | grep rt2500
rt2500pci              22948  0 
rt2x00pci              14202  1 rt2500pci
rt2x00lib              48114  2 rt2500pci,rt2x00pci
eeprom_93cx6           12653  1 rt2500pci

5) dmesg
I couldn't find anything relating to rt2500, but there are some entries regarding wlan0

[  147.194861] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  148.197189] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  148.201840] wlan0: authenticated
[  148.202968] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  148.209392] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  148.209402] wlan0: associated
[  152.008651] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  162.557417] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  162.562104] wlan0: authenticated
[  162.563229] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  162.569665] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  162.569676] wlan0: associated
[  172.577698] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  172.595672] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  173.599092] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  173.603765] wlan0: authenticated
[  173.605468] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  173.611765] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  173.611776] wlan0: associated
[  183.617489] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  183.637718] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  184.643064] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  184.647782] wlan0: authenticated
[  184.649588] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  184.655944] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  184.655953] wlan0: associated
[  194.664913] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  194.685835] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  195.689383] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  195.694054] wlan0: authenticated
[  195.695115] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  195.704041] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  195.704052] wlan0: associated
[  205.711253] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  205.729926] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  206.741382] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  206.746025] wlan0: authenticated
[  206.747085] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  206.753793] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  206.753803] wlan0: associated
[  216.761026] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  216.781460] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  217.785390] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  217.790070] wlan0: authenticated
[  217.791143] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  217.797465] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  217.797474] wlan0: associated
[  222.006331] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  230.545409] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  230.550079] wlan0: authenticated
[  230.551148] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  230.557426] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  230.557435] wlan0: associated
[  240.564373] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  240.585908] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  241.593399] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  241.598092] wlan0: authenticated
[  241.599155] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  241.605508] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  241.605517] wlan0: associated
[  242.439249] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  242.628571] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  245.813391] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  245.818505] wlan0: authenticated
[  245.820197] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  245.826431] wlan0: RX AssocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  245.826441] wlan0: associated
[  245.827455] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  255.834176] wlan0: disassociating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  255.848984] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  256.712032] wlan0: no IPv6 routers present
[  256.853388] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  256.858083] wlan0: authenticated
[  256.859141] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  256.865492] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  256.865501] wlan0: associated
[  263.766724] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  264.060586] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  267.273387] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  267.278545] wlan0: authenticated
[  267.279616] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  267.286357] wlan0: RX AssocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  267.286366] wlan0: associated
[  267.287314] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  274.032519] wlan0: deauthenticating from 30:46:9a:3b:08:ba by local choice (reason=3)
[  276.440929] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  278.273364] wlan0: authenticate with 30:46:9a:3b:08:ba (try 1)
[  278.278096] wlan0: authenticated
[  278.279150] wlan0: associate with 30:46:9a:3b:08:ba (try 1)
[  278.285450] wlan0: RX ReassocResp from 30:46:9a:3b:08:ba (capab=0x431 status=0 aid=1)
[  278.285458] wlan0: associated
[  278.286362] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  288.560033] wlan0: no IPv6 routers present

After this boot I did not have wireless, and the reason=3 suggests that the password is wrong (which is similar to what I observe in GUI)

6) Network configuration:
lshw -C network

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:af:0d:57
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:e800(size=256) memory:fbfffc00-fbfffcff memory:fbfe0000-fbfeffff
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g
       vendor: Ralink corp.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wlan0
       version: 01
       serial: 00:13:d3:6e:16:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.0.0-14-generic firmware=N/A ip=192.168.0.3 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fbffc000-fbffdfff

7) Scan for networks
iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 30:46:9A:3B:08:BA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"tajemnicza_wyspa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000067b737d190
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 001074616A656D6E69637A615F7779737061
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 0706444520010D14
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E10030000000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609071800000000000000000000000000000000000000
                    IE: Unknown: DD970050F204104A0001101044000102103B00010310470010824FF22B8C7D41C5A13144F534E12555102100074E455447454152102300164E4554474541522044474E3130303020526F757465721024000A312E30302E32385F77771042000831323334353637381054000800060050F2040001101100164E4554474541522044474E3130303020526F757465721008000201AA103C000103
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

8) Ubuntu version
Description:    Ubuntu 11.10

9) Kernel/arch
3.0.0-14-generic i686
32-bit version (although running on AMD Thurion 64 if that matters)

10) root@salon:/home/mike# sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by Gelupah on 2012-01-05
Hey,

I wonder if our problems could be related :

[http://ubuntuforums.org/showthread.php?p=11571938](http://ubuntuforums.org/showthread.php?p=11571938)

Does everything work with WEP? Try the different types of WPA too, AES, TKIP etc...

PS : it's driving me nuts too...

---

### Post by mike_pl on 2012-01-06
> **Gelupah said:**
> Hey,

I wonder if our problems could be related :

[http://ubuntuforums.org/showthread.php?p=11571938](http://ubuntuforums.org/showthread.php?p=11571938) Does everything work with WEP? Try the different types of WPA too, AES, TKIP etc...

PS : it's driving me nuts too...
I'm sure there are. I've searched the web and it seems many problems have a problem with "bad password". But I couldn't find any solution.

---

### Post by lz1dsb on 2012-01-06
I think I'm experiencing the same issue even though my hardware is rather different (Dell Studio 1555 with BCM4312 wireless controller chip). It's quite sporadic. It happens only from time to time. Sometimes I stay connected for 5-6 hours without a glitch and than suddenly I'm disconnected and the only way to get back connected is to reboot the machine. 
I also recently installed 11.10. With the STA Broadcom wireless driver the wireless was rock solid in 9.10.
I was thinking that maybe the Broadcom driver is to be blamed, but if other folks with different hardware are experiencing this...
Any luck in finding anything useful as a workaround at least?

---

### Post by Gelupah on 2012-01-06
> **mike_pl said:**
> I'm sure there are. I've searched the web and it seems many problems have a problem with "bad password". But I couldn't find any solution.

Well in my case changing the type of WPA fixed it for me, at home only though. It's a pain, when I travel, most of the WPA don't work...

I used to have the same internal Realtek mini pci express card as you, had the problem, changed it to Intel 6300, still have the problem...

---

