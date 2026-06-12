---
title: "audio card unrecognized in ibex"
date: 2009-01-16
forum: Multimedia Software
---

### Post by C++ on 2009-01-16
i have an AMD 3800++, m2npv-vm mainboard computer. i use intrepid ibex and this is the first time i have so many times problems at ubuntu.

after flash 10 plugin install, youtube did not give any sounds and i tried nearly all methods i could find on internet. a little later on, my computer was unable to give any audio media!

i got "No volume control GStreamer plugins and/or devices found." message from the volume icon on the taskbar. so tried a lot of things to get the audio back(no audio on either firefox and amarok,vlc etc.).

on system>preferences>sound, there's no audio device to choose.

i have ubuntu intrepid ibex(as the main operating system), gOS(for a try) and vista(i need for some programs). there's no audio problem on neither vista nor gOS.

this is what i see when i look at my alsa information:

> 
!!Linux Distribution
!!------------------

Ubuntu 8.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.10"


!!Kernel Information
!!------------------

Kernel release:    2.6.27-10-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

aRts:
      Installed - Yes (/usr/bin/artsd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
	Subsystem: 1043:81cb


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:217: no soundcards found...

ARECORD

arecord: device_list:217: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ipv6
af_packet
binfmt_misc
bridge
stp
bnep
rfcomm
sco
l2cap
bluetooth
ppdev
powernow_k8
cpufreq_ondemand
cpufreq_powersave
cpufreq_userspace
cpufreq_stats
freq_table
cpufreq_conservative
video
output
wmi
pci_slot
container
sbs
sbshc
battery
iptable_filter
ip_tables
x_tables
ac
sbp2
lp
fglrx
agpgart
evdev
pcspkr
parport_pc
parport
i2c_nforce2
button
i2c_core
k8temp
isp1760
shpchp
pci_hotplug
ext3
jbd
mbcache
sr_mod
cdrom
sd_mod
crc_t10dif
sg
usbhid
hid
pata_amd
sata_nv
ata_generic
ohci1394
pata_acpi
forcedeth
ieee1394
libata
scsi_mod
dock
ehci_hcd
ohci_hcd
usbcore
thermal
processor
fan
fuse
vesafb
fbcon
tileblit
font
bitblit
softcursor


you see, my sound card is not recognised, but this is my hwinfo:

> 
guven@guven-desktop:~$ hwinfo --sound
17: PCI 10.1: 0403 Audio device                                 
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_10de_26c
  Unique ID: wRyD.WL+f1WXqJn7
  SysFS ID: /devices/pci0000:00/0000:00:10.1
  SysFS BusID: 0000:00:10.1
  Hardware Class: sound
  Model: "nVidia MCP51 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x026c "MCP51 High Definition Audio"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81cb 
  Revision: 0xa2
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 5 (no events)
  Module Alias: "pci:v000010DEd0000026Csv00001043sd000081CBbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown



what can i do? it's terrible to pass to another operating system to listen music and nothing else(maybe video play also:) )

really please find me a way other than new installation.

---

