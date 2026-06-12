---
title: "wireless not working (dual boot Windows 7) It works in windows."
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by briandeyoung on 2011-10-02
I have a dual boot Windows 7 Ubuntu (Studio) 11.04 (codename natty) 2.6.38-11-generic in an HP Pavilion dv7 machine.  The wireless doesn't work.  Wired is slow (Comcast), but fine in Windows. 
I am typing, because I am using a different computer to enter this info, so I apologize in advance.

Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vender: Realtek Semiconductor Co. Ltd.
physical id:0
bus info: pci@0000:01:00.0
logical name: eth)
version:06
serial: 10:1f:74:12:b2:81
size: 10Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.LK-NAPI duplex=half ip=192.168.2.6 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:40 ioport:4000(size=256) memory:c0404000-c0404fff memory:c 0400000-c0403fff
description: wireless interface
product: centrino wireless-N 1000
vendor Intel
physical id:0
bus info: pci@0000:07:00.0
logical name: wlan0
version 00
width 64 bits
clock 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=128.50.3.1 build 13488 ip=192.168.2.4 latency=0 link=yes multicast=yes wirelss=IEEE 802.11bgn
resources: irq:51 memory: c4500000-c4501fff


cell 01- address:00:17:3F:75:2A:37
channel:11;Frequency:2.462 GHz (channel 11)
quality=32/70 signal level=-78 dBm
Encryption key: off
ESSID: "Is Comcast working?"
Bit rates: 1 Mb/s; 2 Mb/s; 5.5Mb/s 11Mb/s; 6Mb/s 9Mb/s; 12 Mb/s 18Mb/s
24Mb/s; 36Mb/s;48 Mb/s; 54 Mb/s
Mode: Master
Extra:tsf=000000106e50cd7f
Extra: Last Beacon: 1493850ms ago
and a bunch of IE: unknown:  and some numbers...

---

### Post by briandeyoung on 2011-10-04
I would appreciate any help here.  What information should I provide?  Where should I look?  What am I missing?  I had great success with the 32 bit install.  I read a bunch and talked to some and it seemed like 32 is getting obsolete.    I want to do both movie editing and  sound recording and editing.  It seemed like Ubuntu studio 64 was the very best choice.  Now, I cannot connect wirelessly and have some trouble with wired connections.

Please, help me!

Thanks,

Brian

---

