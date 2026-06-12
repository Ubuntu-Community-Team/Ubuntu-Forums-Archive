---
title: "Intermittent logon problems"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by jdkl81 on 2011-09-15
Hey guys.  Just a quick introduction first.  I'm new to Ubuntu and like it very much.  After my windows workstation began to suffer from malware related problems I decided this was my excuse to try Ubuntu like I've wanted to for a long time.  Anyway almost everything has been smooth except that my wireless access to my secured network is intermittent.  The computer will connect to any unsecured network and has at times accessed my secured Linksys network.  I have run the diagnostic test recommended in the Ubuntu community help page and will paste the output (long)  if  it is necessary but I really have no idea why it would not work since apparently the hardware and software are ok.  Anyway the computer is an HP probook 4710s and the Ubuntu is Natty Narwhal 11.04.  The wireless router is a Linksys WRT300N so I'm hoping some of you that know what you're doing a lot better than I do will be able to help.  Thanks a lot for looking.

---

### Post by wildmanne39 on 2011-09-15
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then copy and paste these commands into it, then paste the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jdkl81 on 2011-09-16
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux jd-HP-ProBook-4710s 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

```
```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:00:55:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=8.83.5.1 build 33692 ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:d8200000-d8201fff
  *-network
       description: Ethernet interface
       product: 88E8072 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:86:00.0
       logical name: eth0
       version: 10
       serial: 18:a9:05:a2:67:5b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:d0100000-d0103fff ioport:2000(size=256) memory:d8e00000-d8e1ffff

```
```
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        18:A9:05:A2:67:5B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto DDOG] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:26:C6:00:55:CE

  Capabilities:
    Speed:           5 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Anne Wifi:       Infra, 00:25:3C:08:11:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WEP
    *DDOG:           Infra, 00:13:10:42:09:DE, Freq 2432 MHz, Rate 54 Mb/s, Strength 38
    Wolfie2:         Infra, 00:1D:7E:70:67:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA
    2WIRE950:        Infra, 00:26:50:57:04:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WEP
    NETGEAR:         Infra, 00:24:B2:53:81:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    CParm:           Infra, 00:1C:10:A9:7A:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             205.152.111.23
    DNS:             205.152.144.23

```
```
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
86:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller [11ab:436c] (rev 10)

```
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:03b0 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"DDOG"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:13:10:42:09:DE   
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:278   Missed beacon:0

```
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
[CODEModule                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_analog    75442  1 
arc4                   12473  2 
binfmt_misc            13213  1 
iwlagn                284745  0 
rfcomm                 38125  8 
radeon                900494  3 
iwlcore               148964  1 iwlagn
mac80211              257001  2 iwlagn,iwlcore
sco                    17827  2 
bnep                   17785  2 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
hp_wmi                 13418  0 
ttm                    65184  1 radeon
sparse_keymap          13666  1 hp_wmi
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               75143  1 uvcvideo
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  3 iwlagn,iwlcore,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
drm                   184164  5 radeon,ttm,drm_kms_helper
hp_accel               21632  0 
video                  18951  0 
lis3lv02d              19285  1 hp_accel
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 
[/CODE]
That was the set of commands you asked for in order however it was done while connected to an unsecured wireless network "DDOG"  In the next post I will repeat this process while trying to connect to my secured wireless network "Wolfie2"

---

### Post by jdkl81 on 2011-09-16
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux jd-HP-ProBook-4710s 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

```
```
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:00:55:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:d8200000-d8201fff
  *-network
       description: Ethernet interface
       product: 88E8072 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:86:00.0
       logical name: eth0
       version: 10
       serial: 18:a9:05:a2:67:5b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:d0100000-d0103fff ioport:2000(size=256) memory:d8e00000-d8e1ffff

```
```
NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        18:A9:05:A2:67:5B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Wolfie2] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:26:C6:00:55:CE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Wolfie2:         Infra, 00:1D:7E:70:67:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    DDOG:            Infra, 00:13:10:42:09:DE, Freq 2432 MHz, Rate 54 Mb/s, Strength 35
    2WIRE895:        Infra, 98:2C:BE:A5:2C:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Anne Wifi:       Infra, 00:25:3C:08:11:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    2WIRE950:        Infra, 00:26:50:57:04:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    NETGEAR:         Infra, 00:24:B2:53:81:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    CParm:           Infra, 00:1C:10:A9:7A:F2, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA


```
```
lspci -nn | grep -e 0280 -e 0200
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
86:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller [11ab:436c] (rev 10)

```
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:03b0 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Wolfie2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
```
Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_analog    75442  1 
arc4                   12473  2 
binfmt_misc            13213  1 
iwlagn                284745  0 
rfcomm                 38125  8 
radeon                900494  3 
iwlcore               148964  1 iwlagn
mac80211              257001  2 iwlagn,iwlcore
sco                    17827  2 
bnep                   17785  2 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
hp_wmi                 13418  0 
ttm                    65184  1 radeon
sparse_keymap          13666  1 hp_wmi
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               75143  1 uvcvideo
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  3 iwlagn,iwlcore,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
drm                   184164  5 radeon,ttm,drm_kms_helper
hp_accel               21632  0 
video                  18951  0 
lis3lv02d              19285  1 hp_accel
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 

```
So that's the same set of data from the same commands in order while trying unsuccessfully to connect to my secured wireless network "Wolfie2" if anything it should show if there is any difference between how it's working with the unsecured networks and "not" working with the secured ones.  Thanks for looking and trying to help
JD

---

### Post by wildmanne39 on 2011-09-16
Hi, first set your encryption to just wpa2 not mixed mode please and see if that helps if not post the results of these commands please:
```
dmesg | egrep 'iwl|firm'
```
```
lsmod | grep iwl
```
```
sudo iwlist scan
```
run these commands while you can not connect to your network.
Thank you

---

### Post by jdkl81 on 2011-09-16
Hey, how do you change your encryption settings?  Oddly enough, now my network is working...this is a strange problem.

---

### Post by wildmanne39 on 2011-09-16
Hi, you need to be connected to your router with  wired connection, then open a browser and in the address bar type 192.168.0.1 then click on wireless in your router configuration settings and it is there you will find your encryption settings.

Also make sure your router is set to b,g,n, speed and not just n speed.
Thank you

---

### Post by jdkl81 on 2011-09-16
Hey so I really appreciate your time Wildmane, I will do a wired connection to the router, though that too has been problematic in the past, not just in Ubuntu but even when I had Windows.  Honestly, I'm nowhere near as computer smart as I should be for jumping into Linux but as I said I took this as an opportunity to jump in with both feet and learn some stuff.  Thanks for helping.  I'll try the wired connection and get back with you if I have any more problems or if the problem appears to be resolved for good.

---

### Post by wildmanne39 on 2011-09-16
Hi, let us know we can run some commands to try to find the cause but a lot of the time what I suggested works.
Thank you

---

