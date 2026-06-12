---
title: "No Network on HP Mini 1000"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by Mr_Electric on 2013-06-24
Hi Everyone (sorry, posted this in the hardware section first before seeing that it related more to networking), I recently tried to install Ubuntu on my HP Mini 1000 but ran into the problem of network connectivity. The wireless card and the Ethernet port both failed connect to my network and I am unable to install the missing drivers. I did see a link (and downloaded) the Linux drivers for the Broadcom chip, but I have no idea on how to install this driver. Any help would be greatly appreciated!

Thanks!
Mr_E

---

### Post by praseodym on 2013-06-24
Hi,

please show these outputs:
```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Check the file **linux-firmware-nonfree** for Broadcom cards:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

---

### Post by Mr_Electric on 2013-06-25
Ok, here's what I got:

administrator@administrator-HP-Mini:~$ uname -a
Linux administrator-HP-Mini 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
administrator@administrator-HP-Mini:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel modules: i2c-i801
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1507]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
	Subsystem: Hewlett-Packard Company Device [103c:361a]
	Kernel driver in use: sky2
	Kernel modules: sky2
administrator@administrator-HP-Mini:~$ grep -ia2 net
^[[D^[[C^C
administrator@administrator-HP-Mini:~$ grep -ia2 net
^C
administrator@administrator-HP-Mini:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE          1419  1 
xt_state                1014  1 
ipt_REJECT              2004  2 
xt_tcpudp               1927  4 
iptable_filter          1302  1 
nf_nat_h323             5121  0 
nf_conntrack_h323      46894  1 nf_nat_h323
nf_nat_pptp             1996  0 
nf_conntrack_pptp       4681  1 nf_nat_pptp
nf_conntrack_proto_gre     3901  1 nf_conntrack_pptp
nf_nat_proto_gre        1271  1 nf_nat_pptp
nf_nat_tftp              728  0 
nf_conntrack_tftp       2905  1 nf_nat_tftp
nf_nat_sip              5574  0 
nf_conntrack_sip       18703  1 nf_nat_sip
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_conntrack_ftp        5361  1 nf_nat_ftp
iptable_nat             3752  1 
nf_nat                 16289  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10783  4 iptable_nat,nf_nat
nf_conntrack           63258  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
ip_tables              10460  2 iptable_filter,iptable_nat
x_tables               15921  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
nls_iso8859_1           3261  2 
nls_cp437               4931  2 
vfat                    9201  2 
fat                    48240  1 vfat
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
arc4                    1165  2 
i915                  290938  3 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
b43                   168681  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231541  1 b43
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
joydev                  8735  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                  5191  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
uvcvideo               55847  0 
cfg80211              144470  2 b43,mac80211
btusb                  10969  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
intel_agp              26360  2 i915
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
video                  18712  1 i915
led_class               2633  1 b43
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ssb                    39288  1 b43
sky2                   45127  0 
usb_storage            40172  2 
administrator@administrator-HP-Mini:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"5-0"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 32:8D:CB:DD:FA:4C   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
administrator@administrator-HP-Mini:~$ rfkill list
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
4: hp-wwan: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
administrator@administrator-HP-Mini:~$ 

I also installed the .deb package you provided and it asked me to connect to a wireless network, but I still am having connectivity issues.

Thanks!
Mr_E

---

### Post by Mr_Electric on 2013-06-25
Oh, I almost forgot to mention that the wired connection now works, but I'm still having trouble with the wireless.

Thanks,
Mr_E

---

### Post by kurt18947 on 2013-06-25
I just set one of those up with Xubuntu.  I used an ethernet (wired) connection to run updates after the initial install.  One of those updates was the Broadcom WiFi driver/firmware.  I didn't have to explicitly install via "additional drivers".  Unless there's more than one model of the HP 1000 mini with slightly different hardware?

---

### Post by praseodym on 2013-06-25
Kernel 2.6.35 looks like Ubuntu 10.10 which is outdated! Check
```

lsb_release -a
```
For the low-power chipset install the missing firmware (if it works!):
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