### Post by wildmanne39 on 2011-10-05
Hi, Try this and see if it works please, do what is in post 7.
[http://ubuntuforums.org/showthread.php?p=11121782#post11121782](http://ubuntuforums.org/showthread.php?p=11121782#post11121782)
Thank you

---

### Post by briandeyoung on 2011-10-06
I tried what you suggested.  It didn't seem to change my ability to connect.  What should I run to see if the changes you suggested worked in the way you thought they might?

i.e. What should I try next?

THANKS!

---

### Post by wildmanne39 on 2011-10-06
Hi, if they worked you should be able to connect, please run these commands and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep iwl
```
```
dmesg | egrep 'iwl|firm|wlan0'
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by briandeyoung on 2011-10-10
brian@ubuntustudiohp:~$ cat /etc/lsb-release; uname -a 
  DISTRIB_ID=Ubuntu 
  DISTRIB_RELEASE=11.04 
  DISTRIB_CODENAME=natty 
  DISTRIB_DESCRIPTION="Ubuntu 11.04" 
  Linux ubuntustudiohp 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
  brian@ubuntustudiohp:~$ nm-tool 
   
  NetworkManager Tool 
   
  State: connected 
   
  - Device: eth0 ----------------------------------------------------------------- 
    Type:              Wired 
    Driver:            r8169 
    State:             unmanaged 
    Default:           no 
    HW Address:        10:1F:74:12:B2:81 
   
    Capabilities: 
      Carrier Detect:  yes 
      Speed:           100 Mb/s 
   
    Wired Properties 
      Carrier:         on 
   
   
  - Device: wlan0 ---------------------------------------------------------------- 
    Type:              802.11 WiFi 
    Driver:            iwlagn 
    State:             unmanaged 
    Default:           no 
    HW Address:        8C:A9:82:A3:B6:A2 
   
    Capabilities: 
   
    Wireless Properties 
      WEP Encryption:  yes 
      WPA Encryption:  yes 
      WPA2 Encryption: yes 
   
    Wireless Access Points 
   
   
  brian@ubuntustudiohp:~$ lspci -nnk | grep -iA2 net 
  01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
            Subsystem: Hewlett-Packard Company Device [103c:165b] 
            Kernel driver in use: r8169 
  -- 
  07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084] 
            Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315] 
            Kernel driver in use: iwlagn 
  brian@ubuntustudiohp:~$ iwconfig 
  lo        no wireless extensions. 
   
  eth0      no wireless extensions. 
   
  wlan0     IEEE 802.11bg  ESSID:"Is Comcast working?"  
            Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:75:2A:37   
            Bit Rate=54 Mb/s   Tx-Power=14 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off 
            Power Management:on 
            Link Quality=70/70  Signal level=-36 dBm  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
            Tx excessive retries:0  Invalid misc:55   Missed beacon:0 
   
  brian@ubuntustudiohp:~$ rfkill list all 
  0: phy0: Wireless LAN 
            Soft blocked: no 
            Hard blocked: no 
  brian@ubuntustudiohp:~$ lsmod | grep iwl 
  iwlagn                333716  0 
  iwlcore               167502  1 iwlagn 
  mac80211              294370  2 iwlagn,iwlcore 
  cfg80211              178528  3 iwlagn,iwlcore,mac80211 
  brian@ubuntustudiohp:~$ dmesg | egrep 'iwl|firm|wlan0' 
  [   13.149805] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree: 
  [   13.149807] iwlagn: Copyright(c) 2003-2010 Intel Corporation 
  [   13.149851] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
  [   13.149861] iwlagn 0000:07:00.0: setting latency timer to 64 
  [   13.149889] iwlagn 0000:07:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C 
  [   13.171173] iwlagn 0000:07:00.0: device EEPROM VER=0x15d, CALIB=0x6 
  [   13.171175] iwlagn 0000:07:00.0: Device SKU: 0X9 
  [   13.171176] iwlagn 0000:07:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3 
  [   13.171185] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels 
  [   13.171272] iwlagn 0000:07:00.0: irq 50 for MSI/MSI-X 
  [   13.195355] iwlagn 0000:07:00.0: loaded firmware version 128.50.3.1 build 13488 
  [   13.199714] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs' 
  [   13.348168] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
  [   13.927080] wlan0: authenticate with 00:17:3f:75:2a:37 (try 1) 
  [   13.929324] wlan0: authenticated 
  [   13.933393] wlan0: associate with 00:17:3f:75:2a:37 (try 1) 
  [   13.936333] wlan0: RX AssocResp from 00:17:3f:75:2a:37 (capab=0x421 status=0 aid=1) 
  [   13.936335] wlan0: associated 
  [   13.938777] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
  [   24.746628] wlan0: no IPv6 routers present 
  brian@ubuntustudiohp:~$ 



THANKS again!


I had to save to a thumb drive as a .doc in order to get this posted.  Sorry if there are formatting errors.

---

### Post by wildmanne39 on 2011-10-10
Hi, I recommend taking the spaces out of your ESSID.

Please post the results of these commands:```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e iwlagn -e firmware -e wlan0| tail -n35
```
```
sudo iwconfig wlan0 power off
```
if this works we will need to make it permanent.
Thank you

---

### Post by briandeyoung on 2011-10-10
brian@ubuntustudiohp:~$ sudo iwlist scan 
sudo: unable to resolve host ubuntustudiohp 
[sudo] password for brian:  
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 68:7F:74:AF:0C:58 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=38/70  Signal level=-72 dBm   
                    Encryption key:on 
                    ESSID:"MyValet" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000001bec4edccb1 
                    Extra: Last beacon: 720ms ago 
                    IE: Unknown: 00074D7956616C6574 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0106 
                    IE: Unknown: 2F0106 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                     IE: Unknown:  DD670050F204104A00011010440001021041000100103B00010310470010FD6D2C363B16F91C0DC151B53DB2D0BD102100074C696E6B737973102300034D3230102400063132333435361042000234321054000800060050F2040001101100034D3230100800020084  
                    IE: Unknown: DD090010180201F0040000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000 
          Cell 02 - Address: 00:18:E7:EF:DF:34 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=31/70  Signal level=-79 dBm   
                    Encryption key:on 
                    ESSID:"249" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000051f595ed80 
                    Extra: Last beacon: 530ms ago 
                    IE: Unknown: 0003323439 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 030106 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 2A0102 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000 
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD0900037F01010000FF7F 
                    IE: Unknown: DD0A00037F04010000004000 
                     IE: Unknown:  DD770050F204104A0001101044000102103B00010310470010000000000000100000000018E7EFDF3410210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103  
          Cell 03 - Address: 00:17:3F:75:2A:37 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=70/70  Signal level=-33 dBm   
                    Encryption key:off 
                    ESSID:"Is Comcast working?" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000006557bba29 
                    Extra: Last beacon: 170ms ago 
                    IE: Unknown: 0013497320436F6D6361737420776F726B696E673F 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010B 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C334E10030000000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000 
 
