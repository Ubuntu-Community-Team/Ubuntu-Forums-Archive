---
title: "Sierra Wireless AirCard 330U"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by M_Mynaardt on 2012-04-13
Hi!

I just got a new wireless modem and, as I thought, it's being a bit of a tough one trying to get it to work with Linux.  It is, of course, a Sierra Wireless AirCard 330U; a fairly new gadget with good connect speeds and all.  But not much use if I can't make it work on my Lubuntu laptop!

Has anyone had experience getting Sierra Wireless gear working on their computers?  The best I could find so far from the Sierra site is a link to an app called NetworkManager (NM).  Anyone had experience with that?  I downloaded at TAR file to install it but haven't had a chance to do so yet (working nights is my standard excuse).

The provider for this is Rogers Wireless.  The last wireless modem I got from them was a Nortel number and I was able to download a Linux driver for that easily.  But this Sierra Wireless thing isn't quite so easy, it seems.

Any hints or tips would be much appreciated!

Thanks in advance!

---

### Post by praseodym on 2012-04-14
Hi,

pleas shoe the outputs of:

```
lspci -nnk
lsusb
lsmod
usb-devices
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by M_Mynaardt on 2012-04-14
> **praseodym said:**
> Hi,

pleas shoe the outputs of:

```
lspci -nnk
lsusb
lsmod
usb-devices
ifconfig -a
cat /etc/resolv.conf
```

Should I try this with or without that Wireless AirCard 330U thingy plugged into a USB port?

Thanks!

---

### Post by praseodym on 2012-04-15
Without, please

---

### Post by M_Mynaardt on 2012-04-16
> **praseodym said:**
> Without, please

Right!

Well, it's kind of long, but here are the results of those commands from my Lubuntu terminal:

```

... :~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Kernel modules: shpchp
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
	Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7106]
	Kernel driver in use: ath5k
	Kernel modules: ath5k
05:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
05:0a.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
... :~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
... :~$ lsmod
Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  13 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_realtek   254163  1 
snd_hda_codec_si3054    12864  1 
snd_hda_intel          24262  5 
snd_hda_codec          91859  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_pcm                80435  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
pcmcia                 39822  0 
snd_seq_midi           13132  0 
radeon                929507  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
ath5k                 145100  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
psmouse                73673  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
yenta_socket           27428  0 
snd                    55902  18 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
drm                   192194  4 radeon,ttm,drm_kms_helper
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
cfg80211              172427  3 ath5k,ath,mac80211
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
video                  18908  0 
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
sparse_keymap          13658  0 
shpchp                 32356  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
usbhid                 41905  0 
hid                    77367  1 usbhid
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
sata_sil               13278  2 
pata_atiixp            12967  0 
... :~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.01
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
... :~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:67:05:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20416 (20.4 KB)  TX bytes:20416 (20.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:e3:ba:23:0a  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:feba:230a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6491479 (6.4 MB)  TX bytes:1871219 (1.8 MB)

... :~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.59.161.68
... :~$ 

```

Thanks!

---

### Post by praseodym on 2012-04-16
Is it a USB device? Plugged into a USB-hub? Its not shown there. Try to plug it directly

---

### Post by M_Mynaardt on 2012-04-17
> **praseodym said:**
> Is it a USB device? Plugged into a USB-hub? Its not shown there. Try to plug it directly

Okay, I've plugged it in, and it's just sitting there doing nought.  I've run those commands again, but with the Sierra Wireless AirCard 330U plugged in to a USB this time.  There's also a Logitech wireless USB trackball plugged in as well.

```

... :~$ lspci -nnk
00:00.0 Host bridge [0600]: ATI Technologies Inc Device [1002:5a31] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Kernel modules: shpchp
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
	Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7106]
	Kernel driver in use: ath5k
	Kernel modules: ath5k
05:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
05:0a.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
... :~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 1199:68a3 Sierra Wireless, Inc. 
... :~$ lsmod
Module                  Size  Used by
sierra                 17960  0 
usbserial              37203  1 sierra
sierra_net             13465  0 
usbnet                 25214  1 sierra_net
usb_storage            44173  0 
uas                    17699  0 
xt_limit               12541  8 
xt_tcpudp              12531  13 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_realtek   254163  1 
snd_hda_codec_si3054    12864  1 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
snd_hda_intel          24262  5 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec          91859  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
radeon                929507  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
psmouse                73673  0 
ath5k                 145100  0 
yenta_socket           27428  0 
ath                    19387  1 ath5k
serio_raw              12990  0 
pcmcia_rsrc            18367  1 yenta_socket
ttm                    65224  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac80211              393421  1 ath5k
snd                    55902  18 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 radeon
soundcore              12600  1 snd
drm                   192194  4 radeon,ttm,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
cfg80211              172427  3 ath5k,ath,mac80211
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
shpchp                 32356  0 
ati_agp                13242  0 
video                  18908  0 
binfmt_misc            17292  1 
sparse_keymap          13658  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
8139too                23283  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_core          56937  1 firewire_ohci
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
sata_sil               13278  2 
pata_atiixp            12967  0 
... :~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a3 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=AirCard 330U
S:  SerialNumber=359615040041420
C:  #Ifs= 7 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra_net
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.01
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-17-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
... :~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:67:05:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20416 (20.4 KB)  TX bytes:20416 (20.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:e3:ba:23:0a  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:feba:230a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21083 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23663890 (23.6 MB)  TX bytes:2962588 (2.9 MB)

wwan0     Link encap:Ethernet  HWaddr 5e:36:4a:93:01:07  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

... :~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.59.161.68
... :~$ 

```

Thanks, again!

---

### Post by praseodym on 2012-04-17
> Bus 001 Device 004: ID 1199:68a3 Sierra Wireless, Inc. 
There it is. The driver is also loaded. IMHO the package "modemmanager" is missing in Lubuntu. See also here:

[http://ubuntuforums.org/showpost.php?p=9143090&postcount=10](http://ubuntuforums.org/showpost.php?p=9143090&postcount=10)

---

### Post by M_Mynaardt on 2012-04-19
> **praseodym said:**
> There it is. The driver is also loaded. IMHO the package "modemmanager" is missing in Lubuntu. See also here:

[http://ubuntuforums.org/showpost.php?p=9143090&postcount=10](http://ubuntuforums.org/showpost.php?p=9143090&postcount=10)

I still couldn't get it to work after all that!  I had pretty much given up hope on that AirCard.  But I had one last look at the Sierra website and _finally_ found some manner of driver that I'd overlooked.  It's basically the contents of a **.tar** file (attached here) that you need to unpack, and compile (as root or with *sudo*).

And after that, you just plug it it, then connect with the default mobile broadband settings and ... Bob's your uncle!  Huzzah!

Here's the Sierra link for all this that I managed to overlook several times: [http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=9D1F7D34B2744B9EB97A8C3E71CD0368ZMLCIN[J&aid=44]("http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?sSessionID=9D1F7D34B2744B9EB97A8C3E71CD0368ZMLCIN[J&aid=44")

Took me a while to get my act together on this one, but I got there eventually!
:rolleyes:

---

