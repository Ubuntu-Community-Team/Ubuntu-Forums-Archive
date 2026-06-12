---
title: "No Wireless - eth1 has disappeared."
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by Sef on 2011-01-16
My wireless suddenly no longer works either in Ubuntu 10.10 or Windows 7. Upon some investigation, I have found that my eth1 is no longer showing up as it used to.

What can I do to get my wireless back?

Right below is some current specs, while below that is an older set of specs from a while ago.

```
sef@sef:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

sef@sef:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 13fe:3100 Kingston Technology Company Inc. 2 GB USB stick
Bus 002 Device 003: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sef@sef:~$ lspci -nn | grep Broadcom
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

sef@sef:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3a:34:33  
          inet addr:192.168.10.111  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe3a:3433/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1039568 (1.0 MB)  TX bytes:119924 (119.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

sef@sef:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

sef@sef:~$ lsmod
Module                  Size  Used by
nls_utf8                1453  1 
udf                    86514  1 
nls_iso8859_1           4657  1 
crc_itu_t               1739  1 udf
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
binfmt_misc             7984  1 
parport_pc             30086  0 
vboxnetadp              5267  0 
ppdev                   6804  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
snd_hda_codec_idt      64667  1 
joydev                 11395  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
i915                  334267  4 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
drm_kms_helper         32836  1 i915
drm                   206230  4 i915,drm_kms_helper
lib80211_crypt_tkip     8732  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
dell_wmi                3372  0 
dell_wmi_aio            2097  0 
dell_laptop             6722  0 
snd_timer              23850  2 snd_pcm,snd_seq
dcdbas                  6910  1 dell_laptop
uvcvideo               62379  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   1965231  0 
psmouse                62080  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
serio_raw               4910  0 
v4l2_compat_ioctl32    12614  1 videodev
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                6175  2 lib80211_crypt_tkip,wl
soundcore               1240  1 snd
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
intel_agp              32462  2 i915
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
output                  2527  1 video
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
ses                     7065  0 
enclosure               8553  1 ses
hid                    84710  1 usbhid
usb_storage            50372  4 
sky2                   53371  0 
ahci                   22210  2 
libahci                26052  1 ahci

ef@sef:~$ lamod | grep “wlan_module_name
No command 'lamod' found, did you mean:
 Command 'lamd' from package 'lam-runtime' (universe)
 Command 'lamed' from package 'texlive-omega' (universe)
 Command 'lsmod' from package 'module-init-tools' (main)
lamod: command not found


sef@sef:~$ sudo lshw -C network
[sudo] password for sef: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:af:e9:8d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3a:34:33
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.10.111 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
sef@sef:~$  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

sef@sef:~$ uname -mr
2.6.35-24-generic x86_64

sef@sef:~$  sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
sef@sef:~$ 

```

Here is a version from a while ago.