brian@ubuntustudiohp:~$ sudo cat /var/log/syslog | grep -e firmware -e wlan0| tail -n35 
sudo: unable to resolve host ubuntustudiohp 
Oct   9 20:17:14 ubuntustudiohp NetworkManager[795]:    SCPlugin-Ifupdown:  update_connection_setting_from_if_block: name:wlan0,  type:802-11-wireless, id:Ifupdown (wlan0), uuid:  5391eba4-6426-faca-338e-5828034ff9d1 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]:    SCPlugin-Ifupdown: update wireless settings (wlan0). 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]:    SCPlugin-Ifupdown: update wireless security settings (wlan0). 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]:    SCPlugin-Ifupdown: adding iface wlan0 to well_known_interfaces 
Oct   9 20:17:14 ubuntustudiohp NetworkManager[795]:    SCPlugin-Ifupdown:  devices added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/net/wlan0, iface:  wlan0) 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01). 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3) 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1 
Oct  9 20:17:14 ubuntustudiohp NetworkManager[795]: <info> (wlan0): supplicant manager state:  down -> idle 
Oct  9 20:17:15 ubuntustudiohp dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
Oct  9 20:17:15 ubuntustudiohp dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67 
Oct  9 20:17:16 ubuntustudiohp dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
Oct  9 20:17:16 ubuntustudiohp dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67 
Oct  9 20:17:24 ubuntustudiohp kernel: [   24.746628] wlan0: no IPv6 routers present 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]: <info> monitoring kernel firmware directory '/lib/firmware'. 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.141850] iwlagn 0000:07:00.0: loaded firmware version 128.50.3.1 build 13488 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.248173] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.734571] wlan0: authenticate with 00:17:3f:75:2a:37 (try 1) 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.736913] wlan0: authenticated 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.740311] iwlagn 0000:07:00.0: On demand firmware reload 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.740755] wlan0: associate with 00:17:3f:75:2a:37 (try 1) 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.786817] wlan0: RX AssocResp from 00:17:3f:75:2a:37 (capab=0x421 status=0 aid=2) 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.786825] wlan0: associated 
Oct 10 19:39:14 ubuntustudiohp kernel: [   13.789931] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
Oct 10 19:39:14 ubuntustudiohp kernel: [   24.266930] wlan0: no IPv6 routers present 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless 
Oct  10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPlugin-Ifupdown:  update_connection_setting_from_if_block: name:wlan0,  type:802-11-wireless, id:Ifupdown (wlan0), uuid:  5391eba4-6426-faca-338e-5828034ff9d1 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPlugin-Ifupdown: update wireless settings (wlan0). 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPlugin-Ifupdown: update wireless security settings (wlan0). 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPlugin-Ifupdown: adding iface wlan0 to well_known_interfaces 
Oct  10 19:39:14 ubuntustudiohp NetworkManager[1001]:    SCPlugin-Ifupdown:  devices added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0/net/wlan0, iface:  wlan0) 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01). 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3) 
Oct  10 19:39:14 ubuntustudiohp NetworkManager[1001]: <info> (wlan0):  exported as /org/freedesktop/NetworkManager/Devices/1 
Oct 10 19:39:14 ubuntustudiohp NetworkManager[1001]: <info> (wlan0): supplicant manager state:  down -> idle 
brian@ubuntustudiohp:~$ sudo iwconfig wlan0 power off 
sudo: unable to resolve host ubuntustudiohp 



Thanks Again for trying to help!

---

### Post by briandeyoung on 2011-10-10
So, although the symbol for internet has a red 'x' and there are no active connections found, the internet seems to be working wirelessly.

THANKS!  How do I make this permanent?

