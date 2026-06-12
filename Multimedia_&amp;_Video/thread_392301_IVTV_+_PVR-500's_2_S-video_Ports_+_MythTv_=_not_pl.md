---
title: "IVTV + PVR-500's 2 S-video Ports + MythTv = not playing nice?"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by dillanlaughlin on 2007-03-24
I've got some craziness going on with my MythTV setup.

I am connecting 2 DirecTV STB's to my PVR-500 via S-Video and stereo audio.

IVTV drivers are installed successfully on this Ubuntu 6.10 machine, with the following output:

[   42.203799] ivtv:  ==================== START INIT IVTV ====================
[   42.203802] ivtv:  version 0.7.3 (tagged release) loading
[   42.203804] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload gcc-4.1
[   42.203806] ivtv:  In case of problems please include the debug info between
[   42.203808] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   42.203810] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   42.228444] ts: Compaq touchscreen protocol output
[   42.574539] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   42.579647] ACPI: PCI Interrupt 0000:04:08.0[A] -> GSI 18 (level, low) -> IRQ 201
[   42.645718] tveeprom 0-0050: Hauppauge model 23552, rev D587, serial# 8897747
[   42.645721] tveeprom 0-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   42.645724] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   42.645727] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   42.645730] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   42.645732] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   42.645734] tveeprom 0-0050: has radio, has no IR remote
[   42.645736] ivtv0: This is the first unit of a PVR500
[   42.746223] tuner 0-0060: TEA5767 detected.
[   42.746226] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   42.746247] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   42.746624] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   43.093929] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   43.122780] NET: Registered protocol family 17
[   48.752004] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   48.888501] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   49.617129] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   49.835288] ivtv0: Encoder revision: 0x02060039
[   49.835291] ivtv0 warning: Encoder Firmware can be buggy, use version 0x02040011, 0x02040024 or 0x02050032.
[   49.835450] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   49.835682] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[   49.835926] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[   49.836117] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   49.836552] ivtv0: Create encoder radio stream
[   49.836593] tuner 0-0061: type set to 70 (Samsung TCPN 2121P30A)
[   50.033930] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   50.033965] ivtv:  ======================  NEXT CARD  ======================
[   50.033968] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[   50.034013] ACPI: PCI Interrupt 0000:04:09.0[A] -> GSI 19 (level, low) -> IRQ 209
[   50.126053] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   50.433970] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   53.099861] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   56.071061] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   56.186931] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   56.266166] tveeprom 1-0050: Hauppauge model 23552, rev D587, serial# 8897747
[   56.266170] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   56.266173] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   56.266176] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   56.266179] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   56.266181] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   56.266183] tveeprom 1-0050: has radio, has no IR remote
[   56.266185] ivtv1: This is the second unit of a PVR500
[   56.266187] ivtv1: Correcting tveeprom data: no radio present on second unit
[   56.991901] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   57.209038] ivtv1: Encoder revision: 0x02060039
[   57.209041] ivtv1 warning: Encoder Firmware can be buggy, use version 0x02040011, 0x02040024 or 0x02050032.
[   57.209237] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[   57.209473] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[   57.209722] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[   57.209927] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[   57.210312] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[   57.404994] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   57.405009] ivtv:  ====================  END INIT IVTV  ====================


After doing a: ivtvctl -d /dev/video0 -p 1 (sets video input on video0 to svideo-1)
and ivtvctl -d /dev/video1 -p 1 (sets video input on video0 to svideo-1)

I can do: cat /dev/video0 > /tmp/test_capture0.mpg and cat /dev/video1 > /tmp/test_capture1.mpg
The output for each file is correct and reflects the correct STB.

My mythtv-setup capture card section has /dev/video0 and /dev/video1 per the instructions.
mythtv-setup input connections has /dev/video0 - S-Video 1 with a DirecTV Video Source setup and /dev/video1 - S-Video 1 with the same DirecTV Video Source setup.

However, when MythTV attempts to record from both tuners the second S-Video is always black w/o audio.

The PVR-500's daughter board jumpers are set correctly and the daughter board is connected to the PVR-500 Header 2 connection, as indicated in the instructions on the Hauppauge website.

I have also tried setting MythTV to look for the Input Connection /dev/video1 S-Video 2 with no luck.

Any assistance is greatly appreciated!

-Dillan

---

### Post by superm1 on 2007-03-29
Hi, 
A newer driver, 0.7.4 was recently released (and is supposed to co-operate better with new firmware).  Can you update to that and try again?

