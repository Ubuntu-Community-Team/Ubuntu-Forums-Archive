---
title: "Sound Blaster Audigy 2 Value (not detected)"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by mycologist on 2007-02-12
I am new to Ubuntu but I have managed to solve most of my hardware problems so far except this one. To start off, if I click the volume icon on the top of the screen i get "No volume control GStreamer plugins and/or devices found.". I have a Sound Blaster Audigy 2 Value installed in one of my PCI slots. I do have integrated sound but I have disabled it in the BIOS. When i type lspci in the terminal, i get:

```

mycologist@mycologist-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
[COLOR="Red"]02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller
[/COLOR]
```

Is what i highlighted in red causing this issue? Here is what comes up when i do lsmod:

```

mycologist@mycologist-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8                3200  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 406988  8 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
tsdev                   9152  0 
joydev                 11200  0 
usb_storage            75072  1 
ipv6                  272288  10 
af_packet              24584  2 
snd_hda_intel          20116  0 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
libusual               17040  1 usb_storage
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
sg                     37404  0 
usbhid                 45152  0 
psmouse                41352  0 
serio_raw               8452  0 
via_agp                11264  1 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
via_rhine              26116  0 
mii                     6912  1 via_rhine
agpgart                34888  2 fglrx,via_agp
floppy                 63044  0 
evdev                  11392  1 
pcspkr                  4352  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
sd_mod                 22656  5 
generic                 6276  0 
sata_via               10500  2 
libata                 74892  1 sata_via
scsi_mod              144648  4 usb_storage,sg,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

also, when i type alsamixer, i get this:

```

mycologist@mycologist-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Any help is appreciated!

---

