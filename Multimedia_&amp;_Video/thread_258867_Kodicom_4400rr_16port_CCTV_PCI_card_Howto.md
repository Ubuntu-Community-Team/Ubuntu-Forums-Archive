---
title: "Kodicom 4400rr 16port CCTV PCI card Howto"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by JamesX on 2006-09-16
Hi Everyone :) 

I've installed a Kodicom 4400r clone PCI card with 16port CCTV inputs and 4x BT878a chips on the board into my PC - however it appears that the BTTV driver is not recognising the card and I think I need to place some text in the "modprobe.conf" file to get the BTTV driver to recognise the card correctly.

Here's a link to a picture of the card: [http://www.linuxtv.org/v4lwiki/index.php/Kodicom_4400R](http://www.linuxtv.org/v4lwiki/index.php/Kodicom_4400R)

The PC is running Ubuntu 6.06 LTS and ZoneMinder, ZoneMinder works as I can view the webpage on the local machine and start and stop ZoneMinder however all I see in the ZoneMinder video screens is blue screen where the video should be showing?

After reading the Ubuntu and ZoneMinder forums I'm pretty sure the card is not being recognised by the BTTV driver when it loads, I'me a newbie to Linux but have learn't that running a few commands gives me some information as follows:

When I run "dmesg" from a Terminal I get the following output, it's a bit long and so I've choped a bit off from the start of the output that's not relevant:

