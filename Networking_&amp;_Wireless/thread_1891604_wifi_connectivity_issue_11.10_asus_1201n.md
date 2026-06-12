---
title: "wifi connectivity issue 11.10 asus 1201n"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by GiladGressel on 2011-12-06
Hi Folks,

computer is : asus 1201n
ubuntu : 11.10 32bit desktop

I have an annoying wifi problem that will not seem to go away. (each time i upgrade version of ubuntu  it comes right back)

Currently my wifi will sometimes connect to a wpa/wpa2 network.  however when it does it will not load any webpages (the browser declares sites are not responding fast enough).  

in my last test when i attempted to connect to wep -- it simply would not connect at all, network manager just attempted to connect over and over and repeatedly asked me for the password. 
 It may be worth noting that I am trying to share a connection with a macbook that has internet sharing turned on.  I have tested the connection with no password and it will not connect to that either. 
however my ipod touch connects no problem (to all the above networks)

Whats really confusing me is this:
 a few months ago when i was running 11.04 i downloaded and installed compatdrivers.  I blacklisted my computers native mod "r8192se_pci"s
and i added the compat mod "rtl8192se" to /etc/modules. 

currently when i run lsmod the driver in use is called "rtl812se" (which is the same name as the driver i installed manually in 11.04)
I thought perhaps that 11.10 was not using the native drivers  because of my edits to /etc/modules and /etc/modprobe.d/blacklist.conf  in 11.04

so i undid those changes (deleted the blacklist and addtion to /etc/modules)
after a restart the result of that small test was no wifi at all.  no signal nothing.  when i ran the command "modprobe rtl819se" i get a wifi signal.

is my ubuntu still running an old driver that i installed in 11.04?
why is it not using the new drivers which are baked into 11.10 (and said to work for my realtek card?)

when i run lsmod i see the following

lsmod
```

gilad@maya:~$ lsmod
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
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vboxnetadp             13328  0 
vboxnetflt             27840  0 
vboxdrv               230133  2 vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
nvidia              10390874  42 
joydev                 17393  0 
arc4                   12473  2 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
shpchp                 32356  0 
video                  18908  0 
wmi                    18744  1 asus_wmi
i2c_nforce2            12906  0 
[COLOR="Red"]rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393459  2 rtl8192se,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211[/COLOR]
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36638  0 
ahci                   21634  3 
libahci                25727  1 ahci
gilad@maya:~$ 


```you see the mod is rtl8192se
this is the same name of the driver i previously installed in 11.04.
however when i run modinfo rtl8129se

```

gilad@maya:~$ modinfo rtl8192se
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     937F4C8CF0D06038BBDF950
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.0.0-13-generic SMP mod_unload modversions 686 
parm:           fwlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           swlps:using linked sw control power save (default 1 is open)
 (bool)
gilad@maya:~$ 

```

it shows the rtl8192se as part of my lib/modules
it also shows it is built for kernel 3.0 -- the compat driver i installed in 11.04 was built for 2.6

this makes me think i am indeed running the current native driver for 11.10

what mystifies me is that no driver loads unless i keep "rtl8192se" in my /etc/modules
or run modprobe manually

i'm completely confused and possibly totally off track.

help is greatly appreciated.
here is a lot of code (possibly overkill -- but hey! better more than less)
these were all requested of me last time I had problems with wifi, so I'm just putting them up again -- i ran them all after failing to connect to the macbook internet sharing connection (essid: kali)

thanks in advance

-gilad


sudo iwlist wlan0 scan
```

gilad@maya:~$ sudo iwlist wlan0 scan
[sudo] password for gilad: 
wlan0     Scan completed :
          Cell 01 - Address: 16:9D:3A:89:0A:78
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"hmmmm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000019f5371f4
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 0005686D6D6D6D
                    IE: Unknown: 010882040B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181B0000000000000000000000000000000000000000000000
                    IE: Unknown: 3D160108000000000F000000000000000000000000000000
                    IE: Unknown: DD09001018020000450000
                    IE: Unknown: DD1E00904C330C181B0000000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340108000000000F000000000000000000000000000000
          Cell 02 - Address: D8:A2:5E:90:E5:CB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Kali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000010acc183
                    Extra: Last beacon: 728ms ago
                    IE: Unknown: 00044B616C69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                   IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200100C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```iwconfig wlan0
