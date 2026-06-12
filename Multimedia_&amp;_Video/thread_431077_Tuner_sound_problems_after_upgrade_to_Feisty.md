---
title: "Tuner sound problems after upgrade to Feisty"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by jaymode on 2007-05-02
I have upgraded to Feisty successfully. There is one annoying problem I have been having after the upgrade though. My tv tuner card's sound will just go out. dmesg shows the folowing:

```


[427189.250093] msp3400 1-0040: I/O error #0 (read 0x10/0x200)
[427189.260658] msp3400 1-0040: I/O error #1 (read 0x10/0x200)
[427189.272775] msp3400 1-0040: I/O error #2 (read 0x10/0x200)
[427189.283280] msp3400 1-0040: giving up, resetting chip. Sound will go off, sorry folks :-|
[427189.287064] msp3400 1-0040: chip reset failed
[427189.875497] msp3400 1-0040: I/O error #0 (read 0x10/0x200)
[427189.887471] msp3400 1-0040: I/O error #1 (read 0x10/0x200)
[427189.899457] msp3400 1-0040: I/O error #2 (read 0x10/0x200)
[427189.910079] msp3400 1-0040: giving up, resetting chip. Sound will go off, sorry folks :-|
[427189.913768] msp3400 1-0040: chip reset failed
[428959.617286] msp3400 1-0040: I/O error #0 (read 0x10/0x200)
[428959.630744] msp3400 1-0040: I/O error #1 (read 0x10/0x200)
[428959.646785] msp3400 1-0040: I/O error #2 (read 0x10/0x200)
[428959.661240] msp3400 1-0040: giving up, resetting chip. Sound will go off, sorry folks :-|
[428959.665067] msp3400 1-0040: chip reset failed
[432973.212847] msp3400 1-0040: I/O error #0 (read 0x10/0x200)
[432973.226222] msp3400 1-0040: I/O error #1 (read 0x10/0x200)
[432973.242172] msp3400 1-0040: I/O error #2 (read 0x10/0x200)
[432973.256793] msp3400 1-0040: giving up, resetting chip. Sound will go off, sorry folks :-|
[432973.260486] msp3400 1-0040: chip reset failed


```

I can usually get sound back in MythTV by stop watching live tv and then going back to live tv. Or I can also rmmod msp3400 and then modprobe msp3400 again and it works. 

My tuner card is an Adaptec AVC-2410 and it is very similar to the Hauppauge PVR-150.

Here is the ivtv info:
```

[   18.518823] ivtv:  ==================== START INIT IVTV ====================
[   18.518828] ivtv:  version 0.10.1 (tagged release) loading
[   18.518831] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   18.518833] ivtv:  In case of problems please include the debug info between
[   18.518835] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   18.518838] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   18.518965] ivtv0: Autodetected Adaptec VideOh! AVC-2410 card (cx23416 based)
[   18.519235] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
[   18.577128] usbcore: registered new interface driver hiddev
[   18.620229] nvidia: module license 'NVIDIA' taints kernel.
[   18.911235] input: Chicony USB Wireless HID Receiver as /class/input/input2
[   18.911287] input: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:10.1-1
[   18.957977] parport: PnPBIOS parport detected.
[   18.958070] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.025934] input: Chicony USB Wireless HID Receiver as /class/input/input3
[   19.026034] input,hiddev96: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:10.1-1
[   19.050898] input: Chicony USB Wireless HID Receiver as /class/input/input4
[   19.051032] input: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:10.1-1
[   19.051065] usbcore: registered new interface driver usbhid
[   19.051070] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   19.051074] usbcore: registered new interface driver xpad
[   19.051084] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   19.350900] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   19.574773] ivtv0: Encoder revision: 0x02050032
[   19.574779] ivtv0: Recommended firmware version is 0x02060039.
[   19.611223] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   19.611270] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   19.616122] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   19.616126] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   19.629869] tuner 1-006b: chip found @ 0xd6 (ivtv i2c driver #0)
[   19.756163] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   19.975603] msp3400 1-0040: MSP3425G-B8 found @ 0x80 (ivtv i2c driver #0)
[   19.975608] msp3400 1-0040: MSP3425G-B8 supports radio, mode is autodetect and autoselect
[   20.003912] cs53l32a 1-0011: chip found @ 0x22 (ivtv i2c driver #0)
[   20.025918] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.026209] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.026492] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.026613] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.026907] tuner 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   20.387450] ivtv0: Initialized Adaptec VideOh! AVC-2410, card #0
[   20.387607] ivtv:  ====================  END INIT IVTV  ====================


```

Any help or anyone experiencing similar issues? It is very annoying because my recordings mess up due to the fact that sound goes out and MythTV doesn't know it.

---

### Post by jaymode on 2007-05-03
Bump for any ideas or suggestions.

---

