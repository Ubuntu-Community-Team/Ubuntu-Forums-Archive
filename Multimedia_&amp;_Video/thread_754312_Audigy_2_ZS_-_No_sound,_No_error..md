---
title: "Audigy 2 ZS - No sound, No error."
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by skenmy on 2008-04-13
Hey all,

Fresh install of Gutsy, fully updated. Everything seems to be okay at the moment, except for my sound. I have none. Not a peep, poop, tone, tinkle, or boop. And I, for the life of me, can't figure out why.

The card is the only one being detected by aplay -l:

```
paul@neuron:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And is, as you can see above, the default card. snd-emu10k1 is loaded:

```
paul@neuron:~$ cat /proc/asound/modules
 0 snd_emu10k1

```

And I actually receive no errors when playing audio to ALSA. But no sound comes out. alsamixer has all my volumes up (including surrounds, PCMs, and Masters), Audigy Analog/Digital Output Jack switch of Off (Mute), and everything else seems dandy. But still no sound.

Sound worked previously on this install, but only through my USB Phone (which acts as its' own soundcard). Having removed that from my system, I hoped it would switch the default to my Audigy card, which it has, but I'm getting no sound at all. I've even checked that my cables are connected (which they are, thank you :KS). Now i'm stumped - over to you guys to throw your ideas at me!

Here's the info you may or may not need:

```
paul@neuron:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1b.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 50)
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:1f.1 RAID bus controller: ALi Corporation ULi 5287 SATA (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:15.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:15.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:15.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

```

```
paul@neuron:~$ lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
container               5504  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       9856  0 
snd_emux_synth         39808  1 snd_emu10k1_synth
snd_seq_virmidi         8320  1 snd_emux_synth
snd_seq_midi_emul       8064  1 snd_emux_synth
snd_emu10k1           145056  3 snd_emu10k1_synth
snd_pcm_oss            53632  0 
snd_ac97_codec        102180  1 snd_emu10k1
ac97_bus                3456  1 snd_ac97_codec
snd_util_mem            6400  2 snd_emux_synth,snd_emu10k1
snd_mixer_oss          18304  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_pcm                88836  3 snd_emu10k1,snd_pcm_oss,snd_ac97_codec
snd_page_alloc         11528  2 snd_emu10k1,snd_pcm
snd_usb_lib            17920  0 
snd_seq_oss            35712  0 
snd_seq_midi           10752  0 
snd_seq_midi_event      8576  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_rawmidi            27392  4 snd_seq_virmidi,snd_emu10k1,snd_usb_lib,snd_seq_midi
snd_seq                58608  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26116  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9740  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_hwdep              10884  2 snd_emux_synth,snd_emu10k1
nvidia               6221648  34 
emu10k1_gp              4736  0 
snd                    64012  23 snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_emu10k1,snd_pcm_oss,snd_ac97_codec,snd_util_mem,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
usblp                  15104  0 
soundcore               8800  1 snd
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
xpad                    9988  0 
analog                 13344  0 
gameport               16776  3 emu10k1_gp,analog
pcspkr                  4224  0 
psmouse                39952  0 
uli526x                17556  0 
i2c_ali1535             8196  0 
i2c_ali15x3             9092  0 
i2c_core               26112  3 nvidia,i2c_ali1535,i2c_ali15x3
shpchp                 34580  0 
serio_raw               8068  0 
pci_hotplug            32704  1 shpchp
ati_agp                10124  0 
agpgart                35016  2 nvidia,ati_agp
evdev                  11136  6 
joydev                 11328  0 
usb_storage            73024  0 
libusual               18448  1 usb_storage
sg                     36764  0 
sd_mod                 30336  4 
usbhid                 29536  0 
hid                    28928  1 usbhid
reiserfs              248704  4 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
sata_uli                8452  2 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  9 snd_usb_lib,usblp,xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
floppy                 60004  0 
alim15x3               12556  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,alim15x3
ata_generic             8452  0 
libata                125168  2 sata_uli,ata_generic
scsi_mod              147084  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

```
paul@neuron:~$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 2 Platinum [SB0240P]
                      Audigy 2 Platinum [SB0240P] (rev.4, serial:0x10021102) at 0xe800, irq 18

```

P.S. There is an odd buzzing sound, if that makes any difference. Definitely coming from the speakers - didn't do this with Windows.

---

### Post by mc4man on 2008-04-13
> Audigy Analog/Digital Output Jack switch of Off (Mute)
I've got the same card and that switch has to be checked (on) or i get no sound

---

### Post by skenmy on 2008-04-14
Tried this, still no sound :(

---

### Post by mc4man on 2008-04-14
Went thru the alsamixer - didn't see anything that should be on that wasn't obvious (though some seemed redundant ie. pcm and surround).  By switch I meant the one you access from d. clicking speaker icon in upper panel - try opposite of what it is (also should be on in alsamixer)
You could try going to preferences>sound and picking alsa over autodetect
otherwise you may need to create/edit /etc/asound.conf. (never had the need but you could search that out)

---

