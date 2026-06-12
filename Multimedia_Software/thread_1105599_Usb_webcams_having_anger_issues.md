---
title: "Usb webcams having anger issues"
date: 2009-03-24
forum: Multimedia Software
---

### Post by iscariot on 2009-03-24
Hey everybody.  I'm having some issues.  I friend gave me a Logitech Quickcam express.  I couldn't get it going so I tried downloading and installing that gspcav driver.  I now have lost one of my other webcams I had connected.  When I look in /dev I see only video0, there should also be video1 and video2.  All the other cameras were working but now none of them seem to want to work.  Here's the output of lsusb 

Bus 004 Device 002: ID 04f2:a133 Chicony Electronics Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 001 Device 001: ID 0000:0000

and the output of lsmod

Module                  Size  Used by
zc0301                 54148  0
gspca_zc3xx            48256  0
gspca_main             22784  1 gspca_zc3xx
compat_ioctl32          2304  0
videodev               36864  2 zc0301,gspca_main
v4l1_compat            15748  1 videodev
af_packet              23812  2
via                    43648  2
drm                    82452  3 via
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
ipv6                  267780  78
cpufreq_powersave       2688  0
cpufreq_stats           7104  0
cpufreq_ondemand        9740  0
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
sbs                    15112  0
container               5632  0
dock                   11280  0
sbshc                   7680  1 sbs
video                  19856  0
output                  4736  1 video
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0
rtl8180                32256  0
lbm_cw_mac80211       233076  1 rtl8180
lbm_cw_cfg80211        36448  2 rtl8180,lbm_cw_mac80211
eeprom_93cx6            3200  1 rtl8180
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
evdev                  13056  3
serio_raw               7940  0
psmouse                40336  0
pcspkr                  4224  0
via_ircc               27796  0
irda                  203068  1 via_ircc
button                  9232  0
crc_ccitt               3072  1 irda
i2c_viapro              9876  0
i2c_core               24832  1 i2c_viapro
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
via_agp                11136  1
agpgart                34760  2 drm,via_agp
ext3                  136840  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
dm_mirror              24832  2
dm_mod                 62660  6 dm_mirror
pata_acpi               8320  0
pata_via               13316  2
sg                     36880  0
sd_mod                 30720  5
via_rhine              26632  0
mii                     6400  1 via_rhine
ata_generic             8324  0
ehci_hcd               37900  0
uhci_hcd               27024  0
sata_sil               12296  2
usbcore               146412  6 zc0301,gspca_zc3xx,gspca_main,ehci_hcd,uhci_hcd
libata                159344  4 pata_acpi,pata_via,ata_generic,sata_sil
scsi_mod              151436  3 sg,sd_mod,libata
thermal                16796  0
processor              37384  1 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

Can someone please give me a hand getting my three usb cameras going?

---

### Post by iscariot on 2009-03-25
Bump

---

