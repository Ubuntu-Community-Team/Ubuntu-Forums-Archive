---
title: "DVB-T Toshiba PX1211E-1TVD on gutsy"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by iakko86 on 2007-11-16
Hello everybody, this is my first post...i'm an ubuntu newbie, just installed gutsy, and i love it! :D
But now i'm trying to make everything that works under windows run on gutsy...and here's the first problem: my usb 2.0 toshiba dvb-t just won't work! :(
I connected it to my laptop (a toshiba satellite m50-106) but, typing dmesg, i get the following:
```
[ 2626.700000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[ 2626.832000] usb 5-4: configuration #1 chosen from 1 choice
[ 2628.084000] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in cold state, will try to load a firmware
[ 2628.192000] dvb-usb: downloading firmware from file 'dvb-usb-dibusb-6.0.0.8.fw'
[ 2628.244000] usbcore: registered new interface driver dvb_usb_dibusb_mc
[ 2628.248000] usb 5-4: USB disconnect, address 3
[ 2628.248000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[ 2630.004000] usb 5-4: new high speed USB device using ehci_hcd and address 4
[ 2630.144000] usb 5-4: configuration #1 chosen from 1 choice
[ 2630.144000] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in warm state.
[ 2630.144000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2630.148000] DVB: registering new adapter (LITE-ON USB2.0 DVB-T Tuner).
[ 2630.148000] dvb-usb: no frontend was attached by 'LITE-ON USB2.0 DVB-T Tuner'
[ 2630.148000] input: IR-receiver inside an USB DVB receiver as /class/input/input8
[ 2630.148000] dvb-usb: schedule remote query interval to 150 msecs.
[ 2630.148000] dvb-usb: LITE-ON USB2.0 DVB-T Tuner successfully initialized and connected.

```
I'm a noob, but i can get something is wrong by the line ```
[ 2630.148000] dvb-usb: no frontend was attached by 'LITE-ON USB2.0 DVB-T Tuner'
```.
In fact, if i type from terminal, after having created a frequency list, ```
scan <frequency_file.txt>[CODE] i get the following error:
[CODE]
scanning <frequency_file.txt>
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```.
Please everybody help me!! I've been looking for help on google, but i can't find anything that helps me! :(
Thanks a lot!
Byebye! :D

---

### Post by iakko86 on 2007-11-17
Nobody? (

---

