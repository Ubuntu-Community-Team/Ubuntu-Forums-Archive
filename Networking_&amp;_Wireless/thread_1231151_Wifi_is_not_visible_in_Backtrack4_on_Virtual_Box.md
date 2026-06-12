---
title: "Wifi is not visible in Backtrack4 on Virtual Box"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by tommy_mm on 2009-08-04
I have installed VB on Windows XP. I use BackTRack 4 OS in VB as guest and my wifi does not work. I dont have any problems with LAN connection. 
See VB configuration in attached file.
My wifi card is Atheros AR5006EG. Used linux kernel kernel: 2.6.29.4
Does anyone know how to solve that issue?


```

output form iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

``````

output from lsmod 

Module                  Size  Used by
ipv6                  238260  8
vboxvideo               1836  1
drm                   137824  2 vboxvideo
agpgart                29384  1 drm
video                  16572  0
output                  2380  1 video
sbs                    10932  0
sbshc                   4492  1 sbs
cpufreq_ondemand        6712  0
cpufreq_conservative     6004  0
cpufreq_performance     1292  0
cpufreq_powersave       1260  0
cpufreq_stats           4720  0
freq_table              3468  2 cpufreq_ondemand,cpufreq_stats
vboxvfs                43808  0
iptable_filter          2316  0
ip_tables              10684  1 iptable_filter
x_tables               13328  1 ip_tables
lp                      9380  0
snd_intel8x0           28808  0
snd_ac97_codec        100752  1 snd_intel8x0
ac97_bus                1356  1 snd_ac97_codec
snd_pcm_oss            37664  0
snd_mixer_oss          14156  1 snd_pcm_oss
snd_pcm                68144  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2416  0
snd_seq_oss            29728  0
snd_seq_midi            5952  0
snd_rawmidi            19104  1 snd_seq_midi
snd_seq_midi_event      5964  2 snd_seq_oss,snd_seq_midi
psmouse                41340  0
parport_pc             24068  0
parport                30444  2 lp,parport_pc
serio_raw               5040  0
snd_seq                47536  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19124  2 snd_pcm,snd_seq
snd_seq_device          6008  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    50276  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtc_cmos               10124  0
rtc_core               15848  1 rtc_cmos
rtc_lib                 2380  1 rtc_core
i2c_piix4               8924  0
soundcore               5856  1 snd
vboxadd                73152  8 vboxvfs
snd_page_alloc          7924  2 snd_intel8x0,snd_pcm
evdev                   9152  6
pata_acpi               3852  0
ata_generic             4496  0
fuse                   52936 

``````

output from lshw -C network

  *-network:0
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 40
       serial: 08:00:27:c2:2c:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pcnet32 driverversion=1.35 duplex=full ip=10.0.2.15 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=MII speed=100MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 40
       serial: 08:00:27:d0:a0:78
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=pcnet32 driverversion=1.35 duplex=half latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=MII speed=10MB/s

``````

output from lspci

00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:08.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:0b.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller


```

---

### Post by martinbaselier on 2009-08-04
It would be better to ask you question on the backtrack forums. Though it is based on ubuntu, I believe the kernel is different. This also means the kernel modules (drivers) will differ. 

It seems your card is not recognised. This could be a backtrack issue, a virtual box issue or a general linux issue. Have you tried to use backtrack as a live cd? You could also try ubuntu instead of backtrack.

---

### Post by Oglon3r on 2009-09-04
facepalm ive seen this question so many times....
THERE IS NO WIRELESS SUPPORT DURING VIRTUALIZATION.
just try the live cd

---

