---
title: "webcam and tv tuner not working in karmic"
date: 2010-02-06
forum: Multimedia Software
---

### Post by pickarooney on 2010-02-06
Since moving to karmic I've ben unable to get either of my video devies to work. Both were fine in Jaunty and are both recognised by Karmicbut don't actually do anything.

When I run tvtime there are no channels active. I can scan and rescan but necer find one that works. When I flick through the inactive channels sometimes I get a half-second of an image which then disappears. 

The webcam is listed in the video capture devices section of skype, but when I press the Test Video button, nothing happens at all. I tried camorama and one other capture program but neither picked up an image.

I wonder if I'm not missing some vital package that I used to have in Jaunty for v4l devices?

---

### Post by Blackie_Chan on 2010-02-07
More details is needed, which video device is used by the webcam or tv card?

What kind of video card do you have? What kind of webcam do you have? Which video device are they assigned to? 

What's the output of:
```
$> ls /dev/video*
$> dmesg  {what the portion related to your tv card or webcam}
$> less /var/log/udev {what the portion related to your tv card or webcam}
```

---

### Post by no2498 on 2010-02-07
for the webcam
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
get programs ( cheese and wxcam ) 1 if not both will see the cam
if gstreamer is not installed install it

---

### Post by pickarooney on 2010-02-08
> **no2498 said:**
> for the webcam
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
get programs ( cheese and wxcam ) 1 if not both will see the cam
if gstreamer is not installed install it

v4l2 gives me a green screen while v4l1 gives a 'supported format' error.

Cheese recognised the camera and displayed an image!
I couldn't find wxcam.

skype still won't react to the TEST button in the video devices section.
I tried exporting 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

but no change.

---

### Post by no2498 on 2010-02-08
there is a v4l1 to v4l2 package you need
it is so you can use v4l1 with the v4l2 

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

that will tell you what all you need to install wxcam read it


