---
title: "Nova-T 500 Tuning Problems"
date: 2008-04-07
forum: Mythbuntu
---

### Post by Freddie on 2008-04-07
Hi,

Well today I finally tried to set-up my Nova-T 500 under Mythbuntu 8.04. I had read about disconnects, but read that they had mostly been fixed and so long as I did not use the EIT I would be fine. I do not use the remote (my PVR-150 has one).

So I first tried to add the two tuners as new capture cards, it seemed to work. Then I tried to tune them, however, there was a 5-10 minute wait before I saw the scanning window and then an strace of the process showed:
```

read(3, 0x813c72c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1207574729, 384382}, NULL) = 0
select(6, [3 4 5], [], [], {0, 11464})  = 0 (Timeout)
gettimeofday({1207574729, 396144}, NULL) = 0
gettimeofday({1207574729, 396266}, NULL) = 0
read(3, 0x813c72c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1207574729, 396461}, NULL) = 0
select(6, [3 4 5], [], [], {0, 13385})  = 0 (Timeout)
gettimeofday({1207574729, 412104}, NULL) = 0
gettimeofday({1207574729, 412177}, NULL) = 0
read(3, 0x813c72c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1207574729, 412374}, NULL) = 0
select(6, [3 4 5], [], [], {0, 11472})  = 0 (Timeout)
gettimeofday({1207574729, 424098}, NULL) = 0
gettimeofday({1207574729, 424164}, NULL) = 0

```
It took it well over 30 minutes to get to 30%.

At this point I killed the process. Can anyone give me any advice on getting this tuner working.

The boot-up messages are:
```

[   50.060735] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   50.345364] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   51.181276] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   51.814345] dvb-usb: schedule remote query interval to 150 msecs.
[   51.814359] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   51.814572] usbcore: registered new interface driver dvb_usb_dib0700
[  221.380085] dvb-usb: error while querying for an remote control event.
[  226.527616] dvb-usb: error while querying for an remote control event.
[  231.675141] dvb-usb: error while querying for an remote control event.

```

Regards, Freddie.

---