```

gilad@maya:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

```dmesg | grep -e wlan -e 819
```

gilad@maya:~$ dmesg | grep -e wlan -e 819
[    0.381919] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.468190] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.518819] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *15
[    1.381902] Write protecting the kernel text: 5332k
[    1.672962] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 40
[   17.541516] rtl8192se 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   17.541539] rtl8192se 0000:07:00.0: setting latency timer to 64
[   17.553659] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   17.553666]            Loading firmware rtlwifi/rtl8192sefw.bin
[   25.158819] type=1400 audit(1323144319.272:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=882 comm="apparmor_parser"
[   77.498412] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.820073] wlan0: Creating new IBSS network, BSSID 46:d8:4b:2b:1c:d5
[   88.792023] wlan0: no IPv6 routers present
[  145.994937] Modules linked in: ipt_MASQUERADE xt_state ipt_REJECT xt_tcpudp iptable_filter nf_nat_h323 nf_conntrack_h323 nf_nat_pptp nf_conntrack_pptp nf_conntrack_proto_gre nf_nat_proto_gre nf_nat_tftp nf_conntrack_tftp nf_nat_sip nf_conntrack_sip nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_conntrack_ftp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables bnep rfcomm bluetooth vboxnetadp vboxnetflt vboxdrv parport_pc ppdev vesafb binfmt_misc snd_hda_codec_hdmi snd_hda_codec_realtek nvidia(P) joydev arc4 eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo videodev snd soundcore snd_page_alloc psmouse serio_raw shpchp video wmi i2c_nforce2 rtl8192se rtlwifi mac80211 cfg80211 lp parport atl1c ahci libahci
[  146.154056] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  146.154973] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  146.352057] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  146.552059] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  146.752059] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  158.779361] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  158.976072] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  159.176069] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  159.376052] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  165.435779] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  165.632075] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  165.832067] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  166.032112] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  172.079616] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  172.276074] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  172.476093] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  172.676111] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  178.695871] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  178.892076] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  179.092092] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  179.292056] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  185.347505] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  185.544053] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  185.744081] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  185.944084] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  192.011102] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  192.208056] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  192.408063] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  192.608054] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  217.628078] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  217.828065] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  218.028062] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  218.228064] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  224.243727] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  224.440056] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  224.640049] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  224.840051] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  230.931462] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  231.128088] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  231.328057] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  231.528058] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  237.552221] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  237.752043] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  237.952049] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  238.152062] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  244.199709] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  244.396069] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  244.596053] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  244.796066] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  250.844335] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  251.044064] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  251.244056] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  251.444055] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  257.463565] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  257.660093] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  257.860059] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  258.060076] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  264.107931] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  264.304087] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  264.504066] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  264.704088] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  270.760573] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  270.960063] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  271.160140] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  271.360070] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out
[  321.343851] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 1/3)
[  321.540091] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 2/3)
[  321.740070] wlan0: direct probe to d8:a2:5e:90:e5:cb (try 3/3)
[  321.940053] wlan0: direct probe to d8:a2:5e:90:e5:cb timed out


```rfkill list all
```

gilad@maya:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


```lspci -v
```

gilad@maya:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: 66MHz, fast devsel, IRQ 9
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f9f80000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f9f7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f9f7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f9f7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f9f7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 83ce
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f9f78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Capabilities: <access denied>

00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
    I/O ports at b080 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at ac00 [size=8]
    I/O ports at a880 [size=4]
    I/O ports at a800 [size=16]
    Memory at f9f76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fa000000-fbdfffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f7ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbe00000-fbefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

05:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8402
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fbde0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
    Subsystem: AzureWave Device 1107
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at d800 [size=256]
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se

09:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 14e5
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c


```lspci -nn
```

gilad@maya:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0b.0 IDE interface [0101]: nVidia Corporation MCP79 SATA Controller [10de:0ab5] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
05:00.0 VGA compatible controller [0300]: nVidia Corporation ION VGA [GeForce 9400M] [10de:0876] (rev b1)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
09:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)


```sudo cat /var/log/syslog | grep etwork | tail -n20
```

gilad@maya:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  6 09:40:14 maya NetworkManager[906]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  6 09:40:14 maya NetworkManager[906]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0/wireless): connection 'Auto Kali' has security, and secrets exist.  No new secrets needed.
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'ssid' value 'Kali'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'scan_ssid' value '1'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'key_mgmt' value 'NONE'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'auth_alg' value 'OPEN'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'wep_key0' value '<omitted>'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: added 'wep_tx_keyidx' value '0'
Dec  6 09:40:14 maya NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  6 09:40:14 maya NetworkManager[906]: <info> Config: set interface ap_scan to 1
Dec  6 09:40:14 maya NetworkManager[906]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec  6 09:40:15 maya NetworkManager[906]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec  6 09:40:21 maya NetworkManager[906]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Dec  6 09:40:21 maya NetworkManager[906]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Dec  6 09:40:21 maya NetworkManager[906]: <info> (wlan0): supplicant interface state: authenticating -> disconnected


```ifconfig
```

gilad@maya:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 48:5b:39:2b:c1:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19296 (19.2 KB)  TX bytes:19296 (19.2 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:84:31:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8576 (8.5 KB)

```sudo lshw -c network
```

gilad@maya:~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:84:31:63
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-13-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:d800(size=256) memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:2b:c1:0a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:fbfc0000-fbffffff ioport:ec00(size=128)

```

---

