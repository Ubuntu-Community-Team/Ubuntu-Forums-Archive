---
title: "bttv/bt87x blacklist problems in xen"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by John Williams on 2007-04-25
I am running xen on Feisty desktop. Got is all running with the very good howtos, even running gdm/gnome!

:guitar: 

I am wanting to run a LAMP stack in a domU so that I can isolate external apache access from my other apps running in the dom0 (samba, email, backups). In the DomU I am running Zoneminder, on apache/mysql/python. Yes, this is all working.

The problem is that I am trying to pass my pci capture card to domU. I used pciback on the boot cmd line and blacklisted as much bttv stuff as I could. 

blacklist is - 

# blacklist video drivers 
blacklist bttv
blacklist bt878
blacklist snd_bt87x
blacklist dvb_bt8xx

I see a dmesg saying the device is being seized. 

[    0.447738] pciback 0000:02:02.0: seizing device
[    0.447805] pciback 0000:02:02.1: seizing device

But when I bring up the guest I get this in the dom0 dmesg

pciback: vpci: 0000:02:02.0: assign to virtual slot 0
pciback pci-1-0: 22 Couldn't locate PCI device (0000:02:02.0)! perhaps already in-use?

lsmod is - 

Module                  Size  Used by
xt_physdev              4112  1 
iptable_filter          4096  1 
ip_tables              15204  1 iptable_filter
loop                   18568  4 
x_tables               17412  2 xt_physdev,ip_tables
binfmt_misc            13320  1 
rfcomm                 43544  0 
l2cap                  27136  5 rfcomm
bluetooth              59620  4 rfcomm,l2cap
bridge                 62236  1 xt_physdev
i915                   21632  2 
drm                    83476  3 i915
ppdev                  10628  0 
capability              6024  0 
commoncap               8704  1 capability
acpi_cpufreq            9160  1 
cpufreq_stats           7744  0 
cpufreq_ondemand        9740  2 
freq_table              6048  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8968  0 
cpufreq_powersave       2944  0 
cpufreq_userspace       5664  0 
container               5504  0 
video                  17540  0 
sbs                    16676  0 
i2c_ec                  6144  1 sbs
i2c_core               23936  1 i2c_ec
asus_acpi              17688  0 
button                  7824  0 
battery                11396  0 
ac                      6404  0 
ipv6                  269600  14 
sbp2                   27268  0 
lp                     12964  0 
tsdev                   9152  0 
snd_hda_intel          21784  1 
snd_hda_codec         172288  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          18432  1 snd_pcm_oss
snd_pcm                85508  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36352  0 
snd_seq_midi            9984  0 
snd_rawmidi            26880  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                58480  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25092  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 40224  0 
pci_hotplug            34752  1 shpchp
serial_core            23936  0 
serio_raw               8452  0 
intel_agp              26780  1 
parport_pc             42212  1 
parport                39496  3 ppdev,lp,parport_pc
pcspkr                  4352  0 
snd                    58500  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                36168  3 drm,intel_agp
psmouse                41480  0 
soundcore               9312  1 snd
af_packet              24840  2 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11520  1 
ext3                  144008  3 
jbd                    63272  1 ext3
mbcache                10244  1 ext3
sg                     37788  0 
sd_mod                 23040  10 
generic                 6532  0 [permanent]
ata_piix               17160  7 
ehci_hcd               35208  0 
ohci1394               37552  0 
ieee1394              304184  2 sbp2,ohci1394
floppy                 58916  0 
e1000                 128448  0 
ata_generic             8452  0 
libata                113556  2 ata_piix,ata_generic
scsi_mod              144908  4 sbp2,sg,sd_mod,libata
uhci_hcd               26504  0 
usbcore               144644  3 ehci_hcd,uhci_hcd
raid1                  26880  3 
md_mod                 84500  5 raid1
thermal                15624  0 
processor              32328  2 acpi_cpufreq,thermal
fan                     5892  0 

however, I still see a listing in lspci for the card

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

Any ideas? Is there a better way to stop access of the card in dom0?

---

