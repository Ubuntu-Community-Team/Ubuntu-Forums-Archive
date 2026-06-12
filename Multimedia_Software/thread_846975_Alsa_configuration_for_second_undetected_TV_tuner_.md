---
title: "Alsa configuration for second undetected TV tuner sound device"
date: 2008-07-02
forum: Multimedia Software
---

### Post by kessaris on 2008-07-02
Hello all,

Hope this message finds you all well, as close to hardware/software nirvana as you can be.

I've been making steady progress in converting a 2004-era japanese XP-Home laptop to more general open source functionality.

At present, my list of unconfigured hardware consists of two items!  The card reader (lost cause) and the tv tuner audio input!! woo hoo!

I've been over in the hardware/laptop forums for a while, working out how to activate the built-in tv tuner, and now that it's working, I thought maybe I'd try the multimedia forums for a fresh perspective on [B]how to get ALSA to recognize the tuner's sound input device!!!
[/B]
Just a bit of background, here is my lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
[COLOR="Red"]00:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)[/COLOR]
00:09.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
00:09.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
00:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```

I have marked the culprit device in [COLOR="Red"]RED[/COLOR].

I managed to get the video portion of this device working by using the ATI Tv Wonder driver.. [you can read about it in this thread here]("http://ubuntuforums.org/showthread.php?t=844941")

When it comes to the audio, so far, no luck unfortunately.  I know that Alsa does have a driver for this device, it's called **cx88-alsa**.

There is some information about this device over at video4linux, but it's for Gentoo and I'm still not sure how to adapt it to my particular system.

[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))

I've tried following the instructions on the ALSA page and Video4Linux page to get this device configured, but I'm afraid I really don't know enough about how ALSA is supposed to work to get it done.  Also, I have tried following the thread about hardware problems but it just left me without X for the longest time until I realized I had to reinstall some of the files for gnome, but that's a totally different story.

At present, here is my aplay configuration:

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and some output form my /proc/asound directory

```
root@alex-laptop:/home/alex# cat /proc/asound/
card0/   cards    modem/   oss/     seq/     V8235/   
card1/   devices  modules  pcm      timers   version  
root@alex-laptop:/home/alex# cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 48: [ 1- 0]: digital audio playback
 56: [ 1- 0]: digital audio capture
root@alex-laptop:/home/alex# cat /proc/asound/modules 
 0 snd_via82xx
 1 snd_via82xx_modem
root@alex-laptop:/home/alex# 