```
1. Dell Inspiron 1545

2. lspci

sef@osg:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
sef@osg:~$ 

lsusb

sef@osg:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 03f0:1d04 Hewlett-Packard 
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3. lspci -nn | grep Broadcom
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

sef@osg:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:3a:34:33  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:af:e9:8d  
         inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
         inet6 addr: fe80::222:5fff:feaf:e98d/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:57 errors:41 dropped:0 overruns:0 frame:627
         TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:6340 (6.3 KB)  TX bytes:5912 (5.9 KB)
         Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:8388 errors:0 dropped:0 overruns:0 frame:0
         TX packets:8388 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:1183085 (1.1 MB)  TX bytes:1183085 (1.1 MB)

sef@osg:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
         Link Quality:5  Signal level:209  Noise level:166
         Rx invalid nwid:0  invalid crypt:0  invalid misc:0
sef@osg:~$ iwconfig wlan0
wlan0     No such device

4. sef@osg:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE          1863  1 
nf_nat_h323             5978  0 
nf_conntrack_h323      55193  1 nf_nat_h323
nf_nat_pptp             2245  0 
nf_conntrack_pptp       5566  1 nf_nat_pptp
nf_conntrack_proto_gre     4798  1 nf_conntrack_pptp
nf_nat_proto_gre        1719  1 nf_nat_pptp
nf_nat_tftp             1017  0 
nf_conntrack_tftp       4001  1 nf_nat_tftp
nf_nat_sip              6169  0 
nf_conntrack_sip       18894  1 nf_nat_sip
iptable_nat             5219  1 
michael_mic             2164  4 
arc4                    1473  2 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61450  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
ipt_REJECT              2384  3 
ipt_LOG                 5370  4 
xt_limit                2180  6 
xt_tcpudp               2667  11 
ipt_addrtype            2151  4 
xt_state                1490  10 
ip6table_filter         2887  1 
snd_hda_intel          25773  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
ip6_tables             19618  1 ip6table_filter
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_dummy           1782  0 
nf_nat_ftp              2513  0 
nf_nat                 19501  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,iptable_nat,nf_nat_irc,nf_nat_ftp
snd_seq_oss            31219  0 
nf_conntrack_ipv4      12980  13 iptable_nat,nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_midi            5829  0 
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_rawmidi            23420  1 snd_seq_midi
nf_conntrack           73966  18 ipt_MASQUERADE,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,iptable_nat,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2791  1 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
ip_tables              18390  2 iptable_nat,iptable_filter
x_tables               22461  10 ipt_MASQUERADE,iptable_nat,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8676  0 
i915                  322087  4 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2177  0 
snd                    71187  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62595  0 
dell_laptop             7941  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
dcdbas                  6886  1 dell_laptop
usblp                  12407  0 
v4l2_compat_ioctl32    11956  1 videodev
psmouse                64576  0 
serio_raw               4918  0 
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
drm_kms_helper         30742  1 i915
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198948  5 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
intel_agp              29095  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41084  0 
hid                    83472  1 usbhid
usb_storage            49961  0 
ahci                   37870  2 
sky2                   48835  0 

lamod | grep “wlan_module_name

Not sure what module name is.

dmesg (I can only see the bottom part.  Is there a way to break it into sections?)

[    0.478217] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.478234] vgaarb: loaded
[    0.478347] SCSI subsystem initialized
[    0.478446] libata version 3.00 loaded.
[    0.478531] usbcore: registered new interface driver usbfs
[    0.478543] usbcore: registered new interface driver hub
[    0.478575] usbcore: registered new device driver usb
[    0.478771] ACPI: WMI: Mapper loaded
[    0.478773] PCI: Using ACPI for IRQ routing
[    0.479368] NetLabel: Initializing
[    0.479370] NetLabel:  domain hash size = 128
[    0.479371] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.479384] NetLabel:  unlabeled traffic allowed by default
[    0.479424] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.479430] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.490034] Switching to clocksource tsc
[    0.491900] AppArmor: AppArmor Filesystem Enabled
[    0.491921] pnp: PnP ACPI init
[    0.491943] ACPI: bus type pnp registered
[    0.542515] pnp: PnP ACPI: found 13 devices
[    0.542518] ACPI: ACPI bus type pnp unregistered
[    0.542535] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.542538] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.542553] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.542560] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.542564] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.542566] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    0.542569] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    0.542576] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.542578] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    0.542581] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    0.542584] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    0.542587] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.542590] system 00:0b: ioport range 0x1100-0x111f has been reserved
[    0.542592] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    0.542595] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.542601] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.542604] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.542606] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.542609] system 00:0c: iomem range 0xe0000-0xfffff has been reserved
[    0.542612] system 00:0c: iomem range 0x100000-0xddabf3ff could not be reserved
[    0.542615] system 00:0c: iomem range 0xddabf400-0xddafffff could not be reserved
[    0.542617] system 00:0c: iomem range 0xddb00000-0xddbfffff has been reserved
[    0.542620] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.542623] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.542626] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.542629] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.542632] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.542635] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.542637] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.542640] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.542643] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.542646] system 00:0c: iomem range 0xfed1c800-0xfed1cfff has been reserved
[    0.542649] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.542651] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.547452] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.547458] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.547465] pci 0000:00:1c.0:   MEM window: 0xf0200000-0xf03fffff
[    0.547471] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
[    0.547480] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.547483] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.547489] pci 0000:00:1c.1:   MEM window: 0xf6900000-0xf69fffff
[    0.547494] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
[    0.547503] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:09
[    0.547506] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.547512] pci 0000:00:1c.2:   MEM window: 0xf6800000-0xf68fffff
[    0.547517] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0800000-0x000000f09fffff
[    0.547525] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.547529] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.547535] pci 0000:00:1c.4:   MEM window: 0xf6600000-0xf67fffff
[    0.547540] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.547548] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.547550] pci 0000:00:1e.0:   IO window: disabled
[    0.547556] pci 0000:00:1e.0:   MEM window: disabled
[    0.547560] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.547583]   alloc irq_desc for 16 on node -1
[    0.547585]   alloc kstat_irqs on node -1
[    0.547593] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.547598] pci 0000:00:1c.0: setting latency timer to 64
[    0.547609]   alloc irq_desc for 17 on node -1
[    0.547611]   alloc kstat_irqs on node -1
[    0.547614] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.547619] pci 0000:00:1c.1: setting latency timer to 64
[    0.547630]   alloc irq_desc for 18 on node -1
[    0.547631]   alloc kstat_irqs on node -1
[    0.547634] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.547639] pci 0000:00:1c.2: setting latency timer to 64
[    0.547650] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.547655] pci 0000:00:1c.4: setting latency timer to 64
[    0.547664] pci 0000:00:1e.0: setting latency timer to 64
[    0.547669] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.547671] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.547674] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.547676] pci_bus 0000:0b: resource 1 mem: [0xf0200000-0xf03fffff]
[    0.547679] pci_bus 0000:0b: resource 2 pref mem [0xf0400000-0xf05fffff]
[    0.547681] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
[    0.547683] pci_bus 0000:0c: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.547686] pci_bus 0000:0c: resource 2 pref mem [0xf0600000-0xf07fffff]
[    0.547688] pci_bus 0000:09: resource 0 io:  [0xd000-0xdfff]
[    0.547690] pci_bus 0000:09: resource 1 mem: [0xf6800000-0xf68fffff]
[    0.547693] pci_bus 0000:09: resource 2 pref mem [0xf0800000-0xf09fffff]
[    0.547696] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.547698] pci_bus 0000:0d: resource 1 mem: [0xf6600000-0xf67fffff]
[    0.547700] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.547703] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.547705] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.547744] NET: Registered protocol family 2
[    0.547928] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.549294] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.554052] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.554586] TCP: Hash tables configured (established 524288 bind 65536)
[    0.554589] TCP reno registered
[    0.554714] NET: Registered protocol family 1
[    0.554737] pci 0000:00:02.0: Boot video device
[    0.555151] Scanning for low memory corruption every 60 seconds
[    0.555314] audit: initializing netlink socket (disabled)
[    0.555325] type=2000 audit(1286134559.549:1): initialized
[    0.565446] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.566904] VFS: Disk quotas dquot_6.5.2
[    0.566968] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.567578] fuse init (API version 7.13)
[    0.567671] msgmni has been set to 7834
[    0.567902] alg: No test for stdrng (krng)
[    0.567966] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.567970] io scheduler noop registered
[    0.567971] io scheduler anticipatory registered
[    0.567973] io scheduler deadline registered
[    0.568009] io scheduler cfq registered (default)
[    0.568181]   alloc irq_desc for 24 on node -1
[    0.568183]   alloc kstat_irqs on node -1
[    0.568195] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.568208] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.568372]   alloc irq_desc for 25 on node -1
[    0.568374]   alloc kstat_irqs on node -1
[    0.568383] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.568394] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.568554]   alloc irq_desc for 26 on node -1
[    0.568556]   alloc kstat_irqs on node -1
[    0.568565] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.568576] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.568730]   alloc irq_desc for 27 on node -1
[    0.568732]   alloc kstat_irqs on node -1
[    0.568740] pcieport 0000:00:1c.4: irq 27 for MSI/MSI-X
[    0.568751] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.568860] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.568978] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.569131] ACPI: AC Adapter [AC] (on-line)
[    0.569219] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.570506] ACPI: Lid Switch [LID]
[    0.570554] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.570561] ACPI: Power Button [PBTN]
[    0.570601] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.570604] ACPI: Sleep Button [SBTN]
[    0.571373] ACPI: SSDT 00000000ddac29cf 0023F (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.571819] ACPI: SSDT 00000000ddac2de5 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.572194] Monitor-Mwait will be used to enter C-1 state
[    0.572225] Monitor-Mwait will be used to enter C-2 state
[    0.572231] Marking TSC unstable due to TSC halts in idle
[    0.572292] processor LNXCPU:00: registered as cooling_device0
[    0.572770] ACPI: SSDT 00000000ddac2c0e 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.573106] ACPI: SSDT 00000000ddac33ab 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.573391] Switching to clocksource hpet
[    0.579969] processor LNXCPU:01: registered as cooling_device1
[    0.592058] thermal LNXTHERM:01: registered as thermal_zone0
[    0.592069] ACPI: Thermal Zone [THM] (59 C)
[    0.593688] Linux agpgart interface v0.103
[    0.593728] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.595038] brd: module loaded
[    0.595516] loop: module loaded
[    0.595617] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.596045] Fixed MDIO Bus: probed
[    0.596078] PPP generic driver version 2.4.2
[    0.596120] tun: Universal TUN/TAP device driver, 1.6
[    0.596122] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.596224] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.596254]   alloc irq_desc for 22 on node -1
[    0.596257]   alloc kstat_irqs on node -1
[    0.596264] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.596296] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.596300] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.596333] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.596369] ehci_hcd 0000:00:1a.7: debug port 1
[    0.600250] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.600280] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.631349] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.631831] usb usb1: configuration #1 chosen from 1 choice
[    0.631860] hub 1-0:1.0: USB hub found
[    0.632242] hub 1-0:1.0: 6 ports detected
[    0.632318]   alloc irq_desc for 20 on node -1
[    0.632320]   alloc kstat_irqs on node -1
[    0.632327] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.632355] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.632730] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.632775] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.632807] ehci_hcd 0000:00:1d.7: debug port 1
[    0.636689] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.636707] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.651709] ACPI: Battery Slot [BAT0] (battery present)
[    0.656051] Freeing initrd memory: 8138k freed
[    0.670024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.670170] usb usb2: configuration #1 chosen from 1 choice
[    0.670210] hub 2-0:1.0: USB hub found
[    0.670224] hub 2-0:1.0: 6 ports detected
[    0.670294] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.670317] uhci_hcd: USB Universal Host Controller Interface driver
[    0.670366] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.670378] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.670381] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.670420] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.670454] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    0.670552] usb usb3: configuration #1 chosen from 1 choice
[    0.670577] hub 3-0:1.0: USB hub found
[    0.670584] hub 3-0:1.0: 2 ports detected
[    0.670631]   alloc irq_desc for 21 on node -1
[    0.670633]   alloc kstat_irqs on node -1
[    0.670639] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.670646] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.670649] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.670690] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.670729] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    0.670819] usb usb4: configuration #1 chosen from 1 choice
[    0.670846] hub 4-0:1.0: USB hub found
[    0.670852] hub 4-0:1.0: 2 ports detected
[    0.670901] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.670907] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.670911] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.670945] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.670976] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    0.671059] usb usb5: configuration #1 chosen from 1 choice
[    0.671086] hub 5-0:1.0: USB hub found
[    0.671092] hub 5-0:1.0: 2 ports detected
[    0.671137] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.671143] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.671147] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.671186] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.671215] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    0.671304] usb usb6: configuration #1 chosen from 1 choice
[    0.671328] hub 6-0:1.0: USB hub found
[    0.671334] hub 6-0:1.0: 2 ports detected
[    0.671381] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.671387] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.671391] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.671422] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.671455] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    0.671540] usb usb7: configuration #1 chosen from 1 choice
[    0.671564] hub 7-0:1.0: USB hub found
[    0.671570] hub 7-0:1.0: 2 ports detected
[    0.671620] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.671626] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.671630] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.671661] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.671689] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.671781] usb usb8: configuration #1 chosen from 1 choice
[    0.671805] hub 8-0:1.0: USB hub found
[    0.671811] hub 8-0:1.0: 2 ports detected
[    0.671906] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.690140] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.705551] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.705557] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.705582] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.705605] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.705626] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.705743] mice: PS/2 mouse device common for all mice
[    0.706710] rtc_cmos 00:04: RTC can wake from S4
[    0.706755] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.706787] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.706917] device-mapper: uevent: version 1.0.3
[    0.707038] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.707119] device-mapper: multipath: version 1.1.0 loaded
[    0.707122] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.707344] cpuidle: using governor ladder
[    0.707428] cpuidle: using governor menu
[    0.707763] TCP cubic registered
[    0.707911] NET: Registered protocol family 10
[    0.708343] lo: Disabled Privacy Extensions
[    0.708617] NET: Registered protocol family 17
[    0.710508] PM: Resume from disk failed.
[    0.710519] registered taskstats version 1
[    0.711305]   Magic number: 14:844:646
[    0.711429] rtc_cmos 00:04: setting system clock to 2010-10-03 19:36:00 UTC (1286134560)
[    0.711433] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.711434] EDD information not available.
[    0.711498] Freeing unused kernel memory: 872k freed
[    0.711759] Write protecting the kernel read-only data: 7692k
[    0.729513] udev: starting version 151
[    0.735425] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.836331] sky2 driver version 1.25
[    0.836401] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.836422] sky2 0000:09:00.0: setting latency timer to 64
[    0.836471] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    0.836578]   alloc irq_desc for 28 on node -1
[    0.836580]   alloc kstat_irqs on node -1
[    0.836598] sky2 0000:09:00.0: irq 28 for MSI/MSI-X
[    0.837261] sky2 eth0: addr 00:23:ae:3a:34:33
[    0.853726] ahci 0000:00:1f.2: version 3.0
[    0.853748] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.853809]   alloc irq_desc for 29 on node -1
[    0.853812]   alloc kstat_irqs on node -1
[    0.853824] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.853880] ahci: SSS flag set, parallel bus scan disabled
[    0.853923] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.853927] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    0.853933] ahci 0000:00:1f.2: setting latency timer to 64
[    0.920133] scsi0 : ahci
[    0.920271] scsi1 : ahci
[    0.920355] scsi2 : ahci
[    0.920420] scsi3 : ahci
[    0.920482] scsi4 : ahci
[    0.920542] scsi5 : ahci
[    0.920989] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 29
[    0.920993] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 29
[    0.920995] ata3: DUMMY
[    0.920997] ata4: DUMMY
[    0.921000] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 29
[    0.921003] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 29
[    1.000053] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    1.151109] usb 1-5: configuration #1 chosen from 1 choice
[    1.161301] Initializing USB Mass Storage driver...
[    1.161468] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.161561] usbcore: registered new interface driver usb-storage
[    1.161564] USB Mass Storage support registered.
[    1.161571] usb-storage: device found at 2
[    1.161572] usb-storage: waiting for device to settle before scanning
[    1.260047] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.261687] ata1.00: ATA-8: WDC WD5000BEVT-75ZAT0, 01.01A01, max UDMA/133
[    1.261690] ata1.00: 976773168 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    1.263418] ata1.00: configured for UDMA/133
[    1.270044] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.280142] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-7 01.0 PQ: 0 ANSI: 5
[    1.280328] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.280425] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.280472] sd 0:0:0:0: [sda] Write Protect is off
[    1.280474] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.280497] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.280636]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.350691] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.496103] usb 1-6: configuration #1 chosen from 1 choice
[    1.950057] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    2.030075] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.042819] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7560S, SD03, max UDMA/100
[    2.056481] ata2.00: configured for UDMA/100
[    2.072385] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7560S SD03 PQ: 0 ANSI: 5
[    2.079122] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.079126] Uniform CD-ROM driver Revision: 3.20
[    2.079256] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.079326] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.129341] usb 6-1: configuration #1 chosen from 1 choice
[    2.410051] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    2.420063] ata5: SATA link down (SStatus 0 SControl 300)
[    2.601371] usb 6-2: configuration #1 chosen from 1 choice
[    2.790084] ata6: SATA link down (SStatus 0 SControl 300)
[    2.815238] usbcore: registered new interface driver hiddev
[    2.828542] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5
[    2.828658] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1/input0
[    2.828704] usbcore: registered new interface driver usbhid
[    2.828707] usbhid: v2.6:USB HID core driver
[    3.599745] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.150345] usb-storage: device scan complete
[    6.152424] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.152959] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.157020] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   16.125085] udev: starting version 151
[   16.136309] Adding 4297348k swap on /dev/sda7.  Priority:-1 extents:1 across:4297348k 
[   16.193435] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   16.196687] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   16.261304] lp: driver loaded but no devices found
[   16.473115] [drm] Initialized drm 1.1.0 20060810
[   16.478371] lib80211: common routines for IEEE802.11 drivers
[   16.478375] lib80211_crypt: registered algorithm 'NULL'
[   16.484592] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.484595] Disabling lock debugging due to kernel taint
[   16.495296] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.498308] Linux video capture interface: v2.00
[   16.501398] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1D04
[   16.501418] usbcore: registered new interface driver usblp
[   16.512969] uvcvideo: Found UVC 1.00 device Integrated_Webcam_1.3M (0c45:63ee)
[   16.522435] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.522450] wl 0000:0c:00.0: setting latency timer to 64
[   16.528906] input: Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
[   16.529901] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   16.550916] usbcore: registered new interface driver uvcvideo
[   16.550920] USB Video Class driver (v0.1.0)
[   16.553740] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   16.604519] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.604525] i915 0000:00:02.0: setting latency timer to 64
[   16.608295] lib80211_crypt: registered algorithm 'TKIP'
[   16.608805] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   16.634235] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.644247] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   16.644252] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   16.644342]   alloc irq_desc for 30 on node -1
[   16.644344]   alloc kstat_irqs on node -1
[   16.644357] i915 0000:00:02.0: irq 30 for MSI/MSI-X
[   16.644365] [drm] set up 31M of stolen space
[   16.651337] type=1505 audit(1286159776.431:2):  operation="profile_load" pid=733 name="/sbin/dhclient3"
[   16.652019] type=1505 audit(1286159776.431:3):  operation="profile_load" pid=733 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.652384] type=1505 audit(1286159776.431:4):  operation="profile_load" pid=733 name="/usr/lib/connman/scripts/dhclient-script"
[   16.660354] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.662790] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.662795] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   16.662797] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.753841] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   17.048791] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input8
[   17.076313] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input9
[   17.329507] fb0: inteldrmfb frame buffer device
[   17.329510] registered panic notifier
[   17.342952] acpi device:39: registered as cooling_device2
[   17.344421] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input10
[   17.344526] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.344606] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   17.344757] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:02/input/input11
[   17.344847] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   17.344915] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.345230] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.345285] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.347382] vga16fb: initializing
[   17.347388] vga16fb: mapped to 0xffff8800000a0000
[   17.347392] vga16fb: not registering due to another framebuffer present
[   17.482076] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   17.514019] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.514271] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   17.783207] Console: switching to colour frame buffer device 170x48
[   17.867838] type=1505 audit(1286159777.648:5):  operation="profile_load" pid=1032 name="/usr/share/gdm/guest-session/Xsession"
[   17.869694] type=1505 audit(1286159777.648:6):  operation="profile_replace" pid=1033 name="/sbin/dhclient3"
[   17.870386] type=1505 audit(1286159777.658:7):  operation="profile_replace" pid=1033 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.870757] type=1505 audit(1286159777.658:8):  operation="profile_replace" pid=1033 name="/usr/lib/connman/scripts/dhclient-script"
[   17.874325] type=1505 audit(1286159777.658:9):  operation="profile_load" pid=1034 name="/usr/bin/evince"
[   17.886955] type=1505 audit(1286159777.668:10):  operation="profile_load" pid=1034 name="/usr/bin/evince-previewer"
[   17.892556] type=1505 audit(1286159777.678:11):  operation="profile_load" pid=1034 name="/usr/bin/evince-thumbnailer"
[   18.359677] sky2 eth0: enabling interface
[   18.360569] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.572094] ppdev: user-space parallel port driver
[   19.700747] usb 6-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   28.550053] eth1: no IPv6 routers present
[   45.046554] lo: Disabled Privacy Extensions
[  624.210260] CE: hpet increasing min_delta_ns to 15000 nsec
[ 5743.893536] lo: Disabled Privacy Extensions
6. sef@osg:~$ sudo lshw -C network
[sudo] password for sef: 
 *-network               
      description: Wireless interface
      product: BCM4312 802.11b/g
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:0c:00.0
      logical name: eth1
      version: 01
      serial: 00:22:5f:af:e9:8d
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
      resources: irq:17 memory:f69fc000-f69fffff
 *-network
      description: Ethernet interface
      product: 88E8040 PCI-E Fast Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@0000:09:00.0
      logical name: eth0
      version: 13
      serial: 00:23:ae:3a:34:33
      capacity: 100MB/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
      resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

7. sef@osg:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

8. sef@osg:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS

9. sef@osg:~$ uname -mr
2.6.32-25-generic x86_64

10. sef@osg:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth0=eth0.
                                                                        [ OK ]

```

---

