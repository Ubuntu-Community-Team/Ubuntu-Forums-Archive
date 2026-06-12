---
title: "Pinnacle PCTV USB Sttick"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by caesar753 on 2007-06-23
Hi all,

i have a big problem with my usb dvbt device.
I bought it some weeks ago and i tried to get channels in Windows XP, but it didn't find anything, then i tried to install it under linux, i follow some how-to's and i think i've installed a hundred time both em2880 and em28xx and every program needed to watch the Tv, but they didn't function at all.
today i tried to launch **dmesg** and it gave me this answer
```
[  675.935800] em28xx-input.c: remote control handler detached
[  694.928839] usb 3-2: new high speed USB device using ehci_hcd and address 4
[  695.063952] usb 3-2: configuration #1 chosen from 1 choice
[  695.064152] em28xx new video device (eb1a:2870): interface 0, class 255
[  695.064157] em28xx: device is attached to a USB 2.0 bus
[  695.064158] em28xx: you're using the experimental/unstable tree from mcentral.de
[  695.064160] em28xx: there's also a stable tree available but which is limited to
[  695.064162] em28xx: linux <=2.6.19.2
[  695.064163] em28xx: it's fine to use this driver but keep in mind that it will move
[  695.064165] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[  695.064166] em28xx: proved to be stable
[  695.064170] em28xx #0: Alternate settings: 8
[  695.064172] em28xx #0: Alternate setting 0, max size= 0
[  695.064173] em28xx #0: Alternate setting 1, max size= 0
[  695.064175] em28xx #0: Alternate setting 2, max size= 1448
[  695.064177] em28xx #0: Alternate setting 3, max size= 2048
[  695.064178] em28xx #0: Alternate setting 4, max size= 2304
[  695.064180] em28xx #0: Alternate setting 5, max size= 2580
[  695.064182] em28xx #0: Alternate setting 6, max size= 2892
[  695.064183] em28xx #0: Alternate setting 7, max size= 3072
[  695.277408] input: em2880/em2870 remote control as /class/input/input9
[  695.277438] em28xx-input.c: remote control handler attached
[  695.278240] attach_inform: eeprom detected.
[  695.304642] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 70 28 c0 12 81 00 6a 22 00 00
[  695.304652] em28xx #0: i2c eeprom 10: 00 00 04 57 02 0d 00 00 00 00 00 00 00 00 00 00
[  695.304658] em28xx #0: i2c eeprom 20: 44 00 00 00 f0 10 02 00 00 00 00 00 5b 00 00 00
[  695.304664] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 9d d0 ba 4b
[  695.304671] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304676] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304681] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[  695.304687] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 37 00 30 00 20 00 44 00
[  695.304693] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[  695.304699] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304705] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304710] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304715] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304721] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304726] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304732] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  695.304737] EEPROM ID= 0x9567eb1a
[  695.304739] Vendor/Product ID= eb1a:2870
[  695.304741] No audio on board.
[  695.304742] 500mA max power
[  695.304744] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[  695.308129] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[  695.308133] tuner 1-0060: chip found @ 0xc0 (em28xx #0)
[  695.308185] attach inform (default): detected I2C address c0
[  695.308191] /home/caesar753/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[  695.308193] /home/caesar753/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[  695.313620] tuner 1-0060: Tuner has no way to set tv freq
[  695.313625] em2880-dvb.c: DVB Init
[  695.314233] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[  695.314236] ===============================
[  695.314237] 7f 
[  695.314239] ================================
[b][u][  695.314610] zl10353_read_register: readreg error (reg=127, ret==-19)
[  695.314648] em2880-dvb.c: failed initializing zl10353 DVB-T demodulator
[  695.314650] em2880-dvb.c: retrying with mt352 DVB-T demodulator
[  695.314983] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[  695.314985] ===============================
[  695.314986] 7f 
[  695.314988] ================================
[  695.315357] mt352_read_register: readreg error (reg=127, ret==-19)
[  695.315387] em2880-dvb.c: no luck with mt352 demodulator, not attaching em2880-dvb
[  695.315389] em2880-dvb.c: DVB-T demodulator not reachable, did you try "modprobe em28xx device_mode=1"[/b][/u]
[  695.315392] em28xx #0: Found Pinnacle PCTV DVB-T

```
Now, do you think that if he cannot retrive any demodulator my device is broken and i can go back to the shop and try to change it? I think it is very strange that it doesn't function nor under Windows nor under Ubuntu...
Or do you have any solution?

thank you...

---

### Post by geekgirl74 on 2007-07-06
did you connect your device to an usb-hub? it could be possible, that it doesn't get enough power... had the same problem (FIXME:em28xx_i2c_send_bytes(1e): write failed), which disappeared after connecting it directly into the usb slot of my notebook (though the crappy driver is still not working) :(
I invested many days to get this evil stick to work, but support for this seems to be broken (tuner mt2060 is removed from the driver and the workaround does find a tuner, but it can't tune)...

---

