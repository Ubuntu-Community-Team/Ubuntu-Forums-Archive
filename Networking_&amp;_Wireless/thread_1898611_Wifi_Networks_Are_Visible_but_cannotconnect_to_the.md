---
title: "Wifi Networks Are Visible but cannotconnect to them .. Help?"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by reloaded1212 on 2011-12-21
Hey everyone, I can see all the wifi networks around me on my Xubuntu 11.04-loaded laptop, but i can't connect to them. I have tried to set a static IP address for the wifi network, and while i do get connected to the wifi then, i cant browse the internet.

Any suggestions?? 

Thanks,
Reloaded1212

EDIT: It is version 11.10, my mistake

---

### Post by reloaded1212 on 2011-12-21
Also I am new in Linux, please go easy on me :X

---

### Post by wildmanne39 on 2011-12-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by reloaded1212 on 2011-12-21
Hi thanks for going easy on me, it really helps :)

This is what I got:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux albert-Evo-N1020v 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 20)
    Subsystem: Compaq Computer Corporation Device [0e11:0056]
    Kernel driver in use: 8139cp

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
albert@albert-Evo-N1020v:~$ lsmod
Module                  Size  Used by
binfmt_misc            17292  1 
joydev                 17393  0 
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
ppdev                  12849  0 
arc4                   12473  2 
rt2500usb              22652  0 
rt2x00usb              20092  1 rt2500usb
rt2x00lib              48114  2 rt2500usb,rt2x00usb
mac80211              393459  2 rt2x00usb,rt2x00lib
orinoco_usb            26599  0 
orinoco                70112  1 orinoco_usb
cfg80211              172392  3 rt2x00lib,mac80211,orinoco
psmouse                73673  0 
serio_raw              12990  0 
snd_ali5451            23459  3 
radeon                925193  2 
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
i2c_ali15x3            12878  0 
ip6t_LOG               16846  4 
i2c_ali1535            12777  0 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd_rawmidi            25241  1 snd_seq_midi
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
ipt_REJECT             12512  1 
pcmcia                 39822  0 
parport_pc             32114  1 
video                  18908  0 
ipt_LOG                12783  5 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   192194  4 radeon,ttm,drm_kms_helper
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
xt_state               12514  14 
yenta_socket           27428  0 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
pcmcia_rsrc            18367  1 yenta_socket
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
i2c_algo_bit           13199  1 radeon
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  1 snd_pcm
shpchp                 32356  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
pata_ali               13562  2 
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 
```

This is what I got, if it is wrong, tell me what I did  so I can improve it 

Thanks a lot!

---

### Post by wildmanne39 on 2011-12-21
Hi, okay it looks like you have an usb wireless adapter so I will need to see the output of:
```
lsusb
```
plus
```
nm-tool
```
```
sudo iwlist scan
```
for the command with sudo you will need to enter your user password , it will not be shown in the terminal so when you are done typing it just hit enter.

Do you also have an internal card? that is what it looks like but it must be an old one from the driver it is using.
Thanks

---

### Post by reloaded1212 on 2011-12-21
Lsusb Output:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. AirPlus G DWL-G122 Wireless Adapter(rev.B1) [Ralink RT2500USB]
Bus 002 Device 002: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200

```

(you are right, I have a built-in Wifi card called the WLan MultiPort that came with my Compaq Evo N1020V laptop)

Nm-Tool Ouput:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. AirPlus G DWL-G122 Wireless Adapter(rev.B1) [Ralink RT2500USB]
Bus 002 Device 002: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200

```

Sudo Iwlist Scan Output:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:56:77:28:B1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BELL366"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e1265f7181
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 000742454C4C333636
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:13:F7:01:3F:66
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043077abf82
                    Extra: Last beacon: 1016ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 78:CD:8E:C5:FC:12
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000035deaf6e78f
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010013127A
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: 78:CD:8E:C5:FC:11
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"rogers11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000035deaf61edb
                    Extra: Last beacon: 468ms ago
                    IE: Unknown: 0008726F676572733131
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010013127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
          Cell 05 - Address: 00:23:69:E3:FD:0E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Mainiacs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000041bc20d80
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 00084D61696E69616373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080800000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A000110104400010210470010002369FFFFFFE3FFFFFFFD0F00000000103C000103

```

Thanks again for all the help. :)

---

