---
title: "Cannot connect to wireless!"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Tejano09 on 2011-05-27
Howdy all,

I have installed xubuntu 11.04 and cannot connect to my wireless router - The computer picks up all the local signals, so it's working from that end. When I do try to connect wirelessly it tries for a bit and then tells me I am disconnected. The password is correct and the wireless is WPA-Personal TKIP Encrypted. 

Any help? I've been searching for an answer for days with nothing to show for it.:(

---

### Post by Toz on 2011-05-27
Can you post back:

1. The make/model of your computer.

2. The results of running the following commands from a terminal window:```
nm-tool
``````
sudo lshw -C network
``````
lspci
``````
rfkill list all
``````
lsmod
``````
sudo iwconfig
``````
sudo iwlist scan
```

---

### Post by tigerente on 2011-05-28
I'm having similar problems on Lubuntu 10.10. The network manager automatically tries to connect to my wireless but fails after maybe four or five attempts and tells me that I am now disconnected. The strange thing is that it did connect once but ever after refuses to do so. As far as I am aware of I didn't change any of the relevant settings, but as I am a computer illiterate I wasn't able to check where the problem is (I tried but wasn't able to make head or tail of the terminal outputs :(). 
Hopefully someone can come up with a solution.

---

### Post by Toz on 2011-05-28
> **tigerente said:**
> I'm having similar problems on Lubuntu 10.10. The network manager automatically tries to connect to my wireless but fails after maybe four or five attempts and tells me that I am now disconnected. The strange thing is that it did connect once but ever after refuses to do so. As far as I am aware of I didn't change any of the relevant settings, but as I am a computer illiterate I wasn't able to check where the problem is (I tried but wasn't able to make head or tail of the terminal outputs :(). 
Hopefully someone can come up with a solution.

Please post back the results of those commands. Maybe we can help.

---

### Post by Tejano09 on 2011-05-28
Make and Model: Toshiba Satellite M45 (upgraded to 1G RAM)

nm-tool gives:
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:A0:D1:21:4F:F1

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:63:B9:3F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Altamuro - Home: Infra, 98:2C:BE:01:70:D9, Freq 2417 MHz, Rate 54 Mb/s, Strength 25 WEP
    2WIRE240:        Infra, C0:83:0A:68:7D:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    2WIRE999:        Infra, C0:83:0A:E8:6D:81, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    2WIRE334:        Infra, B0:E7:54:48:EB:81, Freq 2427 MHz, Rate 54 Mb/s, Strength 38 WPA
    2WIRE276:        Infra, 00:21:7C:E7:E1:D9, Freq 2437 MHz, Rate 54 Mb/s, Strength 68 WPA
    NETGEAR:         Infra, 00:22:3F:6F:EE:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE007:        Infra, 00:1B:5B:7C:6E:49, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WEP
    2WIRE358:        Infra, 00:23:51:E1:76:B1, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA
    2WIRE124:        Infra, 00:22:A4:1B:43:B9, Freq 2442 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    2WIRE269:        Infra, 00:21:7C:4C:3C:F9, Freq 2427 MHz, Rate 54 Mb/s, Strength 61 WPA
    2WIRE424:        Infra, 00:1F:B3:A9:23:99, Freq 2457 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    THOMPSON:        Infra, C0:3F:0E:AE:00:94, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    2WIRE855:        Infra, 00:1B:5B:E0:36:21, Freq 2432 MHz, Rate 54 Mb/s, Strength 94 WPA

sudo lshw -C network gives:
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 01
       serial: 00:11:f5:63:b9:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:21:4f:f1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.74 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0211000-c02110ff

---

### Post by Tejano09 on 2011-05-28
lspci gives:
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

rfkill list all gives:
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/QUOTE]

lsmod gives:
[QUOTE]Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_atiixp             19400  3 
snd_atiixp_modem       18624  1 
arc4                   12473  2 
snd_ac97_codec        105614  2 snd_atiixp,snd_atiixp_modem
radeon                896428  2 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
ath5k                 144412  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
joydev                 17322  0 
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 radeon,ttm,drm_kms_helper
cfg80211              156212  3 ath5k,ath,mac80211
yenta_socket           27230  0 
snd                    55295  16 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_atiixp,snd_atiixp_modem,snd_pcm
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
shpchp                 32345  0 
ati_agp                13202  0 
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
8139cp                 22497  0 
pata_atiixp            12968  2 

