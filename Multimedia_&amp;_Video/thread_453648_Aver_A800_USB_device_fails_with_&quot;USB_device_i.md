---
title: "Aver A800 USB device fails with &quot;USB device isn't matched the configuration&quot; error"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by NickD-NLUG on 2007-05-24
Hi,

When I plug in my shiny new "AVerMedia AverTV DVB-T USB 2.0 (A800)" I get the following error:

localhost kernel: [18386328.216000] dvb-usb: found a 'AVerMedia AverTV DVB-T USB 2.0 (A800)' in cold state, will try to load a firmware
localhost kernel: [18386328.328000] dvb-usb: downloading firmware from file 'dvb-usb-avertv-a800-02.fw'

Which all looks fine, but then I get....

localhost usbmgr[4251]: vendor:0x7ca product:0xa800
localhost usbmgr[4251]: class:0xff subclass:0x0 protocol:0x0
localhost usbmgr[4251]: USB device isn't matched the configuration

Any ideas on how to fix this?  I'm currently delving into udev config files.

---

