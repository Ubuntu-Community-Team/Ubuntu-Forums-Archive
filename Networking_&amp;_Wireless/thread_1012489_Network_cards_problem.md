---
title: "Network cards problem"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by aalekso on 2008-12-15
I've just installed Ubuntu Desktop 8.10, but my network cards (D-link System Inc RTL8139 Ethernet and Via Technologies inc VT6102) are greyed out. I have a dual boot Windows 2003/Ubuntu!

Ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:1c:f0:f9:45:f6  
          inet6 addr: fe80::21c:f0ff:fef9:45f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:607575 (607.5 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:17 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:0b:74:ca  
          inet6 addr: fe80::215:f2ff:fe0b:74ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:243 (243.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:23 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17488 (17.4 KB)  TX bytes:17488 (17.4 KB)



ifconfig -a output

eth0      Link encap:Ethernet  HWaddr 00:1c:f0:f9:45:f6  
          inet6 addr: fe80::21c:f0ff:fef9:45f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:680337 (680.3 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:17 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:0b:74:ca  
          inet6 addr: fe80::215:f2ff:fe0b:74ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:819 (819.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:23 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18704 (18.7 KB)  TX bytes:18704 (18.7 KB)

pan0      Link encap:Ethernet  HWaddr fa:09:02:70:7c:f1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lsmod output

Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
pci_slot               12552  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_via82xx            32536  3 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15360  1 snd_via82xx
evdev                  17696  7 
snd_seq_dummy          10884  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_viapro             15764  0 
snd                    63268  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               31892  1 i2c_viapro
soundcore              15328  1 snd
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
shpchp                 37908  0 
via_agp                16256  1 
pci_hotplug            35236  1 shpchp
agpgart                42184  1 via_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_via               16132  0 
pata_acpi              12160  0 
sata_via               15492  3 
ata_generic            12932  0 
uhci_hcd               30736  0 
ehci_hcd               43276  0 
libata                177312  4 pata_via,pata_acpi,sata_via,ata_generic
usbcore               148848  3 uhci_hcd,ehci_hcd
via_rhine              30216  0 
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
8139too                31616  0 
mii                    13440  2 via_rhine,8139too
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  9 


lspci output
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)

---

### Post by aalekso on 2008-12-15
Oh I forgot! Thanks! It's just I've been banging my head for hours.... :)

---

### Post by aalekso on 2008-12-15
Another thing I forgot. My cable ISP is giving Ip addresses with DHCP! So static IP doesn't work.

---

### Post by aalekso on 2008-12-16
Any ideas?

---

### Post by Iowan on 2008-12-16
So it vorks via DHCP?  There's a workaround for using static addresses with the new NM - [here]("http://ubuntuforums.org/showthread.php?t=974382")

---

### Post by aalekso on 2008-12-16
I guess I didn't explain my self very good! One one card I have to enable DHCP and the other one is static. But the thing is that both are greyed out.

---