---

### Post by wildmanne39 on 2011-10-10
Hi, I am guessing the power off is what made it start working.

What is the network you are wanting to connect too? 

To make the changes permanent so you do not have to re-enter it after every reboot, run 
```
sudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```

#!/bin/sh

/sbin/iwconfig wlan0 power off
```
Thank you

---

### Post by briandeyoung on 2011-10-11
I want to use "Is Comcast working?" at home and another "room14" at work.

The last fix seemed to have survived the reboot.  

:D   Thank You SO MUCH!

---

### Post by wildmanne39 on 2011-10-11
Hi, I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by briandeyoung on 2011-10-11
Are you up for another connection problem?  I have an ASUS dual boot UbuntuStudio / Windows 7 that cannot connect wirelessly.

I tried to turn the power off like in the HP machine.  It didn't work.

Here is what I get:
jeikemeijer@ubuntustudioasus:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntustudioasus 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
jeikemeijer@ubuntustudioasus:~$ nm -tool
nm: 'a.out': No such file
jeikemeijer@ubuntustudioasus:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlagn
--
04:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1905]
    Kernel driver in use: jme
jeikemeijer@ubuntustudioasus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jeikemeijer@ubuntustudioasus:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jeikemeijer@ubuntustudioasus:~$ sudo iwlist scan
[sudo] password for jeikemeijer: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

jeikemeijer@ubuntustudioasus:~$ lsmod | grep iwl
iwlagn                333716  0 
iwlcore               167502  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
cfg80211              178528  3 iwlagn,iwlcore,mac80211
jeikemeijer@ubuntustudioasus:~$ dmesg | egrep 'iwl|firm|wlan0'
[   12.730461] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.730465] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.730540] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.730551] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.730592] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   12.751208] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   12.751211] iwlagn 0000:02:00.0: Device SKU: 0X9
[   12.751213] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.751226] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.751306] iwlagn 0000:02:00.0: irq 46 for MSI/MSI-X
[   12.797418] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[   12.803294] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.819153] elantech: assuming hardware version 2, firmware version 4.1.2
jeikemeijer@ubuntustudioasus:~$ 


Thanks again!

---

### Post by wildmanne39 on 2011-10-11
Hi, I need a while I am going to eat dinner.
Thank you

---

### Post by wildmanne39 on 2011-10-11
Hi, go to synaptic and install nm-tool then run that command again please.


Also post the results of:
```
sudo cat /var/log/syslog | grep -e iwlagn -e firmware -e wlan0| tail -n35
```
make sure your wired connection is unplugged.
Thank you

---

### Post by briandeyoung on 2011-10-12
Thanks! AGAIN!

Here goes on the ASUS:

jeikemeijer@ubuntustudioasus:~$ sudo cat /var/log/syslog | grep -e iwlagn -e wlan0| tail -n35
[sudo] password for jeikemeijer: 
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.953006] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.953009] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.953072] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.953080] iwlagn 0000:02:00.0: setting latency timer to 64
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.953116] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.973493] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.973497] iwlagn 0000:02:00.0: Device SKU: 0X9
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.973500] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.977959] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Oct 11 21:08:00 ubuntustudioasus kernel: [   15.978044] iwlagn 0000:02:00.0: irq 46 for MSI/MSI-X
Oct 11 21:08:00 ubuntustudioasus kernel: [   16.065537] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPlugin-Ifupdown: adding iface wlan0 to well_known_interfaces
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 11 21:08:00 ubuntustudioasus NetworkManager[768]: <info> (wlan0): supplicant manager state:  down -> idle
jeikemeijer@ubuntustudioasus:~$ 


But the HP wireless stopped working when the system went to sleep and woke.  It was fine when I shut it down and restarted it...  So then I restarted it and it worked again.  Is there something I need to fix?

Thanks so much!

Brian

---

### Post by wildmanne39 on 2011-10-12
Hi, please post the results of:
```
ps -ef | grep wpa
```
I will see if I can find a fix for the wireless and sleeping issue.
Thank you

---

### Post by briandeyoung on 2011-10-12
This is for the ASUS:

jeikemeijer@ubuntustudioasus:~$ ps -ef | grep wpa
root       875     1  0 19:41 ?        00:00:00 /sbin/wpa_supplicant -u -s
1000      1781  1709  0 19:42 pts/0    00:00:00 grep --color=auto wpa
jeikemeijer@ubuntustudioasus:~$

---

### Post by briandeyoung on 2011-10-12
This is for the HP that works (except after sleeping):

brian@ubuntustudiohp:~$ ps -ef | grep wpa
root       817     1  0 19:36 ?        00:00:00 /sbin/wpa_supplicant -u -s
brian     1947  1892  0 19:45 pts/0    00:00:00 grep --color=auto wpa
brian@ubuntustudiohp:~$ 


It still shows a red 'X' over the symbol for internet and when I check "connection information" it indicates that "no active connection found."

Thanks YOU so MUCH, WildManne39!

---

### Post by wildmanne39 on 2011-10-12
Hi, I am researching your issues this is going to take some time.
Thank you

---

### Post by briandeyoung on 2011-10-13
No problem.  I can wait.  Thanks! WildManne39

---

### Post by wildmanne39 on 2011-10-13
Hi, please post the output of:
```
lsmod
```
install nm-tools
then post the output of:
```
nm -tool
``` 
for the Asus, let's work on this one first.
Thank you

---

### Post by briandeyoung on 2011-10-13
jeikemeijer@ubuntustudioasus:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12784  1 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33176  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                333716  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  515121  7 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  3 snd_seq_midi,snd_seq_midi_event
iwlcore               167502  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
snd_timer              29602  3 snd_hrtimer,snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 iwlagn,iwlcore,mac80211
psmouse                73535  0 
serio_raw              13166  0 
drm                   227534  3 i915,drm_kms_helper
intel_ips              18097  0 
asus_laptop            24173  0 
i2c_algo_bit           13400  1 i915
jmb38x_ms              17596  0 
memstick               16520  1 jmb38x_ms
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13898  1 asus_laptop
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
jme                    40728  0 
ahci                   25951  2 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
jeikemeijer@ubuntustudioasus:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unmanaged
  Default:           no
  HW Address:        00:26:C7:CE:3D:BC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             unmanaged
  Default:           no
  HW Address:        BC:AE:C5:9E:97:57

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


jeikemeijer@ubuntustudioasus:~$ 


I hope this is what you wanted.

Thanks again WildManne39

---

### Post by wildmanne39 on 2011-10-14
Hi, let´s try this please:
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlan0 mode Managed
```
```
sudo ifconfig wlan0 up
```
Then run:
```
sudo iwlist scan
```
Thank you

