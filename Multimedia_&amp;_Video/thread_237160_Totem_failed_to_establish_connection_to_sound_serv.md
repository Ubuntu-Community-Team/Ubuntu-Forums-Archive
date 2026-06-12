---
title: "Totem: failed to establish connection to sound server ( Sony Vaio )"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by alakriti on 2006-08-15
if anyone could offer me some suggestions on things to try i would be greatful, i have been fighting to get sound working on this laptop Sony Vaio ( FE550G ) and have had no luck, sound worked when i installed and works when i boot from the live CD, but after an update i believe is when it stopped working i have tried outputing lsmod and it seems all the same modules are loaded on the livecd as are on my install. i have tried following the comprehensive sound guide and havent had any luck either. i have also reinstalled alsa etc. and still have had no luck.

output:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [5109]

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: fast devsel
        Memory at 52000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: [d0] Power Management version 2

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d01c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8000000-c9ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c1f00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: ca000000-cbffffff
        Prefetchable memory behind bridge: 00000000c2000000-00000000c3f00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: cc000000-cdffffff
        Prefetchable memory behind bridge: 00000000c4000000-00000000c5f00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: ce000000-cfffffff
        Prefetchable memory behind bridge: 00000000c6000000-00000000c7f00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 58
        Memory at d03c4000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] #09 [100c]

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 50
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d03c4400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)        Subsystem: Intel Corporation: Unknown device 1050
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] #10 [0011]

0000:0a:03.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 00006400-000064ff
        I/O window 1: 00006800-000068ff
        16-bit legacy interface ports at 0001

0000:0a:03.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d0006000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:0a:03.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: medium devsel, IRQ 3
        Memory at d0004000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: [44] Power Management version 2

0000:0a:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)
        Subsystem: Sony Corporation: Unknown device 81ef
        Flags: bus master, medium devsel, latency 64, IRQ 74
        Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 6000 [size=64]
        Capabilities: [dc] Power Management version 2



lsmod

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
sonypi                 23084  0
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
arc4                    2048  1
parport                36296  3 ppdev,parport_pc,lp
ieee80211_crypt_wep     4992  1
af_packet              22920  4
ipw3945               126620  1
pcmcia                 40508  0
joydev                 10048  0
e100                   40580  0
mii                     5888  1 e100
tsdev                   8000  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              37064  1 ipw3945
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
snd_hda_intel          18964  3
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  3 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
sg                     37920  0
ext3                  135688  1
jbd                    58772  1 ext3
usb_storage            74176  0
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  4 usb_storage,ehci_hcd,uhci_hcd
sd_mod                 19984  3
ata_piix               11012  6
libata                 78992  1 ata_piix
scsi_mod              139496  6 sr_mod,sbp2,sg,usb_storage,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit







this is lsmod from the live cd



Module                  Size  Used by
arc4                    2048  1
ieee80211_crypt_wep     4992  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipv6                  265600  6
sonypi                 23084  0
ppdev                   9220  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
i915                   20608  1
drm                    73236  2 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
pcmcia                 40508  0
joydev                 10048  0
tsdev                   8000  0
ipw3945               126492  1
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
rtc                    13492  0
psmouse                36228  0
serio_raw               7300  0
ieee80211              37064  1 ipw3945
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
intel_agp              22940  1
af_packet              22920  4
agpgart                34888  3 drm,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  2
e100                   40580  0
mii                     5888  1 e100
squashfs               44980  1
unionfs                89884  1
loop                   17288  2
nls_cp437               5888  1
isofs                  37688  1
ide_generic             1536  0
usb_storage            74176  0
ohci1394               35124  0
uhci_hcd               33680  0
ieee1394              299832  1 ohci1394
ehci_hcd               32008  0
usbcore               129668  4 usb_storage,uhci_hcd,ehci_hcd
sd_mod                 19984  2
ata_piix               11012  5
libata                 78992  1 ata_piix
scsi_mod              139496  4 sg,usb_storage,sd_mod,libata
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


any suggestions would be helpful,

thanks in advance

---

### Post by exactt on 2006-09-06
had the same problem on my machine...

removing my logitech webcam(which has a built-in mic) did the thing...

---

