---
title: "Ubuntu 8.04 does not recognise Atheros Wireless"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by markhc on 2012-01-31
Hi

I have retro desktop hardware that supports only Ubuntu 8.04, and am trying to install a wireless card.  The packaging reads TP-Link TL-WN350GD.  I was led to believe it would work out of the box, but not so.

Knoppix 6.0.1 shows that the card works and connects to my wireless network without effort.  My problem seems to be with Ubuntu.

If I may, please see the output of my commands:
> root@gizmo:/home/markhc# lsmod
Module                  Size  Used by
ath_pci                99232  0 
wlan                  206832  1 ath_pci
ath_hal               191568  1 ath_pci
reiserfs              235264  1 
rfcomm                 39444  2 
l2cap                  23300  13 rfcomm
bluetooth              57092  4 rfcomm,l2cap
ppdev                   9348  0 
ipv6                  255876  18 
speedstep_lib           5380  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5124  0 
freq_table              4484  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       4120  0 
cpufreq_powersave       1792  0 
cpufreq_conservative     7200  0 
container               4736  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
video                  18960  0 
output                  3712  1 video
dock                   10124  0 
battery                13316  0 
af_packet              21764  2 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
ac                      6020  0 
lp                     11332  0 
parport_pc             35108  1 
parport                35912  3 ppdev,lp,parport_pc
usb_storage            73152  1 
evdev                  11776  3 
rtc                    13212  0 
usbhid                 30976  0 
pcspkr                  3072  0 
hid                    36480  1 usbhid
libusual               19872  1 usb_storage
i2c_core               23696  0 
button                  8336  0 
sis_agp                 9220  1 
agpgart                33456  1 sis_agp
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
ext3                  133128  2 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sg                     36256  0 
sd_mod                 29584  7 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
pata_acpi               7424  0 
sata_sis                8836  3 
floppy                 58116  0 
ehci_hcd               36748  0 
ohci_hcd               25488  0 
ata_generic             7428  0 
pata_sis               14340  1 sata_sis
sis900                 23040  0 
mii                     5504  1 sis900
usbcore               144108  6 usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
libata                160112  4 pata_acpi,sata_sis,ata_generic,pata_sis
scsi_mod              151308  5 usb_storage,sg,sd_mod,sr_mod,libata
thermal                15772  0 
processor              28336  1 thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2688  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  3 

> root@gizmo:/home/markhc# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA (rev 01)
00:09.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

> root@gizmo:/home/markhc# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:13:d4:15:83:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
> 
root@gizmo:/home/markhc# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

As I say, Knoppix sees the card and loads the driver, connects to my wireless network without a whimper.  Can anyone here suggest my solution?

Thanks in advance

Mark

---

### Post by Bucky Ball on 2012-01-31
Get a cable and install MadWifi which is specifically for Atheros, but honestly, 8.04 LTS has been out of support since last April and you may not get much support there either. From lspci above it sees the Atheros but doesn't know the model so you are going to need driver and firmware probably. Check their site perhaps. 

You may want to look at what Knoppix is using to get the card up re driver and locate and install that in Ubuntu. 

Wondering why you can only run 8.04. Have you tried 10.04 LTS? How much RAM do you have and what processor? You might also consider Xubuntu 10.04 LTS which is specifically for lower spec machines ...

---

### Post by markhc on 2012-01-31
Thanks for quick reply Bucky Ball.  MadWifi installed already and no help there.

10.04 requires grub2 and my hardware just will not do it.  I spent a hellish weekend on it and am scared to go there again.  Maybe Xubuntu is where I need to go ...

---

### Post by Bucky Ball on 2012-01-31
Did you try the alternate install ISO? What is it specifically about grub2 that kills the install? Ubuntu install has swollen since 2008 also. ;)

You probably don't have enough room on your drive but if you could create 15Gb of free space you could use that to experiment with some installs of more recent things without killing your working 8.04.

Does it work via a cable and you have gotten your updates? Then try checking 'Administration>System>Hardware Drivers' from memory.

---

### Post by markhc on 2012-02-01
Thanks again Bucky Ball for your suggestions.  From memory I recall that all of my efforst to upgrade to later versions of Ubuntu kept revealing "Grub error 5".  My googling led me to infer that my hardware was deficient.

I will bite the bullet and upgrade my hardware.  It's beyond time ... allow me to mark this thread as "solved".

---

