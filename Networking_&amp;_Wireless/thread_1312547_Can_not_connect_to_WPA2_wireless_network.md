---
title: "Can not connect to WPA2 wireless network"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by toca180 on 2009-11-03
Hi

I have just installed Xubuntu 9.10. I have a wireless network that is protected by WPA2 encryption. I have a Netgear WG511v2 ([http://www.netgear.co.uk/wireless_laptop_networkcard_wg511.php](http://www.netgear.co.uk/wireless_laptop_networkcard_wg511.php)) wireless card. I have set this up with ndiswrapper as xubuntu did not recognise it after install. Network manager can see the network and tries to connect but keeps asking for the key. I know the key is correct as I have copied and pasted it from the router control panel. The same laptop and wireless card can connect to the router fine with Windows XP, so I know that the hardware is capable of connecting. If I disable WPA2 then it can connect fine, obviously this is not a solution. What else can I try so that I can connect? If you want me to provide further information please ask and I will provide it.

Thanks
Robert

---

### Post by Carlicuslinux on 2009-11-03
I am having the exact same problme with my Gateway NV52 laptop...able to connect wirelessly with Vista or Ubuntu 9.04, but can't connect with 9.10...keeps asking for my passphrase over and over again when I know it is exactly correct...can't connect.
 
Can someone help us out?

---

### Post by toca180 on 2009-11-03
Now that I am I home an in front of mu computer I thought that I could post some more information about my problem:

```

ndiswrapper -l
wg511v2 : driver installed
    device (11AB:1FAA) present

``````

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:08.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
lsmod | grep ndiswrapper
ndiswrapper           185404  0
``````

dmesg | grep ndiswrapper
[  917.015249] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  917.030355] ndiswrapper: driver wg511v2 (NETGEAR,02/22/2005,3.1.1.7) loaded
[  917.030682] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0002)
[  917.030696] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  917.030715] ndiswrapper 0000:02:00.0: setting latency timer to 64
[  917.032650] ndiswrapper: using IRQ 17
[  917.296992] usbcore: registered new interface driver ndiswrapper
[  982.156575] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  988.935399] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  995.707645] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1002.481208] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1009.252227] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1016.027835] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1022.801725] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1029.568328] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1036.339677] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1043.112352] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1045.762366] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1052.531707] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1059.303673] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1066.078473] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1072.974885] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1079.743722] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1086.513567] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1093.284957] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1100.055641] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1106.852387] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1113.627137] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1120.399980] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1127.172203] ndiswrapper (iw_set_auth:1602): invalid cmd 12
``````
lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:12:00:22
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.8 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:e800(size=256) memory:dfffe000-dfffefff memory:dffc0000-dffdffff(prefetchable)
  *-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 0
       resources: irq:17
  *-network DISABLED
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:40:d1:69
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg511v2 driverversion=1.55+NETGEAR,02/22/2005,3.1.1.7 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:44000000-4400ffff memory:44010000-4401ffff
``````
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0E:2E:6E:7B:FA
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1C:DF:38:82:23
                    ESSID:"Belkin_G_Plus_MIMO_388223"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:22:57:62:21:0C
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: 00:22:3F:CC:98:86
                    ESSID:"kestrel11"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```Hope this information is able to give you more insight into what might be causing the problem. Any ideas gratefully received. (Also glad to see that I an not the only person with this problem.)

Thanks
Robert

---

### Post by rearviewmirror on 2009-11-04
I just installed Ubuntu 9.10 and have the same issues.  I can see the AP using the iwlist scan, and I verified my WPA2 password is correct.  On my Linksys I have AES only enabled, not the AES+TKIP option.

---

### Post by toca180 on 2009-11-11
Hello

Bump.

Any ideas? Any more information I can give?

Thanks
Robert

---

### Post by ambo on 2009-11-14
There is a bug report open on this issue: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

We have however had no feedback from the ndiswrapper developers. This appears to affect any connection to an encrypted network using an ndiswrapper based device.

---

