---
title: "dlink g520+ acx 111 chipset (seems driver have changed the name)"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by jarechu on 2006-06-16
First of all sorry for my english.

After installing dapper, it seems that my dlink wireless card is correctly installed. I tried to configure my network with System/Administration/Network and there is wlan0, but nothing happens after entering my network configuration.

Following some instructions found here [https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide")
I made a lshw -C network and this is the output:
```
jare@jareserver:/etc$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 00
       serial: 00:13:46:b1:c0:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=acx_pci** ip=10.0.0.101 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:dfffa000-dfffbfff iomemory:dffc0000-dffdffff irq:185
``` 
After this I made a lsmod you can see that there is only an "acx" entry, not an "acx_pci" one:

```
jare@jareserver:/etc$ lsmod
Module                  Size  Used by
**acx                   101132  0**
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
nls_utf8                2176  2
ntfs                  103536  1
sg                     37920  0
sd_mod                 19984  3
usb_storage            74176  2
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
af_packet              22920  0
md_mod                 72532  0
lp                     11844  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  2180  0
tsdev                   8000  0
rtc                    13492  0
parport_pc             35780  1
snd_via82xx            28824  1
snd_ac97_codec         92704  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
parport                36296  3 ppdev,lp,parport_pc
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
psmouse                36228  0
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
floppy                 62148  0
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_agp                 9856  1
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
serio_raw               7300  0
agpgart                34888  2 drm,via_agp
analog                 12320  0
soundcore              10208  1 snd
i2c_viapro              8980  0
gameport               15496  2 snd_via82xx,analog
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 acx,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
via82cxxx               9988  0 [permanent]
generic                 5124  0
sata_via                8964  0
libata                 78992  1 sata_via
scsi_mod              139496  4 sg,sd_mod,usb_storage,libata
thermal                13576  0
processor              23360  1 thermal
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
``` 
If I try "modprobe acx_pci", it can't find the module. But it works if I try "modprobe acx".

Anybody can help me with this?

Thanks in advance.

---

### Post by DoctorMO on 2006-06-17
The name was changed recently and includes better support for acx wireless cards, yay for me.

you need to make sure that when your linux is loading the module it's loading the correct one and it's also creating wlan0 with the correct module name. not that I had a problem with that side of it, I just had a problem compiling the source code against kernel headers.

---

### Post by william_nbg on 2006-06-25
OK, I have the same problem and the same card.

I see that it's loading with acx instead of acx_pci

it show up fine, I can restart it fine

but it's not working

any ideas??

---

### Post by funkydan2 on 2006-06-25
Yep - have a look [here](http://daniel.saunders.googlepages.com/howto.html#UseACX111WirelessCardsInUbuntuDapper) for a quick howto I've written to get ACX111 cards working in Dapper.

---

### Post by william_nbg on 2006-06-26
[QUOTE=funkydan2]Yep - have a look [here](http://daniel.saunders.googlepages.com/howto.html#UseACX111WirelessCardsInUbuntuDapper) for a quick howto I've written to get ACX111 cards working in Dapper.[/QUOTE]

Thanks!

Somebody pointed me to your fix on another thread last night.

worked like a charm.

---

