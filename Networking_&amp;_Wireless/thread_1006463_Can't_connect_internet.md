---
title: "Can't connect internet"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by kool124 on 2008-12-09
hi,

well just install ubuntu 7.10 on my Toshiba satellite M35 

just configured my connection,

i have static ip address, so i manually configured my ip address, and dns

problem is, it doesnot connect..


this is my ifconfig and other commands details



abhi@abhi-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:08:0D:9D:55:63
inet addr:172.25.9.148 Bcast:172.25.9.191 Mask:255.255.255.192
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2384 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:318275 (310.8 KB) TX bytes:2261 (2.2 KB)

eth1 Link encap:Ethernet HWaddr 00:04:23:79:D9:E0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11 Base address:0xe000 Memory:c2005000-c2005fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


also when i am executing

sudo ifup eth0

its give me this thing

abhi@abhi-laptop:~$ sudo ifup eth0
SIOCADDRT: No such process
Failed to bring up eth0.

and when i try ifdown thing

it gives

abhi@abhi-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
abhi@abhi-laptop:~$

---

### Post by Iowan on 2008-12-09
Just a guess - your interface may need a (different) driver. You can check **lspci** to see if it shows up.

---

### Post by mscout2004 on 2008-12-09
how do you access that lspci??  do you just type that in the terminal or is it a program in the menus???

NEWBIE...LOL

---

### Post by Iowan on 2008-12-09
> **mscout2004 said:**
> how do you access that lspci??  do you just type that in the terminal or is it a program in the menus???Yes, it's a terminal command - sorry, I should have pointed that out.

I notice your ifconfig shows eth0 AND eth1...
(FYI, eth0 is a Toshiba card, eth1 is Intel)
[MAC finder]("http://www.coffer.com/mac_find/")

---

### Post by kool124 on 2008-12-10
here is the ouput of lspci

root@abhi-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
root@abhi-laptop:~# 


also here is the output of lsmod


root@abhi-laptop:~# lsmod
Module                  Size  Used by
ipv6                  273892  8 
isofs                  36412  1 
udf                    87204  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
container               5504  0 
button                  8976  0 
toshiba_acpi           11952  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
sbs                    19592  0 
dock                   10656  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  2 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
joydev                 11328  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcmcia                 41388  0 
pcspkr                  4224  0 
ipw2100                72240  0 
ieee80211              35656  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_core               26112  0 
shpchp                 34580  0 
intel_agp              25620  1 
pci_hotplug            32704  1 shpchp
agpgart                35016  1 intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  2 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ata_piix               17540  4 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
root@abhi-laptop:~# 


i don't think its problem with my lan card driver, coz i am able to view files of other computer of the workgroup

when i am trying to ping 172.25.1.1(default gateway) its doesnot even try to ping and says that connect: network unrechable

---

### Post by superprash2003 on 2008-12-10
post output of /etc/network/interfaces file

---

### Post by kool124 on 2008-12-14
hi

sorry my internet was down so i was not able to reply

here is the output

auto lo
iface lo inet loopback


iface eth0 inet static
address 172.25.9.148
netmask 255.255.255.192
gateway 172.25.1.1

auto eth0

i did couple of things, i bought friends router, and configured my eth0 to dhcp mode and it accepted ip address from router and i was able to ping router.

so its clear that, problem is not with driver and that some thing else

---

