---
title: "mythtv no video"
date: 2009-07-24
forum: Multimedia Software
---

### Post by tony.morse on 2009-07-24
Hi I've just broken my mythtv install :-(

I have a nova t-500 duel card, and I had only set up one tunner but things worked.  When I set up the second tuner it seems to work but on watching tv I get a blank screen and then it returns to the menu.

I've tried to uninstall and re-install but all my settings are still there and I still have no tv.

Help please, what should I do, how do I uninstall and start again? or should I try something else first?

---

### Post by tony.morse on 2009-07-25
dmesg | grep -i dvb
[   12.111998] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   12.112032] usb 1-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   12.173476] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   13.052050] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   13.052281] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.052882] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   13.164471] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   13.703029] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.703554] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   13.710432] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   14.273183] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0c.2/usb1/1-1/input/input6
[   14.277489] dvb-usb: schedule remote query interval to 50 msecs.
[   14.277500] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   14.277815] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by tony.morse on 2009-07-26
ok, so now I've installed mythbuntu rather than ubuntu and myth.  This has fixed these problems and I'd reccomend that to others.

Now though from watching TV escape exits back to the desktop rather than back to the mythtv menu???

Also no remote... there are threds on this so I'll report back if I fix it.

---

