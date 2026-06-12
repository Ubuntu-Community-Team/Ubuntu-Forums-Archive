---
title: "USB-DVB Firmware / Initialisation Problem"
date: 2010-05-02
forum: Multimedia Software
---

### Post by redger on 2010-05-02
I have 2 USB DVB tuners, a LifeView TV Walker and a KWorld DVB-T PC160-2T.

I have tried using them both on Ubuntu Karmic and Lucid, AMD64 in each case. In each case I've installed linux-firmware-nonfree and the appropriate firmware files have been found and installed (dvb-usb-tvwalkert.fw and dvb-usb-af9015.fw)

The hardware is found, the firmware is loaded eg. (from dmesg|grep dvb)
> [INDENT][10064.817301] dvb-usb: found a 'LifeView TV Walker Twin DVB-T USB2.0' in cold state, will try to load a firmware
[10064.817304] usb 2-1: firmware: requesting dvb-usb-tvwalkert.fw
[10064.830175] dvb-usb: downloading firmware from file 'dvb-usb-tvwalkert.fw'
[10066.340458] dvb-usb: found a 'LifeView TV Walker Twin DVB-T USB2.0' in warm state.
[10066.340495] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[10066.345359] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[10066.350220] dvb-usb: schedule remote query interval to 100 msecs.
[10066.350224] dvb-usb: LifeView TV Walker Twin DVB-T USB2.0 successfully initialized and connected.[/INDENT]

I can then see the tuners in /dev/dvb and Kaffeine can find them and run a channel scan successfully.

BUT

Kaffeine cannot lock onto a channel (returns "could not open media source" error)
dvbscan cannot open them either, as either a regular user or root ... it just sits and waits for ever
Mythtv will recognise the cards, but won't scan or lock on to a channel, though the signal strength is about 70%

I've tried this on 2 different machines with 3 different cards (I also have a Dvico Dual which includes a PCI and a USB tuner on a single PCI card) It seems that all the DVB cards which require firmware will not work.
Note that the PCI tuner on the Dvico Dual works fine, even tho the USB device on the same card doesn't. Furthermore a separate Dvico single PCI card works fine.

I check to see if USB-HID had acquired the card, but is seems not to have eg. (from dmesg|grep hid)
[INDENT]> [    3.867989] usbcore: registered new interface driver hiddev
[   13.867543] /build/buildd/linux-2.6.31/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   13.869015] generic-usb 0003:1DD2:1009.0001: input,hidraw0: USB HID v1.10 Joystick [Leo Bodnar Logitech® G25 Pedals] on usb-0000:00:1a.0-1/input0
[   13.872354] generic-usb 0003:04B3:3109.0003: input,hidraw1: USB HID v1.00 Mouse [HID 04b3:3109] on usb-0000:00:1d.7-4.2/input0
[   13.911028] generic-usb 0003:04B3:3018.0004: input,hidraw2: USB HID v1.10 Keyboard [Lite-On Tech IBM USB Keyboard with UltraNav] on usb-0000:00:1d.7-4.4.3/input0
[   13.959963] generic-usb 0003:04B3:3018.0005: input,hidraw3: USB HID v1.10 Device [Lite-On Tech IBM USB Keyboard with UltraNav] on usb-0000:00:1d.7-4.4.3/input1
[   14.013452] generic-usb 0003:06CB:0009.0006: input,hidraw4: USB HID v1.00 Mouse [Synaptics Inc. Composite TouchPad / TrackPoint] on usb-0000:00:1d.7-4.4.4/input0
[   14.075557] generic-usb 0003:06CB:0009.0007: input,hidraw5: USB HID v1.00 Mouse [Synaptics Inc. Composite TouchPad / TrackPoint] on usb-0000:00:1d.7-4.4.4/input1
[   14.108610] usbcore: registered new interface driver usbhid
[   14.125564] usbhid: v2.6:USB HID core driver
[   14.250133] logitech 0003:046D:C294.0002: input,hidraw6: USB HID v1.00 Joystick [G25 Racing Wheel] on usb-0000:00:1d.1-1/input0[/INDENT]

I've also checked the loaded modules, which look ok (lsmod)
 ```
[INDENT]lsmod |grep m920
dvb_usb_m920x          24452  0 
dvb_usb                19276  1 dvb_usb_m920x
[/INDENT]
```


PS in both cases the motherboards have working USB2 ports, which is what I'm using (one is an ASUS A8N-E the other an ASUS P6T). Other USB devices work fine and the cards are fine
It's not clear whether the problem relates to USB or firmware or the combination, but it seems quire consistent

I would much appreciate any advice [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

