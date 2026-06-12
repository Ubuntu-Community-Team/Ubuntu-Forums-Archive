---
title: "usb dvb-t and Kaffeine"
date: 2010-08-05
forum: Multimedia Software
---

### Post by 10.04newbie on 2010-08-05
I have managed to get my Freecom tv dongle to function in Kaffeine but only to a limited degree. The firmware (wt-220U) is installed and recognized and I was able to scan based on the relevant UK transmitter but strangely, the scan could not find any BBC channels.

The output from the latest dmesg | tail command is as follows :-

 19.921532] dvb-usb: schedule remote query interval to 300 msecs.
[   19.921541] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[   20.261091] usb 3-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   20.500234] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   20.500260] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   20.500328] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   22.220128] dvb-usb: recv bulk message failed: -110
[   29.236065] eth0: no IPv6 routers present
[   40.736103] end_request: I/O error, dev fd0, sector 0
[   40.776102] end_request: I/O error, dev fd0, sector 0


Can anyone suggest why only a limited number of channels can be found ? I hate to mention Windows but using Windows 2000 this problem does not occur.

---

