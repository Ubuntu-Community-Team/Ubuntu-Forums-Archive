---
title: "AverMedia AverTV Cardbus Hybrid E506R"
date: 2009-04-19
forum: Multimedia Software
---

### Post by SunflowerIT on 2009-04-19
;);)
Hello sound is not working :)

Kernel 2.6.27  .Carefully looked to internet found interesting fact
about this/.


File: avermedia-e506r-2.6.28.patch

--- a/linux/drivers/media/video/saa7134/saa7134-cards.c	Mon Oct 13 09:37:06 2008 -0200
+++ b/linux/drivers/media/video/saa7134/saa7134-cards.c	Fri Nov 14 01:03:00 2008 +0000
@@ -6151,7 +6151,7 @@
 		struct v4l2_priv_tun_config  xc2028_cfg;
 		struct xc2028_ctrl           ctl;
 
-		memset(&xc2028_cfg, 0, sizeof(ctl));
+		memset(&xc2028_cfg, 0, sizeof(xc2028_cfg));
 		memset(&ctl, 0, sizeof(ctl));
 
 		ctl.fname   = XC2028_DEFAULT_FIRMWARE;

Applied new patch to kernel 2.6.28

Compiled  New kernel....

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Installed 

sound still not working

root@heaven:~# lsmod
Module                  Size  Used by
pppoe                  18240  2 
pppox                  11404  1 pppoe
ppp_generic            32284  6 pppoe,pppox
slhc                   14336  1 ppp_generic
ipw2200               149832  0 
ipt_REJECT             11264  1 
xt_tcpudp              11264  3 
ipt_MASQUERADE         11008  1 
xt_state               10240  3 
iptable_mangle         11008  0 
i915                   64772  2 
iptable_nat            13700  1 
drm                    96040  3 i915
af_packet              25344  4 
nf_nat                 26260  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21516  6 iptable_nat,nf_nat
nf_conntrack           72008  5 ipt_MASQUERADE,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         10240  1 nf_conntrack_ipv4
binfmt_misc            16776  1 
sco                    18180  2 
bridge                 56212  0 
stp                    10756  1 bridge
bnep                   20352  2 
rfcomm                 43280  0 
l2cap                  29952  6 bnep,rfcomm
bluetooth              61412  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
acpi_cpufreq           16140  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       15372  1 
cpufreq_stats          13316  0 
freq_table             12800  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14472  0 
cpufreq_userspace      11396  0 
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
container              11648  0 
input_polldev          12040  0 
iptable_filter         11008  1 
ip_tables              19472  3 iptable_mangle,iptable_nat,iptable_filter
x_tables               23044  6 ipt_REJECT,xt_tcpudp,ipt_MASQUERADE,xt_state,iptable_nat,ip_tables
parport_pc             40100  0 
lp                     17156  0 
parport                42476  3 ppdev,parport_pc,lp
mt352                  14596  1 
saa7134_dvb            28812  0 
videobuf_dvb           15364  1 saa7134_dvb
dvb_core               91904  2 saa7134_dvb,videobuf_dvb
saa7134_alsa           20000  0 
tuner_xc2028           30000  2 
tuner                  32964  0 
saa7134               152404  2 saa7134_dvb,saa7134_alsa
ir_common              52356  1 saa7134
videodev               41728  2 tuner,saa7134
v4l1_compat            21892  1 videodev
compat_ioctl32          9472  1 saa7134
v4l2_common            21120  2 tuner,saa7134
videobuf_dma_sg        20612  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          26372  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               20356  1 saa7134
i2c_core               32020  7 mt352,saa7134_dvb,tuner_xc2028,tuner,saa7134,v4l2_common,tveeprom
pcmcia                 44876  0 
rfkill                 19020  0 
led_class              12292  0 
wmi                    14760  0 
psmouse                49680  0 
serio_raw              13572  0 
ieee80211              37832  1 ipw2200
ieee80211_crypt        13700  1 ieee80211
joydev                 18368  0 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  17696  15 
pcspkr                 10752  0 
iTCO_wdt               19236  0 
iTCO_vendor_support    11780  1 iTCO_wdt
snd_hda_intel         419508  7 
snd_pcm_oss            46208  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82692  5 saa7134_alsa,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11012  0 
snd_seq_oss            38016  0 
snd_seq_midi           14464  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15360  2 snd_seq_oss,snd_seq_midi
video                  24976  0 
output                 11136  1 video
snd_seq                57008  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29320  4 snd_pcm,snd_seq
shpchp                 40340  0 
pci_hotplug            34720  1 shpchp
snd_seq_device         15244  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62500  23 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15456  1 snd
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm
battery                18436  0 
ac                     12420  0 
button                 14352  0 
intel_agp              34108  1 
agpgart                42440  3 drm,intel_agp
ipv6                  258420  45 
ext3                  133128  1 
jbd                    55188  1 ext3
mbcache                16132  1 ext3
usbhid                 31968  0 
hid                    49152  1 usbhid
usb_storage            81984  4 
libusual               30484  1 usb_storage
sr_mod                 22212  0 
cdrom                  42784  1 sr_mod
sd_mod                 41880  6 
crc_t10dif             10112  1 sd_mod
sg                     36404  0 
ata_piix               29700  0 
pata_acpi              12416  0 
ata_generic            13060  0 
libata                179872  3 ata_piix,pata_acpi,ata_generic
8139too                31488  0 
8139cp                 28032  0 
mii                    13568  2 8139too,8139cp
scsi_mod              158996  5 usb_storage,sr_mod,sd_mod,sg,libata
ehci_hcd               43276  0 
uhci_hcd               30864  0 
usbcore               152464  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23580  0 
processor              48812  3 acpi_cpufreq,thermal
fan                    12676  0 
fuse                   59548  7 
root@heaven:~# 