sudo iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by Tejano09 on 2011-05-28
sudo iwlist scan gives:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:7C:4C:3C:F9
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"2WIRE269"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033c85d1b39
                    Extra: Last beacon: 420ms ago
                    IE: Unknown: 00083257495245323639
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1 : TKIP
                        Authentication Suites (1 : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303232303831313036393236391021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3232303831313036393236391054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 02 - Address: 00:1B:5B:E0:36:21
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"2WIRE855"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d0df8f3f2
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 00083257495245383535
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030105
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1 : TKIP
                        Authentication Suites (1 : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303335303731313034353835351021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3335303731313034353835351054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 03 - Address: 00:21:7C:E7:E1:D9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"2WIRE276"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000060b2fb181
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 00083257495245323736
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1 : TKIP
                        Authentication Suites (1 : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303238303831313030373237361021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3238303831313030373237361054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 04 - Address: 00:1F:B3:A9:23:99
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"2WIRE424"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019767bcc4f
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00083257495245343234
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2 : CCMP TKIP
                        Authentication Suites (1 : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2 : CCMP TKIP
                        Authentication Suites (1 : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303134303831313034373432341021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3134303831313034373432341054000800060050F20400011011000A686F6D65706F7274616C10080002008E

---

### Post by Tejano09 on 2011-05-28
Cell 05 - Address: 00:22:3F:6F:EE:0C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033cb74a8ec
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B000103104700108C35A479F67A8B523E86D4CC77FBC4761021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180204F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: C0:3F:0E:AE:00:94
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"THOMPSON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033cbfff81a
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000854484F4D50534F4E
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700105F3D4FB3DA686D7D681957CC25C6DB8E1021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 07 - Address: 00:22:A4:1B:43:B9
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE124"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013f61df1181
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 00083257495245313234
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030107
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown DD900050F204104A0001101044000102103B00010210470010303030303333303831313031343132341021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3333303831313031343132341054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 08 - Address: 00:23:51:E1:76:B1
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"2WIRE358"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033c879d181
                    Extra: Last beacon: 484ms ago
                    IE: Unknown: 00083257495245333538
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102



sorry it took me so long, and thanks for responding.

(and sorry about the multiple responses - there were hidden smilies in the code and I couldn't find them)

---

### Post by Toz on 2011-05-28
The files look good to me. Have a look at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775104](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775104) for a known bug report for your wireless card and a temporary workaround using madwifi.

---

### Post by tigerente on 2011-05-30
Here are my specifications. My network is rhw-19269. 
When I collected all this information and looked through it I realized that my Frequency is zero. I changed the channel of my router from originally "7" to "6", restarted my router, trashed my wireless connection and added it again but the result is still the same.
All the output is made after I changed to channel 6.

I didn't know (and didn't find a how-to) how to put all the information in boxes with scroll bars hence the text got very long. Would someone kindly tell me how to do this or where the relevant information on how to do this is hidden?

Tanks in advance. Any help appreciated!


                                 **The make/model of my computer**: Toshiba Satellite SA 50-493

**1) NetworkManager Tool**

[FONT=Courier New]State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:0E:7B:19:8F:03

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:0E:35:2D:47:F3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Vogel in der Nacht: Infra, 00:0F:CC:F8:A9:50, Freq 2442 MHz, Rate 54 Mb/s, Strength 33 WPA WPA2
    Blume:           Infra, 00:1B:2F:E1:06:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    rhw-19269:       Infra, 00:24:C8:56:28:40, Freq 0 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    4425 7634:       Infra, 00:21:1E:5D:B1:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    fhw-35226:       Infra, 00:24:C8:6B:9B:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Sweet Lorraine:  Infra, 00:24:C9:60:22:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    fyn-21927:       Infra, 00:24:37:99:EF:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 33 WPA WPA2
    Schorsch:        Infra, C0:3F:0E:E8:66:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    GWP-36135:       Infra, 00:23:A3:85:AC:20, Freq 2447 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    amore:           Infra, 00:14:6C:D3:91:C4, Freq 2437 MHz, Rate 11 Mb/s, Strength 25 WEP
    NEW040511_wlan@thenet: Infra, 00:15:6D:7C:09:AB, Freq 2412 MHz, Rate 54 Mb/s, Strength 31
    The Matrix:      Infra, 00:0F:CC:30:99:00, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WEP
    wlan@thenet:     Infra, 00:16:B6:A4:03:A9, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    Underverse:      Infra, 00:0F:CC:08:67:CC, Freq 2442 MHz, Rate 54 Mb/s, Strength 29 WEP
    wlan@thenet:     Infra, 00:16:B6:A4:03:A6, Freq 2462 MHz, Rate 54 Mb/s, Strength 46
    Kosmos:          Infra, 00:24:C9:7B:4E:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ralphkienzi52:   Infra, 00:22:10:A2:3D:30, Freq 2447 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    reseau modele:   Infra, 00:0F:CC:B3:FE:EC, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WEP
    ZGO-57896:       Infra, 00:0F:CC:B8:11:D4, Freq 2457 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    NETGEAR:         Infra, 00:09:5B:FD:FC:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WEP
    7062 4130:       Infra, 00:23:A3:8E:58:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    da herz 3000:    Infra, 00:01:E3:EB:E3:C5, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WEP
    siriusb:         Infra, 00:0F:CC:F8:ED:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 23 WPA WPA2
    GiuseppinaNetz:  Infra, 00:0F:CC:B4:5F:D8, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    rider:           Infra, C0:3F:0E:84:47:B0, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    cdi-73377:       Infra, 64:87:D7:07:84:59, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    tfi-24119:       Infra, 00:24:C8:85:17:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    fbb-01363:       Infra, 00:24:93:02:8F:20, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    spinnefeind:     Infra, 00:22:B0:8F:A3:5B, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA
    7061 1100m:      Infra, 00:0F:CC:E3:1D:8C, Freq 2442 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    enm-01228:       Infra, 00:24:37:B0:BD:A0, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    AVS:             Infra, 00:22:B0:D3:42:6C, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
[/FONT][FONT=Courier New]
 [/FONT] **2) sudo lshw -C network**
  [FONT=Courier New]  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:2d:47:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:cffff000-cfffffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:19:8f:03
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.33 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:cfffe000-cfffefff ioport:cf00(size=64)

[/FONT]   **3) lspci**
[FONT=Courier New]00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
[/FONT]

**4) rfkill list all**
[FONT=Courier New]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/FONT]