```
[17179589.584000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.592000] agpgart: Detected NVIDIA nForce2 chipset
[17179589.596000] agpgart: AGP aperture is 64M @ 0xd8000000
[17179589.904000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.928000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.940000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[17179589.940000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[17179590.048000] Real Time Clock Driver v1.12
[17179590.092000] input: PC Speaker as /class/input/input1
[17179590.100000] **** SET: Misaligned resource pointer: f7d7fda2 Type 07 Len 0
[17179590.100000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179590.100000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 22 (level, high) -> IRQ 185
[17179590.100000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179590.236000] Floppy drive(s): fd0 is 1.44M
[17179590.252000] FDC 0 is a post-1991 82077
[17179590.376000] parport: PnPBIOS parport detected.
[17179590.376000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.420000] intel8x0_measure_ac97_clock: measured 54529 usecs
[17179590.420000] intel8x0: clocking to 47445
[17179590.508000] logips2pp: Detected unknown logitech mouse model 85
[17179590.540000] IT8212: IDE controller at PCI slot 0000:01:0c.0
[17179590.540000] **** SET: Misaligned resource pointer: dfa45ce2 Type 07 Len 0
[17179590.544000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179590.544000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 217
[17179590.544000] IT8212: chipset revision 16
[17179590.544000] it821x: controller in smart mode.
[17179590.544000] IT8212: 100% native mode on irq 217
[17179590.544000]     ide2: BM-DMA at 0xb400-0xb407, BIOS settings: hde:pio, hdf:pio
[17179590.544000]     ide3: BM-DMA at 0xb408-0xb40f, BIOS settings: hdg:pio, hdh:pio
[17179590.544000] Probing IDE interface ide2...
[17179590.648000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179590.672000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179590.672000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17179590.672000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179590.672000] eth0: RTL8169 at 0xf8aba000, 00:0d:61:1b:89:e9, IRQ 209
[17179591.056000] nvidia: module license 'NVIDIA' taints kernel.
[17179591.112000] Linux video capture interface: v1.00
[17179591.124000] Probing IDE interface ide3...
[17179591.156000] bttv: driver version 0.9.16 loaded
[17179591.156000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179591.260000] ts: Compaq touchscreen protocol output
[17179591.696000] **** SET: Misaligned resource pointer: dfa456e2 Type 07 Len 0
[17179591.696000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179591.696000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 225
[17179591.696000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179591.700000] bttv: Bt8xx card found (0).
[17179591.700000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179591.700000] bttv0: Bt878 (rev 17) at 0000:02:0c.0, irq: 177, latency: 32, mmio: 0xdc000000
[17179591.700000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179591.700000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17179591.704000] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[17179591.704000] bttv0: using tuner=-1
[17179591.704000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179591.704000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179591.708000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179591.708000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179591.712000] bttv0: registered device video0
[17179591.712000] bttv0: registered device vbi0
[17179591.712000] bttv: Bt8xx card found (1).
[17179591.712000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 225
[17179591.712000] bttv1: Bt878 (rev 17) at 0000:02:0d.0, irq: 225, latency: 32, mmio: 0xdc002000
[17179591.712000] bttv1: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179591.712000] bttv1: gpio: en=00000000, out=00000000 in=00feffff [init]
[17179592.964000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[17179592.964000] usbcore: registered new driver usblp
[17179592.964000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179604.512000] tveeprom 3-0050: Huh, no eeprom present (err=-121)?
[17179604.512000] bttv1: using tuner=-1
[17179604.512000] bttv1: i2c: checking for MSP34xx @ 0x80... not found
[17179610.912000] bttv1: i2c: checking for TDA9875 @ 0xb0... not found
[17179617.312000] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[17179623.712000] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[17179630.112000] bttv1: registered device video1
[17179630.112000] bttv1: registered device vbi1
[17179630.128000] bttv: Bt8xx card found (2).
[17179630.128000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17179630.128000] bttv2: Bt878 (rev 17) at 0000:02:0e.0, irq: 209, latency: 32, mmio: 0xdc004000
[17179630.128000] bttv2: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179630.128000] bttv2: gpio: en=00000000, out=00000000 in=00feffff [init]
[17179630.764000] r8169: eth0: link up
[17179631.796000] NET: Registered protocol family 17
[17179633.556000] NET: Registered protocol family 10
[17179633.556000] lo: Disabled Privacy Extensions
[17179633.556000] IPv6 over IPv4 tunneling driver
[17179642.928000] tveeprom 4-0050: Huh, no eeprom present (err=-121)?
[17179642.928000] bttv2: using tuner=-1
[17179642.928000] bttv2: i2c: checking for MSP34xx @ 0x80... <7>eth0: no IPv6 routers present
[17179649.328000] not found
[17179649.328000] bttv2: i2c: checking for TDA9875 @ 0xb0... not found
[17179655.728000] bttv2: i2c: checking for TDA7432 @ 0x8a... not found
[17179662.128000] bttv2: i2c: checking for TDA9887 @ 0x86... not found
[17179668.528000] bttv2: registered device video2
[17179668.528000] bttv2: registered device vbi2
[17179668.528000] bttv: Bt8xx card found (3).
[17179668.528000] ACPI: PCI Interrupt 0000:02:0f.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 217
[17179668.528000] bttv3: Bt878 (rev 17) at 0000:02:0f.0, irq: 217, latency: 32, mmio: 0xdc006000
[17179668.528000] bttv3: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179668.528000] bttv3: gpio: en=00000000, out=00000000 in=00feffff [init]
[17179681.328000] tveeprom 5-0050: Huh, no eeprom present (err=-121)?
[17179681.328000] bttv3: using tuner=-1
[17179681.328000] bttv3: i2c: checking for MSP34xx @ 0x80... not found
[17179687.728000] bttv3: i2c: checking for TDA9875 @ 0xb0... not found
[17179694.128000] bttv3: i2c: checking for TDA7432 @ 0x8a... not found
[17179700.528000] bttv3: i2c: checking for TDA9887 @ 0x86... not found
[17179706.928000] bttv3: registered device video3
[17179706.928000] bttv3: registered device vbi3
[17179706.956000] bt878: AUDIO driver version 0.0.0 loaded
[17179706.956000] bt878: Bt878 AUDIO function found (0).
[17179706.956000] ACPI: PCI Interrupt 0000:02:0c.1[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179706.956000] bt878(0): Bt878 (rev 17) at 02:0c.1, irq: 177, latency: 32, memory: 0xdc001000
[17179706.956000] bt878: Bt878 AUDIO function found (1).
[17179706.956000] ACPI: PCI Interrupt 0000:02:0d.1[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 225
[17179706.956000] bt878(1): Bt878 (rev 17) at 02:0d.1, irq: 225, latency: 32, memory: 0xdc003000
[17179706.956000] bt878: Bt878 AUDIO function found (2).
[17179706.956000] ACPI: PCI Interrupt 0000:02:0e.1[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 209
[17179706.956000] bt878(2): Bt878 (rev 17) at 02:0e.1, irq: 209, latency: 32, memory: 0xdc005000
[17179706.956000] bt878: Bt878 AUDIO function found (3).
[17179706.956000] ACPI: PCI Interrupt 0000:02:0f.1[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 217
[17179706.956000] bt878(3): Bt878 (rev 17) at 02:0f.1, irq: 217, latency: 32, memory: 0xdc007000
[17179707.488000] lp0: using parport0 (interrupt-driven).
[17179707.520000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179707.520000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179707.520000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179707.584000] Adding 1028152k swap on /dev/hda2.  Priority:-1 extents:1 across:1028152k
[17179707.772000] EXT3 FS on hda1, internal journal
[17179707.912000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179707.912000] md: bitmap version 4.39
[17179708.468000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179709.256000] cdrom: open failed.
[17179715.548000] ACPI: Power Button (FF) [PWRF]
[17179715.548000] ACPI: Power Button (CM) [PWRB]
[17179715.640000] ibm_acpi: ec object not found
[17179715.668000] pcc_acpi: loading...
[17179720.728000] ppdev: user-space parallel port driver
[17179721.084000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179721.084000] apm: overridden by ACPI.
[17179727.836000] Bluetooth: Core ver 2.8
[17179727.836000] NET: Registered protocol family 31
[17179727.836000] Bluetooth: HCI device and connection manager initialized
[17179727.836000] Bluetooth: HCI socket layer initialized
[17179727.880000] Bluetooth: L2CAP ver 2.8
[17179727.880000] Bluetooth: L2CAP socket layer initialized
[17179727.880000] Bluetooth: RFCOMM socket layer initialized
[17179727.880000] Bluetooth: RFCOMM TTY layer initialized
[17179727.880000] Bluetooth: RFCOMM ver 1.7
```