[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

use the get deb it has wxcam 1.0.4 is the latest for 910 or 1.0.2 for 804

i did not find the package v4l1 to v4l2 to say what 1 you need
but if cheese sees it thats a good thing
try it in ( ekiga softphone ) also


now tell the forum what you are using  


$> ls /dev/video*
$> dmesg  {what the portion related to your tv card or webcam}
$> less /var/log/udev {what the portion related to your tv card or webcam}

---

### Post by pickarooney on 2010-02-09
Forgive the long post, I'm not sure which bits are relevant.

dmesg
```

[    7.403416] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[    7.942543] udev: starting version 147
[    8.584301] Linux video capture interface: v2.00
[    8.603488] gspca: main v2.6.0 registered
[    8.605394] gspca: probing 093a:2468
[    8.608063] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[    8.608067] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[    8.614307] gspca: probe ok
[    8.614325] usbcore: registered new interface driver pac207
[    8.614328] pac207: registered
[    9.197337] nvidia: module license 'NVIDIA' taints kernel.
[    9.197342] Disabling lock debugging due to kernel taint
[    9.453887] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.464215]   alloc irq_desc for 18 on node -1
[    9.464219]   alloc kstat_irqs on node -1
[    9.464227] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.464234] nvidia 0000:01:00.0: setting latency timer to 64
[    9.464480] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[    9.678951] parport_pc 00:08: reported by Plug and Play ACPI
[    9.678989] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    9.720830] ppdev: user-space parallel port driver
[    9.887969] lp0: using parport0 (interrupt-driven).
[   10.007432] bttv: driver version 0.9.18 loaded
[   10.007436] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.007482] bttv: Bt8xx card found (0).
[   10.007501] bttv 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.007515] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 64, mmio: 0xdfeff000
[   10.010403] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   10.010408] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   10.010411] IRQ 21/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.010449] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   10.012941] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   10.058761] tveeprom 1-0050: The eeprom says no radio is present, but the tuner type
[   10.058764] tveeprom 1-0050: indicates otherwise. I will assume that radio is present.
[   10.058768] tveeprom 1-0050: Hauppauge model 44809, rev E1A5, serial# 10095533
[   10.058771] tveeprom 1-0050: tuner model is TCL MPE05-2 (idx 105, type 38)
[   10.058774] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   10.058777] tveeprom 1-0050: audio processor is None (idx 0)
[   10.058780] tveeprom 1-0050: decoder processor is BT878 (idx 14)
[   10.058782] tveeprom 1-0050: has radio
[   10.058784] bttv0: Hauppauge eeprom indicates model#44809
[   10.058786] bttv0: tuner type=38
[   10.372307] bttv0: audio absent, no audio device found!
[   10.616333] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.740596] tuner 1-0043: chip found @ 0x86 (bt878 #0 [sw])
[   11.068100] tda9887 1-0043: creating new instance
[   11.068104] tda9887 1-0043: tda988[5/6/7] found
[   11.072053] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   11.364697] tuner-simple 1-0061: creating new instance
[   11.364703] tuner-simple 1-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   11.366427] bttv0: registered device video1
[   11.366449] bttv0: registered device vbi0
[   11.366469] bttv0: registered device radio0
[   11.366505] bttv0: PLL: 28636363 => 35468950 ..
[   11.389095] EXT4-fs (sda3): internal journal on sda3:8
[   11.396029]  ok
[   11.398382] Bt87x 0000:02:01.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.398572] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   11.400249] C-Media PCI 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.400451] cmipci: no OPL device at 0x388, skipping...
[   11.914188] EXT4-fs (sda1): barriers enabled
[   11.923637] kjournald2 starting: pid 855, dev sda1:8, commit interval 5 seconds
[   11.923828] EXT4-fs (sda1): internal journal on sda1:8
[   11.923832] EXT4-fs (sda1): delayed allocation enabled
[   11.923835] EXT4-fs: file extents enabled
[   11.923950] EXT4-fs: mballoc enabled
[   11.923965] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   12.026179] kjournald starting.  Commit interval 5 seconds
[   12.029381] EXT3 FS on sdb1, internal journal
[   12.029386] EXT3-fs: mounted filesystem with writeback data mode.
[   12.136277] kjournald starting.  Commit interval 5 seconds
[   12.136555] EXT3 FS on sdc1, internal journal
[   12.136560] EXT3-fs: mounted filesystem with writeback data mode.
[   13.473086] kjournald starting.  Commit interval 5 seconds
[   13.473284] EXT3 FS on sda4, internal journal
[   13.473289] EXT3-fs: mounted filesystem with writeback data mode.
[   14.567074] __ratelimit: 3 callbacks suppressed
[   14.567077] type=1505 audit(1265706694.978:12): operation="profile_replace" pid=932 name=/sbin/dhclient3
[   14.567348] type=1505 audit(1265706694.978:13): operation="profile_replace" pid=932 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.567505] type=1505 audit(1265706694.978:14): operation="profile_replace" pid=932 name=/usr/lib/connman/scripts/dhclient-script
[   14.575928] type=1505 audit(1265706694.986:15): operation="profile_replace" pid=933 name=/usr/bin/evince
[   14.582001] type=1505 audit(1265706694.994:16): operation="profile_replace" pid=933 name=/usr/bin/evince-previewer
[   14.585446] type=1505 audit(1265706694.998:17): operation="profile_replace" pid=933 name=/usr/bin/evince-thumbnailer
[   14.592366] type=1505 audit(1265706695.006:18): operation="profile_replace" pid=935 name=/usr/lib/cups/backend/cups-pdf
[   14.592701] type=1505 audit(1265706695.006:19): operation="profile_replace" pid=935 name=/usr/sbin/cupsd
[   14.597110] type=1505 audit(1265706695.010:20): operation="profile_replace" pid=936 name=/usr/sbin/mysqld-akonadi
[   14.599782] type=1505 audit(1265706695.010:21): operation="profile_replace" pid=937 name=/usr/sbin/tcpdump
[   17.237082] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   27.648018] eth0: no IPv6 routers present
[ 2284.203445] usb 3-4: USB disconnect, address 2
[ 2284.203594] gspca: disconnect complete
[ 2284.640032] usb 3-4: new full speed USB device using ohci_hcd and address 3
[ 2284.848090] usb 3-4: configuration #1 chosen from 1 choice
[ 2284.850579] gspca: probing 093a:2468
[ 2284.858914] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[ 2284.858919] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[ 2284.864091] gspca: probe ok
[ 2318.853565] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[30568.212176] usb 3-4: USB disconnect, address 3
[30568.212332] gspca: disconnect complete
[30585.524033] usb 3-4: new full speed USB device using ohci_hcd and address 4
[30585.732163] usb 3-4: configuration #1 chosen from 1 choice
[30585.734121] gspca: probing 093a:2468
[30585.738062] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[30585.738066] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[30585.744127] gspca: probe ok
[30585.859239] usb 3-4: USB disconnect, address 4
[30585.859383] gspca: disconnect complete
[30600.852029] usb 3-4: new full speed USB device using ohci_hcd and address 5
[30601.060160] usb 3-4: configuration #1 chosen from 1 choice
[30601.062753] gspca: probing 093a:2468
[30601.070095] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[30601.070099] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[30601.080589] gspca: probe ok
[30601.145812] usb 3-4: USB disconnect, address 5
[30601.145963] gspca: disconnect complete
[30606.140044] usb 2-4: new full speed USB device using ohci_hcd and address 4
[30606.347595] usb 2-4: configuration #1 chosen from 1 choice
[30606.350374] gspca: probing 093a:2468
[30606.359256] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[30606.359261] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[30606.368120] gspca: probe ok
[30607.428049] usb 2-4: USB disconnect, address 4
[30607.428196] gspca: disconnect complete
[36751.644039] usb 3-4: new full speed USB device using ohci_hcd and address 6
[36751.852159] usb 3-4: configuration #1 chosen from 1 choice
[36751.854692] gspca: probing 093a:2468
[36751.858083] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[36751.858088] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468

```

ls /dev/video*

```

/dev/video0  /dev/video1

```

video0 is the webcam at this moment in time

less /var/log/udev 

```

KERNEL[1265706690.423951] add      /module/bttv (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/bttv
SUBSYSTEM=module
SEQNUM=1482

KERNEL[1265706690.423972] add      /bus/bttv-sub (bus)
UDEV_LOG=3
ACTION=add
DEVPATH=/bus/bttv-sub
SUBSYSTEM=bus
SEQNUM=1483

KERNEL[1265706690.423985] add      /module/snd_seq_device (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/snd_seq_device
SUBSYSTEM=module
SEQNUM=1484

KERNEL[1265706690.428233] add      /devices/pci0000:00/0000:00:14.4/0000:02:01.0/i2c-adapter/i2c-1 (i2c-adapter)
UDEV_LOG=3

```

I installed wxcam from a .deb but it won't run because of dependency issues (liblavjpeg). I'll try find that v4l1 to v4l2 pacakge.

---

### Post by no2498 on 2010-02-09
there is more than 1 wxcam on 910 1.0.4
804 is 1.0.2
and ive seen a 1.0.3
on 804 i had to get all the other files first
look in the old getdeb's
and have you restarted the computer

---

### Post by pickarooney on 2010-02-09
OK, I'm not sure if it was restarting X or installing Ekiga that did it, but I now have video in skype! Nothing in tvtime though...

---

### Post by HappyFeet on 2010-02-09
> **pickarooney said:**
> OK, I'm not sure if it was restarting X or installing Ekiga that did it, but I now have video in skype! Nothing in tvtime though...

What kind of tv tuner do you have?

---

### Post by pickarooney on 2010-02-10
Hauppauge WinTV, btb878

---

### Post by pickarooney on 2010-02-16
Resolved by reinstalling Jaunty.

---