**5) lsmod**[FONT=Courier New]
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ipw2200               145664  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
libipw                 46641  1 ipw2200
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 ipw2200,libipw
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14570  2 ipw2200,libipw
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
toshiba_acpi           13796  0 
sparse_keymap          13666  1 toshiba_acpi
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  450944  2 
drm_kms_helper         40745  1 i915
drm                   180037  2 i915,drm_kms_helper
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
crc_itu_t              12627  1 firewire_core[/FONT]

**6) sudo iwconfig**[FONT=Courier New]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"rhw-19269"  
          Mode:Managed  Channel:0  Access Point: 00:24:C8:56:28:40   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]

**7) sudo iwlist scan**
[FONT=Courier New]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:24:37:99:EF:40
                    ESSID:"fyn-21927"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2692ms ago
          Cell 02 - Address: 00:22:B0:D3:42:6C
                    ESSID:"AVS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 108ms ago
          Cell 03 - Address: 00:22:B0:8F:A3:5B
                    ESSID:"spinnefeind"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 112ms ago
          Cell 04 - Address: C0:3F:0E:84:47:B0
                    ESSID:"rider"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 452ms ago
          Cell 05 - Address: 00:24:37:B0:BD:A0
                    ESSID:"enm-01228"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 64ms ago
          Cell 06 - Address: 00:14:6C:D3:91:C4
                    ESSID:"amore"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 1868ms ago
          Cell 07 - Address: 00:24:C8:85:17:D0
                    ESSID:"tfi-24119"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 392ms ago
          Cell 08 - Address: 00:0F:CC:E3:1D:8C
                    ESSID:"7061 1100m"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 24ms ago
          Cell 09 - Address: 00:0F:CC:B4:5F:D8
                    ESSID:"GiuseppinaNetz"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2940ms ago
          Cell 10 - Address: 00:24:93:02:8F:20
                    ESSID:"fbb-01363"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 312ms ago
          Cell 11 - Address: 64:87:D7:07:84:59
                    ESSID:"cdi-73377"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 984ms ago
          Cell 12 - Address: 00:01:E3:EB:E3:C5
                    ESSID:"da herz 3000"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 1884ms ago
          Cell 13 - Address: 00:0F:B5:7A:4C:22
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 320ms ago
          Cell 14 - Address: 00:23:A3:8E:58:C0
                    ESSID:"7062 4130"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 16ms ago
          Cell 15 - Address: 00:24:C8:56:28:40
                    ESSID:"rhw-19269"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-58 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 260ms ago
                    Extra: Channel flags: INVALID 
          Cell 16 - Address: 00:09:5B:FD:FC:E4
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 240ms ago
          Cell 17 - Address: 00:0F:CC:B3:FE:EC
                    ESSID:"reseau modele"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 512ms ago
          Cell 18 - Address: 00:0F:CC:B8:11:D4
                    ESSID:"ZGO-57896"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 600ms ago
          Cell 19 - Address: 00:24:C9:7B:4E:C0
                    ESSID:"Kosmos"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8340ms ago
          Cell 20 - Address: 00:16:B6:A4:03:A6
                    ESSID:"wlan@thenet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 256ms ago
          Cell 21 - Address: 00:22:10:A2:3D:30
                    ESSID:"ralphkienzi52"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 320ms ago
          Cell 22 - Address: 00:15:6D:7C:09:AB
                    ESSID:"NEW040511_wlan@thenet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 496ms ago
          Cell 23 - Address: 00:16:B6:A4:03:A9
                    ESSID:"wlan@thenet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 4192ms ago
          Cell 24 - Address: 00:0F:CC:30:99:00
                    ESSID:"The Matrix"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 1836ms ago
          Cell 25 - Address: 00:1B:2F:E1:06:8E
                    ESSID:"Blume"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 7212ms ago
          Cell 26 - Address: C0:3F:0E:E8:66:C8
                    ESSID:"Schorsch"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1360ms ago
