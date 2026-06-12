---
title: "Hauppauge HVR-1700 Troubles"
date: 2010-11-16
forum: Multimedia Software
---

### Post by Blues- on 2010-11-16
Hey all!

I just bought myself a HVR-1700 PCI-ex DVB-t card.
First I plugged the card into my desktop machine running ubuntu 10.10 32 bit.  I followed the instructions from [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1700](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1700) and everything worked out great, it works as it should and I'm able to watch all the channels found in the scan.

How ever the purpose I bought this card was to stream TV to my internal network from my server.  So In good believe I moved the card from my desktop to my server which is running ubuntu server 10.04 LTS (2.6.32-25-server) 64 bit.  I installed the card just as I had done on my desktop machine.  The card is identified, firmware loads and the /dev/dvb/* entries are created, all looking normal.  However I'm not able to scan any channels, which worked like a charm on the desktop machine.

using scan just gives me the output ..
```
 tune to: 818000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
```

I've also tried to use the existing channels.conf which was created on the desktop machine with tzap, same results, No Channel lock is acquired.

So, the card is unusable on my server, does anyone have any idea what might be wrong ?
According to linuxtv.org the card should work out of the box with Kernel 2.6.28 ...
Could this be a 64 bit issue ?  I'm out of ideas and I've tried everything to get a signal lock.

Any help would be very appreciated,

Cheers,
Konni.

---

### Post by Blues- on 2010-11-19
Again .. anyone that might have a clue ?
Could it be that I would need to update the kernel on my server machine to get this working ?
Is there any way of upgrading the kernel to 2.6.35 with upgrading to 10.10 ?

---

