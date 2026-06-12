---
title: "No sound output (after using Wine)"
date: 2009-03-27
forum: Multimedia Software
---

### Post by cousteau on 2009-03-27
Friends,

this morning the sound output on my Ubuntu 8.10 machine stopped. After thinking about it for some time it seems to me that it stopped after I tried to use the dj-application Deckadance (Windows) with Wine. Might be a coincidence, but who knows.

Anyway. I tried headphones in case the speakers are dead, but no sound at all. The audio preferences report no error if I check the sound output. It seems the systems 'thinks' everything is normal, but I can't hear anything. I use ALSA, but switching to OSS doesn't change anything.

I also booted my system via cd just to check if there's a hardware problem: Sound works fine from the current installation cd. So it ain't the hardware.

Next thing I did was reinstalling alsa_base - still no sound. Sigh.

However, here's my _lspci_:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

and _lsmod_ returns

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
nvram                  16524  0 
ipv6                  263972  21 
af_packet              25728  2 
binfmt_misc            16904  1 
i915                   38528  2 
drm                    86056  3 i915
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  2 
sco                    18308  2 
l2cap                  30464  16 bnep,rfcomm
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
dcdbas                 15008  0 
btusb                  19736  3 
evdev                  17696  6 
bluetooth              61924  11 bnep,rfcomm,sco,l2cap,btusb
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
intel_agp              33724  1 
shpchp                 38036  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pci_hotplug            34976  1 shpchp
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            82752  1 
libusual               30356  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
e1000                 132292  0 
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  7 btusb,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

I'd be grateful for any ideas.

thomas

---

### Post by cousteau on 2009-03-28
Now I reinstalled the complete ALSA package, still no success.
Anyone has an idea?

---

### Post by kokonobs on 2009-03-28
I've not used my ubuntu in over 5 weeks. Today i boot it up and i get no sound. Looks like i may have the same problem as you. I dont remember installing anything before that. Also previously when i start up, i dont get sound from Firefox or my music players until i restart.

---

### Post by cousteau on 2009-03-28
I really don't have any idea what to do :/
Seems the only option is a reinstallation? Can't be true.

All my audio apps are running, so drivers seem to be ok. There just ain't any output :/

thomas

---

### Post by cousteau on 2009-03-29
A new guess was installing the Pulse Audio Device Chooser.
Still no success :/

---

