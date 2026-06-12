---
title: "Audio application crash"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by madtinkerer on 2007-11-19
Hey all,

I'm running gutsy.  I just wiped an old dapper install in which sound worked and installed gutsy.  Nothing else changed.  I'm having an odd problem.  Whenever I try to do anything involving sound the program crashes.  If I play an mp3 or video, the program locks up.  I'f i try to use youtibe, firefox locks up.  I have no idea what the problem is.  Here is what I've got
```
02:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

```  and ```
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
button                  8976  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
loop                   19076  0 
snd_cmipci             37024  0 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_mpu401_uart         9600  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54660  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
nvidia               6221648  24 
pcspkr                  4224  0 
i2c_core               26112  1 nvidia
soundcore               8800  1 snd
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
ipv6                  273892  12 
joydev                 11328  0 
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  10 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
sata_sil24             15236  3 
e100                   37644  0 
mii                     6528  1 e100
ata_piix               17540  3 
libata                125168  3 ata_generic,sata_sil24,ata_piix
scsi_mod              147084  3 sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  5 dm_mirror,dm_snapshot
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
commoncap               8320  1 capability
fuse                   47124  1 
  
```

any ideas what might be the problem?

---

### Post by Tiede on 2008-01-05
I am having the same problem... Is this still an open thread?
My Multimedia problems crash, firefoz crashes when soemthing with sound is played.
I keep having to restart my pc to recover from random freezes...
I also notice that if I start an audio app within a terminal, I get a message ```
sh:jackd not found
``` displayed then a few moments later, my app locks up...

---

### Post by Death4Life on 2008-01-19
same problem here...
Just started today, and everything worked fine till yesterday when rhytmbox keept crashed :(

I'm starting to miss my music!

---

### Post by Yellow Pasque on 2008-01-19
Tiede, I wonder why your programs are looking fro the JACK daemon. Do you know if you have the jack package installed or your programs set to output to JACK?

---

