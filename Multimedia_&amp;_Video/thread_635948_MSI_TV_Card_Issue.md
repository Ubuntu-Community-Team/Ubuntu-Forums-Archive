---
title: "MSI TV Card Issue"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by dontpannic on 2007-12-09
Hello there,

I've got an MSI Mega Sky 580 USB stick. Works fine in Windows, picks up all the channels fine. I have got Ubuntu Gutsy seeing it:

dmesg output:
> [ 3166.288000] usb 2-8: new high speed USB device using ehci_hcd and address 7
[ 3166.484000] usb 2-8: configuration #1 chosen from 1 choice
[ 3166.504000] input: PC-DTV Receiver PC-DTV Receiver as /class/input/input9
[ 3166.504000] input: USB HID v1.01 Keyboard [PC-DTV Receiver PC-DTV Receiver] on usb-0000:00:02.1-8
[ 3166.576000] dvb-usb: found a 'MSI Mega Sky 55801 DVB-T USB2.0' in warm state.
[ 3166.576000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 3166.580000] DVB: registering new adapter (MSI Mega Sky 55801 DVB-T USB2.0)
[ 3166.608000] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[ 3166.628000] Quantek QT1010 successfully identified.
[ 3166.628000] dvb-usb: MSI Mega Sky 55801 DVB-T USB2.0 successfully initialized and connected.
[ 3166.632000] usbcore: registered new interface driver dvb_usb_gl861

Thats all fine, but MythTV nor Kaffeine can find channels? I get 60% Signal Strength most of the time, it locks onto one particular mux I presume, but doesn't find any channels. In Windows, it has the same setup, same aerial, and picks up all the channels fine.

Any ideas as to what I can do now?

Thanks,

Nick

---

### Post by dontpannic on 2007-12-10
no-one ?

---

