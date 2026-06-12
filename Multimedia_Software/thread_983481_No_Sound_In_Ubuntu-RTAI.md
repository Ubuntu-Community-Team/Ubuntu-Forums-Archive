---
title: "No Sound In Ubuntu-RTAI"
date: 2008-11-15
forum: Multimedia Software
---

### Post by ivodalves on 2008-11-15
Hi,

I had to build a linux kernel with RTAI in UBUNTU 8.04 with kernel 2.6.24-19 generic.

I used a vanilla kernel (2.6.24) whith the ".config" from "2.6.24-19 generic." and did the "#make oldconfig" and pressed enter at all prompts.

Every thing seems to work fine, except the sound.

Here's the output of lspci:

ivo@realmachine:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller



We can see the audio device: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02).



But I can not see the module for this device in 

ivo@realmachine:~$ lsmod
Module                  Size  Used by
ppp_deflate             5632  0 
zlib_deflate           20376  1 ppp_deflate
bsd_comp                6400  0 
ppp_async              10240  1 
crc_ccitt               2944  1 ppp_async
ppp_generic            24212  7 ppp_deflate,bsd_comp,ppp_async
slhc                    6400  1 ppp_generic
ipv6                  238596  10 
i915                   22656  2 
drm                    70676  3 i915
rfcomm                 34320  2 
l2cap                  20992  13 rfcomm
bluetooth              50788  4 rfcomm,l2cap
ppdev                   8324  0 
iptable_filter          3328  0 
ip_tables              11876  1 iptable_filter
x_tables               12164  1 ip_tables
sbp2                   20360  0 
lp                      9764  0 
loop                   14340  0 
joydev                 10304  0 
pcmcia                 33068  0 
option                  9984  1 
parport_pc             31524  1 
parport                31816  3 ppdev,lp,parport_pc
usbserial              30568  4 option
usb_storage            68672  0 
libusual               17572  1 usb_storage
sdhci                  15236  0 
evdev                   9856  2 
mmc_core               43524  1 sdhci
iTCO_wdt               11044  0 
iTCO_vendor_support     4228  1 iTCO_wdt
psmouse                37008  0 
serio_raw               6276  0 
yenta_socket           23180  1 
rsrc_nonstatic         11648  1 yenta_socket
pcmcia_core            33044  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  3456  0 
intel_agp              22164  1 
agpgart                27848  3 drm,intel_agp
shpchp                 29972  0 
pci_hotplug            23068  1 shpchp
ext3                  121608  2 
jbd                    40468  1 ext3
mbcache                 7552  1 ext3
sg                     31248  0 
sr_mod                 14628  0 
cdrom                  34464  1 sr_mod
sd_mod                 26368  5 
usbhid                 26496  0 
hid                    34560  1 usbhid
ata_piix               13572  4 
ata_generic             5892  0 
ohci1394               28464  0 
libata                128112  2 ata_piix,ata_generic
ieee1394               80056  2 sbp2,ohci1394
scsi_mod              129932  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               30732  0 
uhci_hcd               21648  0 
usbcore               114284  8 option,usbserial,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
e1000                 118848  0 
fuse                   42516  5 

And in the "System->Preferences->Sound->Device" in gnome I cannot see the intel sound device.

When I trie to access sound volume this message is showed: "No plugin or device for GStreamer control can be found"

Does anyone knows how to solve this without messing a lot with the kernel (because of RTAI)  ?

---

