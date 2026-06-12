---
title: "MythTV- Cannot find  tuners"
date: 2008-09-06
forum: Multimedia Software
---

### Post by ysr23 on 2008-09-06
Hi, I havejust successfully installed my nova-t 500 twin tuner pci card, isay succesfully as all went as described in the very helpfull guide here:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

dmesg and lsusb (despite it being a PCI not sure i  understand that) all report happily likethey should and indeed kaffeine finds it fine and i can  watch tv on that - but i am trying to build a PVR, using MYTHtv and can't get that to find my card at all.

I am presuming that the card i want is the mpeg-2 encoder card, yet probed info reads 'failed to open' and 'video device' is blank - perhaps i should be entering something here?

many thanks in advance

---

### Post by ysr23 on 2008-09-06
$ dmesg | grep DVB
```

[   44.100283] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   44.101027] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   44.217620] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   44.811163] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   44.817974] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   45.380649] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb5/5-1/input/input7
[   45.410801] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
toast@SKYNET:/$ dmesg | grep DVB
[   44.100283] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   44.101027] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   44.217620] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   44.811163] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   44.817974] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   45.380649] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb5/5-1/input/input7
[   45.410801] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

```

---

### Post by gizmo911uk on 2009-04-02
Did you ever get this sorted, I'm in the same position as you.

---

