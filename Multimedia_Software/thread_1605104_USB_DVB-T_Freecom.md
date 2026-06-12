---
title: "USB DVB-T Freecom"
date: 2010-10-24
forum: Multimedia Software
---

### Post by susanto on 2010-10-24
I am using Ubuntu 10.04-64, Freecom USB DVB-T, and Kaffeine.
I am having many problem using this device.

I managed to make this device works for a couple of days 
(includes daily shutdown).
Somehow, now and then the device suddenly did not want to work.
Kaffeine reported that the device is not connected.
Running dmesg | grep dvb (result at the end of this message),
It seems that the device is already initialised and connected.
SOmetimes, reinstall the program and reboot the machine can solve 
the problem.

Can somebody help?
Or have anybody have the same experience and got a solution?
====
[   17.419876] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[   17.419967] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   17.421642] dvb-usb: schedule remote query interval to 300 msecs.
[   17.421644] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[   17.421658] usbcore: registered new interface driver dvb_usb_dtt200u
[   19.725583] dvb-usb: recv bulk message failed: -110
====

---

### Post by susanto on 2010-10-26
Additional note:
My problem can be solved by uninstall kaffeine, reboot and install it back. It works immediately, including previously scan channels.
I am really annoyed with this new feature.

---

### Post by susanto on 2011-03-22
Latest software update, solved the issue.

---

