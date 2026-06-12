---
title: "Nvidia Sis 760 problem"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by Mickeysofine1972 on 2006-11-06
Hi

I've just installed a Geforce 6 series card in an amd64 2.8 with 512mb ram running Kubuntu 6.06 LTS (32bit version though) using the k7 kernel

Ive done the standard install from tseliots guide but can get it to start X.

Here is my system info:
```

my-desktop:~$ lsmod
Module                  Size  Used by
ppp_deflate             6720  0
zlib_deflate           24664  1 ppp_deflate
bsd_comp                6592  0
ipv6                  287456  22
pppoatm                 7168  1
ppp_generic            34004  7 ppp_deflate,bsd_comp,pppoatm
slhc                    8128  1 ppp_generic
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54372  4 rfcomm,l2cap
ppdev                  10052  0
cpufreq_userspace       6816  0
cpufreq_stats           6912  0
freq_table              5152  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
dm_mod                 63640  1
md_mod                 76244  0
fuse                   41616  0
lp                     12612  0
af_packet              25224  2
sn9c102                93708  0
spca5xx               653072  0
videodev               10368  2 sn9c102,spca5xx
tsdev                   8320  0
speedtch               13576  0
usbatm                 18176  2 speedtch
floppy                 65924  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
pcspkr                  2564  0
psmouse                40132  0
serio_raw               8132  0
snd_intel8x0           35804  1
snd_ac97_codec         99296  1 snd_intel8x0
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
sis900                 25280  0
snd_pcm                96772  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  1 snd_pcm
mii                     6528  1 sis900
i2c_core               23168  1 i2c_acpi_ec
snd                    60068  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11040  1 snd
snd_page_alloc         11592  2 snd_intel8x0,snd_pcm
amd64_agp              13252  0
sis_agp                 9284  1
agpgart                37072  2 amd64_agp,sis_agp
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
evdev                  10432  1
ext3                  148424  1
jbd                    65684  1 ext3
ide_generic             1792  0
ehci_hcd               36104  0
ohci_hcd               22788  0
usbcore               139012  7 sn9c102,spca5xx,speedtch,usbatm,ehci_hcd,ohci_hcd
sata_sis                8772  0
libata                 84176  1 sata_sis
scsi_mod              145736  1 libata
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
ide_disk               19520  4
sis5513                17544  1
generic                 5444  0
thermal                14088  0
processor              27208  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vga16fb                14344  1
vgastate               10304  1 vga16fb
fbcon                  44640  74
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              252  1 bitblit

```


I tried this too:
```

rigga@rigga-desktop:~$ sudo modprobe nvidia
Password:
FATAL: Error inserting nvidia (/lib/modules/2.6.15-27-k7/kernel/drivers/video/nvidia.ko): Invalid module format


```


here is my pci list:
```

lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)


```

I've tried blacklisting amd64_agp and sis_agp too and this thing wont load the nvidia module.

I compiled the module using the same kernel sources that I get when I use 'uname -r' but it still say no cigar!

PLEASE HELP!

Mike

---

### Post by RiggaTheMighty on 2006-11-06
I have exactly the same problem!!
 
Ive tried everything i can think of and its just not good.

SOMEONE OUT THERE MUST KNOW THE TRUTH!!

PLEASE HELP!!!!](*,)

---

### Post by tseliot on 2006-11-07
try blacklisting sis_agp and agpgart.

---

### Post by Mickeysofine1972 on 2006-11-07
Hi

I did that but no joy

Mike

---

### Post by Mickeysofine1972 on 2006-11-07
I've been doing some looking around on the net and have heard that if you change the ID for the 755 in the amd64_agp.c file to 760 then recompile it, it will recognize it.

Anyone know how I can get hold of the amd64_agp.c file and how I can recompile it?

Mike

---