logs from kernel 2.6.28

Apr 19 20:49:50 heaven kernel: [   30.356196] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Apr 19 20:49:50 heaven kernel: [   30.357922] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Apr 19 20:49:50 heaven kernel: [   30.358650] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Apr 19 20:49:50 heaven kernel: [   30.359253] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Apr 19 20:49:50 heaven kernel: [   30.360031] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Apr 19 20:49:50 heaven kernel: [   30.564675] Linux video capture interface: v2.00
Apr 19 20:49:50 heaven kernel: [   30.731103] saa7130/34: v4l2 driver version 0.2.14 loaded
Apr 19 20:49:50 heaven kernel: [   30.731157] saa7134 0000:07:00.0: enabling device (0000 -> 0002)
Apr 19 20:49:50 heaven kernel: [   30.731166] saa7134 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 19 20:49:50 heaven kernel: [   30.731175] saa7133[0]: found at 0000:07:00.0, rev: 209, irq: 18, latency: 0, mmio: 0x58000000
Apr 19 20:49:50 heaven kernel: [   30.731190] saa7133[0]: subsystem: 1461:f436, board: AVerMedia Cardbus TV/Radio (E506R) [card=136,autodetected]
Apr 19 20:49:50 heaven kernel: [   30.731323] saa7133[0]: board init: gpio is 220000
Apr 19 20:49:50 heaven kernel: [   30.900029] saa7133[0]: i2c eeprom 00: 61 14 36 f4 00 00 00 00 00 00 00 00 00 00 00 00
Apr 19 20:49:50 heaven kernel: [   30.900039] saa7133[0]: i2c eeprom 10: 00 ff e2 0e ff 20 ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900049] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900058] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900067] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900077] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900086] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900095] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900104] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900114] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900123] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900132] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900141] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900151] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900160] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.900169] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 19 20:49:50 heaven kernel: [   30.932039] tuner' 0-0061: chip found @ 0xc2 (saa7133[0])
Apr 19 20:49:50 heaven kernel: [   31.011109] xc2028 0-0061: creating new instance
Apr 19 20:49:50 heaven kernel: [   31.011113] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Apr 19 20:49:50 heaven kernel: [   31.011135] i2c-adapter i2c-0: firmware: using built-in firmware xc3028-v27.fw
Apr 19 20:49:50 heaven kernel: [   31.011138] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Apr 19 20:49:50 heaven kernel: [   31.024036] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Apr 19 20:49:50 heaven kernel: [   39.552031] (0), id 00000000000000ff:
Apr 19 20:49:50 heaven kernel: [   39.552033] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
Apr 19 20:49:50 heaven kernel: [   39.720029] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.
Apr 19 20:49:50 heaven kernel: [   40.161106] saa7133[0]: registered device video0 [v4l2]
Apr 19 20:49:50 heaven kernel: [   40.161864] saa7133[0]: registered device vbi0
Apr 19 20:49:50 heaven kernel: [   40.162618] saa7133[0]: registered device radio0
Apr 19 20:49:50 heaven kernel: [   40.585840] saa7134 ALSA driver for DMA sound loaded
Apr 19 20:49:50 heaven kernel: [   40.585874] saa7133[0]/alsa: saa7133[0] at 0x58000000 irq 18 registered as card -2
Apr 19 20:49:50 heaven kernel: [   40.733093] dvb_init() allocating 1 frontend
Apr 19 20:49:50 heaven kernel: [   40.820136] xc2028 0-0061: attaching existing instance
Apr 19 20:49:50 heaven kernel: [   40.820140] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Apr 19 20:49:50 heaven kernel: [   40.820144] DVB: registering new adapter (saa7133[0])