### Post by reloaded1212 on 2011-12-21
Sorry I pasted the wrong output for Nm-Tool ..

Here is what it is:

```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139cp
  State:             connected
  Default:           yes
  HW Address:        00:0B:CD:5E:2F:D8

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             209.197.128.2
    DNS:             209.195.95.95


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
  State:             disconnected
  Default:           no
  HW Address:        00:13:46:E4:A6:84

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR:         Infra, 00:0F:B5:69:64:04, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WEP
    Mainiacs:        Infra, 00:23:69:E3:FD:0E, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    BELL366:         Infra, 00:24:56:77:28:B1, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WEP
    rogers11:        Infra, 78:CD:8E:C5:FC:11, Freq 2457 MHz, Rate 54 Mb/s, Strength 32 WPA
    SMC:             Infra, 00:13:F7:01:3F:66, Freq 2417 MHz, Rate 54 Mb/s, Strength 65

```

---

### Post by wildmanne39 on 2011-12-21
Hi, which network do you want to connect too?

Please post output of:
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by reloaded1212 on 2011-12-21
Hey again, I am trying to connect to the SMC network, that is my Home one .. 
Output is:

```
Dec 21 19:58:56 albert-Evo-N1020v wpa_supplicant[1703]: CTRL-EVENT-CONNECTED - Connection to 00:13:f7:01:3f:66 completed (reauth) [id=0 id_str=]
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): supplicant interface state: associating -> completed
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SMC'.
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <error> [1324515536.987257] [nm-device.c:1784] dhcp6_start(): (wlan0): failed to add IPv6 multicast route: Object not found
Dec 21 19:58:56 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Dec 21 19:58:57 albert-Evo-N1020v NetworkManager[613]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 21 19:58:57 albert-Evo-N1020v dhclient: Listening on LPF/wlan0/00:13:46:e4:a6:84
Dec 21 19:58:57 albert-Evo-N1020v dhclient: Sending on   LPF/wlan0/00:13:46:e4:a6:84
Dec 21 19:58:57 albert-Evo-N1020v dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec 21 19:58:57 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 21 19:58:57 albert-Evo-N1020v dhclient: Listening on Socket/wlan0
Dec 21 19:58:57 albert-Evo-N1020v dhclient: Sending on   Socket/wlan0
Dec 21 19:58:57 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): DHCPv6 state changed nbi -> preinit6
Dec 21 19:58:57 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 1040ms.
Dec 21 19:58:58 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 2130ms.
Dec 21 19:59:00 albert-Evo-N1020v dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 21 19:59:00 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 4460ms.
Dec 21 19:59:00 albert-Evo-N1020v kernel: [ 4029.112082] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:00 albert-Evo-N1020v kernel: [ 4029.112095] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:04 albert-Evo-N1020v kernel: [ 4033.052310] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:04 albert-Evo-N1020v kernel: [ 4033.052322] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:04 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 9100ms.
Dec 21 19:59:06 albert-Evo-N1020v dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 21 19:59:08 albert-Evo-N1020v kernel: [ 4037.040075] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:08 albert-Evo-N1020v kernel: [ 4037.040088] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:11 albert-Evo-N1020v dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Dec 21 19:59:12 albert-Evo-N1020v kernel: [ 4040.876062] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:12 albert-Evo-N1020v kernel: [ 4040.876074] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:13 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 18570ms.
Dec 21 19:59:16 albert-Evo-N1020v kernel: [ 4044.724124] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:16 albert-Evo-N1020v kernel: [ 4044.724137] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:20 albert-Evo-N1020v kernel: [ 4048.560110] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:20 albert-Evo-N1020v kernel: [ 4048.560123] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:23 albert-Evo-N1020v kernel: [ 4052.396118] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:23 albert-Evo-N1020v kernel: [ 4052.396131] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:26 albert-Evo-N1020v dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Dec 21 19:59:27 albert-Evo-N1020v kernel: [ 4056.232181] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:27 albert-Evo-N1020v kernel: [ 4056.232194] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:31 albert-Evo-N1020v kernel: [ 4060.068086] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:31 albert-Evo-N1020v kernel: [ 4060.068099] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.
Dec 21 19:59:32 albert-Evo-N1020v dhclient: XMT: Solicit on wlan0, interval 36340ms.
Dec 21 19:59:35 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): device state change: ip-config -> disconnected (reason 'user-requested') [70 30 39]
Dec 21 19:59:35 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Dec 21 19:59:35 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 7158
Dec 21 19:59:35 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 7159
Dec 21 19:59:35 albert-Evo-N1020v kernel: [ 4063.736945] wlan0: deauthenticating from 00:13:f7:01:3f:66 by local choice (reason=3)
Dec 21 19:59:35 albert-Evo-N1020v wpa_supplicant[1703]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Dec 21 19:59:35 albert-Evo-N1020v NetworkManager[613]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 21 19:59:35 albert-Evo-N1020v kernel: [ 4063.912068] phy1 -> rt2500usb_set_device_state: Error - Device failed to enter state 3 (-16).
Dec 21 19:59:35 albert-Evo-N1020v kernel: [ 4063.912081] phy1 -> rt2x00lib_autowakeup: Error - Device failed to wakeup.

```

