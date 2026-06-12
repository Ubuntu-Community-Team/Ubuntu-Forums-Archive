---
title: "PVR-500 not working in Gutsy Gibbon"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by miklo025 on 2007-11-18
i,
I posted the same letter on the ivtv users list but thought that I would post it here too just in case someone has some good information.
I just decided to move my trustworthy FC3 mythtv setup to a new box
using ubuntu instead, this turned out to be a bad idea. Both of the tuners on the PVR-500 is just giving me static.
Since I had seen someone else posting about this on the list and was
told it was suspected, broken hardware I decided to move the capture card back to the FC3 setup and guess what it worked like a charm so there has to be something wrong with this combination.
Below I have posted the output of dmesg.

[ 54.931206] ivtv: ==================== START INIT IVTV ==================
[ 54.931212] ivtv: version 1.0.0 (2.6.22-14-generic SMP mod_unload
586 ) loading
[ 54.931304] ivtv0: Autodetected Hauppauge card (cx23416 based)
[ 54.931355] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 16 (level,
low) -> IRQ 16
[ 55.218180] usbcore: registered new interface driver hiddev
[ 55.235082] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[ 55.235611] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical
Mouse] on usb-0000:00:03.1-1
[ 55.235633] usbcore: registered new interface driver usbhid
[ 55.235637] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c:
v2.6:USB HID core driver
[ 55.585608] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4157069656 bytes)
[ 55.799606] ivtv0: Encoder revision: 0x02050032
[ 55.799610] ivtv0: Recommended firmware version is 0x02060039.
[ 55.857654] tveeprom 0-0050: Hauppauge model 23559, rev D591, serial# 7787583
[ 55.857659] tveeprom 0-0050: tuner model is Philips FQ1216AME MK4
(idx 91, type 56)
[ 55.857663] tveeprom 0-0050: TV standards PAL(B/G) PAL(I)
SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[ 55.857666] tveeprom 0-0050: second tuner model is Philips
TEA5768HL FM Radio (idx 101, type 62)
[ 55.857669] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[ 55.857672] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[ 55.857675] tveeprom 0-0050: has radio, has no IR receiver, has no
IR transmitter
[ 55.857678] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[ 55.877517] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[ 55.877553] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[ 55.881142] tuner 0-0060: TEA5767 detected.
[ 55.881145] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[ 55.881161] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[ 55.881390] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[ 55.912626] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[ 59.136704] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 59.223607] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[ 59.268185] tuner 0-0061: type set to 56 (Philips PAL/SECAM multi
(FQ1216AME MK4))
[ 59.581104] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[ 59.581527] ivtv0: Registered device video32 for encoder YUV (2 MB)
[ 59.581920] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[ 59.582220] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[ 59.582649] ivtv0: Registered device radio0 for encoder radio
[ 59.609621] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[ 59.609666] ivtv: ====================== NEXT CARD ======================
[ 59.609672] ivtv1: Autodetected Hauppauge card (cx23416 based)
[ 59.609732] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 17 (level,
low) -> IRQ 22
[ 60.243267] ivtv1: loaded v4l-cx2341x-enc.fw firmware (4157070696 bytes)
[ 60.457052] ivtv1: Encoder revision: 0x02050032
[ 60.457056] ivtv1: Recommended firmware version is 0x02060039.
[ 60.461772] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[ 60.461792] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[ 60.464780] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[ 60.480317] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[ 63.702778] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 63.774605] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[ 63.840123] tveeprom 1-0050: Hauppauge model 23559, rev D591, serial# 7787583
[ 63.840128] tveeprom 1-0050: tuner model is Philips FQ1216AME MK4
(idx 91, type 56)
[ 63.840132] tveeprom 1-0050: TV standards PAL(B/G) PAL(I)
SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[ 63.840136] tveeprom 1-0050: second tuner model is Philips
TEA5768HL FM Radio (idx 101, type 62)
[ 63.840139] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[ 63.840142] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[ 63.840145] tveeprom 1-0050: has radio, has no IR receiver, has no
IR transmitter
[ 63.840148] ivtv1: Correcting tveeprom data: no radio present on second unit
[ 63.840151] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[ 63.907616] tuner 1-0061: type set to 56 (Philips PAL/SECAM multi
(FQ1216AME MK4))
[ 64.222606] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[ 64.223025] ivtv1: Registered device video33 for encoder YUV (2 MB)
[ 64.223432] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[ 64.223766] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[ 64.249890] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[ 64.249921] ivtv: ==================== END INIT IVTV ====================


If you need anymore input from me just let me know

Kind Regards

Mikael

---

