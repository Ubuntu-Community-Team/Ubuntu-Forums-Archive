---
title: "Pinnacle 800i - no digital on Mythbuntu 8.10"
date: 2009-01-04
forum: Mythbuntu
---

### Post by gmangum on 2009-01-04
I've tried Mythbuntu 8.04.1, 8.10, and 9.04 alpha2 with similar results.   I've tried the drivers included with each of these distributions plus several versions of the v4l-dvb drivers I've downloaded at various times.   I also have tried applying available updates as well as just after a clean install.

I have the firmware in /lib/firmware, and the analog portion of the card works fine.   I just can't get the digital portion to work at all.   Symptoms are: lspci only shows 1 device (rather than 3 which others appear to have when it works), and no /dev/dvb hierarchy gets created.   I did have this working (sort of) with MythDora 5.0 at one point, but want to switch to Mythbuntu so I can run Boxee.   I've installed the same v4l-dvb drivers from October that were working with Mythdora - no luck.

I also have a WinTV PVR USB2 on this box.   It works fine.

lspci:

root@mythtv2:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
00:0b.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

There should also be a 00:0b.1 and 00:0b.2 I think.

dmesg:

[   13.195076] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   13.196243] cx8800 0000:00:0b.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.200553] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,insmod option]
[   13.200563] cx88[0]: TV tuner type 76, Radio tuner type -1
[   13.225306] logips2pp: Detected unknown logitech mouse model 127
[   13.702530] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   14.792896] nvidia: module license 'NVIDIA' taints kernel.
[   15.183348] tuner' 1-0064: chip found @ 0xc8 (cx88[0])
[   15.232491] parport_pc 00:0a: reported by Plug and Play ACPI
[   15.232582] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.660148] xc5000 1-0064: creating new instance
[   15.661101] xc5000: Successfully identified at address 0x64
[   15.661106] xc5000: Firmware has not been loaded previously
[   15.662048] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   15.662055] firmware: requesting dvb-fe-xc5000-1.1.fw
[   15.829458] lirc_dev: IR Remote Control driver registered, major 61
[   15.887879]
[   15.887886] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $
Revision: 1.44 $
[   15.887893] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   16.092114] usb 1-2: reset full speed USB device using uhci_hcd and address 3
[   16.258113] lirc_dev: lirc_register_plugin: sample_rate: 0
[   16.262100] lirc_mceusb2[3]: SMK CORPORATION MCE TRANCEIVR Emulator Device 2006 on usb1:3
[   16.262258] usbcore: registered new interface driver lirc_mceusb2
[   16.262412] usbcore: registered new interface driver pvrusb2
[   16.262421] pvrusb2: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   16.262426] pvrusb2: Debug mask is 31 (0x1f)
[   16.799305] tuner' 2-0043: chip found @ 0x86 (pvrusb2_a)
[   16.934709] tda9887 2-0043: creating new instance
[   16.934718] tda9887 2-0043: tda988[5/6/7] found
[   16.968123] tuner' 2-0061: chip found @ 0xc2 (pvrusb2_a)
[   16.999013] cx25840' 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   17.001068] wm8775' 2-001b: chip found @ 0x36 (pvrusb2_a)
[   17.029864] tveeprom 2-00a2: Hauppauge model 24012, rev E1A3, serial# 10129003
[   17.029874] tveeprom 2-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   17.029880] tveeprom 2-00a2: TV standards NTSC(M) (eeprom 0x08)
[   17.029885] tveeprom 2-00a2: audio processor is CX25843 (idx 37)
[   17.029891] tveeprom 2-00a2: decoder processor is CX25843 (idx 30)
[   17.029895] tveeprom 2-00a2: has radio, has IR receiver, has no IR transmitter
[   17.029909] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk
[   17.029918] pvrusb2: Mapping standards mask=0xb700 (PAL-M/N/Nc;NTSC-M/Mj/Mk)
[   17.029924] pvrusb2: Setting up 6 unique standard(s)
[   17.029931] pvrusb2: Set up standard idx=0 name=PAL-M
[   17.029936] pvrusb2: Set up standard idx=1 name=PAL-N
[   17.029940] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   17.029945] pvrusb2: Set up standard idx=3 name=NTSC-M
[   17.029949] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   17.029953] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   17.029961] pvrusb2: Initial video standard guessed as NTSC-M
[   17.029991] pvrusb2: Device initialization completed successfully.
[   17.030519] pvrusb2: registered device video0 [mpeg]
[   17.031005] pvrusb2: registered device radio0 [mpeg]
[   17.059133] firmware: requesting v4l-cx25840.fw
[   20.535094] xc5000: firmware read 12332 bytes.
[   20.535102] xc5000: firmware upload
[   20.535113] cx88[0]: Calling XC5000 callback
[   23.244880] cx25840' 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   23.429928] tuner-simple 2-0061: creating new instance
[   23.429940] tuner-simple 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   23.657780] tda9887 2-0043: Data bytes: b=0x14 c=0x30 e=0x44
[   23.657791] tuner' 2-0061: Tuner mode:      analog TV
[   23.657796] tuner' 2-0061: Frequency:       175.25 MHz
[   23.657800] tuner' 2-0061: Standard:        0x00001000
[   23.663761] cx25840' 2-0044: Video signal:              not present
[   23.663767] cx25840' 2-0044: Detected format:           NTSC-M
[   23.663772] cx25840' 2-0044: Specified standard:        NTSC-M
[   23.663776] cx25840' 2-0044: Specified video input:     Composite 7
[   23.663781] cx25840' 2-0044: Specified audioclock freq: 48000 Hz
[   23.677772] cx25840' 2-0044: Detected audio mode:       forced mode
[   23.677780] cx25840' 2-0044: Detected audio standard:   no detected audio standard
[   23.677785] cx25840' 2-0044: Audio muted:               no
[   23.677789] cx25840' 2-0044: Audio microcontroller:     detecting
[   23.677795] cx25840' 2-0044: Configured audio standard: automatic detection
[   23.677800] cx25840' 2-0044: Configured audio system:   BTSC
[   23.677805] cx25840' 2-0044: Specified audio input:     Tuner (In8)
[   23.677810] cx25840' 2-0044: Preferred audio mode:      stereo
[   23.677817] wm8775' 2-001b: Input: 2
[   23.677838] firmware: requesting v4l-cx2341x-enc.fw
[   23.848978] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:0b.0/input/input7
[   23.850121] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 11, latency: 32, mmio: 0xdf000000
[   23.851143] cx88[0]/0: registered device video1 [v4l2]
[   23.852171] cx88[0]/0: registered device vbi0
[   25.945785] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   25.946755] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   25.949927] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   25.949944] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   25.950109] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   27.716494] lp0: using parport0 (interrupt-driven).
[   28.178248] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   28.899330] EXT3 FS on sda1, internal journal
[   30.140836] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   30.145992] SGI XFS Quota Management subsystem
[   30.178191] XFS mounting filesystem sda6
[   30.376793] Ending clean XFS mount for filesystem: sda6
[   31.453316] type=1505 audit(1231074306.951:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name
2="default" pid=3899
[   31.454207] type=1505 audit(1231074306.951:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid
=3899
[   31.557497] type=1505 audit(1231074307.055:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pi
d=3903
[   31.812154] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.031475] ACPI: WMI: Mapper loaded
[   35.852913] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   36.350386] NET: Registered protocol family 10
[   36.354465] lo: Disabled Privacy Extensions
[   38.158947] ppdev: user-space parallel port driver
[   51.405702] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   51.405732] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   51.405791] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   52.950359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.952269] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   52.966255] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   53.400333] NET: Registered protocol family 17
[   63.768081] eth0: no IPv6 routers present


