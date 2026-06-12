---
title: "Can't get n speeds or scan 5ghz band on 11.10"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by KeithKris on 2011-12-16
Fresh install of 11.10.  Intel 6200 network adapter.  I can connect fine to my 2.4ghz network, but I've never gotten above 54mbps.  Signal quality is decent (I'm using a directional antenna.)  I also can't see my 5GHz network, which I'd prefer to use because there is less interference on this band in my neighborhood.  I tried booting into a newer kernel hoping that the issue might be resolved already, but no luck.  I installed 3.2.0-030200rc5.  I have googled this extensively, and I've tried all the standard stuff I could find like making sure the driver didn't have 802.11n disabled in the kernel module.

Any thoughts?

Some info on my config:

root@storage:~# iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"REDACTED"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: REDACTED   
          Bit Rate=39 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8935  Invalid misc:455   Missed beacon:0


root@storage:~# lshw -c network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:cd:e0:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-030200rc5-generic firmware=9.221.4.1 build 25532 ip=192.168.1.43 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:feafe000-feafffff



root@storage:~# lsmod
...SNIP...
iwlwifi               326338  0 
mac80211              495815  1 iwlwifi
cfg80211              200055  2 iwlwifi,mac80211



root@storage:~# rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no




root@storage:~# lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS880 [Radeon HD 4200] [1002:9710]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)



root@storage:~# iwlist scan #(cell 1 is definitely 802.11n, I connect at n speeds from other machines.)
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: REDACTED
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key: on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d67d8398da
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0006627269646765
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010703D8377738F10D281DF9C1184F9BBA41021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409081100000000000000000000000000000000000000
          Cell 02 - Address: REDACTED
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key: on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d6396cb13a
                    Extra: Last beacon: 5196ms ago
                    IE: Unknown: 00096B656974686D696B65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0113FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: DD1E00904C33EC0113FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: DDA90050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F0022755212E41021001442656C6B696E20496E7465726E6174696F6E616C102300114E20576972656C65737320526F757465721024000C463544383233362D342076331042000E32303931373832333631323839341054000800060050F20400011011001842656C6B696E204E20576972656C65737320526F75746572100800020084103C000101
          Cell 03 - Address: REDACTED
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key: on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000021c3ad4175
                    Extra: Last beacon: 5208ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: REDACTED
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key: on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e8bf0c3b17
                    Extra: Last beacon: 5016ms ago
                    IE: Unknown: 000A4465536865746C657232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010C1387C5D8DE589E334A63FAD412186901021000D4E4554474541522C20496E632E10230008574E44523333303010240008574E4452333330301042000230311054000800060050F204000110110008574E445233333030100800020084103C000103
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: REDACTED
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key: on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000009f6181
                    Extra: Last beacon: 5296ms ago
                    IE: Unknown: 0006706F6D6F6475
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010080
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

---

### Post by KeithKris on 2011-12-17
If no one has an answer, does anyone at least have an idea to point me in the right direction?

---

### Post by ThePol1 on 2012-01-11
I am having this same problem with my new Intel 6230 WiFi card on 11.10 and I just posted on this in the hardware forum. Did you ever find a solution?

---

### Post by praseodym on 2012-01-11
Hi,

the N-mode is buggy in kernel 3.0, try to compile the driver by hand via linux-wireless or try mainline kernel 3.2 (you may need to reinstall the VGA driver after that)

---

### Post by ThePol1 on 2012-01-12
> **praseodym said:**
> Hi,
 
the N-mode is buggy in kernel 3.0, try to compile the driver by hand via linux-wireless or try mainline kernel 3.2 (you may need to reinstall the VGA driver after that)
 
Actually, this ended up being a problem with my router and not the wireless card -- it seems to work just fine using N (5 Ghz) and Ubuntu 11.10 (32 bit).

---

