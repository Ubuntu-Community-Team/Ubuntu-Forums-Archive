---
title: "Dropped wireless connections and reconnections with a Broadcom BCM4321"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by ianthealy on 2012-04-29
With the newest distribution, beginning yesterday, both of the Ubuntu   computers on my network that connect via wireless are randomly dropping   the connection several times an hour. The connection re-establishes in a   few seconds, but it interrupts downloads, browsing, and updates. The   Windows computer connected via Ethernet is not affected by these   outages. This didn't happen during the previous several weeks where I   had the 12.04 Beta version installed; only beginning yesterday with the   new distro. In fact, the connection dropped twice while I was typing   this.

sudo lshw -class network returns:
```
  *-network               
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth3
       version: 01
       serial: 00:16:cf:c9:36:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:efdfc000-efdfffff memory:e0000000-e00fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: 00:18:8b:ab:dc:fd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

```lsusb returns:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
```lspci returns:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 01)

```rfkill list all returns:
```
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```So far, I  have confirmed that my Broadcom driver is installed and working. I have  reinstalled it. I have run the update manager several times and  rebooted. I have also confirmed that my backports were already enabled.  I'm looking for additional suggestions as this is affecting both my  laptop and my son's. I was running 12.04 Beta as a fresh install with no  wireless connectivity issues prior to the official release. My son  upgraded from 11.10 and also had no connectivity issues prior to the  release.


As I'm looking to get as many suggestions as possible to repair this, I've cross-posted this on Ask Ubuntu here: [http://askubuntu.com/questions/127094/dropped-wireless-connections-and-reconnections-with-a-broadcom-bcm4321](http://askubuntu.com/questions/127094/dropped-wireless-connections-and-reconnections-with-a-broadcom-bcm4321)

---

### Post by chili555 on 2012-04-29
Let's see:```
lsmod
lspci -nn | grep 0280
```Thanks.

---

### Post by gokulsurendiran on 2012-04-29
Hi,

I also have the same problem in my samsung n150 netbook.

I'm just a end user, if you could help in simple english it would be helpful! Thanks in Advance.

Regards,
Gokul

---

### Post by chili555 on 2012-04-29
> I'm just a end user, So am I and so are most of us. Please open a terminal and enter this text:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Press Enter. Do you have a Broadcom [COLOR="Red"]BCM4321[/COLOR] 802.11a/b/g/n card? If so, post the pci.id here in your reply. The pci.id is a number like this: 14e4:4987, except yours is different. It will be essential to know exactly what it is.

Also run and post:```
lsmod
```If yours is not the same card, post a new thread and leave the link here. I'll be very happy to help you.

---

### Post by gokulsurendiran on 2012-04-30
> lspci -nn | grep 0280 

05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

> lsmod

Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  0 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
easy_slow_down_manager    12985  0 
dm_crypt               22528  0 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
samsung_backlight      13487  0 
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
ath9k                 117425  0 
uvcvideo               67203  0 
mac80211              436455  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               86588  1 uvcvideo
ath9k_common           13781  1 ath9k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              391523  2 ath9k,ath9k_common
psmouse                87213  0 
snd_timer              28931  2 snd_pcm,snd_seq
btusb                  17912  1 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
rfcomm                 38139  12 
bnep                   17830  2 
bluetooth             158438  23 btusb,bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414568  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
sky2                   49545  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915

> I'll be very happy to help you 

thanks very much!

---

### Post by chili555 on 2012-04-30
You don't have a Broadcom 4321 card; you have an Atheros Communications Inc. AR9285 Wireless Network Adapter. Please start a new thread and I'll be happy to help. Leave the link here.

---

### Post by ianthealy on 2012-04-30
> **chili555 said:**
> Let's see:```
lsmod
lspci -nn | grep 0280
```Thanks.

lsmod returns:
```
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
bnep                   17830  2 
rfcomm                 38139  12 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
b44                    31364  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
ssb                    50691  1 b44
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
joydev                 17393  0 
usbhid                 41906  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
coretemp               13269  0 
snd_rawmidi            25424  1 snd_seq_midi
i915                  414603  3 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
psmouse                72919  0 
nand_bch               13003  1 nand
r592                   17808  0 
bch                    21757  1 nand_bch
memstick               15857  1 r592
nand_ecc               13070  1 nand
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            13671  0 
dcdbas                 14098  1 dell_laptop
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
i2c_algo_bit           13199  1 i915
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 dell_wmi
serio_raw              13027  0 
mac_hid                13077  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```lspci -nn | grep 0280 returns:
```
0c:00.0 Network controller [[COLOR=Red]0280[/COLOR]]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 01)

```Note: the [[COLOR=Red]0280[/COLOR]] is [COLOR=Red]red[/COLOR] for some reason in my terminal.

---

### Post by gokulsurendiran on 2012-05-01
> **chili555 said:**
> You don't have a Broadcom 4321 card; you have an Atheros Communications Inc. AR9285 Wireless Network Adapter. Please start a new thread and I'll be happy to help. Leave the link here.

Hi, started a new thread, here is the link:
[http://ubuntuforums.org/showthread.php?p=11894075#post11894075](http://ubuntuforums.org/showthread.php?p=11894075#post11894075)

---

### Post by chili555 on 2012-05-01
> Note: the [[COLOR="Red"]0280[/COLOR]] is red for some reason in my terminal.That simply means, roughly, 'here is the term you grepped for.'

Your readings look really good so far; I see nothing glaring to fix. We need to dig deeper. Please post:```
sudo iwlist eth1 scan  <--I assume your wireless interface is eth1
sudo cat /var/log/syslog | grep -e wl -e etwork | tail -n20
```

---

### Post by ianthealy on 2012-05-01
> **chili555 said:**
> That simply means, roughly, 'here is the term you grepped for.'

Your readings look really good so far; I see nothing glaring to fix. We need to dig deeper. Please post:```
sudo iwlist eth1 scan  <--I assume your wireless interface is eth1
sudo cat /var/log/syslog | grep -e wl -e etwork | tail -n20
```

Actually, my wireless interface seems to be eth3.
sudo iwlist eth3 scan returns:
```

