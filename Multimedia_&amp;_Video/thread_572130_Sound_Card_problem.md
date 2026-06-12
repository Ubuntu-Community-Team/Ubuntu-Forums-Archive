---
title: "Sound Card problem"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by Aryding on 2007-10-10
Not sure why my sound doesn't work... I've read almost everything I could find on the forum, but this is where I'm stuck at:

Any help would be great!  This is the last thing stopping me from totally converting to linux over windows!

Typed code into terminal: aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Next code: lspci -v

(I bolded my sound card results)

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-0000bfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000ddefffff
        Capabilities: <access denied>

[B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1302
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[/B]

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe000000-fe0fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fe100000-fe1fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: fea00000-feafffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 10b2
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at b000 [size=256]
        Memory at fdff0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fdfc0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at c800 [size=256]
        Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fe0e0000 [disabled] [size=64K]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

06:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: medium devsel, IRQ 10
        Memory at feafec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1307
        Flags: medium devsel, IRQ 10
        Memory at feafe800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by Aryding on 2007-10-11
Bump...  Anything?

---

### Post by Aryding on 2007-10-11
The driver that I installed was the HDA Intel one, btw.

---

### Post by nzadLithium on 2007-10-11
Subsystem: ASUSTeK Computer Inc. Unknown device 1302

im pretty sure that is your problem.

can you post a link to where you got the driver from?

---

### Post by Aryding on 2007-10-11
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

The hda-intel driver

---

### Post by nzadLithium on 2007-10-11
can you post the output of lsmod?

---

### Post by Aryding on 2007-10-12
results of lsmod

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
fglrx                 540004  40 
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  2 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sbs                    15652  0 
asus_acpi              17308  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
video                  16388  0 
container               5248  0 
battery                10756  0 
button                  8720  0 
dock                   10268  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
nls_utf8                3072  2 
ntfs                  107764  2 
ipv6                  268960  12 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
ipw3945               118816  1 
sdhci                  18700  0 
tpm_infineon            9112  0 
tpm                    16672  1 tpm_infineon
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
irda                  201276  0 
mmc_core               26756  1 sdhci
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
crc_ccitt               3072  1 irda
tpm_bios                8448  1 tpm
joydev                 10816  0 
hci_usb                18204  2 
bluetooth              55908  7 rfcomm,l2cap,hci_usb
pcspkr                  4224  0 
intel_agp              26140  1 
psmouse                38920  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
serio_raw               7940  0 
agpgart                35400  2 fglrx,intel_agp
snd_pcm                79876  2 snd_hda_intel,snd_hda_codec
snd_timer              23684  1 snd_pcm
snd                    54020  6 snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
af_packet              23816  6 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  6 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
ata_generic             9092  0 
ata_piix               15492  4 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
r8169                  32392  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 hci_usb,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by Aryding on 2007-10-12
I just upgraded to gutsy and now it works...  Hmmmm

Thanks for the support though!

---