---

### Post by briandeyoung on 2011-10-14
THANK YOU WIldManne39

jeikemeijer@ubuntustudioasus:~$ sudo ifconfig wlan0 down
jeikemeijer@ubuntustudioasus:~$ sudo iwconfig wlan0 mode managed
jeikemeijer@ubuntustudioasus:~$ sudo ifconfig wlan0 up
jeikemeijer@ubuntustudioasus:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:AF:0C:58
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MyValet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020f6d2b2c26
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00074D7956616C6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD670050F204104A00011010440001021041000100103B00010310470010FD6D2C363B16F91C0DC151B53DB2D0BD102100074C696E6B737973102300034D3230102400063132333435361042000234321054000800060050F2040001101100034D3230100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 02 - Address: 00:18:E7:EF:DF:34
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"249"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003748d41992
                    Extra: Last beacon: 420ms ago
                    IE: Unknown: 0003323439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010000000000000100000000018E7EFDF3410210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103
          Cell 03 - Address: 00:17:3F:75:2A:37
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:off
                    ESSID:"Is Comcast working?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008afb4d80
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 0013497320436F6D6361737420776F726B696E673F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000
          Cell 04 - Address: 00:1E:2A:02:2F:42
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Saturn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003972e76535
                    Extra: Last beacon: 320ms ago
                    IE: Unknown: 000653617475726E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F0301000000001E2A022F42021E2A022F4264002C010E08


THANKS AGAIN!
Brian

---

### Post by wildmanne39 on 2011-10-14
Hi, it is looking for connections know, you maybe able to connect.

Click on your internet icon and make sure wireless is enabled and see if you see a network there to connect too.

It was showing your comcast network, you will have to unplug your wired connection first.

If you have not restarted since you ran those commands please unplug wired and restart.
Thank you

---

### Post by briandeyoung on 2011-10-15
Well, WIldmanne39, I am not happy to report that it didn't work.  I restarted twice and enabled and disabled both networking and wireless repeatedly.  I added "Is Comcast working?" in both network-admin and in wireless connections.

