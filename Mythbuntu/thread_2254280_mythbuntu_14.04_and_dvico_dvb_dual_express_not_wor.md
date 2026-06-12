---
title: "mythbuntu 14.04 and dvico dvb dual express not working. junk it or keep trying?"
date: 2014-11-26
forum: Mythbuntu
---

### Post by andrew174 on 2014-11-26
hi folks,
just decided to dig out some assorted parts and make a HTPC, using my old
DVico DVB-T dual express. 
Unfortunately the process hasn't been as easy as the advertising. sigh.
Far as I can tell the dvico is being detected and installed at boot.
Below is a DMESG | LESS that suggests this to me.

[   11.052202] rc0: i2c IR (FusionHDTV) as /devices/virtual/rc/rc0
[   11.052204] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-6/6-006b/ir0 [cx2
3885[0]]
[   11.053268] cx23885_dvb_register() allocating 1 frontend(s)
[   11.053270] cx23885[0]: cx23885 based dvb card
[   11.065982] xc2028 6-0061: creating new instance
[   11.065985] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
[   11.065992] DVB: registering new adapter (cx23885[0])
[   11.065996] cx23885 0000:02:00.0: DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   11.066444] cx23885_dvb_register() allocating 1 frontend(s)
[   11.066447] cx23885[0]: cx23885 based dvb card
[   11.066925] xc2028 7-0061: creating new instance
[   11.066927] xc2028 7-0061: type set to XCeive xc2028/xc3028 tuner
[   11.066930] DVB: registering new adapter (cx23885[0])
[   11.066933] cx23885 0000:02:00.0: DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   11.067428] cx23885_dev_checkrevision() Hardware revision = 0xa5
[   11.067434] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfea00000
[   11.365742] hidraw: raw HID events driver (C) Jiri Kosina
[   11.382326] usbcore: registered new interface driver usbhid
[   11.382329] usbhid: USB HID core driver
[   11.385178] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input9
[   11.386701] hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2/input0
[   11.479890] xc2028 6-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   11.479946] xc2028 7-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7

But MythTv still will not detect the tuner. Correction, I go into the MythTv desktop and select watch tv and it comes back with 
no installed/configured tuner. 
I am aware of the Chris Pascoe drivers but they seem to have vanished, maybe Chris moved on. Even
then the info I've found is inconsistent as to whether or not I need Chris's drivers. But since I can't find them
I can't test them, can I?
Oh, and now the v4l-dvb drivers from linuxtv will now longer install. Make install fails on the making of **/firmware dir,
even though it is on a vanilla system. Weird.

Would it be easier to throw the Dvico in a microwave and buy a Hauppauge TVR-1??? series tuner.
Or can someone start pointing me in the right direction?

Many thanks in advance,
Andrew.
ps. I'm not a newbie, just an oldie who has forgotten everthing.

---

### Post by dannyboy79 on 2014-11-26
see if this helps at all [http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices).

---

