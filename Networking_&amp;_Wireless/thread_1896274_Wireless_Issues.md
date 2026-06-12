---
title: "Wireless Issues"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by AlexNagy on 2011-12-16
```
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8182
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at a000 [size=256]
        Region 1: Memory at f0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-

Capabilities: [140 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [160 v1] Device Serial Number 00-00-fa-1b-5d-b6-26-00
        Kernel driver in use: r8180
        Kernel modules: r8187se
```

That's my wireless card (via lspci -vv).

```
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:b6:5d:1b:fa  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe5d:1bfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22061 errors:15 dropped:20796 overruns:0 frame:0
          TX packets:19953 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15605978 (15.6 MB)  TX bytes:2658842 (2.6 MB)
          Interrupt:18 Memory:f8708000-f8708100
```

I'm having problems on my parents network (wireless router, DSL) but no others I've been on (free hotspots at cafes, school, etc.). I'm lucky I'm able to come here but anything with https is unavailable, including all the major social media networks (but only through the browser, I can ping just fine). I'm clueless at this point (and very much disliking 11.10).

---

### Post by praseodym on 2011-12-16
Hi,

please show:
```
iwconfig
route -n
cat /etc/resolv.conf
sudo iwlist scan
lsmod
```

---

### Post by AlexNagy on 2011-12-21
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  link  ESSID:"House Blend Cafe"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: C0:C1:C0:06:7A:F9   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=89/100  Signal level=-33 dBm  Noise level=-114 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.16.0.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

```
 cat /etc/resolv.conf
# Generated by NetworkManager
domain lan
search lan
nameserver 172.16.0.1
```

```
iwlist scan
          Cell 01 - Address: 00:27:22:16:14:DF
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-50 dBm  Noise level=-96 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 113ms ago
          Cell 02 - Address: C0:C1:C0:06:7A:F9
                    ESSID:"House Blend Cafe"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=89/100  Signal level=-33 dBm  Noise level=-113 dBm
                    Extra: Last beacon: 122ms ago
          Cell 03 - Address: 00:1A:2B:63:19:7F
                    ESSID:"Comtrenda3a2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 

 Quality=63/100  Signal level=-51 dBm  Noise level=-95 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 131ms ago
          Cell 04 - Address: 5C:0E:8B:9E:CF:93
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 2 5.5 11 18 24 36 54 
                    Quality=45/100  Signal level=-64 dBm  Noise level=-82 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 79ms ago
          Cell 05 - Address: 5C:0E:8B:9E:CF:91
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 2 5.5 11 18 24 36 54 
                    Quality=45/100  Signal level=-64 dBm  Noise level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : Proprietary
                        Pairwise Ciphers (0) :

Authentication Suites (1) : Proprietary
                    Extra: Last beacon: 76ms ago
          Cell 06 - Address: 5C:0E:8B:9E:CF:92
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 11 12 18 24 36 48 54 
                    Quality=45/100  Signal level=-64 dBm  Noise level=-83 dBm
                    Extra: Last beacon: 85ms ago
          Cell 07 - Address: 5C:0E:8B:9E:CF:90
                    ESSID:"str241xvce"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 11 12 18 24 36 48 54 
                    Quality=46/100  Signal level=-63 dBm  Noise level=-83 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 83ms ago
          Cell 08 - Address: 5C:0E:8B:65:E5:03
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on

Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 2 5.5 11 18 24 36 54 
                    Quality=43/100  Signal level=-65 dBm  Noise level=-81 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 1555ms ago
          Cell 09 - Address: 5C:0E:8B:65:E5:01
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 2 5.5 11 18 24 36 54 
                    Quality=43/100  Signal level=-65 dBm  Noise level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : Proprietary
                        Pairwise Ciphers (0) :
                        Authentication Suites (1) : Proprietary
                    Extra: Last beacon: 1552ms ago
          Cell 10 - Address: 00:40:96:A3:37:41
                    ESSID:"<hidden>\x00"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=41/100  Signal level=-67 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 1523ms ago
```


```
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  39 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
bluetooth             148839  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
joydev                 17393  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
fglrx                2595537  50 
dm_multipath           22771  0 
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
soundcore              12600  1 snd
i2c_piix4              13093  0 
k10temp                12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
r8187se               157152  0 
sparse_keymap          13658  0 
eeprom_93cx6           12653  1 r8187se
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
pata_atiixp            12967  0

libahci                25727  1 ahci
r8169                  43104  0 
video                  18908  0 
zram                   18007  1 
```

That's all she wrote.

---

### Post by AlexNagy on 2011-12-21
Fixed. Saw the iptables stuff in lsmod and tinkered around with the firewall settings. Forgot to allow HTTPS in my outbound policy rules. (:

Thanks for the help. (:

---