Thanks for any help.

--
Gene

---

### Post by false_apology on 2009-01-05
I'm not sure exactly, but I would suggest trying a fresh install of Mythbuntu 8.10. I just installed this same card on 8.10 and it recognized it instantly. According to [this]("http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)") article on the mythtv wiki, the kernel in 8.10 should have the necessary drivers built in to read this card. 

What I did to get this work with digital was:
1. Copy the firmware as dictated in the wiki article
2. Plug in the card to the PCI slot
3. Opened up mythtv backend setup and it was there listed as "DVB" card. I had to change the lock timeout up a bit but after that I scanned and found channels. I am NOT using the analog portion of the card at the moment, if that's worth anything.

Maybe since you have the newer kernel *and*the v4l drivers, it's not working? That's why I would think starting with a fresh install to get the card working , and then adding pieces as you need them would be the best bet to figure out what is causing your problem.

good luck

---

### Post by dylan1055 on 2009-01-06
i have the same problem. 
it all works fine on a fresh install , until i run update manager.
the update manager asks to download a 'debian core something'. and that seems to kill it.:confused:

---

### Post by gmangum on 2009-01-06
Thanks for the reply.   I had tried just after a clean install of 8.10, but I had the card installed already.    I tried again this evening with a clean install without the card.   After the install I copied the firmware over and then installed the card.   Same result.   When I went into setup and tried selecting a DVB card, it did not have anything in the DVB card number field and there was a message that said unable to get info for card #0.   I saw from dmesg that it wasn't regocnizing the card, so I added "options cx88xx card=58" to /etc/modprobe.d/options and rebooted.   It then sees the card but only creates /dev/video0 and no /dev/dvb/...   Also if I try to "modprobe cx88-dvb" I get:

