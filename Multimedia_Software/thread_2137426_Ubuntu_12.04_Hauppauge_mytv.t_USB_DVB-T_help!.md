---
title: "Ubuntu 12.04 Hauppauge mytv.t USB DVB-T help!"
date: 2013-04-20
forum: Multimedia Software
---

### Post by razza30 on 2013-04-20
I'm new to the world of Ubuntu and I am struggling getting my Hauppauge MyTV.t to play nicely with a scan (/usr/bin/scan or Kaffeine).

The USB device seems to be recognised correctly, as "[COLOR=#0000ff]dmesg | grep -i dvb[/COLOR]" gives:
[COLOR=#0000ff][    8.004875] dvb-usb: found a 'Hauppauge Nova-T MyTV.t' in warm state.
[    8.005476] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.006138] DVB: registering new adapter (Hauppauge Nova-T MyTV.t)
[    8.220465] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    8.612392] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/rc/rc0/input4
[    8.614463] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/rc/rc0
[    8.614606] dvb-usb: schedule remote query interval to 50 msecs.
[    8.614614] dvb-usb: Hauppauge Nova-T MyTV.t successfully initialized and connected.
[    8.614760] usbcore: registered new interface driver dvb_usb_dib0700[/COLOR]

Also the structure under "[COLOR=#0000ff]/dev/dvb/adapter0[/COLOR]" appears correct: [COLOR=#0000ff]demux0  dvr0  frontend0  net0[/COLOR]

"[COLOR=#0000ff]dvb-usb-dib0700-1.20.fw[/COLOR]" is present in "[COLOR=#0000ff]/lib/firmware[/COLOR]".

I have tried adding "[COLOR=#0000cd]options dvb_usb_dib0700 force_lna_activation=1[/COLOR]" to the following files:
[COLOR=#0000cd]/etc/modprobe.d/options
/etc/modprobe.d/dvb-usb-dib0700
/etc/modprobe.d/dvb_usb_dib0700[/COLOR]

Kaffeine recognises the device and allows me to configure but finds nothing on a scan.

Help! :)

---

### Post by razza30 on 2013-04-23
No one?

---

### Post by razza30 on 2013-04-27
Any advice where else I could ask?

---

### Post by EcosseB@ntu on 2013-08-14
Hi there,
Were you able to make any progress with this?  Ready to pull my hair out - followed all the correct procedures and still getting failure to load any channels.  Bought and installed a new aerial - getting 57%-77%  signal strength with Kaffeine but absolutely no joy in getting any channels.  Any help would be greatly appreciated!

Cheers,

---

