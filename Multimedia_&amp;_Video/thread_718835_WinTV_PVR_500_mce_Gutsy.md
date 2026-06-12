---
title: "WinTV PVR 500 mce Gutsy"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by dngn on 2008-03-08
I have zero luck with getting this card to work.Below are messages from zapping tv viewer,tvtime
and dmesg. Any HELP will greatly appreciated would just like to get it to work

Zapping TV Viewer::"Couldn't open /dev/video0, try other devices?"

 When the NO option is chosen I get :: "Sorry, but "/dev/video0" could not be opened:
The device cannot be attached to any controller"

TVTime:: "No such file or directory" & "Cannot capture device /dev/video0."
                
DMESG::
[   61.956150] ivtv:  ==================== START INIT IVTV ====================
[   61.956157] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   61.956256] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   62.037521] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 22 (level, low) -> IRQ 22
[   62.120023] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   62.120028] Uniform CD-ROM driver Revision: 3.20
[   62.120100] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   62.129105] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   62.129129] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   62.667896] 2:3:3: cannot set freq 16000 to ep 0x86
[   62.739774] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4160676200 bytes)
[   62.955657] ivtv0: Encoder revision: 0x02060039
[   63.014157] tveeprom 0-0050: Hauppauge model 23552, rev E687, serial# 10025309
[   63.014161] tveeprom 0-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   63.014164] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   63.014167] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   63.014170] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   63.014173] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   63.014175] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   63.014178] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   63.037141] tuner 0-0060: TEA5767 detected.
[   63.037145] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   63.037174] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   63.037402] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   63.064340] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   64.667161] usbcore: registered new interface driver snd-usb-audio
[   64.667286] usbcore: registered new interface driver uvcvideo
[   64.667290] USB Video Class driver (v0.1.0)
[   66.281115] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   66.384338] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   66.429135] tuner 0-0061: type set to 70 (Samsung TCPN 2121P30A)
[   66.740071] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   66.740283] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   66.740523] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   66.740626] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   66.740898] ivtv0: Registered device radio0 for encoder radio
[   66.763455] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   66.763492] ivtv:  ======================  NEXT CARD  ======================
[   66.763497] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   66.763571] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 23 (level, low) -> IRQ 19
[   67.401061] ivtv1: loaded v4l-cx2341x-enc.fw firmware (4160677272 bytes)
[   67.613905] ivtv1: Encoder revision: 0x02060039
[   67.619276] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   67.634408] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   70.842714] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   70.914541] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   70.980080] tveeprom 1-0050: Hauppauge model 23552, rev E687, serial# 10025309
[   70.980085] tveeprom 1-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[   70.980088] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   70.980091] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   70.980094] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   70.980096] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   70.980099] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   70.980102] ivtv1: Correcting tveeprom data: no radio present on second unit
[   70.980104] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   71.044613] tuner 1-0061: type set to 70 (Samsung TCPN 2121P30A)
[   71.354360] ivtv1: Registered device video2 for encoder MPEG (4 MB)
[   71.354565] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   71.354816] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   71.354918] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   71.376548] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   71.376570] ivtv:  ====================  END INIT IVTV  ====================

---