root@mythtv2:/etc/modprobe.d# modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

Any suggestions?

-- 
Gene

---

### Post by dylan1055 on 2009-01-06
Grate, i just re installed and followed [this guide]("http://www.zimbio.com/Ubuntu+Linux/articles/151/Ubuntu+And+Pinnacle+PCTV+HD") the same as i did last time.
however this time i got the same results as gmangum (unable to get info for card #0) WTF? 
The only difference (assuming) is the v4l-dvb driver has been updated. 
ive been 3 days fighting with this , so back to bestbuy with the card. swap it out for the usb stick pro thing ......

---

### Post by RonPDX on 2009-01-12
I am having the same problems as well, I am not able to pick any digital stations using Myth.

In my case I just have regular basic cable with Comcast. The only digital stations I can get are our local statons in the 700's (i.e. NBC HD is 708) with a converter box. 

So the question in this case is if there is a way to scan for channels that are that high up the channel latter?

What is interesting is that on a the Windows side using the Pinnacle software, I am able to tune into our local HD stations but they show up under a weird channel like 811.1192 (or something like that). 

Does anyone have any other ideas how to tune into local HD stations using Myth?

---

### Post by micro77 on 2009-02-13
hi
i tried win nova dvb-s2 equal to pinnacle dvb card.
and same results ;
```
dmesg | grep -i cx 
[   15.510197] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   15.511060] cx8800 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   15.511714] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   15.511785] cx88[0]: TV tuner type -1, Radio tuner type -1
[   15.528073] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   15.546158] cx2388x alsa driver version 0.0.6 loaded
[   16.098085] tveeprom 2-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   16.098259] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[   16.098379] cx88[0]: hauppauge eeprom: model=69100
[   16.104269] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:09.0/0000:01:08.0/input/input5
[   16.152207] cx88[0]/0: found at 0000:01:08.0, rev: 5, irq: 18, latency: 32, mmio: 0xfc000000
[   16.152343] cx88[0]/0: registered device video0 [v4l2]
[   16.152430] cx88[0]/0: registered device vbi0
[   16.152937] cx88[0]/2: cx2388x 8802 Driver Manager
[   16.153002] cx88-mpeg driver manager 0000:01:08.2: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   16.153075] cx88[0]/2: found at 0000:01:08.2, rev: 5, irq: 18, latency: 32, mmio: 0xfa000000
[   16.153556] cx88_audio 0000:01:08.1: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   16.153644] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   16.230056] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   16.230114] cx88/2: registering cx8802 driver, type: dvb access: shared
[   16.230170] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   16.230239] cx88[0]/2: cx2388x based DVB/ATSC card
[   16.230291] cx8802_alloc_frontends() allocating 1 frontend(s)
[   22.680802] cx24116_readreg: reg=0xff (error=-6)
[   29.084841] cx24116_readreg: reg=0xfe (error=-6)
[   29.084907] Invalid probe, probably not a CX24116 device
[   29.084992] cx88[0]/2: frontend initialization failed
[   29.085046] cx88[0]/2: dvb_register failed (err = -22)
[   29.085099] cx88[0]/2: cx8802 probe failed, err = -22

```

i thing ubuntu do not want to work this cards :(


```
sudo modprobe cx88-dvb 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```

---

