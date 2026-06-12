---
title: "Problem with sound"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by Daniel15 on 2006-09-23
Hi,
 I'm having a few problems with sound on my laptop (a Dell Inspiron 6400). Basically, sound does not work in some programs.

When starting 'DOSBOX', I get this error:
> 
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory


Also, any program ran under Wine doesn't seem to have sound working. When I try to run a program under Wine, I get:
> 
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".


Or sometimes:
> 
err:wave:DSDB_MapBuffer Could not map sound device for direct access (No such device)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".



Going to the 'Audio' tab of winecfg crashes the program:
> 
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** double free or corruption (out): 0x7c1391d0 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...


Can someone please help me?

lspci:
```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0000:0b:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

```

lsmod:
```

Module                  Size  Used by
usbhid                 42752  0
acpi_sbs               20172  0
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
thermal                13768  0
fan                     4836  0
button                  6704  0
ipw3945               132348  1
ieee80211              38952  1 ipw3945
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
b44                    27980  0
mii                     6176  1 b44
michael_mic             2784  4
arc4                    2048  4
ieee80211_crypt_tkip    11456  2
ipv6                  286976  29
vmnet                  40004  16
vmmon                 117612  0
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ppdev                   9668  0
fglrx                 402796  133
speedstep_centrino      8752  1
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
nls_utf8                2240  1
ntfs                  111728  1
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   14496  2
fat                    55548  1 vfat
dm_mod                 63256  1
md_mod                 76052  0
i8k                     7160  0
sbp2                   25060  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
af_packet              24520  6
joydev                 10432  0
tsdev                   8032  0
ieee80211_crypt         6528  2 ieee80211,ieee80211_crypt_tkip
pcspkr                  2244  0
psmouse                40004  0
sdhci                  16096  0
mmc_core               31816  1 sdhci
snd_hda_intel          20468  1
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
serio_raw               7748  0
intel_agp              24700  1
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
agpgart                36784  2 fglrx,intel_agp
shpchp                 49504  0
soundcore              10784  1 snd
pci_hotplug            30788  1 shpchp
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
hw_random               5716  0
sg                     40160  0
sr_mod                 17988  0
cdrom                  41408  1 sr_mod
evdev                  10176  2
ext3                  148296  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 20448  7
generic                 5124  0
ata_piix               11364  12
libata                 83440  1 ata_piix
scsi_mod              145960  5 sbp2,sg,sr_mod,sd_mod,libata
processor              26888  2 thermal,speedstep_centrino
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  73
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

EDIT: I just installed a game called 'Nexiuz', and the sound 'stutters' quite a bit. Does anyone know how to fix these problems?

---

### Post by Daniel15 on 2006-09-26
So, nobody knows? :(

---