Thanks again for the help

---

### Post by wildmanne39 on 2011-12-21
Hi, please post the output of:
```
ps aux | grep nm-apple
```
```
ps aux | egrep 'Network|wicd'
```

Are you using wicd instead of network manager?
Thanks

---

### Post by reloaded1212 on 2011-12-21
As far as I know, I have both on my system. Would that affect my Internet connections?

Output of first one:

```
albert    1459  0.3  1.3 237816 13028 ?        Sl   18:52   0:24 nm-applet
albert    8907  0.0  0.0   5412   784 pts/0    S+   21:03   0:00 grep --color=auto nm-apple

```

Output of second one:

```
root       613  0.0  0.4  26900  4680 ?        Ssl  18:52   0:02 NetworkManager
root       905  0.1  0.6  24180  6228 ?        S    18:52   0:13 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root      1001  0.0  0.7  14692  7708 ?        S    18:52   0:06 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
albert    1466  0.0  1.8  37832 18108 ?        S    18:52   0:00 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py
root      1741  0.0  0.0   2736   416 ?        Ss   18:53   0:00 /sbin/dhclient -v -cf /var/lib/wicd/dhclient.conf eth0
root      2021  0.0  0.1   2736  1220 ?        S    18:55   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-2d1d3b8e-077e-49c7-8aef-7d45425ff3b9-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

```

Again thanks for the support

---

### Post by wildmanne39 on 2011-12-21
Hi, yes you can only have one installed.

Do you want a static ip or is that just something you tried?

If it is ok let's get rid of wicd and see what happens just open software center and remove everything that says wicd then reboot and see if it comes on and it is best to unplug your wired connection first because it will over ride the wireless connection.
Thanks

---

### Post by reloaded1212 on 2011-12-21
I just tried the static IP to see if it would connect, all my other computers use a dynamic IP (even this laptop had a dynamic IP on Windows 7).

I will try uninstalling wicd now and see what happens..

---

### Post by wildmanne39 on 2011-12-21
Hi, also if you manually setup your wireless in network manager remove the connection not network manager and when ubuntu boots back up it should find it itself.
Thanks

---

### Post by reloaded1212 on 2011-12-21
Sorry to bother you , but I recall in a different tutorial that I was to blacklist my current driver (rt2500usb). Now because of that my Internet won't work; basically, how do I un blacklist a driver?

Thanks again

---

### Post by wildmanne39 on 2011-12-21
Hi, the driver is loading so it is not blacklisted when you tried to blacklist it it must have failed, also it would not see any networks if it was blacklisted unless the internal card is the one seeing the networks.
Thanks

---

### Post by reloaded1212 on 2011-12-21
The thing is, I think by restarting my computer when you told me to do it, it blacklisted the driver  =S

I can do another Terminal output, to check, but which command is it?

EDIT: I can confirm that it isn't working, the lights on my USB Wifi adapter are not blinking anymore.

---

### Post by wildmanne39 on 2011-12-21
Hi, okay please post the output of:
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
removing wicd should not have caused that sometimes you have to unplug your usb adapter and plug it back in.
Thanks

---

### Post by reloaded1212 on 2011-12-21
Lsmod Output:

