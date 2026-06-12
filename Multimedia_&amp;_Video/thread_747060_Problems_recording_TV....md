---
title: "Problems recording TV..."
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by toddk111 on 2008-04-06
Hello,

I have an AMD 64x2 4200+ with 1GB RAM running Ubuntu 7.10 64 with Kaffeine 0.85. I have four tuners (2 DVICO FusionHDTV5 USB Gold and 2 Avermedia AVerTVHD MCE A180). I'm using a QAM ATSC cable source and I'm able to tune channels with Kaffeine but they pixelate a lot and the recorded files show a lot of errors when I run them through stream fix in VideoRedo. In Windows 2000, I don't have any picture quality problems and I don't get errors in my recorded files so I don't think it is a problem with my cards or my signal. Would please tell me what I can do to improve the quality of my recordings? Are there any settings that I need to change?  Is there a better application for simple multi-tuner timed recordings? (I don't want to use a big application like MythTV).

Thanks,
Todd

---

### Post by xc3RnbFO8P on 2008-04-06
Can you show the output of:
> lsusb
> dmesg   (-dvb-usb information)

---

### Post by toddk111 on 2008-04-06
Thanks for the reply.  Here is the info:

lsusb
------------------------------------------------
Bus 002 Device 008: ID 0fe9:d501 DVICO 
Bus 002 Device 007: ID 0fe9:d501 DVICO 


lspci
-------------------------------------------------
01:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


dmesg
________________________________
[   44.579609] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in cold state, will try to load a firmware

[   44.647479] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'

[   44.721068] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in cold state, will try to load a firmware

[   44.723403] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'

[   44.727809] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22

[   44.727816] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22

[   44.728063] PCI: Setting latency timer of device 0000:00:05.0 to 64

[   44.753542] usb 2-3: USB disconnect, address 3

[   44.753583] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.

[   44.884999] usb 2-4: USB disconnect, address 4

[   44.885036] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.

[   44.940952] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

[   45.016924] usbcore: registered new interface driver dvb_usb_cxusb

[   45.770552] loop: module loaded

[   45.796055] lp0: using parport0 (interrupt-driven).

[   45.906507] Linux video capture interface: v2.00

[   45.971226] saa7130/34: v4l2 driver version 0.2.14 loaded

[   45.973256] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16

[   45.973262] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16

[   45.973270] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 16, latency: 84, mmio: 0xfdfff000

[   45.973276] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]

[   45.973285] saa7133[0]: board init: gpio is 110400

[   46.119986] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92

[   46.119995] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00

[   46.120001] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00

[   46.120007] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

[   46.120012] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00

[   46.120018] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.120024] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.120031] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.122318] saa7133[0]: registered device video0 [v4l2]

[   46.124241] saa7133[0]: registered device vbi0

[   46.124695] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17

[   46.124705] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17

[   46.124712] saa7133[1]: found at 0000:01:06.0, rev: 209, irq: 17, latency: 84, mmio: 0xfdffe000

[   46.124718] saa7133[1]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]

[   46.124727] saa7133[1]: board init: gpio is 10400

[   46.271863] saa7133[1]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92

[   46.271872] saa7133[1]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00

[   46.271878] saa7133[1]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00

[   46.271883] saa7133[1]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

[   46.271889] saa7133[1]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00

[   46.271894] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.271901] saa7133[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.271907] saa7133[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   46.272652] saa7133[1]: registered device video1 [v4l2]

[   46.273105] saa7133[1]: registered device vbi1

[   46.287537] saa7134 ALSA driver for DMA sound loaded

[   46.287616] saa7133[0]/alsa: saa7133[0] at 0xfdfff000 irq 16 registered as card -2

[   46.301438] saa7133[1]/alsa: saa7133[1] at 0xfdffe000 irq 17 registered as card -1

[   46.359795] nxt200x: NXT2004 Detected

[   46.359868] DVB: registering new adapter (saa7133[0]).

[   46.359872] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...

[   46.371795] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...

[   46.389584] nxt2004: Waiting for firmware upload(2)...

[   46.553903] usb 2-3: new high speed USB device using ehci_hcd and address 7

[   46.695322] usb 2-3: configuration #1 chosen from 1 choice

[   46.695515] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.

[   46.695625] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   46.726609] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold).

[   46.755678] DVB: registering frontend 1 (LG Electronics LGDT3303 VSB/QAM Frontend)...

[   46.757002] input: IR-receiver inside an USB DVB receiver as /class/input/input5

[   46.757027] dvb-usb: schedule remote query interval to 100 msecs.

[   46.757031] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.

[   47.017528] usb 2-4: new high speed USB device using ehci_hcd and address 8

[   47.166821] usb 2-4: configuration #1 chosen from 1 choice

[   47.167019] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.

[   47.167126] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   47.198109] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold).

[   47.201432] DVB: registering frontend 2 (LG Electronics LGDT3303 VSB/QAM Frontend)...

[   47.202483] input: IR-receiver inside an USB DVB receiver as /class/input/input6

[   47.202504] dvb-usb: schedule remote query interval to 100 msecs.

[   47.202508] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.

[   48.102377] nxt2004: Firmware upload complete

[   50.680265] nxt200x: NXT2004 Detected

[   50.680304] DVB: registering new adapter (saa7133[1]).

[   50.680308] DVB: registering frontend 3 (Nextwave NXT200X VSB/QAM frontend)...

[   50.692267] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...

[   50.694539] nxt2004: Waiting for firmware upload(2)...

[   52.406861] nxt2004: Firmware upload complete




I'd really appreciate any help you could give me.
Thanks,
Todd

---

### Post by xc3RnbFO8P on 2008-04-07
You have to compile the the driver from source, install, and then add the following to your /etc/modprobe.d/options file:

options cx23885 card=4

[http://ubuntuforums.org/showthread.php?t=748048]("http://ubuntuforums.org/showthread.php?t=748048")

---

