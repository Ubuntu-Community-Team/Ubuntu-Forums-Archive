---
title: "wifi realtek problem"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by tekkit on 2010-10-31
Hello community

I have problems with my wireless card after upgrading to 10.10. The card was partly working under 9.04 but not any more. Here is the results of my ifconfig:

eth0   Link encap:Ethernet  HWaddr 00:10:a7:05:0e:2c  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a7ff:fe05:e2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44300 errors:6211 dropped:0 overruns:0 frame:0
          TX packets:45691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59808964 (59.8 MB)  TX bytes:4599825 (4.5 MB)
          Interrupt:11 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:78:72:bb  
          inet6 addr: fe80::214:bfff:fe78:72bb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5198 (5.1 KB)  TX bytes:9819 (9.8 KB)

The hardware listing

       *-network:0
             description: Wireless interface
             product: RT2500 802.11g
             vendor: RaLink
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: wlan0
             version: 01
             serial: 00:14:bf:78:72:bb
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-22-generic firmware=N/A latency=32 multicast=yes wireless=IEEE 802.11bg
             resources: irq:10 memory:e6000000-e6001fff
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth0
             version: 10
             serial: 00:10:a7:05:0e:2c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.101 latency=32 maxlatency=64 mingnt=32 multicast=yes
             resources: irq:11 ioport:c800(size=256) memory:e6003000-e60030ff

The card identifies my network, but cant log on to it. I am really clueless after having tried several options.

JO

---

### Post by chili555 on 2010-10-31
May I assume that Network Manager is running?

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themI notice you have an ethernet connection. Is Network Manager preventing a wireless connection as it is designed to do?

If you disconnect the ethernet cable and reboot can you connect? If not, please let me see:```
lspci -nn
lsmod | grep rt2
```Thanks.

---

### Post by tekkit on 2010-10-31
That is correct, network manager is running. 
I am currently using a cabled network, which works fine.
I tried disconnecting the cable and restarting, but that didn't work. I only get prompted for the password over and over again. So here are the results of 

lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:06.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:06.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:06.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51)
00:08.0 Network controller [0280]: RaLink RT2500 802.11g [1814:0201] (rev 01)
00:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:0a.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 08)
00:0a.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 08)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233A ISA Bridge [1106:3147]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 40)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV31 [GeForce FX 5600] [10de:0312] (rev a1)



lsmod | grep rt2
rt2500pci              13731  0 
rt2x00pci               6029  1 rt2500pci
rt2x00lib              27275  2 rt2500pci,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231541  2 rt2x00pci,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2500pci

Hope this helps, thanks.

JO

---

### Post by chili555 on 2010-10-31
Everything looks really healthy, actually. Are you quite sure about your password? Is your network WPA or WPA2 or the troublesome mixed WPA ***and*** WPA2 mode? May I see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by tekkit on 2010-11-02
Been away for some time. 
I have triple checked the password. I have also changed the password and tried over. I seems like i have the troublesome WPA & WPA2 mode, at least i am prompted with this wireless security. I doesnt seem to be possible to change this option. The result of the scan

wlan0     Scan completed :
          Cell 01 - Address: 1C:AF:F7:7E:E0:4E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Untermensch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002cf0b96e00
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 000B556E7465726D656E736368
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001017BC20EACE14090355791CAFF77EE04E10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
        
Thanks for the help so far.

JO

---

### Post by chili555 on 2010-11-02
Network Manager will prompt you for the WPA and WPA2 password whether you have one or the other or the dreaded mixed mode. Here is why I think you have it:> Cell 01 - Address: 1C:AF:F7:7E:E0:4E
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=59/70 Signal level=-51 dBm
Encryption keyn
ESSID:"Untermensch"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000002cf0b96e00
Extra: Last beacon: 768ms ago
[...]
IE: [COLOR="Red"]WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: [COLOR="Red"]IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
[...]Both are listed.

Are you not able to select the mode in the router's setup pages? See attached.

---

### Post by tekkit on 2010-11-02
It seems that i only have 3 options 1. no crypto 2. WEP 3. WPA & WPA2.
I guess this is my bad for buying a cheap router.

---

### Post by chili555 on 2010-11-02
Just so we can rule out the router or the driver, if you temporarily change to no crypto, can you connect?

---

### Post by tekkit on 2010-11-03
I tried no crypto today. The computer prompted me with a message that it was connected to the wireless, but still i was unable to access the Internet. I also tried to ping the router, but that didn't work either. I also tried to connect to the crypto free network with a Windows computer, but i was unable to connect with that. Another thing is that i am unable to reset the router to fabric settings. Maybe it is something wrong with the router. 

JO

---