eth3      Scan completed :
          Cell 01 - Address: 20:76:00:10:DF:A8
                    ESSID:"healyhousehold"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010D4ACEF79FC9155B266E8D578FCA699241021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 7C:4F:B5:D0:CA:F7
                    ESSID:"MOTOROLA-0E7DC"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD790050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100084D6F746F726F6C61102300084D6F746F726F6C611024000631323334353610420007303030303030311054000800060050F20400011011000A4D6F746F726F6C614150100800020088103C000101
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:24:7B:F5:C8:10
                    ESSID:"myqwest5203"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: CC:5D:4E:85:F4:01
                    ESSID:"Jerri"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B00010310470010610FDABBE2CA558D6C27FDE7EA7E242D102100055A7958454C1023000651313030305A1024000B50383730484E552D35316310420004313233341054000800060050F20400011011000751776573744150100800020088103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:14:BF:AB:09:A7
                    ESSID:"ezwallace"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:22:6B:84:09:A7
                    ESSID:"cpod"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A88000226B8409A71021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033030381054000800060050F2040001101100114C696E6B737973205752543136304E7632100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:1D:7E:23:03:05
                    ESSID:"CoreProcess"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 08 - Address: 00:26:B8:FC:43:28
                    ESSID:"myqwest8685"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010951BFD03811E8D663D6E6DC74EFDB2E11021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 09 - Address: C0:3F:0E:1A:E4:2C
                    ESSID:"n8diz"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
```sudo cat /var/log/syslog | grep -e wl -e etwork | tail -n20 returns:
```
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3/wireless): access point 'healyhousehold' has security, but secrets are required.
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> (eth3): device state change: config -> need-auth (reason 'none') [50 60 0]
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 2 of 5 (Device Configure) complete.
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 1 of 5 (Device Prepare) scheduled...
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 1 of 5 (Device Prepare) started...
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> (eth3): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 2 of 5 (Device Configure) scheduled...
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 1 of 5 (Device Prepare) complete.
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 2 of 5 (Device Configure) starting...
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> (eth3): device state change: prepare -> config (reason 'none') [40 50 0]
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3/wireless): connection 'healyhousehold' has security, and secrets exist.  No new secrets needed.
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: added 'ssid' value 'healyhousehold'
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: added 'scan_ssid' value '1'
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: added 'auth_alg' value 'OPEN'
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: added 'psk' value '<omitted>'
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Activation (eth3) Stage 2 of 5 (Device Configure) complete.
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> Config: set interface ap_scan to 1
May  1 20:52:11 IanUbuntu NetworkManager[905]: <info> (eth3): supplicant interface state: disconnected -> scanning
May  1 20:52:13 IanUbuntu NetworkManager[905]: <info> (eth3): supplicant interface state: scanning -> associating

```

---

### Post by ianthealy on 2012-05-01
Note: In the thread on Ask Ubuntu, I've had the following suggestions:
```
Try disabling power management for your WiFi NIC:
  example for eth1: iwconfig eth1 power off
 

```

and

```
I had been having the  same issue with the  wifi staying connected, but no DNS or routing happening after a few  minutes.  I would have to restart to get things back up.  
  What I have done is disable IPV6 and so far, have been connected for 3  hours with no drop.  No idea how to prove if this is the solution or if  I have just been lucky for the  last 3 hours.
 

```

I don't want to jump into any of these in the middle of the diagnosis going on here, but if you think any of those might be a good idea, I'll implement them.

---

### Post by chili555 on 2012-05-02
> ESSID:"healyhousehold"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    <snip>
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/sI don't know if it is Network Manager, wpa_supplicant or your driver, but I think you will have better luck with WPA2 only and not WPA and WPA2 mixed mode. Can you change the router and try again?

---

### Post by ianthealy on 2012-05-02
> **chili555 said:**
> I don't know if it is Network Manager, wpa_supplicant or your driver, but I think you will have better luck with WPA2 only and not WPA and WPA2 mixed mode. Can you change the router and try again?

I changed to WPA2 only, but the problem is continuing.

---

### Post by ianthealy on 2012-05-02
I have found a possible solution at this link:
[http://askubuntu.com/questions/128024/wireless-connection-is-lost-periodically-and-without-apparent-reason-and-is-quic/](http://askubuntu.com/questions/128024/wireless-connection-is-lost-periodically-and-without-apparent-reason-and-is-quic/)

I have disabled IPV6 in my Network Manager, and am forcing excessive traffic by streaming music, video, twitter, and other live feeds. So far the network hasn't reset itself at all. If I can continue without problems for the rest of the evening, I will mark this problem as resolved.

---

### Post by brainwash on 2012-05-03
Just wondering.. maybe the reconnects are caused by the IPv6 Privacy Extensions (enabled by default since 12.04).

The address lifetime might be too short, so checking the *valid* and *preferred* timers should solve the mystery:
```
ip -6 addr
```

---

### Post by ianthealy on 2012-05-03
Setting IPv6 to Ignore in the Network Manager/Edit Connections/Wireless has solved this issue for me and for my son's laptop as well.

---

