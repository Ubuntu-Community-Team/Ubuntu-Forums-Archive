---
title: "Problems Ubuntu and D-Link RTL8139 NIC"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by osotogari on 2006-02-27
Hi all,
First post here at Ubuntu forums.

I just installed Ubuntu Breezy distro last night and upon installation I was informed that it could not find a NIC even though there was one connected. I installed everything anyway and upon my first bootup I noticed that, not surprisingly, there seems to be no network card installed.

When I type ifconfig eth0 I get 
```

eth0: error fetching interface information: Device not found

```

typing ifconfig:

```

lo                     Link encap:Local loopback
                        Inet addr: 127.0.0.1 Mask: 255.0.0.0
                        int6 addr: ::1/128 Scope: Host
                        UP LOOPBACK RUNNING MTU:16436 Metric: 1
                        RX packets: 37083 erroes: 0 dropped:0 overruns:0 frame:0
                        TX packets: 37083 erroes: 0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:0
                        RX bytes:3363202 (3.2 MiB) TX bytes: 3633202 (3.2 MiB)


```

typing ifconfig -a
```

lo                     Link encap:Local loopback
                        Inet addr: 127.0.0.1 Mask: 255.0.0.0
                        int6 addr: ::1/128 Scope: Host
                        UP LOOPBACK RUNNING MTU:16436 Metric: 1
                        RX packets: 37083 erroes: 0 dropped:0 overruns:0 frame:0
                        TX packets: 37083 erroes: 0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:0
                        RX bytes:3363202 (3.2 MiB) TX bytes: 3633202 (3.2 MiB)

sit0                 Link encap:IPv6-in-IPv4
                       NOARP MTU:1480 Metric:0
                       RX packets: 37083 erroes: 0 dropped:0 overruns:0 frame:0
                       TX packets: 37083 erroes: 0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:0
                       RX bytes: 0 (0.0 b) TX bytes:0 (0.0 b)
                       


```

To be perfectly honest I'm at a loss here at what to do to get eth0 up and running. Any help would be much appreciated.

Thanks :)

---

### Post by jamesr on 2006-02-27
dmesg |grep eth0
sudo ifconfig -a
lsmod

post the outputs

---

### Post by osotogari on 2006-02-28
[QUOTE=jamesr]dmesg |grep eth0
sudo ifconfig -a
lsmod

post the outputs[/QUOTE]

dmesg | grep eth0 
Returns nothing at all.

sudo ifconfig -a
```

lo                     Link encap:Local loopback
                        Inet addr: 127.0.0.1 Mask: 255.0.0.0
                        int6 addr: ::1/128 Scope: Host
                        UP LOOPBACK RUNNING MTU:16436 Metric: 1
                        RX packets: 37083 erroes: 0 dropped:0 overruns:0 frame:0
                        TX packets: 37083 erroes: 0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:0
                        RX bytes:3363202 (67.5 KiB) TX bytes: 3633202 (67.5 KiB)

sit0                 Link encap:IPv6-in-IPv4
                       NOARP MTU:1480 Metric:0
                       RX packets: 37083 erroes: 0 dropped:0 overruns:0 frame:0
                       TX packets: 37083 erroes: 0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:0
                       RX bytes: 0 (0.0 b) TX bytes:0 (0.0 b)
                       

```

lsmod
```

Module                  Size  Used by
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
mga                    56448  1
drm                    58004  2 mga
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
tsdev                   7616  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_cmipci             30368  1
gameport               14472  1 snd_cmipci
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10120  1 snd_pcm
snd_opl3_lib            9856  1 snd_cmipci
snd_timer              21764  2 snd_pcm,snd_opl3_lib
snd_hwdep               8608  1 snd_opl3_lib
snd_mpu401_uart         6784  1 snd_cmipci
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  2 snd_opl3_lib,snd_rawmidi
snd                    48644  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
hisax                 458064  0
crc_ccitt               2176  1 hisax
isdn                  121196  1 hisax
slhc                    6656  1 isdn
i2c_amd756              6148  0
i2c_core               19728  2 i2c_acpi_ec,i2c_amd756
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
amd_k7_agp              8460  1
agpgart                32328  2 drm,amd_k7_agp
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
dm_mod                 50364  4
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
8139too                23552  0
mii                     5248  1 8139too
ohci_hcd               18564  0
usbcore               104188  3 usbhid,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  595
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


```

---

### Post by jamesr on 2006-02-28
in the lsmod output i see a reference to 8139too

> mii                     5248  1 8139too

but the > dmesg | grep eth0 
should be 
dmesg |grep eth0 
no space between | and the g
 could also try eth instead or eth0 ie
dmesg |grep eth
dmseg |grep mii

---