...and when I run "xawtv - hwscan" from a Terminal I get the following output:

```
This is xawtv-3.94, running on Linux/i686 (2.6.15-26-386)
looking for available devices
port 65-65
    type : Xvideo, image scaler
    name : NV Video Overlay

port 66-97
    type : Xvideo, image scaler
    name : NV Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner

/dev/video2: OK                         [ -device /dev/video2 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner

/dev/video3: OK                         [ -device /dev/video3 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner
```

...from reading the ZoneMinder forums, and the output above, it appears that the CCTV card I have is not being recognised and some users are able to edit their "modprobe.conf" files to enter "option bttv gbuffers=16 card=133,132,133,133" which will make the BBTV driver recognise the card as a kodicom card type, one master and three slave kodicom BT878a chips.

I've also tried running "modprobe bttv gbuffers=16 card=133,132,133,133" from a Terminal but when running "dmesg" immediately after this it appears nothing has changed as the card is still unrecognised.

I've placed "option bttv gbuffers=16 card=133,132,133,133" into the "/etc/modules" file but after rebooting and running "dmesg" from a Terminal I got the same result as above and so I assume it's not recognised the card - I think i must have edited the wrong file and so if anyone know could help I'd really appreciate it as the only option I have at the moment is to re-install Windows and use the supplied CCTV software --- however I can't stand windows and have wanted to get away from it for ages #-o 


Cheers, JamesX...

---

### Post by JamesX on 2006-09-17
Woo Hoo :p 

I've got it working by creating the file "/etc/modprobe.conf" and pasting the following text into it and then rebooting:

```
alias char-major-81 bttv
options bttv gbuffers=16 card=133,132,133,133 tuner=4,4,4,4
```

After rebooting and running "dmesg" from within a Terminal it picks up the card correctly and I can see video from all the 16 CCTV inputs within xawtv and ZoneMinder.

However I now have another problem which I'm trying to resolve, which is that most of the time when I click on a monitor from within the localhost ZoneMinder webpage I have to click "still" and then "stream" a few times in a row to get it to stream the video... and most of the time ZoneMinder webpage becomes unresponsive after a time - xawtv has no issues whatsoever though and so I'm certain it's a ZoneMinder thing and no longer a driver thing!

If anyone could shed some light on this that would be great, whenever I solve this issue I'll post back.

Oh and also when ZoneMinder becomes unresponsive if you close FireFox and then reopen FireFox and try to visit the ZoneMinder locahost webpage again it never loads - I've also had the machine become unresponsive but the PC hasn't frozen anymore since I created the "modprobe.conf" file.

Cheers, James...

---

### Post by JamesX on 2006-09-17
Took me a while being a newbie but I've sorted it :D 