```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
binfmt_misc            17292  1 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
snd_ali5451            23459  3 
snd_ac97_codec        106082  1 snd_ali5451
radeon                925193  2 
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
orinoco_usb            26599  0 
orinoco                70112  1 orinoco_usb
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_ali5451,snd_ac97_codec
cfg80211              172392  1 orinoco
joydev                 17393  0 
ttm                    65224  1 radeon
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         32889  1 radeon
ppdev                  12849  0 
drm                   192194  4 radeon,ttm,drm_kms_helper
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
evbug                  12581  0 
serio_raw              12990  0 
i2c_algo_bit           13199  1 radeon
snd                    55902  13 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3            12878  0 
pcspkr                 12614  0 
pcmcia                 39822  0 
parport_pc             32114  1 
video                  18908  0 
i2c_ali1535            12777  0 
yenta_socket           27428  0 
soundcore              12600  1 snd
snd_page_alloc         14115  1 snd_pcm
shpchp                 32356  0 
pcmcia_rsrc            18367  1 yenta_socket
ati_agp                13242  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
pata_ali               13562  2 
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
floppy                 60310  0
```

I think I blacklisted the driver before starting this thread, then by removing Wicd and rebooting Ubuntu, blacklisting it actually removed the driver. And I tried unplugging the USB adapter and plugging it back in, Ubuntu still does not recognize it. :(

---

### Post by reloaded1212 on 2011-12-21
Also by typing in the second command, it just leaves a blank line on my Terminal window and back to the command prompt :(

Thanks for the help

---

### Post by wildmanne39 on 2011-12-21
Hi, that command is suppose to show all blacklist files and I double checked it works so that is strange, did you just copy and paste the command? you might try it again.

Also your internal card drivers are still loaded that maybe preventing the usb drivers from loading now try this please:
```
sudo rmmod -f orinoco_usb
sudo modprobe rt2500usb
```
Thanks

---

### Post by reloaded1212 on 2011-12-21
The command is still not giving any response, even with Sudo at the front of it, even if I do not copy and paste it.

Output of first code:

```
ERROR: Removing 'orinoco_usb': No such file or directory
```

Output of second code:

```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

Ok I don't know how, but somehow, typing in that command activated my USB wifi adapter again, and it is "running" now, but still does not connect to any of my WiFi networks.

Thanks for the help

---

### Post by reloaded1212 on 2011-12-21
I will continue this in the morning, it is getting late now..Thanks again for all your support :)

---

### Post by wildmanne39 on 2011-12-22
Hi, that is what one of the commands I gave you was suppose to do and you are right I am to tired to think right myself so see you tomorrow.
Thanks

---

### Post by reloaded1212 on 2011-12-22
Well ok, so I did that command again, because rt2500usb does not automatically start by its self, anything else I should try to unblacklist the driver?

Thanks

EDIT: Since I have a built in card, I believe that it is conflicting with my USB WiFi adapter .. Can u tell me a way to blacklist the built-in one, and un-blacklist the USB one?

---

### Post by wildmanne39 on 2011-12-22
Hi, I believe that is possible too, but I have seen where the usb adapter would not connect without the internal one working, that is what I was testing in post 21 but I think I tried to remove the wrong driver.

This is how you can remove a blacklisted driver.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Then remove the driver you want from the list and add this I believe:
```
blacklist orinoco
```
Thanks

---

### Post by reloaded1212 on 2011-12-23
Thanks for helping me again, when I try to use the first code, the terminal window seems to load for a bit and returns no output. I don't know if that is supposed to happen, but thats what it did ... as for the second code, when I try to blacklist it, this is what it returns:

```
blacklist: command not found

```

Do I have to install something to use the blacklist command?

Thanks for the continued support.

---

### Post by wildmanne39 on 2011-12-23
Hi, no you do not just open the file as described in my last post and blacklist orinoco.

Does this open a window that asks for your password then after you enter it a file should open that says it is the blacklist file if not you must have a corrupt system.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

Thanks

---

### Post by reloaded1212 on 2011-12-24
Yeah, when I try that command, a new window opens asking for my password, then it sends me to the terminal window. No blacklist file is opened...Does this mean my system is corrupt? Is there any fix to this besides reinstalling Ubuntu again?

Thanks

---

### Post by wildmanne39 on 2011-12-24
Hi, there may be, did you remove your blacklist file or move it to a new location by running commands you have seen on here? 
Thanks

---

### Post by reloaded1212 on 2011-12-24
Nope the blacklist file is still in the original location, it has not been moved or deleted .. 
/etc/modprobe.d/blacklist

Oh yes, I will be away for Christmas, so you will not here from me for a couple of days, till Thursday :(

Merry Christmas!

---

### Post by reloaded1212 on 2011-12-29
Well then does this mean that my Ubuntu may be corrupt? If so, I can just stick to using a cable for now.

Thanks

---

### Post by wildmanne39 on 2011-12-29
Hi, no it means I made a mistake, you are using xubuntu and the command needs to be different because xubuntu does not use gedit here is the command and I am sorry I did not catch it until now.
```
gksu leafpad /etc/modprobe.d/blacklist.conf
```
Then follow the directions in my previous post.
Thanks

---

### Post by reloaded1212 on 2011-12-31
Haha thanks for the help again. The file opened this time, and it was completely empty, so i added "blacklist orionoco" to it. 

However, "blacklist rt2500usb" is not there yet my USB wifi adapter still does not run unless I use the modprobe command.

After activating it with the modprobe command, my WiFi still does not connect to my network unless I use a static IP address. Then, it will show up as connected to my network (SMC) but I cannot browse the Internet still. :(

Any ideas?

Thanks again

---

### Post by wildmanne39 on 2011-12-31
Hi, if you blacklisted rt2500usb you need to unblacklist it if you did not then run this command to make it start automatically.
```
sudo su 
echo rt2500usb >> /etc/modules 
exit
```
I think this will make it connect.
```
gksudo leafpad /etc/modprobe.d/rt2500usb.conf
```
Add a single line:
```
options rt2500usb nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by davidafranklin on 2011-12-31
Hello,I have the same problem.I have an old laptop.My wireless card is thru the pcmcia port.I can see the wireless networks but cannot connect. Here is what I have:


davidafranklin@compaq:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux compaq 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
davidafranklin@compaq:~$ lspci -nnk | grep -iA2 net
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Kernel driver in use: 8139too
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
	Kernel driver in use: rtl8180
davidafranklin@compaq:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
davidafranklin@compaq:~$ rfkill list all
The program 'rfkill' is currently not installed.  You can install it by typing:
sudo apt-get install rfkill


Thanks for any help!

---

### Post by wildmanne39 on 2012-01-01
Hi davidafranklin, your card should work in 11.10 so please post the output of:
```
nm-tool
sudo iwlist scan
iwlist chan

```
Please run the last command with your wired connection unplugged.
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.

Also install rfkill and run the command:
```
rfkill list all
```
Thank you

---

### Post by davidafranklin on 2012-01-01
Hi,

I unplugged my wire connection and ran the 3 sets of commands. Not sure if I followed the steps exactly as I was supposed to do.
Also not sure what the information between the brackets mean.

Anyway,here is my entire log. It still does not work.

davidafranklin@compaq:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:08:02:2F:01:92

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [linksys] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:0E:2E:99:A5:66

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    linksys:         Infra, 00:16:B6:4B:05:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 83
    Home Fort Apache:Infra, 00:18:01:F8:FE:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    2327LCCC:        Infra, 00:26:F2:F5:39:8F, Freq 2417 MHz, Rate 54 Mb/s, Strength 0 WEP


davidafranklin@compaq:~$ sudo iwlist scan
[sudo] password for davidafranklin: 
Sorry, try again.
[sudo] password for davidafranklin: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:F8:FE:C4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=100/100  
                    Encryption key:on
                    ESSID:"Home Fort Apache"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003114759181
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 0010486F6D6520466F727420417061636865
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 02 - Address: 00:16:B6:4B:05:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level=100/100  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006fb3824a2
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD060010180202F4

davidafranklin@compaq:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n55
Jan  1 20:13:32 compaq kernel: [ 3249.392118] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:13:38 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:13:39 compaq kernel: [ 3256.120102] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:13:39 compaq kernel: [ 3256.320120] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:13:39 compaq kernel: [ 3256.520124] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:13:39 compaq kernel: [ 3256.720125] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:13:52 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:13:53 compaq kernel: [ 3270.016156] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:13:53 compaq kernel: [ 3270.216510] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:13:53 compaq kernel: [ 3270.416088] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:13:53 compaq kernel: [ 3270.616189] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:13:55 compaq NetworkManager[471]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan  1 20:13:55 compaq NetworkManager[471]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jan  1 20:13:55 compaq NetworkManager[471]: <warn> Activation (wlan0) failed for access point (linksys)
Jan  1 20:13:55 compaq NetworkManager[471]: <warn> Activation (wlan0) failed.
Jan  1 20:13:55 compaq NetworkManager[471]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan  1 20:13:55 compaq NetworkManager[471]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan  1 20:13:56 compaq NetworkManager[471]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  1 20:13:58 compaq NetworkManager[471]: <info> Activation (wlan0) starting connection 'linksys'
Jan  1 20:13:58 compaq NetworkManager[471]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  1 20:13:58 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  1 20:13:59 compaq NetworkManager[471]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jan  1 20:13:59 compaq NetworkManager[471]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  1 20:13:59 compaq NetworkManager[471]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  1 20:14:00 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:14:00 compaq NetworkManager[471]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  1 20:14:00 compaq kernel: [ 3277.796096] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:14:00 compaq kernel: [ 3277.996167] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:14:01 compaq kernel: [ 3278.196125] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:14:01 compaq kernel: [ 3278.396154] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:14:08 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:14:08 compaq kernel: [ 3285.128211] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:14:08 compaq kernel: [ 3285.328114] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:14:08 compaq kernel: [ 3285.528865] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:14:08 compaq kernel: [ 3285.728181] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:14:15 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:14:15 compaq kernel: [ 3292.460129] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:14:15 compaq kernel: [ 3292.660129] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:14:15 compaq kernel: [ 3292.860097] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:14:16 compaq kernel: [ 3293.060101] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:14:22 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:14:22 compaq kernel: [ 3299.788148] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:14:22 compaq kernel: [ 3299.988097] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:14:23 compaq kernel: [ 3300.188188] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:14:23 compaq kernel: [ 3300.388358] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
Jan  1 20:14:29 compaq wpa_supplicant[1128]: Trying to authenticate with 00:16:b6:4b:05:c0 (SSID='linksys' freq=2462 MHz)
Jan  1 20:14:30 compaq kernel: [ 3307.116130] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 1/3)
Jan  1 20:14:30 compaq kernel: [ 3307.316106] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 2/3)
Jan  1 20:14:30 compaq kernel: [ 3307.516136] wlan0: direct probe to 00:16:b6:4b:05:c0 (try 3/3)
Jan  1 20:14:30 compaq kernel: [ 3307.716083] wlan0: direct probe to 00:16:b6:4b:05:c0 timed out
davidafranklin@compaq:~$ rfkill list all
The program 'rfkill' is currently not installed.  You can install it by typing:
sudo apt-get install rfkill

