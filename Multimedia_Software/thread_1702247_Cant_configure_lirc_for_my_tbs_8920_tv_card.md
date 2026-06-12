---
title: "Cant configure lirc for my tbs 8920 tv card"
date: 2011-03-07
forum: Multimedia Software
---

### Post by zannyuk on 2011-03-07
Hi,

Im at a loss and need someone more knowledgeable than me to help.

All my hardware configured properly (i think) and live tv is working :) but my remote isnt.  The manufacturer of the tv card does provide ubuntu compatible drivers and ive been trying to get support from their official forum without success for a few days now, seem they dont care about their users :(

Posting over there as PeterP.   [http://www.buydvb.net/forum/viewtopic.php?f=12&t=61](http://www.buydvb.net/forum/viewtopic.php?f=12&t=61)  As you can see from my grep I do see something about IR but try as I might i dont even know where to start really.  Getting the remote working would make my wife happy and stop nagging me about not buying a settop box to go with the new satellite dish we got installed.

Anyway my "dmesg | grep cx88" returns as.....

[   12.586327] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   12.586726] cx8800 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   12.588059] cx88[0]: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72,autodetected], frontend(s): 1
[   12.588061] cx88[0]: TV tuner type 4, Radio tuner type -1
[   12.601121] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   13.160088] input: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/rc/rc0/input5
[   13.160141] rc0: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/rc/rc0
[   13.160147] cx88[0]/0: found at 0000:01:09.0, rev: 5, irq: 17, latency: 64, mmio: 0xf9000000
[   13.160201] cx88[0]/0: registered device video0 [v4l2]
[   13.160222] cx88[0]/0: registered device vbi0
[   13.160329] cx88[0]/2: cx2388x 8802 Driver Manager
[   13.160345] cx88-mpeg driver manager 0000:01:09.2: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   13.160351] cx88[0]/2: found at 0000:01:09.2, rev: 5, irq: 17, latency: 64, mmio: 0xf8000000
[   13.199501] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   13.199504] cx88/2: registering cx8802 driver, type: dvb access: shared
[   13.199507] cx88[0]/2: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72]
[   13.199510] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.199511] cx8802_alloc_frontends() allocating 1 frontend(s)
[   13.262872] DVB: registering new adapter (cx88[0])


Please if your out there and can help, help meeeeee pleeeaassseeee :)


If i can get lirc to see the device then irrecord would work and id be happy :)

---

