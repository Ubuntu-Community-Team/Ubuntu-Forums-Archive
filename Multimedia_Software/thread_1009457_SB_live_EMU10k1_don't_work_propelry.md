---
title: "SB live EMU10k1 don't work propelry"
date: 2008-12-12
forum: Multimedia Software
---

### Post by bradsorph on 2008-12-12
Hello.
The sound card is a Creative Sound Blaster Live 5.1 (Kernel module)
It works just with OSS (Setted by gnome settings).
But in OSS mode don't works systems sounds, flash animations and videos in the browser, and input microphone too.
This is lcpci:
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)


```

This is lsmod

```

Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12552  0 
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  3 snd_emu10k1_synth
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
evdev                  17696  6 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_intel8x0           37532  4 
snd_ac97_codec        111652  2 snd_emu10k1,snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                83204  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcspkr                 10624  0 
snd_timer              29960  3 snd_emu10k1,snd_seq,snd_pcm
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         16136  3 snd_emu10k1,snd_intel8x0,snd_pcm
snd                    63268  25 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
emu10k1_gp             10880  0 
soundcore              15328  1 snd
gameport               19468  2 emu10k1_gp
nvidia               6900560  36 
i2c_core               31892  1 nvidia
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 nvidia,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usb_storage            81728  0 
libusual               27156  1 usb_storage
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  1 
pata_acpi              12160  0 
8139too                31616  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  6 usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 


```

I've already seen these links without any progress:

[http://ubuntuforums.org/showthread.php?t=968157&highlight=EMU10k1]("http://a")

[http://ubuntuforums.org/showthread.php?t=994486&highlight=EMU10k1]("http://a")

[http://ubuntuforums.org/showthread.php?t=891529&highlight=EMU10k1]("http://a")

Thank you

---

### Post by bradsorph on 2008-12-13
Excuse me for this "UP". But I really need my soundcard.. Please help me.

---

### Post by bradsorph on 2008-12-19
Excuse me for this "UP". But I really need my soundcard.. Please help me.

---

### Post by pseudonym on 2008-12-19
Looks like you've still got your onboard sound still enabled ('snd_intel8x0'). Is that what you want ie to run 2 sound cards?

If not, disable the onboard sound in your BIOS and then see if your problem persists. If you do want to have both cards enabled there are ways to do it but it's best to start with the basics first.

---