logs from UBUNTU orignal kernel 2.6.27

Apr 18 20:03:48 heaven kernel: [   30.313363] acer-wmi: Acer Laptop ACPI-WMI Extras
Apr 18 20:03:48 heaven kernel: [   31.784124] cs: IO port probe 0x100-0x3af: clean.
Apr 18 20:03:48 heaven kernel: [   31.785855] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Apr 18 20:03:48 heaven kernel: [   31.786589] cs: IO port probe 0x820-0x8ff: clean.
Apr 18 20:03:48 heaven kernel: [   31.787194] cs: IO port probe 0xc00-0xcf7: clean.
Apr 18 20:03:48 heaven kernel: [   31.787961] cs: IO port probe 0xa00-0xaff: clean.
Apr 18 20:03:48 heaven kernel: [   31.832971] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Apr 18 20:03:48 heaven kernel: [   31.921887] Linux video capture interface: v2.00
Apr 18 20:03:48 heaven kernel: [   31.979490] saa7130/34: v4l2 driver version 0.2.14 loaded
Apr 18 20:03:48 heaven kernel: [   31.979539] saa7134 0000:07:00.0: enabling device (0000 -> 0002)
Apr 18 20:03:48 heaven kernel: [   31.979550] saa7134 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 18 20:03:48 heaven kernel: [   31.979559] saa7133[0]: found at 0000:07:00.0, rev: 209, irq: 18, latency: 0, mmio: 0x58000000
Apr 18 20:03:48 heaven kernel: [   31.979574] saa7133[0]: subsystem: 1461:f436, board: AVerMedia Cardbus TV/Radio (E506R) [card=136,autodetected]
Apr 18 20:03:48 heaven kernel: [   31.979586] saa7133[0]: board init: gpio is 220000
Apr 18 20:03:48 heaven kernel: [   32.148024] saa7133[0]: i2c eeprom 00: 61 14 36 f4 00 00 00 00 00 00 00 00 00 00 00 00
Apr 18 20:03:48 heaven kernel: [   32.148035] saa7133[0]: i2c eeprom 10: 00 ff e2 0e ff 20 ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148045] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148055] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148066] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148076] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148086] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148097] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148107] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148117] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148127] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148138] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148148] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148158] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148168] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.148179] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Apr 18 20:03:48 heaven kernel: [   32.172038] tuner' 0-0061: chip found @ 0xc2 (saa7133[0])
Apr 18 20:03:48 heaven kernel: [   32.254505] xc2028 0-0061: creating new instance
Apr 18 20:03:48 heaven kernel: [   32.254509] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Apr 18 20:03:48 heaven kernel: [   32.254529] firmware: requesting xc3028-v27.fw
Apr 18 20:03:48 heaven kernel: [   32.298293] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Apr 18 20:03:48 heaven kernel: [   32.312034] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Apr 18 20:03:48 heaven kernel: [   40.840030] (0), id 00000000000000ff:
Apr 18 20:03:48 heaven kernel: [   40.840033] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
Apr 18 20:03:48 heaven kernel: [   41.008029] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.
Apr 18 20:03:48 heaven kernel: [   41.457332] saa7133[0]: registered device video0 [v4l2]
Apr 18 20:03:48 heaven kernel: [   41.457574] saa7133[0]: registered device vbi0
Apr 18 20:03:48 heaven kernel: [   41.457744] saa7133[0]: registered device radio0
Apr 18 20:03:48 heaven kernel: [   41.816163] saa7134 ALSA driver for DMA sound loaded
Apr 18 20:03:48 heaven kernel: [   41.816197] saa7133[0]/alsa: saa7133[0] at 0x58000000 irq 18 registered as card -2
Apr 18 20:03:48 heaven kernel: [   41.908128] xc2028 0-0061: attaching existing instance
Apr 18 20:03:48 heaven kernel: [   41.908133] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Apr 18 20:03:48 heaven kernel: [   41.908137] DVB: registering new adapter (saa7133[0])
Apr 18 20:03:48 heaven kernel: [   41.908140] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
Apr 18 20:03:48 heaven kernel: [   42.661588] lp: driver loaded but no devices found
Apr 18 20:03:48 heaven kernel: [   42.942253] Adding 3068372k swap on /dev/sdc5.  Priority:-1 extents:1 across:3068372k
Apr 18 20:03:48 heaven kernel: [   43.485452] EXT3 FS on sdc6, internal journal
Apr 18 20:03:48 heaven kernel: [   44.727248] type=1505 audit(1240056226.230:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4385
Apr 18 20:03:48 heaven kernel: [   44.945073] type=1505 audit(1240056226.450:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4390
Apr 18 20:03:48 heaven kernel: [   44.945367] type=1505 audit(1240056226.450:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4390
Apr 18 20:03:48 heaven kernel: [   45.002027] type=1505 audit(1240056226.506:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4394
Apr 18 20:03:48 heaven kernel: [   45.066941] type=1505 audit(1240056226.570:6): operation="profile_load" name="/usr/sbin/named" name2="default" pid=4398
Apr 18 20:03:48 heaven kernel: [   45.216447] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 18 20:03:48 heaven kernel: [   47.157130] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Apr 18 20:03:51 heaven kernel: [   50.269142] type=1503 audit(1240056231.774:7): operation="capable" name="sys_resource" pid=5018 profile="/usr/sbin/named"
Apr 18 20:03:51 heaven kernel: [   50.270986] type=1503 audit(1240056231.774:8): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=116 name="/proc/5017/net/if_inet6" pid=5018 profile="/usr/sbin/named"
Apr 18 20:03:51 heaven kernel: [   50.284570] type=1503 audit(1240056231.790:9): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=116 name="/proc/5017/net/if_inet6" pid=5018 profile="/usr/sbin/named"
Apr 18 20:04:09 heaven kernel: [   67.578425] apm: BIOS not found.
Apr 18 20:04:09 heaven kernel: [   67.794005] ppdev: user-space parallel port driver
Apr 18 20:04:19 heaven kernel: [   77.532036] xc2028 0-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
Apr 18 20:04:27 heaven kernel: [   85.892047] xc2028 0-0061: Loading firmware for type=FM (400), id 0000000000000000.
Apr 18 20:04:27 heaven kernel: [   86.264058] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Apr 18 20:04:36 heaven kernel: [   94.812049] (0), id 00000000000000ff:
Apr 18 20:04:36 heaven kernel: [   94.812061] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
Apr 18 20:04:36 heaven kernel: [   94.980046] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.

---

