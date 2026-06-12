---
title: "Suddenly lost wireless card"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by -Ender on 2009-04-06
Hi, I'm a newbie to Ubuntu, and I've been trying out new stuff with the OS and as a result have seemed to have borked something. I was able to connect to the internet using my wireless card up until yesterday, and after installing a few pieces of software (Cinelerra, inkscape, blender), Ubuntu no longer will see my wireless card. The controller is still there, but when I look under my network manager, or print out with ifconfig, or load up the hardware drivers, my wireless card is not there. I have tried booting up from the live cd, and lo and behold I can access the internet from that. So what do I do? I was thinking I might have to reformat, unless there's some way to restore all of the default applications. 

Oh, one thing that I did have to do was remove a lot of restricted drivers to update my nvidia drivers to 180.44 (linux-restricted, linux-restricted-common etc).

Any help at all would be greatly appreciated!

Oh, also, my system is a Dell Vostro 2510, and the wireless card is a Dell Wireless 1395 WLAN Mini-card, and I was using the default restricted Broadcom driver that Ubuntu was telling me to use.

[Edit]
I forgot to list out some more of the required info, sorry:

Kernel: 2.6.27-11-generic i686
Ubuntu 8.10

sudo lshw -C network:
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:f1:f4:c1
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:e6:d9:93:c3:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

lsusb:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0c45:63e0 Microdia 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:21:70:f1:f4:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1216 (1.2 KB)  TX bytes:1216 (1.2 KB)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

lsmod:
Module                  Size  Used by
nvidia               6909268  0 
i2c_core               31892  1 nvidia
binfmt_misc            16904  1 
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
sbs                    19464  0 
container              11520  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
uvcvideo               63624  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
snd_timer              29960  2 snd_pcm,snd_seq
v4l1_compat            22404  2 uvcvideo,videodev
dcdbas                 15008  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  25232  0 
output                 11008  1 video
battery                18436  0 
psmouse                45200  0 
evdev                  17696  14 
ac                     12292  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
intel_agp              33724  0 
serio_raw              13444  0 
mmc_core               58268  1 sdhci
wmi                    14504  0 
pcspkr                 10624  0 
button                 14224  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  2 nvidia,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24580  3 
r8169                  36100  0 
mii                    13440  1 r8169
ata_generic            12932  0 
libata                178208  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

[/Edit]

---

### Post by superprash2003 on 2009-04-06
try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by -Ender on 2009-04-06
That's how I activated my wireless card when I first installed Ubuntu. I had my system working, had the card on (so it's not a hardware switch that I missed), and I had been using the internet with the laptop only a few hours before. It has something to do with some of the software I put on, I believe. Again, it's some configuration that I screwed up when I was editing things, I'm sure. I just am having trouble finding out ways to do a rollback without losing settings.

---

