---
title: "DVB-T USB Stopped working, Help!"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by DMBryant on 2007-02-05
I recently purchased a DVB-T USB device (a Kworld DVB-T 300U) and it worked fine with my Ubuntu 6.10 system (I first had to get a copy of the right firmware file) using Kaffeine.  It found all the channels and everything.  Two days later I plugged it back in and Kaffeine wont recognise it at all!

dmesg gives the following:

```
[17289667.668000] usb 5-6: new high speed USB device using ehci_hcd and address 11
[17289667.800000] usb 5-6: configuration #1 chosen from 1 choice
[17289667.800000] dvb-usb: found a 'KWorld Xpert DVB-T USB2.0' in cold state, will try to load a firmware
[17289667.844000] dvb-usb: downloading firmware from file 'dvb-usb-adstech-usb2-02.fw'
[17289667.932000] usb 5-6: USB disconnect, address 11
[17289667.932000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[17289669.684000] usb 5-6: new high speed USB device using ehci_hcd and address 12
[17289669.816000] usb 5-6: configuration #1 chosen from 1 choice
[17289669.816000] dvb-usb: found a 'KWorld/ADSTech Instant DVB-T USB2.0' in warm state.
[17289669.816000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17289669.816000] DVB: registering new adapter (KWorld/ADSTech Instant DVB-T USB2.0).
**[17289669.816000] dvb-usb: no frontend was attached by 'KWorld/ADSTech Instant DVB-T USB2.0'**
[17289669.816000] input: IR-receiver inside an USB DVB receiver as /class/input/input6
[17289669.816000] dvb-usb: schedule remote query interval to 150 msecs.
[17289669.816000] dvb-usb: KWorld/ADSTech Instant DVB-T USB2.0 successfully initialized and connected.
```

I think the problem is that, for some reason, it's decided to stop attaching a frontend to the DVB device.  I've searched everywhere but cannot find any information as to why it would suddenly stop being recognised. I don't think I did any major updates or anything, the only thing I did do was install MythTV which couldn't recognise any channels (Kaffeine still worked then as well).

Help!

---

### Post by DMBryant on 2007-02-07
Quick update...

I've read everything I can on this and even gone so far as installing the drivers from LinuxTV (even though the 2.6 kernels aren't supposed to need them) and no matter what I do, I always get the same message in dmesg (see post above).

Someone must know what could have changed for it to stop attaching a frontend?  It worked perfectly for a couple of days, got it recording and everything and then just stopped.

Cheers for any help.

---

### Post by Erlander on 2007-02-07
Sorry, my Ubuntu pc has had a hardware failure and until I find what is wrong I can't look at my dmesg for a Dvico USB.

However your dmesg looks ok to me except for that one line.  I've never seen anything like that.

Have you tried Google.  Put the whole line in in quotes.  It's a long shot but you never know.

Rob

---

### Post by DMBryant on 2007-02-07
Cheers for the effort.

I've tried google and it returns this post :) and links to changelogs for patches.  I don't know too much about patches (relatively new to this linux stuff) but it seems that they are for older kernels and i assume they would be in the 2.6.17 kernel already (or at least in the drivers I downloaded and installed from LinuxTV).

Besides, having it working for a couple of days makes me think that the support is included in my install but it's just not working properly any more...

---

### Post by Erlander on 2007-02-07
My Ubuntu pc is up and running again.

Here is the relevant part of my dmesg:

[17179588.308000] dvb-usb: found a 'DViCO FusionHDTV DVB-T USB (TH7579)' in warm state.
[17179588.308000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17179588.312000] DVB: registering new adapter (DViCO FusionHDTV DVB-T USB (TH7579)).
[17179588.312000] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[17179588.312000] input: IR-receiver inside an USB DVB receiver as /class/input/input2
[17179588.312000] dvb-usb: schedule remote query interval to 100 msecs.
[17179588.312000] dvb-usb: DViCO FusionHDTV DVB-T USB (TH7579) successfully initialized and connected.

The bit about the frontend: "Zarlink MT352 DVB-T" is one of the drivers that have to be there.  Nowadays it is part of the linux core but wasn't in earlier releases.

You may have lost one of your drivers.

Worth looking at the LinuxTV Wiki to see what you should have and maybe re-installing them. 

Rob

---

### Post by DMBryant on 2007-02-09
Thanks for your help.  I've installed the LinuxTV driver package but still no go.  I've asked the same question on the LinuxTV mailing list so hopefully someone there will be able to help.

Thanks again.

---