To get ZoneMinder 1.22.2 working on my ubuntu 6.06 LTS system with a Kodicom 4400r 16port CCTV PCI card I had to install from source following the many instructions in this forum.

My eBay Kodicom clone card was not recognised and so by creating "/etc/modprobe.conf" file and pasting the following into it forced the BTTV driver to recognise it as a Kodicom 4400r card:

```
alias char-major-81 bttv
options bttv gbuffers=16 card=133,132,133,133 tuner=4,4,4,4
```

However to resolve the issue of my machine freezing up with multiple ZMS processes not terminating themselves I had to go to the OPTIONS page within ZoneMinder localhost webpage and under the PATHS tab change the "ZM_PATH_ZMS" path from "/cgi-bin/nph-zms" to "/cgi-bin/zms".

However the final issue for me was that I could not stream more than 2 images or videos from ZoneMinder at a time, I found this to be a browser limitation and so by typing "about:config" into FireFox i could change the setting to enable FireFox to raise the maximum simultaneous server connections from 2 to 32.

i now have ZoneMinder 1.22.2 running on Ubuntu 6.06 LTS perfectly with a Kodicom 4400r clone PCI card with 16 CCTV cameras :D 

Hope this post helps someone...

Cheers, JamesX...

---

### Post by kafkaian on 2006-11-18
Thanks. This will help me when I come to do mine shortly

---

### Post by JonFarrimond on 2008-04-10
For me this is excellent news.

Over the last few weeks I've investigated webcam orientated versions of a 12 camera implementation to observe concurrent experiments and found it to be difficult and costly (I estimated about £1000), but it seems that if your version is working well like this I can drop my budget to about £600 (ish).

I do have one question though, when you got your 4400 card with its four main BNC connections, how have you connected up the extra 12? I can't find good documentation online and was wondering if you got the required connectors in the box?

Thanks.

---

### Post by JamesX on 2008-04-13
Hi Jon :)

The eBay 16 port capture card has 4 BNC connectors at the rear and jumper block on the card that connects to an additional external 12 BNC connectors, these came with the card I bought from eBay.

Hope this helps.


Cheers, JamesX...

---

### Post by JonFarrimond on 2008-04-14
Cheers James.

---

### Post by Gordon Bennett on 2008-05-21
Excellent thread, I'll add in some notes following on from having a similar Kodicom 4400 clone installed in Ubuntu 8.0.4.

**IRQ's and motherboards.**

Most of these cctv cards have a note attached to them requiring an Intel motherboard.  Usually this means the capture card is a stubborn IRQ-hog, usually taking over multiple single instances of IRQ allocations (8x IRQ 11's, for example).
Some 2D/3D graphics cards default to IRQ 11 - what may happen, as it did with my system (a DFI nf4 Ultra motherboard, GeForce 7800GTX) is that the capture card and your gfx card will fight over the same IRQ and the machine will either not boot, or boot without video.
The solution is to change your BIOS IRQ allocations or re-arrange your capture card and graphics card into different slots until they cooperate!
As a side note, most graphics cards prefer an exclusive IRQ; after relocation due to the cctv card, they usually wind up sharing with another device or two; for example, my Nvidia 7800 used to have its own IRQ11 allocation, now it shares 3 with three other (low speed) devices.  So far, no problems encountered, though your mileage may vary if it shares the IRQ resource with an interrupt-hungry device.

**Driver loads, but no video/video garbled.**

This took me ages to track down - **[COLOR="Red"]some cards are shipped with the input attenuator set low.[/COLOR]**
If you look at the photo of the card (link: [4400R]("http://linuxtv.org/v4lwiki/index.php/Image:Kmc4400r-small.jpg")) you will notice a blue, square box on the upper middle edge of the card.  Get a screwdriver and turn that setting until you have the desired image - **do not force the turn**, it should rotate smoothly.

**Testing.**

I've found these tools best for testing the actual output (note the command-line versions use 640x480, PAL format and input 0 of the card):

**Xawtv** - run with: xawtv -nodga -geometry 640x480 -device /dev/video0

**TVTime** - run as standard, this works very well and has some nice de-interlacing options.

**MPlayer** - run with:  mplayer -v -tv device=/dev/video0:input=0:width=640:height=480:norm=pal:driver=v4l2:adevice=/dev/dsp:forceaudio tv://

---

