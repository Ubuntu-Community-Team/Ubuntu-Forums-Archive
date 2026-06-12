---
title: "Ubuntu startup error because of unsupported tv card"
date: 2009-11-08
forum: Multimedia Software
---

### Post by idodos on 2009-11-08
I've just installed Ubuntu 9.10 and seem to be getting some startup errors caused by my unsupported tv card. I know this card is not supported and was just wondering if I could disable those errors from appearing.
dmesg report:

```
[   11.761079] intel_rng: FWH not detected
[   12.148017] ivtv 0000:02:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   12.215582] zc3xx: probe 2wr ov vga 0x0000
[   12.260574] zc3xx: probe sensor -> 0011
[   12.260579] zc3xx: Find Sensor HV7131R(c)
[   12.264660] gspca: probe ok
[   12.264693] usbcore: registered new interface driver zc3xx
[   12.264699] zc3xx: registered
[   12.654851] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   12.852132] ivtv0: Encoder revision: 0x02060039
[   12.879136] cx25840 0-0044: firmware: requesting v4l-cx23885-avcore-01.fw
[   12.890715] cx25840 0-0044: firmware load i2c failure
[   13.038004] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.041279] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.044523] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.047686] wm8775 0-001b: I2C: cannot write 102 to register R21
[   13.091090] tuner 0-0060: tuner type not set
[   13.094065] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.097246] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.100454] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.103625] wm8775 0-001b: I2C: cannot write 102 to register R21
[   13.146655] tuner 0-0060: tuner type not set
[   13.147179] tuner 0-0060: tuner type not set
[   13.150843] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.155794] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.159000] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.162182] wm8775 0-001b: I2C: cannot write 108 to register R21
[   13.238076] tuner 0-0060: tuner type not set
[   13.241051] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.244231] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.247522] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.251406] wm8775 0-001b: I2C: cannot write 102 to register R21
[   13.312698] tuner 0-0060: tuner type not set
[   13.323036] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.327506] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.332572] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.336248] wm8775 0-001b: I2C: cannot write 108 to register R21
[   13.447221] tuner 0-0060: tuner type not set
[   13.451261] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   13.470417] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   13.485320] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   13.493284] wm8775 0-001b: I2C: cannot write 102 to register R21
```


Though all I've managed to see at startup were all those "[   xx.xxxxxx] wm8775 0-001b: I2C: cannot write xxx to register xxx" errors.

Thanks in advance!

---

### Post by sisco311 on 2009-11-08
Blacklist the wm8775 module.

Edit the /etc/modprobe.d/blacklist.conf file:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and append it with:
```
blacklist wm8775
```

---

### Post by idodos on 2009-11-08
> **sisco311 said:**
> Blacklist the wm8775 module.

Edit the /etc/modprobe.d/blacklist.conf file:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and append it with:
```
blacklist wm8775
```

Thanks for your time!
I did as you suggested. However, the result are the same..
Any ideas?

---

