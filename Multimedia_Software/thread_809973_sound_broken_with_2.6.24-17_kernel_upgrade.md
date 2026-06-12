---
title: "sound broken with 2.6.24-17 kernel upgrade"
date: 2008-05-27
forum: Multimedia Software
---

### Post by astralsin on 2008-05-27
I upgraded the kernel to 2.6.24-17 this morning and, just like last time, linux-restricted-modules failed to update so when i rebooted, my video defaulted to vesa and had no sound.  i've had this problem before and updated linux-restricted-modules by hand and my nvidia driver was updated properly but I still have no sound.  lspci shows my sound device
```
04:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

```

but i don't see the proper driver in lsmod

```
Module                  Size  Used by
nls_iso8859_1           4096  1 
nls_cp437               5760  1 
vfat                   13184  1 
fat                    52892  1 vfat
af_packet              21636  2 
binfmt_misc            11272  1 
vboxdrv                42160  0 
ipv6                  255044  10 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
cpufreq_powersave       1792  0 
cpufreq_conservative     7200  0 
cpufreq_ondemand        8084  0 
freq_table              4484  2 cpufreq_stats,cpufreq_ondemand
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
lp                     11332  0 
tuner                  42016  0 
tea5767                 5892  1 tuner
tda8290                11524  1 tuner
tuner_simple            9352  1 tuner
mt20xx                 12296  1 tuner
tea5761                 5124  1 tuner
cx8800                 34540  0 
cx88xx                 64936  1 cx8800
ir_common              35204  1 cx88xx
i2c_algo_bit            6404  1 cx88xx
tveeprom               15632  1 cx88xx
videodev               28416  2 cx8800,cx88xx
v4l1_compat            14596  1 videodev
compat_ioctl32          1408  1 cx8800
v4l2_common            17408  4 tuner,cx8800,cx88xx,videodev
videobuf_dma_sg        14084  2 cx8800,cx88xx
videobuf_core          18052  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc               5000  2 cx8800,cx88xx
nvidia               7822720  24 
evdev                  11776  3 
i2c_nforce2             6656  0 
agpgart                33328  1 nvidia
parport_pc             35108  1 
parport                35912  2 lp,parport_pc
i2c_core               23696  11 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,cx88xx,i2c_algo_bit,tveeprom,nvidia,i2c_nforce2
k8temp                  5760  0 
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
pcspkr                  3072  0 
rtc                    13212  0 
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sd_mod                 29584  5 
usbhid                 30592  0 
hid                    36480  1 usbhid
usb_storage            72512  1 
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
libusual               18208  1 usb_storage
sata_nv                26504  2 
pata_amd               13316  0 
ata_generic             7428  0 
floppy                 58116  0 
forcedeth              50060  0 
pata_acpi               7424  0 
ne2k_pci               10848  0 
8390                   10624  1 ne2k_pci
libata                159600  4 sata_nv,pata_amd,ata_generic,pata_acpi
scsi_mod              151180  5 sd_mod,usb_storage,sg,sr_mod,libata
ehci_hcd               36748  0 
ohci_hcd               24196  0 
usbcore               143724  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
fuse                   48404  3 
vesafb                  8068  1 
fbcon                  41888  72 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
```

anyone know how to update this driver?

---

### Post by henqi on 2008-05-28
I also got this problem after upgrade to this kernel. No sound from my speaker.
I am using Ubuntu 8.04 x64 bit Desktop.

Please help...

---

### Post by alexandermimix on 2008-05-28
kernel upgrade killed my sound too :(

I use ASUS A8N-E mobo onboard sound.

---

### Post by santhony on 2008-05-28
Kernel Upgrade killed my sound also, Compaq Presario 2195US Laptop.
 
Sound Device:
 00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]


If I go into boot menu and choose previous Kernel, all is well..

---

### Post by coffeecat on 2008-05-28
No one got an answer? Thought I'd add to the chorus. No sound here with the new 2.6.24-17 kernel, but fine with the 2.6.24.16 kernel.

```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

```Seems to be affecting several different chipsets. No one got any ideas?

**Edit:** I've just booted into the 2.6.24-17 kernel for the second time, and now the sound is working OK - and I didn't do anything except reboot after trying the earlier kernel.

Can anyone explain that? No, I thought not. :-|

---

### Post by alexandermimix on 2008-05-29
Unfortunately booting into old kernel didn't fix new kernel. I don't have time for this at the moment (exams etc.) I think I will just use my vista (gaming) partition until I have time to fix it :(

---

