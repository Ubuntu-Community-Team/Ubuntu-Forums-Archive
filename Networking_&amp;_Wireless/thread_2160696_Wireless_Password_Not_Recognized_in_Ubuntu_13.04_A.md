---
title: "Wireless Password Not Recognized in Ubuntu 13.04 ASUS A54C RaLink 5390"
date: 2013-07-07
forum: Networking &amp; Wireless
---

### Post by TheBookSmart on 2013-07-07
Hello Everyone,
I'm a Ubuntu newbie and would love to pick your brain on this problem. My laptop is Asus A54C with RaLink 5390 wireless card. It didn't have prior operating system and now is installed with Ubuntu 13.04 (32-bit). Upon installation, all available wifi networks (mine and neighbors') were recognized. Once I put in the password for my wifi network, it'd try to connect for a few seconds and then ask for the password again. The password is correct.

I tried to search in the forum but didn't find any thread with the same problem being discussed. So I was wondering if anybody would help me here.

In case you need the basic information, I'm posting the output from some commands here. Please let me know if you need anything else. Thank you very much!

-----------------------------

```
lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)  
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)




iwconfig
wlan0 IEEE 802.11bgn ESSID: off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: on
lo no wireless extensions.
eth0 no wireless extensions.





lsmod
Module Size Used by
ipt_MASQUERADE 12663 0
xt_state 12514 0
ipt_REJECT 12485 0
xt_tcpudp 12531 0
iptable_filter 12706 0
nf_nat_h323 12809 0
nf_conntrack_h323 51810 1 nf_nat_h323
nf_nat_pptp 12536 0
nf_nat_proto_gre 12671 1 nf_nat_pptp
nf_conntrack_pptp 13553 1 nf_nat_pptp
nf_conntrack_proto_gre 13538 1 nf_conntrack_pptp
nf_nat_tftp 12420 0
nf_conntrack_tftp 12790 1 nf_nat_tftp
nf_nat_sip 16971 0
nf_conntrack_sip 24582 1 nf_nat_sip
nf_nat_irc 12542 0
nf_conntrack_irc 13086 1 nf_nat_irc
nf_nat_ftp 12548 0
nf_conntrack_ftp 13118 1 nf_nat_ftp
iptable_nat 12706 0
nf_conntrack_ipv4 14071 1
nf_defrag_ipv4 12649 1 nf_conntrack_ipv4
nf_nat_ipv4 13095 1 iptable_nat
nf_nat 20857 10 nf_nat_ftp,nf_nat_irc,nf_nat_sip,ipt_MASQUERADE,nf_nat_proto_gre,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,iptable_nat
nf_conntrack 67003 19 nf_nat_ftp,nf_nat_irc,nf_nat_sip,nf_conntrack_proto_gre,ipt_MASQUERADE,nf_nat,xt_state,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,nf_conntrack_ftp,nf_conntrack_irc,nf_conntrack_sip,iptable_nat,nf_conntrack_h323,nf_conntrack_ipv4,nf_conntrack_pptp,nf_conntrack_tftp
ip_tables 17791 2 iptable_filter,iptable_nat
x_tables 21974 6 ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_state,iptable_filter,ipt_REJECT
parport_pc 27504 0
ppdev 12817 0
bnep 17669 2
rfcomm 37420 0
bluetooth 202069 10 bnep,rfcomm
arc4 12543 2
rt2800pci 18198 0
rt2800lib 60947 1 rt2800pci
rt2x00pci 14151 1 rt2800pci
rt2x00lib 48522 3 rt2x00pci,rt2800lib,rt2800pci
mac80211 526519 3 rt2x00lib,rt2x00pci,rt2800lib
uvcvideo 71279 0
videobuf2_vmalloc 12920 1 uvcvideo
videobuf2_memops 13042 1 videobuf2_vmalloc
videobuf2_core 39161 1 uvcvideo
joydev 17097 0
videodev 95806 2 uvcvideo,videobuf2_core
cfg80211 436177 2 mac80211,rt2x00lib
eeprom_93cx6 13168 1 rt2800pci
i915 535544 3
crc_ccitt 12627 1 rt2800lib
snd_hda_codec_hdmi 36185 1
snd_hda_codec_realtek 63791 1
snd_hda_intel 38307 6
snd_hda_codec 117580 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13272 1 snd_hda_codec
snd_pcm 80890 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc 14230 2 snd_pcm,snd_hda_intel
snd_seq_midi 13132 0
snd_seq_midi_event 14475 1 snd_seq_midi
snd_rawmidi 25114 1 snd_seq_midi
snd_seq 51280 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14137 3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper 47545 1 i915
snd_timer 24411 2 snd_pcm,snd_seq
drm 228489 4 i915,drm_kms_helper
snd 56485 22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse 81038 0
coretemp 13131 0
soundcore 12600 1 snd
asus_nb_wmi 12734 0
asus_wmi 23517 1 asus_nb_wmi
i2c_algo_bit 13197 1 i915
serio_raw 13031 0
sparse_keymap 13658 1 asus_wmi
microcode 18286 0
mei 36197 0
video 18894 2 i915,asus_wmi
lpc_ich 16925 0
wmi 18590 1 asus_wmi
mac_hid 13037 0
lp 13299 0
parport 40753 3 lp,ppdev,parport_pc
ahci 25507 2
libahci 26108 1 ahci
atl1c 36175 0
```

---

### Post by varunendra on 2013-07-08
Hello, and Welcome to the forums !

> **TheBookSmart said:**
> 
02:00.0 Network controller: Ralink corp. **RT5390** Wireless 802.11n 1T/1R PCIe

For beginners, please try -
```
sudo iwconfig wlan0 power off
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
Then try to connect and see if you can. If not, please download and run "wireless_script" as mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=12350385"), and post back the report it generates.

**PS:**
Please use code tags while posting outputs. It preserves the formatting and makes the post cleaner, easy to read. :)
Follow the "Code Tags example" link in my signature to see an elaborated example.

---

### Post by TheBookSmart on 2013-07-08
Thank you so much for replying, varunendra! the commands didn't work, so I run the wireless script like you mentioned. Here is the output:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


*************** info trace ***************

***** uname -a *****

Linux Alex 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks 

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt2800pci              18198  0 
rt2800lib              60947  1 rt2800pci
rt2x00pci              14151  1 rt2800pci
rt2x00lib              48522  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              526519  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              436177  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    soyo:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    4FB3D2:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Pardi Network:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Belkin.3A69:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"Belkin.3A69"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002eb4d5c19f
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000B42656C6B696E2E33413639
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060D0400000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100094445263DA691021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323130313647313132313530311054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"4FB3D2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008208de0424
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 0006344642334432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180206F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1
search Belkin

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   13.694062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.695330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  269.894286] wlan0: authenticate with <MAC address removed>
[  269.909708] wlan0: send auth to <MAC address removed> (try 1/3)
[  269.917526] wlan0: authenticated
[  269.921176] wlan0: associate with <MAC address removed> (try 1/3)
[  270.125155] wlan0: associate with <MAC address removed> (try 2/3)
[  270.329160] wlan0: associate with <MAC address removed> (try 3/3)
[  270.533154] wlan0: association with <MAC address removed> timed out
[  271.742394] wlan0: authenticate with <MAC address removed>
[  271.757497] wlan0: send auth to <MAC address removed> (try 1/3)
[  271.760785] wlan0: authenticated
[  271.761084] wlan0: associate with <MAC address removed> (try 1/3)
[  271.965107] wlan0: associate with <MAC address removed> (try 2/3)
[  272.169091] wlan0: associate with <MAC address removed> (try 3/3)
[  272.373093] wlan0: association with <MAC address removed> timed out
[  273.587626] wlan0: authenticate with <MAC address removed>
[  273.601457] wlan0: send auth to <MAC address removed> (try 1/3)
[  273.805050] wlan0: send auth to <MAC address removed> (try 2/3)
[  273.813701] wlan0: authenticated
[  273.817101] wlan0: associate with <MAC address removed> (try 1/3)
[  274.021064] wlan0: associate with <MAC address removed> (try 2/3)
[  274.225064] wlan0: associate with <MAC address removed> (try 3/3)
[  274.429061] wlan0: association with <MAC address removed> timed out
[  275.637781] wlan0: authenticate with <MAC address removed>
[  275.653803] wlan0: send auth to <MAC address removed> (try 1/3)
[  275.690090] wlan0: authenticated
[  275.693100] wlan0: associate with <MAC address removed> (try 1/3)
[  275.897015] wlan0: associate with <MAC address removed> (try 2/3)
[  276.101039] wlan0: associate with <MAC address removed> (try 3/3)
[  276.305024] wlan0: association with <MAC address removed> timed out
[  277.517659] wlan0: authenticate with <MAC address removed>
[  277.533304] wlan0: send auth to <MAC address removed> (try 1/3)
[  277.537511] wlan0: authenticated
[  277.541003] wlan0: associate with <MAC address removed> (try 1/3)
[  277.745021] wlan0: associate with <MAC address removed> (try 2/3)
[  277.949030] wlan0: associate with <MAC address removed> (try 3/3)
[  278.153030] wlan0: association with <MAC address removed> timed out
[  279.361414] wlan0: authenticate with <MAC address removed>
[  279.377457] wlan0: send auth to <MAC address removed> (try 1/3)
[  279.381658] wlan0: authenticated
[  279.385100] wlan0: associate with <MAC address removed> (try 1/3)
[  279.589039] wlan0: associate with <MAC address removed> (try 2/3)
[  279.793031] wlan0: associate with <MAC address removed> (try 3/3)
[  279.996991] wlan0: association with <MAC address removed> timed out
[  281.205507] wlan0: authenticate with <MAC address removed>
[  281.221503] wlan0: send auth to <MAC address removed> (try 1/3)
[  281.226012] wlan0: authenticated
[  281.228955] wlan0: associate with <MAC address removed> (try 1/3)
[  281.432958] wlan0: associate with <MAC address removed> (try 2/3)
[  281.637045] wlan0: associate with <MAC address removed> (try 3/3)
[  281.840972] wlan0: association with <MAC address removed> timed out
[  283.051530] wlan0: authenticate with <MAC address removed>
[  283.065316] wlan0: send auth to <MAC address removed> (try 1/3)
[  283.067673] wlan0: authenticated
[  283.068978] wlan0: associate with <MAC address removed> (try 1/3)
[  283.272949] wlan0: associate with <MAC address removed> (try 2/3)
[  283.476989] wlan0: associate with <MAC address removed> (try 3/3)
[  283.680988] wlan0: association with <MAC address removed> timed out
[  284.889889] wlan0: authenticate with <MAC address removed>
[  284.905504] wlan0: send auth to <MAC address removed> (try 1/3)
[  285.108939] wlan0: send auth to <MAC address removed> (try 2/3)
[  285.110458] wlan0: authenticated
[  285.112944] wlan0: associate with <MAC address removed> (try 1/3)
[  285.316937] wlan0: associate with <MAC address removed> (try 2/3)
[  285.520893] wlan0: associate with <MAC address removed> (try 3/3)
[  285.724897] wlan0: association with <MAC address removed> timed out
[  286.933778] wlan0: authenticate with <MAC address removed>
[  286.949385] wlan0: send auth to <MAC address removed> (try 1/3)
[  286.951767] wlan0: authenticated
[  286.952913] wlan0: associate with <MAC address removed> (try 1/3)
[  287.156901] wlan0: associate with <MAC address removed> (try 2/3)
[  287.360894] wlan0: associate with <MAC address removed> (try 3/3)
[  287.564913] wlan0: association with <MAC address removed> timed out
[  288.773889] wlan0: authenticate with <MAC address removed>
[  288.789456] wlan0: send auth to <MAC address removed> (try 1/3)
[  288.791832] wlan0: authenticated
[  288.792925] wlan0: associate with <MAC address removed> (try 1/3)
[  288.996890] wlan0: associate with <MAC address removed> (try 2/3)
[  289.200923] wlan0: associate with <MAC address removed> (try 3/3)
[  289.404881] wlan0: association with <MAC address removed> timed out
[  290.613791] wlan0: authenticate with <MAC address removed>
[  290.629598] wlan0: send auth to <MAC address removed> (try 1/3)
[  290.631156] wlan0: authenticated
[  290.632893] wlan0: associate with <MAC address removed> (try 1/3)
[  290.836854] wlan0: associate with <MAC address removed> (try 2/3)
[  291.040886] wlan0: associate with <MAC address removed> (try 3/3)
[  291.244879] wlan0: association with <MAC address removed> timed out
[  292.453718] wlan0: authenticate with <MAC address removed>
[  292.469292] wlan0: send auth to <MAC address removed> (try 1/3)
[  292.475438] wlan0: authenticated
[  292.476875] wlan0: associate with <MAC address removed> (try 1/3)
[  292.680861] wlan0: associate with <MAC address removed> (try 2/3)
[  292.884868] wlan0: associate with <MAC address removed> (try 3/3)
[  293.088862] wlan0: association with <MAC address removed> timed out
[  301.753682] wlan0: authenticate with <MAC address removed>
[  301.769248] wlan0: send auth to <MAC address removed> (try 1/3)
[  301.770755] wlan0: authenticated
[  301.772752] wlan0: associate with <MAC address removed> (try 1/3)
[  301.976745] wlan0: associate with <MAC address removed> (try 2/3)
[  302.180742] wlan0: associate with <MAC address removed> (try 3/3)
[  302.384743] wlan0: association with <MAC address removed> timed out
[  303.593654] wlan0: authenticate with <MAC address removed>
[  303.609470] wlan0: send auth to <MAC address removed> (try 1/3)
[  303.812683] wlan0: send auth to <MAC address removed> (try 2/3)
[  303.814329] wlan0: authenticated
[  303.816690] wlan0: associate with <MAC address removed> (try 1/3)
[  304.020747] wlan0: associate with <MAC address removed> (try 2/3)
[  304.224673] wlan0: associate with <MAC address removed> (try 3/3)
[  304.428672] wlan0: association with <MAC address removed> timed out
[  305.639194] wlan0: authenticate with <MAC address removed>
[  305.653342] wlan0: send auth to <MAC address removed> (try 1/3)
[  305.657577] wlan0: authenticated
[  305.660681] wlan0: associate with <MAC address removed> (try 1/3)
[  305.864687] wlan0: associate with <MAC address removed> (try 2/3)
[  306.068692] wlan0: associate with <MAC address removed> (try 3/3)
[  306.272680] wlan0: association with <MAC address removed> timed out
[  307.481602] wlan0: authenticate with <MAC address removed>
[  307.497099] wlan0: send auth to <MAC address removed> (try 1/3)
[  307.499495] wlan0: authenticated
[  307.500641] wlan0: associate with <MAC address removed> (try 1/3)
[  307.704625] wlan0: associate with <MAC address removed> (try 2/3)
[  307.908660] wlan0: associate with <MAC address removed> (try 3/3)
[  307.922777] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  307.922887] wlan0: associated
[  307.922948] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  317.924432] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  317.957999] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  320.061443] wlan0: authenticate with <MAC address removed>
[  320.077036] wlan0: send auth to <MAC address removed> (try 1/3)
[  320.082274] wlan0: authenticated
[  320.084457] wlan0: associate with <MAC address removed> (try 1/3)
[  320.288505] wlan0: associate with <MAC address removed> (try 2/3)
[  320.492503] wlan0: associate with <MAC address removed> (try 3/3)
[  320.696515] wlan0: association with <MAC address removed> timed out
[  321.905396] wlan0: authenticate with <MAC address removed>
[  321.920813] wlan0: send auth to <MAC address removed> (try 1/3)
[  321.927053] wlan0: authenticated
[  321.928509] wlan0: associate with <MAC address removed> (try 1/3)
[  322.132485] wlan0: associate with <MAC address removed> (try 2/3)
[  322.336476] wlan0: associate with <MAC address removed> (try 3/3)
[  322.540478] wlan0: association with <MAC address removed> timed out
[  323.749261] wlan0: authenticate with <MAC address removed>
[  323.765017] wlan0: send auth to <MAC address removed> (try 1/3)
[  323.771261] wlan0: authenticated
[  323.772418] wlan0: associate with <MAC address removed> (try 1/3)
[  323.976399] wlan0: associate with <MAC address removed> (try 2/3)
[  324.180394] wlan0: associate with <MAC address removed> (try 3/3)
[  324.384442] wlan0: association with <MAC address removed> timed out
[  325.593173] wlan0: authenticate with <MAC address removed>
[  325.608653] wlan0: send auth to <MAC address removed> (try 1/3)
[  325.610134] wlan0: authenticated
[  325.612419] wlan0: associate with <MAC address removed> (try 1/3)
[  325.816400] wlan0: associate with <MAC address removed> (try 2/3)
[  326.020645] wlan0: associate with <MAC address removed> (try 3/3)
[  326.224370] wlan0: association with <MAC address removed> timed out
[  334.188811] wlan0: authenticate with <MAC address removed>
[  334.204733] wlan0: send auth to <MAC address removed> (try 1/3)
[  334.210901] wlan0: authenticated
[  334.212295] wlan0: associate with <MAC address removed> (try 1/3)
[  334.416286] wlan0: associate with <MAC address removed> (try 2/3)
[  334.620282] wlan0: associate with <MAC address removed> (try 3/3)
[  334.824280] wlan0: association with <MAC address removed> timed out
[  336.033160] wlan0: authenticate with <MAC address removed>
[  336.048691] wlan0: send auth to <MAC address removed> (try 1/3)
[  336.050230] wlan0: authenticated
[  336.052297] wlan0: associate with <MAC address removed> (try 1/3)
[  336.256291] wlan0: associate with <MAC address removed> (try 2/3)
[  336.460294] wlan0: associate with <MAC address removed> (try 3/3)
[  336.664284] wlan0: association with <MAC address removed> timed out
[  337.873175] wlan0: authenticate with <MAC address removed>
[  337.888813] wlan0: send auth to <MAC address removed> (try 1/3)
[  337.891263] wlan0: authenticated
[  337.892269] wlan0: associate with <MAC address removed> (try 1/3)
[  338.096226] wlan0: associate with <MAC address removed> (try 2/3)
[  338.300270] wlan0: associate with <MAC address removed> (try 3/3)
[  338.504214] wlan0: association with <MAC address removed> timed out
[  339.713067] wlan0: authenticate with <MAC address removed>
[  339.728888] wlan0: send auth to <MAC address removed> (try 1/3)
[  339.731340] wlan0: authenticated
[  339.732220] wlan0: associate with <MAC address removed> (try 1/3)
[  339.936250] wlan0: associate with <MAC address removed> (try 2/3)
[  340.140240] wlan0: associate with <MAC address removed> (try 3/3)
[  340.344183] wlan0: association with <MAC address removed> timed out
[  341.553127] wlan0: authenticate with <MAC address removed>
[  341.568689] wlan0: send auth to <MAC address removed> (try 1/3)
[  341.572960] wlan0: authenticated
[  341.576201] wlan0: associate with <MAC address removed> (try 1/3)
[  341.780196] wlan0: associate with <MAC address removed> (try 2/3)
[  341.984224] wlan0: associate with <MAC address removed> (try 3/3)
[  342.188175] wlan0: association with <MAC address removed> timed out
[  343.401065] wlan0: authenticate with <MAC address removed>
[  343.416836] wlan0: send auth to <MAC address removed> (try 1/3)
[  343.620194] wlan0: send auth to <MAC address removed> (try 2/3)
[  343.624334] wlan0: authenticated
[  343.628196] wlan0: associate with <MAC address removed> (try 1/3)
[  343.832151] wlan0: associate with <MAC address removed> (try 2/3)
[  344.036160] wlan0: associate with <MAC address removed> (try 3/3)
[  344.240188] wlan0: association with <MAC address removed> timed out
[  345.450720] wlan0: authenticate with <MAC address removed>
[  345.464813] wlan0: send auth to <MAC address removed> (try 1/3)
[  345.466334] wlan0: authenticated
[  345.468188] wlan0: associate with <MAC address removed> (try 1/3)
[  345.672167] wlan0: associate with <MAC address removed> (try 2/3)
[  345.876164] wlan0: associate with <MAC address removed> (try 3/3)
[  346.080162] wlan0: association with <MAC address removed> timed out
[  347.289073] wlan0: authenticate with <MAC address removed>
[  347.304806] wlan0: send auth to <MAC address removed> (try 1/3)
[  347.306536] wlan0: authenticated
[  347.312105] wlan0: associate with <MAC address removed> (try 1/3)
[  347.516106] wlan0: associate with <MAC address removed> (try 2/3)
[  347.720113] wlan0: associate with <MAC address removed> (try 3/3)
[  347.924120] wlan0: association with <MAC address removed> timed out
[  349.138692] wlan0: authenticate with <MAC address removed>
[  349.152717] wlan0: send auth to <MAC address removed> (try 1/3)
[  349.154228] wlan0: authenticated
[  349.156133] wlan0: associate with <MAC address removed> (try 1/3)
[  349.360119] wlan0: associate with <MAC address removed> (try 2/3)
[  349.564117] wlan0: associate with <MAC address removed> (try 3/3)
[  349.768067] wlan0: association with <MAC address removed> timed out
[  350.977113] wlan0: authenticate with <MAC address removed>
[  350.992636] wlan0: send auth to <MAC address removed> (try 1/3)
[  350.996967] wlan0: authenticated
[  351.000083] wlan0: associate with <MAC address removed> (try 1/3)
[  351.204103] wlan0: associate with <MAC address removed> (try 2/3)
[  351.408100] wlan0: associate with <MAC address removed> (try 3/3)
[  351.612044] wlan0: association with <MAC address removed> timed out
[  352.824932] wlan0: authenticate with <MAC address removed>
[  352.840608] wlan0: send auth to <MAC address removed> (try 1/3)
[  352.844781] wlan0: authenticated
[  352.848050] wlan0: associate with <MAC address removed> (try 1/3)
[  353.052041] wlan0: associate with <MAC address removed> (try 2/3)
[  353.256013] wlan0: associate with <MAC address removed> (try 3/3)
[  353.460019] wlan0: association with <MAC address removed> timed out
[  354.669030] wlan0: authenticate with <MAC address removed>
[  354.684509] wlan0: send auth to <MAC address removed> (try 1/3)
[  354.686016] wlan0: authenticated
[  354.688191] wlan0: associate with <MAC address removed> (try 1/3)
[  354.892013] wlan0: associate with <MAC address removed> (try 2/3)
[  355.096047] wlan0: associate with <MAC address removed> (try 3/3)
[  355.300040] wlan0: association with <MAC address removed> timed out
[  356.508964] wlan0: authenticate with <MAC address removed>
[  356.524537] wlan0: send auth to <MAC address removed> (try 1/3)
[  356.728024] wlan0: send auth to <MAC address removed> (try 2/3)
[  356.729596] wlan0: authenticated
[  356.731991] wlan0: associate with <MAC address removed> (try 1/3)
[  356.935975] wlan0: associate with <MAC address removed> (try 2/3)
[  357.139963] wlan0: associate with <MAC address removed> (try 3/3)
[  357.344014] wlan0: association with <MAC address removed> timed out

****************** done ******************

---

### Post by varunendra on 2013-07-08
Uh-oh, please use code tags, else your outputs will keep turning into smileys ;) (read the "PS" part of my previous post again, then edit your above post to add the tags).

About your issue -

Are you sure the password box is asking for your wireless password and not your user password (the one you use for login or with "sudo")? Try saving your wireless password and correct encryption type in Network Manager settings (nm-applet in the top-right corner of the screen > Edit Connections > Wireless tab > double-click your connection > goto Security tab > enter and save relevant settings), then see if it still asks for password.

If that doesn't help, then another thing to try -
> **TheBookSmart said:**
> 
  Wireless Access Points 
    soyo:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    **4FB3D2**:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
    Pardi Network:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    **Belkin.3A69**:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**

Which is/are your access-point(s) above? If they are one with WPA/WPA2 mixed mode, it is strongly recommended to change that setting in router/access-point to pure WPA2-PSK with AES encryption. No mixed mode, no TKIP.

With (or without) that change, please try -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
The above one is a temporary change and will be lost at reboot. If it helps, we'll make it permanent.

---

### Post by TheBookSmart on 2013-07-08
Darn it! I'm so sorry! I read your code tag tip and thought that, by replying through "adv reply", the format wouldn't be changed. Sorry! Will use code tag in the future.

The password being asked for is the password for wifi. It's saved in the system. Once it pops up the wifi password box with the password pre-filled, I click on "connect", it'll try to connect and then after a while, it'll pop up the wifi password box again, with the password pre-filled. The same thing just goes on and on...

My access point is Belkin.3A69. All the other networks are neighbors'. I checked the setting in my router. The authentication mode is WPA-PSK+WPA2-PSK, so I changed it to WPA2-PSK. Encryption remains AES.

I did run the codes sudo modprobe codes as you advised. It didn't work. The problem persists.

---

### Post by TheBookSmart on 2013-07-08
HA! Fixed it! I was reading old posts with a similar problem but on a different wireless card. Someone's saying to turn off the wireless N in the router. I just figured "what the heck, why not!" Turned it off, the wireless got connected! Yipeeeeee!

---

### Post by TheBookSmart on 2013-07-08
Thank you so much, varunendra! It makes newbies like me feel so hopeful with people like you helping us in the community! Rock on!

---

