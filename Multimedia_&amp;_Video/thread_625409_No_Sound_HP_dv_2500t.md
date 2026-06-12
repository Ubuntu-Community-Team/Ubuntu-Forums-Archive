---
title: "No Sound HP dv 2500t"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by achutammurarka on 2007-11-27
I have a weird issue with sound on my dv 2500t laptop.. I have alsa, jack and oss libraries installed .. and there seems to be playback(on amarok) but there is no sound output.

Here are the modules running:
achutam@achutam:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
aes                    28608  2 
ieee80211_crypt_ccmp     8064  2 
af_packet              24840  4 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
battery                11012  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         291488  2 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               48644  0 
sr_mod                 17828  0 
compat_ioctl32          2304  1 uvcvideo
joydev                 11328  0 
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
cdrom                  37536  1 sr_mod
ipw3945               119840  1 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_ccmp,ieee80211
v4l2_common            18432  2 uvcvideo,videodev
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   46852  0 
hci_usb                18332  2 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
sdhci                  18828  0 
mmc_core               28420  1 sdhci
snd                    54788  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
serio_raw               8068  0 
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  6 
ata_piix               17540  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  5 
ata_generic             8452  0 
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  7 
apparmor               40728  0 
commoncap               8320  1 apparmor
achutam@achutam:~$ 



Please help!

Thanks,
 Muraka

---

### Post by achutammurarka on 2007-11-27
Forgot to mention my hw config:


achutam@achutam:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
achutam@achutam:~$

---

### Post by nnamdi on 2007-11-28
wats up try this link had the same problem let me know what happen after you did these ok

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

later

NB: does your bluetooth work

---

### Post by eamann on 2007-12-06
Hello!

Try the very simple solution proposed by LinuxTechie at

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

It worked for me.

Best of luck!

---

