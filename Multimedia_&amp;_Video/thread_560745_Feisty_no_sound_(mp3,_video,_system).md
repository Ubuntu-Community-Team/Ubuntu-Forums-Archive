---
title: "Feisty no sound (mp3, video, system)"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by Rorscharch on 2007-09-26
Hey there,

I installed Feisty a few days ago, but from the start sound didn't work. I've installed a bunch of codecs and plugins but nothing works. I tested that my system's not muted, and I followed the instructions here: [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639) but that didn't work either.

If anyone could help, I'd really appreciate it. I'm pretty new to Ubuntu (or any Linux distro).


Here are the results of LSPCI and LSMOD:
[COLOR="DimGray"]
LSPCI

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)


LSMOD

Module                  Size  Used by
nls_utf8                3456  1 
ntfs                  101960  1 
binfmt_misc            14604  1 
ppdev                  11272  0 
powernow_k8            16480  1 
cpufreq_userspace       6176  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10640  1 
cpufreq_stats           8416  0 
freq_table              6336  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9736  0 
sony_acpi               7064  0 
pcc_acpi               15616  0 
dev_acpi               17028  0 
tc1100_wmi              9224  0 
ac                      6920  0 
video                  19080  0 
container               6144  0 
sbs                    17856  0 
battery                12040  0 
asus_acpi              19756  0 
i2c_ec                  6912  1 sbs
button                 10016  0 
backlight               8448  1 asus_acpi
dock                   11992  0 
ipv6                  307456  10 
lp                     15048  0 
fuse                   51888  0 
snd_hda_intel          24224  1 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49408  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               5659736  32 
serio_raw               9092  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               26496  2 i2c_ec,nvidia
psmouse                43536  0 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
soundcore              10272  1 snd
pcspkr                  4736  0 
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
af_packet              27020  2 
k8temp                  7552  0 
rt61                  251536  1 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
evdev                  13056  3 
tsdev                  10112  0 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  2 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
ide_disk               18304  3 
sata_nv                24196  1 
ata_generic            10628  0 
libata                137000  2 sata_nv,ata_generic
scsi_mod              166968  3 sg,sd_mod,libata
amd74xx                16944  0 [permanent]
floppy                 67944  0 
forcedeth              48776  0 
ehci_hcd               37004  0 
generic                 6532  0 [permanent]
ohci_hcd               24196  0 
usbcore               154416  3 ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability
[/COLOR]

**[COLOR="Red"]UPDATE: [/COLOR]I just checked and sound comes from my headphones when I plug them in.... so I really have no idea what's going on**

---

### Post by gwoodard on 2007-09-27
Are u using onboard sound or a sound card?

---

### Post by Rorscharch on 2007-09-27
I haven't bought a sound card, but I'm not sure if my graphics card might have sound card capability. When I check my sound preferences my device options are Realtek ALC883 (OSS Mixer) and HDA nVidia (Alsa Mixer). I'm assuming the Realtek is my on-board sound card, it's what my Windows installation uses.

I've tried switching between them and rebooting, but it makes no difference...

---

### Post by gwoodard on 2007-09-27
Okay then... are u tellin me that board is nvidia/intel? if so then go to bios and see if u cant disable one of the sound drivers or sound devices there

---

### Post by Rorscharch on 2007-09-27
I went into the BIOS and the only option to do with sound was disabling on-board sound, which I did.

When I restarted Ubuntu the gnome sound manager told me it couldn't detect any device, so the system was automatically muted.

In the end I went back into BIOS and enabled it again, which means I still have the same problem, and no idea what to do.

---

### Post by terminalvn on 2007-09-27
I've installed Ubuntu and pretty new using it. There's a weird problem: no sound from PC speaker, but there's sound when using a headphone.
On Volume Control, every components is in max volume.
[IMG]http://img517.imageshack.us/img517/8026/screenshotvolumecontrolic0.png[/IMG]
Anyone can help? Thanks in advance.

---

### Post by Rorscharch on 2007-09-27
Yeah, just checked, my headphones work too. Pretty strange.

Someone help us!

---

### Post by gwoodard on 2007-09-28
sorry it took so long but try this...

ubuntuforums.org/showthread.php?t=546931

---

### Post by terminalvn on 2007-09-29
> **gwoodard said:**
> sorry it took so long but try this...

ubuntuforums.org/showthread.php?t=546931

This doesnt work for me!:(
Thanks anyway.
Other tips?

---

### Post by terminalvn on 2007-09-29
**Here is the result of LSPCI command:**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by gwoodard on 2007-09-29
Just a question r u using a laptop?

---

### Post by terminalvn on 2007-09-30
> **gwoodard said:**
> Just a question r u using a laptop?

Yeah, and how to solve the problem?

---

### Post by gwoodard on 2007-09-30
Here try this...

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

