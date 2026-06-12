---
title: "Creative Digital Output"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Khaotik on 2006-06-17
Hello, I have a Pentium 3 1ghz machine running Ubuntu Breezy with a Creative Audio PCI 128D (What windowze says). Alsa says its a Esoniq(I beleive thats the chip) and oss says its a Cirrus Logic CS4297A Rev. 4. I have a set of Boston Acoustic Digital speakers that will ONLY accept the digital input. I get analog out fine, but wearing headphones isnt cutting it; and these speakers rock. Id love to get them working.

> 
LSPCI:
0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 02)
0000:01:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:0b.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:01:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
0000:01:0d.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 04)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:02:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)


> 
LSMOD:
Module                  Size  Used by
nls_cp437               5888  1
isofs                  32824  1
udf                    75524  0
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
snd_ens1371            22240  3
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  1 snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
nls_utf8                2176  3
ntfs                   92016  3
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139too                23552  0
mii                     5248  1 8139too
tulip                  45088  0
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  7
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  726
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


---

### Post by Khaotik on 2006-06-17
Update: I recently upgraded to Dapper. Same problem. Nothing has changed.

---

### Post by Khaotik on 2006-06-18
Bump

---