Thanks AGAIN, Wildmanne39

Brian

---

### Post by wildmanne39 on 2011-10-15
Hi, you really should remove the spaces from your SSID then change it in your wireless setup.

Make sure you do not have any other internet connections 

Then try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig iwlagn up
```

If that does not work please post:
```
iwconfig
```
Thank you

---

### Post by briandeyoung on 2011-10-16
I changed my wireless name to "Brian" to get rid of the spaces and make things obvious.  Now, the HP that was working will not work.  It will only work wired.

My next post will be back to the ASUS machine.

Thanks,

Brian

---

### Post by wildmanne39 on 2011-10-16
Hi, did you change it in your router? or just in network settings from the internet icon?
Thank you

---

### Post by briandeyoung on 2011-10-16
I changed in my wireless router too.  I also added a password again, because my wife was complaining about connectivity and the neighbor likes to stream videos using our wireless.


jeikemeijer@ubuntustudioasus:~$ sudo ifconfig wlan0down
sudo: unable to resolve host ubuntustudioasus
[sudo] password for jeikemeijer: 
wlan0down: error fetching interface information: Device not found
jeikemeijer@ubuntustudioasus:~$ sudo rmmod -f iwlagn
sudo: unable to resolve host ubuntustudioasus
jeikemeijer@ubuntustudioasus:~$ sudo modprobe iwlagn 11n_disable=1
sudo: unable to resolve host ubuntustudioasus
jeikemeijer@ubuntustudioasus:~$ sudo ifconfig iwlagn up
sudo: unable to resolve host ubuntustudioasus
iwlagn: ERROR while getting interface flags: No such device
jeikemeijer@ubuntustudioasus:~$ gksudo gedit /etc/hosts
jeikemeijer@ubuntustudioasus:~$ sudo ifconfig wlan0 down
jeikemeijer@ubuntustudioasus:~$ sudo rmmod -f iwlagn
jeikemeijer@ubuntustudioasus:~$ sudo modprobe iwlagn 11n_disable=1
jeikemeijer@ubuntustudioasus:~$ sudo if config iwlagn up
sudo: if: command not found
jeikemeijer@ubuntustudioasus:~$ sudo ifconfig iwlagn up
iwlagn: ERROR while getting interface flags: No such device
jeikemeijer@ubuntustudioasus:~$ 

So, because it wasn't working, I ran:
gksudo gedit /etc/hosts

and changed the host name (by removing .Belkin - I don't know how that got changed)
and changing "Is Comcast working?" to "Brian"

THANK YOU so much!
-Brian

---

### Post by wildmanne39 on 2011-10-16
Hi, this command is wrong sudo if config iwlagn up.

Please just copy and paste all commands it will make it easier.
Thank you

---

### Post by briandeyoung on 2011-10-17
Hi WildManne39,

The first set of commands were just straight from you.  Then I changed the host name and connection name and ran them again, because it was nothing but errors the first time.  I thought this would save time to solve the host errors.

What should I try next?  Is there something different for the HP which used to work until I changed the network name?  and ASUS which has yet to work?

THANK YOU WildManne39!

---

### Post by briandeyoung on 2011-10-17
Should I put the config iwlagn down and then run the gksudo gedit /etc/hosts and then run the rest?

Thank you.

-Brian

---

### Post by wildmanne39 on 2011-10-17
Hi, I am not sure, I have never altered a host file manually.

The last command that failed I figured it out, where I copied it from was wrong this is what it should have been.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
Thank you

---

### Post by briandeyoung on 2011-10-18
iwconfig got this:

lo   no wireless extensions.

eth0 no wireless ectensions.

wlan0 IEEE 802.11bg ESSID: off/any
mode:Managed Access Point: Not-Associated Tx-Power=14 dBm
Retry long limit:7  RTS thr:off Fragment thr: off
Power Management:off

(SO, no, it didn't work.)

THANKS!

-brian

---

### Post by briandeyoung on 2011-10-19
I believe network manager is working now!  Everything was logical after that.  I am not sure exactly what was done; I will find out and post here.

Thanks!

Brian

---

### Post by wildmanne39 on 2011-10-19
Hi, that is good, I know that if you use network manager you have to be careful about manually editing some files or it will not work anymore.
Thank you

---

