---
title: "No sound from get-go of 6.10..."
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by lan56 on 2007-02-27
Hello,

I just installed a fresh Xubuntu 6.10 today, but I have yet to get any sound. I try playing a CD with gxine to test, and nothing. I hear absolutely nothing in my earphones at any time. I have not changed anything from the default settings for audio related things.

I have an ATI IXP AC97 card. I am rather new to Linux so I feel you may need more information, so tell me how to obtain that info and I will give it to you. I apologize in advance.

How do I get sound working?

Thank you.

---

### Post by renzokuken on 2007-02-28
run this from the terminal and play with the settings and see if it changes anything

```
alsamixer
```

failing that you could always compile the latest asla-driver from source to see if that makes it work. thats how i got my soundcard working

the outputs of 

```
lspci
```
and ```
lsmod
```

may also be useful for us

---

### Post by lan56 on 2007-02-28
lspci reports:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


and lsmod reports:
Module                  Size  Used by
ipv6                  272288  8 
fglrx                 406988  8 
powernow_k8            15008  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
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
af_packet              24584  2 
sbp2                   24584  0 
lp                     12964  0 
snd_atiixp             21388  1 
snd_ac97_codec         97696  1 snd_atiixp
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
tsdev                   9152  0 
sg                     37404  0 
r1000                  17792  0 
r8169                  32136  0 
snd                    58372  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
usbhid                 45152  0 
serio_raw               8452  0 
evdev                  11392  3 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_page_alloc         11400  2 snd_atiixp,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
psmouse                41352  0 
ati_agp                10636  0 
agpgart                34888  2 fglrx,ati_agp
floppy                 63044  0 
pcspkr                  4352  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
atiixp                  7824  1 
sd_mod                 22656  3 
generic                 6276  0 
sata_sil               11016  2 
libata                 74892  1 sata_sil
scsi_mod              144648  4 sbp2,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability



I turned all muted things in alsamixer to unmuted and turned everything to the max volume and still nothing. I am using headphones to listen for sound, if that helps any.

---

### Post by lan56 on 2007-03-01
I have fixed the problem. My headphone connection slot appears to be defective, and plugging the  headphones into the speakers slot seems to work, so I will make do.

Thank you.

---

