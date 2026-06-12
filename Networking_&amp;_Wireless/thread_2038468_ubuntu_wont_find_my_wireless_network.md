---
title: "ubuntu wont find my wireless network"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by Devo88 on 2012-08-06
hi
ive just installed ubuntu 12.04. i installed it using a wired connection but when i try to connect it to my wifi it wont even find my network.
ive done all the system updates and installed wifi radar from USC but still no success. ive never used any linux based OS before so i have no idea how to solve this problem. 
i am using a toshiba satellite pro L10 laptop with built in wireless. 
please help me

---

### Post by praseodym on 2012-08-06
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lspci -nnk
lsusb
iwconfig
lsmod
rfkill list
```
Is the network "hidden"?

---

### Post by Devo88 on 2012-08-06
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: agpgart-intel
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel modules: i915
00:1d.0 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
	Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: snd_intel8x0
	Kernel modules: snd-intel8x0
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel modules: snd-intel8x0m
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
02:04.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
	Subsystem: AMBIT Microsystem Corp. Device [1468:0310]

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1ea7:0002  



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod
Module                  Size  Used by
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39791  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
i915                  414703  2 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                72919  0 
soundcore              14635  1 snd
serio_raw              13027  0 
bnep                   17830  2 
shpchp                 32325  0 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
sbs                    18178  0 
parport_pc             32114  0 
bluetooth             158438  7 bnep
joydev                 17393  0 
ppdev                  12849  0 
sbshc                  13536  1 sbs
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 26759  0 

rfkill list
didnt show anything

---

### Post by praseodym on 2012-08-06
```
02:04.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
Subsystem: AMBIT Microsystem Corp. Device [1468:0310]
```
Here is the card. Unfortunately, it only works with Ndiswrapper and the windows driver (attached)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Devo88 on 2012-08-06
probably a stupid question but how do i install these drivers?

---

### Post by praseodym on 2012-08-07
First you need to install the components needed via cable:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```
After that you can use the ndisgtk-tool to choose the appropriate *.inf file of the driver folder.

---

