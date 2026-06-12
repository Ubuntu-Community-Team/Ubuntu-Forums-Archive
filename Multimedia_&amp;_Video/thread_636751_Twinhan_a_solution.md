---
title: "Twinhan a solution?"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by passbe on 2007-12-10
With the new ubuntu released i plugged my twinhan usb2.0 tv tuner in not expecting it to work. However on the output of dmesg i get.

```

[ 1065.672000] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 1065.804000] usb 5-2: configuration #1 chosen from 1 choice
[ 1065.804000] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in cold state, will try to load a firmware
[ 1065.812000] dvb-usb: downloading firmware from file 'dvb-usb-vp7045-01.fw'
[ 1065.876000] usb 5-2: USB disconnect, address 7
[ 1065.876000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[ 1067.632000] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 1067.764000] usb 5-2: configuration #1 chosen from 1 choice
[ 1067.764000] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in warm state.
[ 1067.920000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 1067.992000] dvb-usb: MAC address: 08:ca:00:00:00:ff
[ 1068.004000] dvb-usb: schedule remote query interval to 400 msecs.
[ 1068.160000] dvb-usb: Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II) successfully initialized and connected.

```

I was stunned. it actually loaded the firmware for me. Lsmod reports that usb_core contains the correct module. However i, like many others are back to the problem of the device not being able to pick up any channels. Even after specifying a channels.conf file the device still does not work.

This is due to /dev/video0 being non-existent.  

Put simply has anyone found a solution to this problem, or can anyone suggest any appropriate actions?

Thank you.

---

### Post by uidb4056 on 2008-01-06
Have you tried to install kaffeine and configure it working with kaffeine-xine engine, then go to digital-tv and scan for channells?

---