The ivtv wiki pages have been updated to reflect the new driver (its mainly switching the ivtvdriver repository to use "all" instead of "firmware"

---

### Post by dillanlaughlin on 2007-04-20
> **superm1 said:**
> Hi, 
A newer driver, 0.7.4 was recently released (and is supposed to co-operate better with new firmware).  Can you update to that and try again?

The ivtv wiki pages have been updated to reflect the new driver (its mainly switching the ivtvdriver repository to use "all" instead of "firmware"

superm1 thanks for the tip, unfortunately I was already using the 0.7.4 release. Still no dice. I decided to wait for the release of Feisty to see if I would have any better luck. I have to say that the Feisty setup thus far has been very easy most things work right out of the box. However I am still stuck with the same issue of a blank screen with no audio. I feel like there st be some idiotic thing I am doing wrong here. Anyway it's got me stumped.

Any and all help is greatly appreciated!

---

### Post by dillanlaughlin on 2007-04-20
dmesg output now is:

[   55.718719] ivtv:  ==================== START INIT IVTV ====================
[   55.718723] ivtv:  version 0.10.1 (tagged release) loading
[   55.718725] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 
[   55.718727] ivtv:  In case of problems please include the debug info between
[   55.718729] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   55.718730] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   55.718876] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   55.719782] ACPI: PCI Interrupt 0000:04:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   56.001384] NET: Registered protocol family 10
[   56.001481] lo: Disabled Privacy Extensions
[   56.001534] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.110495] md: md0 stopped.
[   56.161697] ACPI: PCI Interrupt 0000:00:1d.0[C] -> GSI 22 (level, low) -> IRQ 22
[   56.242786] md: bind<sdb1>
[   56.242977] md: bind<sda1>
[   56.296451] md0: setting max_sectors to 128, segment boundary to 32767
[   56.296456] raid0: looking at sda1
[   56.296458] raid0:   comparing sda1(390708736) with sda1(390708736)
[   56.296460] raid0:   END
[   56.296462] raid0:   ==> UNIQUE
[   56.296463] raid0: 1 zones
[   56.296464] raid0: looking at sdb1
[   56.296466] raid0:   comparing sdb1(390708736) with sda1(390708736)
[   56.296468] raid0:   EQUAL
[   56.296469] raid0: FINAL 1 zones
[   56.296473] raid0: done.
[   56.296475] raid0 : md_size is 781417472 blocks.
[   56.296476] raid0 : conf->hash_spacing is 781417472 blocks.
[   56.296478] raid0 : nb_zone is 1.
[   56.296479] raid0 : Allocating 8 bytes for hash.
[   56.408660] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   56.624665] ivtv0: Encoder revision: 0x02050032
[   56.624669] ivtv0: Recommended firmware version is 0x02060039.
[   56.688531] tveeprom 0-0050: Hauppauge model 23552, rev D587, serial# 8897747
[   56.688536] tveeprom 0-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   56.688539] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   56.688541] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   56.688544] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   56.688546] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   56.688549] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   56.688552] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   56.715191] tuner 0-0060: TEA5767 detected.
[   56.715196] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   56.715225] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   56.715574] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   56.752254] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   61.950591] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   62.075286] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   62.146731] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   62.147046] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   62.147362] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   62.147556] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   62.147883] ivtv0: Registered device radio0 for encoder radio
[   62.147904] tuner 0-0061: type set to 70 (Samsung TCPN 2121P30A)
[   62.553943] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   62.554145] ivtv:  ======================  NEXT CARD  ======================
[   62.554149] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   62.554207] ACPI: PCI Interrupt 0000:04:09.0[A] -> GSI 19 (level, low) -> IRQ 19
[   63.198250] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   63.418441] ivtv1: Encoder revision: 0x02050032
[   63.418444] ivtv1: Recommended firmware version is 0x02060039.
[   63.426555] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   63.448995] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   68.304032] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   68.409041] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   68.478467] tveeprom 1-0050: Hauppauge model 23552, rev D587, serial# 8897747
[   68.478472] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   68.478475] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   68.478478] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   68.478481] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   68.478483] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   68.478485] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   68.478488] ivtv1: Correcting tveeprom data: no radio present on second unit
[   68.478490] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   68.542786] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   68.543107] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   68.543448] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   68.543673] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   68.543879] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[   68.602665] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   68.604548] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   68.936660] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   68.936678] ivtv:  ====================  END INIT IVTV  ====================

---