```

It's obvious that there are no cx88 devices listed as might be desirable.

While I continue searching through the various resources for installing an undetected device, I would really appreciate any tips on how to manually install the cx88 device in the hope of getting it to work by brute force.

Finally, here is some output from hwinfo

```
37: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/video4linux/video0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  video4linux.device = '/dev/video0'
  info.category = 'video4linux'
  linux.hotplug_type = 2 (0x2)
  video4linux.version = '1'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.subsystem = 'video4linux'
  access_control.file = '/dev/video0'
  access_control.type = 'video4linux'
  linux.device_file = '/dev/video0'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }

  38: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/video4linux/vbi0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  video4linux.device = '/dev/vbi0'
  info.category = 'video4linux'
  linux.hotplug_type = 2 (0x2)
  video4linux.version = '1'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.subsystem = 'video4linux'
  access_control.file = '/dev/vbi0'
  access_control.type = 'video4linux'
  linux.device_file = '/dev/vbi0'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }

  85: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  info.subsystem = 'pci'
  pci.vendor = 'Conexant'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.vendor = 'Conexant'
  info.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  pci.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.linux.driver = 'cx8800'
  pci.subsys_vendor = 'Sharp corporation'
  pci.product_id = 34816 (0x8800)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 5361 (0x14f1)
  linux.subsystem = 'pci'
  pci.subsys_product_id = 4150 (0x1036)
  pci.subsys_vendor_id = 5053 (0x13bd)
  pci.device_class = 4 (0x4)

 <6>EXT3-fs: mounted filesystem with ordered data mode.
  <6>Linux agpgart interface v0.103
  <6>agpgart: Detected VIA Apollo Pro266 chipset
  <6>agpgart: AGP aperture is 64M @ 0xa0000000
  <6>Yenta: CardBus bridge found at 0000:00:09.0 [13bd:1036]
  <6>Yenta: Using CSCINT to route CSC interrupts to PCI
  <6>Yenta: Routing CardBus interrupts to PCI
  <6>Yenta TI: socket 0000:00:09.0, mfunc 0x010c1202, devctl 0x44
  <6>Linux video capture interface: v2.00
  <6>input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  <6>ACPI: Power Button (FF) [PWRF]
  <6>input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
  <6>ACPI: Sleep Button (CM) [SBTN]
  <6>input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
  <6>ACPI: Lid Switch [LID]
  <6>cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
  <6>Yenta: ISA IRQ mask 0x0040, PCI irq 10
  <6>Socket status: 30000006
  <6>ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
  <4>cx88[0]: Your board isn't known (yet) to the driver.  You can
  <4>cx88[0]: try to pick one of the existing card configs via
  <4>cx88[0]: card=<n> insmod option.  Updating to the latest
  <4>cx88[0]: version might help as well.
  <4>cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
  <4>cx88[0]:    card=0 -> UNKNOWN/GENERIC
  <4>cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
  <4>cx88[0]:    card=2 -> GDI Black Gold
  <4>cx88[0]:    card=3 -> PixelView
  <4>cx88[0]:    card=4 -> ATI TV Wonder Pro
  <4>cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
  <4>cx88[0]:    card=6 -> AverTV Studio 303 (M126)
  <4>cx88[0]:    card=7 -> MSI TV-@nywhere Master
  <4>cx88[0]:    card=8 -> Leadtek Winfast DV2000
  <4>cx88[0]:    card=9 -> Leadtek PVR 2000
  <4>cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
  <4>cx88[0]:    card=11 -> Prolink PlayTV PVR
  <4>cx88[0]:    card=12 -> ASUS PVR-416
  <4>cx88[0]:    card=13 -> MSI TV-@nywhere
  <4>cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
  <4>cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
  <4>cx88[0]:    card=16 -> KWorld LTV883RF
  <4>cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
  <4>cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
  <4>cx88[0]:    card=19 -> Conexant DVB-T reference design
  <4>cx88[0]:    card=20 -> Provideo PV259
  <4>cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
  <4>cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
  <4>cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
  <4>cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
  <4>cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
  <4>cx88[0]:    card=26 -> IODATA GV/BCTV7E
  <4>cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
  <4>cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
  <4>cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
  <4>cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
  <4>cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
  <4>cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
  <4>cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
  <4>cx88[0]:    card=34 -> ATI HDTV Wonder
  <4>cx88[0]:    card=35 -> WinFast DTV1000-T
  <4>cx88[0]:    card=36 -> AVerTV 303 (M126)
  <4>cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
  <4>cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
  <4>cx88[0]:    card=39 -> KWorld DVB-S 100
  <4>cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
  <4>cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
  <4>cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
  <4>cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
  <4>cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
  <4>cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
  <4>cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
  <4>cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
  <4>cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
  <4>cx88[0]:    card=49 -> PixelView PlayTV P7000
  <4>cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
  <4>cx88[0]:    card=51 -> WinFast DTV2000 H
  <4>cx88[0]:    card=52 -> Geniatech DVB-S
  <4>cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
  <4>cx88[0]:    card=54 -> Norwood Micro TV Tuner
  <4>cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
  <4>cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
  <4>cx88[0]:    card=57 -> ADS Tech Instant Video PCI
  <4>cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
  <6>cx88[0]: subsystem: 13bd:1036, board: UNKNOWN/GENERIC [card=0,autodetected]
  <6>cx88[0]: TV tuner type -1, Radio tuner type -1

snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer, Live 0xee9d6000
  video 16016 0 - Live 0xee9a0000
  output 2560 1 video, Live 0xee9c4000
  tuner 34656 0 - Live 0xee9e3000
  tea5767 5828 1 tuner, Live 0xee967000
  tda8290 12036 1 tuner, Live 0xee9d2000
  tuner_xc2028 18896 1 tuner, Live 0xee9cc000
  tda9887 8772 1 tuner, Live 0xee9b5000
  tuner_simple 8328 1 tuner, Live 0xee9b9000
  via_ircc 23316 0 - Live 0xee9bd000
  mt20xx 11592 1 tuner, Live 0xee97d000
  tea5761 4420 1 tuner, Live 0xee99d000
  irda 174076 1 via_ircc, Live 0xefa01000
  crc_ccitt 1728 1 irda, Live 0xee992000
  i2c_prosavage 3200 0 - Live 0xee995000
  battery 9860 0 - Live 0xee997000
  cx8800 27828 0 - Live 0xee981000
  cx88xx 58344 1 cx8800, Live 0xee9a5000
  ac 3908 0 - Live 0xee96a000
  ir_common 32068 1 cx88xx, Live 0xee989000
  i2c_viapro 7380 0 - Live 0xee97a000
  i2c_algo_bit 5508 2 i2c_prosavage,cx88xx, Live 0xee96d000
  button 5776 0 - Live 0xee91b000
  tveeprom 14032 1 cx88xx, Live 0xee94e000
  videodev 30464 3 tuner,cx8800,cx88xx, Live 0xee971000
  v4l1_compat 13316 1 videodev, Live 0xee95b000
  compat_ioctl32 960 1 cx8800, Live 0xee92f000
  v4l2_common 9600 2 tuner,cx8800, Live 0xee957000
  yenta_socket 22412 1 - Live 0xee960000
  rsrc_nonstatic 10496 1 yenta_socket, Live 0xee953000
  via_agp 7872 1 - Live 0xee918000
  agpgart 26416 2 drm,via_agp, Live 0xee927000
  i2c_core 18448 14 tuner,tea5767,tda8290,tuner_xc2028,tda9887,tuner_simple,mt20xx,tea5761,i2c_prosavage,cx88xx,i2c_viapro,i2c_algo_bit,tveeprom,v4l2_common, Live 0xee876000
  pcmcia_core 31440 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xee91e000
  videobuf_dma_sg 9988 2 cx8800,cx88xx, Live 0xee90f000
  videobuf_core 14340 3 cx8800,cx88xx,videobuf_dma_sg, Live 0xee8c4000
  btcx_risc 3848 2 cx8800,cx88xx, Live 0xee840000
  ext3 111304 3 - Live 0xee931000
  jbd 33876 1 ext3, Live 0xee8fb000
  mbcache 5888 1 ext3, Live 0xee816000
  sg 29552 0 - Live 0xee906000
  sr_mod 13476 0 - Live 0xee87c000
  cdrom 33120 1 sr_mod, Live 0xee8f1000
  sd_mod 24080 5 - Live 0xee8ea000
  pata_acpi 4480 0 - Live 0xee837000
  ata_generic 5060 0 - Live 0xee834000
  pata_via 8260 4 - Live 0xee872000
  via_rhine 19592 0 - Live 0xee85e000
  mii 4416 1 via_rhine, Live 0xee85b000
  libata 136836 3 pata_acpi,ata_generic,pata_via, Live 0xee8a1000
  scsi_mod 126092 5 sbp2,sg,sr_mod,sd_mod,libata, Live 0xee8ca000
  dock 7308 1 libata, Live 0xee842000
  ehci_hcd 30732 0 - Live 0xee865000
  uhci_hcd 20300 0 - Live 0xee83a000
  usbcore 123504 4 usbhid,ehci_hcd,uhci_hcd, Live 0xee881000
  ohci1394 27632 0 - Live 0xee81b000
  ieee1394 75448 2 sbp2,ohci1394, Live 0xee847000
  thermal 14684 0 - Live 0xee82a000
  processor 21664 2 thermal, Live 0xee823000
  fan 3844 0 - Live 0xee819000
----- /proc/modules end -----
  used irqs: 0,1,2,5,7,8,9,10,11,12,14,15

23: PCI 08.0: 11200 TV Card
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_14f1_8800
  Unique ID: RE4e.VYe4YDjmeKA
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: tv card
  Model: "Sharp CX23880/1/2/3 PCI Video and Audio Decoder"
  Vendor: pci 0x14f1 "Conexant"
  Device: pci 0x8800 "CX23880/1/2/3 PCI Video and Audio Decoder"
  SubVendor: pci 0x13bd "Sharp corporation"
  SubDevice: pci 0x1036 
  Revision: 0x05
  Driver: "cx8800"
  Driver Modules: "cx8800"
  Memory Range: 0xf1000000-0xf1ffffff (rw,non-prefetchable)
  IRQ: 5 (246203 events)
  Module Alias: "pci:v000014F1d00008800sv000013BDsd00001036bc04sc00i00"
  Driver Info #0:
    Driver Status: cx8800 is active
    Driver Activation Cmd: "modprobe cx8800"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

In most situations the video and audio devices are listed as separate enries for devices with the conexant tuner chip, but in this case there's only one.

Anyway, all help is appreciated.  I had been hoping to use alsaconf, but it's been deprecated and it probably wouldn't solve the problem.

---