[/FONT]

---

### Post by Toz on 2011-05-30
A couple of things that I find interesting:

1. From iwlist:```
eth1 IEEE 802.11bg ESSID:"rhw-19269" 
Mode:Managed **Channel:0** Access Point: 00:24:C8:56:28:40 
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0 
Retry limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```AFAIK, channel 0 is not a valid channel. However,

And from iwlist:```
Cell 15 - Address: 00:24:C8:56:28:40
ESSID:"rhw-19269"
Protocol:IEEE 802.11bg
Mode:Master
**Channel:0**
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Quality=70/100 Signal level=-58 dBm 
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Extra: Last beacon: 260ms ago
Extra: Channel flags: INVALID 
```Channel is also 0. Is your router setup properly?

2. Also from the iwlist command above:```
Encryption key:on
``` whereas from iwconfig:```
Encryption key:off
```Have you setup the proper key authentication?

I would suggest power-cycling your router one more time and double-checking the settings, then re-setting up the connection with the same settings. Otherwise, you can try to set it up using ndiswrapper. Instructions located here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by tigerente on 2011-05-31
Toz, thank you for your prompt answer.

Yesterday I changed my channel in the router, restarted the router but not the computer with the result that I still couldn't use wireless. Today I started up my computer and everything was fine! 

*rhw-19269:      Infra, 00:24:C8:56:28:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2

It looks as though a reboot was needed to solve the problem.

Thank you very much for your help!

---

### Post by Toz on 2011-05-31
You're welcome. 
Can you please mark this thread as solved via the Thread Tools link above?
Thanks.

---

### Post by tigerente on 2011-05-31
The thread tools don't give me an option to mark this thread as solved? All I get is "Show Printable Version", "Email this Page" and "Subscribe to this Thread". Tejano09 opened the thread, does he have the option to mark the thread as solved?
(My, I feel stupid!!!)

---

### Post by Toz on 2011-05-31
Oops, my bad. You didn't start the thread. Only the thread owner can flag it as solved. We should wait to hear back from them if their problem is solved.

---

