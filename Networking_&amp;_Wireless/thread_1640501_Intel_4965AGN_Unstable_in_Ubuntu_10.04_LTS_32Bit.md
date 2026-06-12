---
title: "Intel 4965AGN Unstable in Ubuntu 10.04 LTS 32Bit"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by auren on 2010-12-07
I'm using a notebook with Intel 4965AGN and connecting to a Linksys WRT320N router. I can connect most of the time but after a while (sometimes a few minutes, sometimes a few hours) I lose connection. The notification icon would not change. I would only find out when I browse or click on a link and it would just get stuck at "Looking for <url>..." My wife's notebook would still be connected to the router even after mine has mysteriously disconnected. But she uses another os.

details are as follows:

1. lspci -nn | grep '4965'

> 02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)


2. iwconfig wlan0
> wlan0     IEEE 802.11abgn  ESSID:"network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:18:8C:76   
          Bit Rate=36 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


3. lsmod | grep 'iwlagn'
> iwlagn                106815  0 
iwlcore               106050  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
cfg80211              126528  3 iwlagn,iwlcore,mac80211


4. sudo lshw -C network
>   *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:95:48:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.151 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:96d00000-96d01fff


5. iwlist scan
> wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:18:8C:76
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009b68b772e
                    Extra: Last beacon: 26320ms ago
                    IE: Unknown: 00076E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700104244ABB52FB8BA544BD45F3C1C38A9C21021000C4C696E6B73797320496E632E102300075752543332304E1024000776312E302E30331042000234321054000800060050F2040001101100075752543332304E100800020084
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000


6. lsb_release -d
> Description:	Ubuntu 10.04.1 LTS

7. uname -mr
> 2.6.32-26-generic i686


8. sudo /etc/init.d/networking restart
> * Reconfiguring network interfaces...                                                                                                                                                                  [ OK ] 


---

### Post by auren on 2010-12-14
Found out something.

Whenever I get disconnected, the router would respond to my ping but outside addresses would not. I've already tried installing compat-wireless (linux-backport-module-wireless-generic) and wicd and they don't help.

---

