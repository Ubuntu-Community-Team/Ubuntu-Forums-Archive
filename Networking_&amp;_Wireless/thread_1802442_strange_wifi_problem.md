---
title: "strange wifi problem"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by nmxdaven on 2011-07-11
Hey everyone,

I'm currently running 2 11.04 ubuntu boxes and 1 scientific linux box.

One of my ubuntu boxes and the scientific one can connect to my wifi perfectly, but my main ubuntu machine cant seem to get in.

Its running on a hp touchsmart 300

> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    
The router is a D-link running dd-wrt, wpa2 security with rts/cts. It can connect to my other wifi (Open) just fine, but for some reason this particular machine wont connect to the wpa2 one. If i watch the wireless connections in my router, I can see the machines mac trying to get in, but it just goes in and out until it times out on the box. 

any ideas????

---

### Post by jmoorse on 2011-07-12
I have seen similar issues with certain devices (drivers perhaps?) and WPA2.

Has this ever worked?

Try setting the encryption to WPA TKIP, or break off a new SSID in dd-wrt and see if you can connect to that.

---

### Post by nmxdaven on 2011-07-12
> **jmoorse said:**
> I have seen similar issues with certain devices (drivers perhaps?) and WPA2.

Has this ever worked?

Try setting the encryption to WPA TKIP, or break off a new SSID in dd-wrt and see if you can connect to that.

Its worked before on this system, but never on natty (finally got around to upgrading a week ago)

Just tried WPA and WEP, still no go. It seems that it wont connect to any type of security.

Heres what a nm-tool gets me. 

> - Device: wlan0  [Auto Comtrend6a67] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        00:*

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Supa:            Infra, 00:*, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    *Comtrend6a67:   Infra, 00:*, Freq 2462 MHz, Rate 54 Mb/s, Strength 70
    Supa:            Infra, 00:*, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WEP

  IPv4 Settings:
    Address:         192.168.*
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.*

    DNS:             207.*
    DNS:             207.*


---

### Post by TBABill on 2011-07-12
Your wifi was not listed when you posted originally. That was your ethernet. Can you paste back here the outputs of ```
lsmod
``` and ```
lspci
``` and ```
sudo lshw -C network
``` That particular driver may take a bit of tweaking...notorious for little niggles but usually not hard to get working.

---

### Post by nmxdaven on 2011-07-12
> **TBABill said:**
> Your wifi was not listed when you posted originally. That was your ethernet. Can you paste back here the outputs of ```
lsmod
``` and ```
lspci
``` and ```
sudo lshw -C network
``` That particular driver may take a bit of tweaking...notorious for little niggles but usually not hard to get working.

Thanks guys, hopefully I can get this working.

```
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
snd_hda_codec_analog    93270  1 
snd_hda_intel          32922  3 
snd_hda_codec         112255  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm               100349  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30434  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
snd_seq                65527  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29395  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2860sta             543010  0 
arc4                   12529  2 
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
rt2800pci              18535  0 
ir_rc6_decoder         12546  0 
rt2800lib              45181  1 rt2800pci
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
usbhid                 46956  0 
ir_nec_decoder         12546  0 
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
mceusb                 17867  0 
rc_core                26918  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
ipt_REJECT             12576  1 
fglrx                2739144  66 
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    78151  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
hid                    91020  1 usbhid
ipt_LOG                17016  10 
xt_limit               12711  11 
xt_tcpudp              12603  10 
ipt_addrtype           12599  4 
xt_state               12578  10 
cfg80211              178528  2 rt2x00lib,mac80211
psmouse                73535  0 
edac_core              53845  0 
ip6table_filter        12815  1 
ip6_tables             27845  1 ip6table_filter
soundcore              12680  1 snd
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12649  0 
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19640  12 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13359  1 nf_nat_ftp
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
ip_tables              27456  1 iptable_filter
edac_mce_amd           23464  0 
k10temp                13119  0 
shpchp                 37297  0 
serio_raw              13166  0 
x_tables               29581  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
eeprom_93cx6           12725  1 rt2800pci
sp5100_tco             13744  0 
i2c_piix4              13303  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
video                  19438  0 
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  4 
r8169                  48022  0 
libahci                26642  1 ahci

``````
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Ralink corp. RT3092 Wireless 802.11n 2T/2R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
``````
*-network               
       description: Wireless interface
       product: RT3092 Wireless 802.11n 2T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:82:6f:1e:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 70:71:bc:1d:78:7a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff memory:febc0000-febdffff


```

---

### Post by TBABill on 2011-07-12
Can you go to [http://ubuntuforums.org/showthread.php?t=1682710&highlight=rt2860](http://ubuntuforums.org/showthread.php?t=1682710&highlight=rt2860) and follow my post for instructions (post #8 in that thread). That should fix you right up.

---

### Post by nmxdaven on 2011-07-12
> **TBABill said:**
> Can you go to [http://ubuntuforums.org/showthread.php?t=1682710&highlight=rt2860](http://ubuntuforums.org/showthread.php?t=1682710&highlight=rt2860) and follow my post for instructions (post #8 in that thread). That should fix you right up.

Thank you so much!!
Worked like a charm!

---

### Post by TBABill on 2011-07-12
Glad to hear you have it sorted and working. Enjoy!

---