---

### Post by wildmanne39 on 2012-01-01
Hi davidafranklin, make sure you have network-manager-applet installed.
Thanks

---

### Post by davidafranklin on 2012-01-02
Hi WIld Man,
How do I do that? Is there a code or a special setting I need to have?

---

### Post by wildmanne39 on 2012-01-02
Hi, show the output of this command and it will tell us.
```
ps aux | grep nm-apple
```
Thanks

---

### Post by davidafranklin on 2012-01-02
This is what I am getting:


davidafranklin@compaq:~$ ps aux | grep nm-apple
1000      1167  6.2  8.4 256280 19656 ?        Sl   19:01   0:13 nm-applet
1000      1703  0.0  0.3   4444   784 pts/0    S+   19:05   0:00 grep --color=auto nm-apple

---

### Post by wildmanne39 on 2012-01-02
Hi davidafranklin, I have been searching for hours and I have not found one post that your wireless card work past 10.10, if you want to stay with the new version of ubuntu I would try to install ndiswrapper here is a link for that.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by davidafranklin on 2012-01-03
Thanks, I will try  ndiswrapper.

It is still bizarre tht 11.10 does not recognizew myc ard, other distros like puppy linuix still does. At least the driver componen should be avaalble somehwere.

In case I have to downgrade to Lunbunto 10.10 (from y current 10.10), is there an easy way to downgrade from Linux or o I have to go through the entire installation from the boot?

Thanks

---

### Post by wildmanne39 on 2012-01-03
Hi davidafranklin, no downgrade process, you should back up all important data and do a complete reinstall if you decide to reinstall.
Thanks

---

### Post by davidafranklin on 2012-01-03
Thanks for your help

---

### Post by wildmanne39 on 2012-01-03
Hi, your welcome!

---

