---
title: "Does Hauppauge Nova-S (model 790) work in mythbuntu?"
date: 2008-01-25
forum: Mythbuntu
---

### Post by Sergiy on 2008-01-25
Hello.

I am using Ubuntu 7.10 + mythbuntu.
It seems that my DVB card has driver problem under Ubuntu and can't work with mythbuntu.

dmesg | grep -i cx
[ 28.922630] cx2388x v4l2 driver version 0.0.6 loaded
[ 28.922962] CORE cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37,autodetected]
[ 28.931548] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 29.076031] tveeprom 2-0050: tuner model is Conexant_CX24109 (idx 111, type 4)
[ 29.076036] tveeprom 2-0050: audio processor is CX883 (idx 32)
[ 29.076038] tveeprom 2-0050: decoder processor is CX883 (idx 22)
[ 29.076042] cx88[0]: hauppauge eeprom: model=92001
[ 29.076140] input: cx88 IR (Hauppauge Nova-S-Plus as /class/input/input5
[ 29.076172] cx88[0]/0: found at 0000:02:08.0, rev: 5, irq: 20, latency: 64, mmio: 0xfa000000
[ 29.076208] cx88[0]/0: registered device video0 [v4l2]
[ 29.076228] cx88[0]/0: registered device vbi0
[ 29.076334] cx88[0]/2: cx2388x 8802 Driver Manager
[ 29.076357] cx88[0]/2: found at 0000:02:08.2, rev: 5, irq: 20, latency: 64, mmio: 0xfc000000
[ 29.201217] cx2388x dvb driver version 0.0.6 loaded
[ 29.201221] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 29.201225] CORE cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[ 29.201228] cx88[0]/2: cx2388x based dvb card
[ 29.282200] DVB: registering new adapter (cx88[0]).
[ 29.282205] DVB: registering frontend 0 (Conexant CX24123/CX24109)...
[ 29.300792] cx2388x alsa driver version 0.0.6 loaded
[ 29.300859] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards


So it seems that all default driver has been loaded without problem.

I pointed my dish on DN satelite 119 (it has FTA channels Nasa TV)
I know that transporter frequency is 12370000 and LOF 11250000
So I tried to lock signal by using:

dvbtune -f 1120000 -s 20000 -p v -m
Using DVB card "Conexant CX24123/CX24109"
tuning DVB-S to L-Band:0, Pol:V Srate=20000000, 22kHz=off
ERROR setting tone
: Invalid argument
polling....
Getting frontend event
Overflow error, trying again (status = -1, errno = 75)FE_STATUS:
polling....
Getting frontend event
FE_STATUS:
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_LOCK FE_HAS_CARRIER FE_HAS_VITERBI FE_HAS_SYNC
Bit error rate: 0
Signal strength: 63488
SNR: 62297
FE_STATUS: FE_HAS_SIGNAL FE_HAS_LOCK FE_HAS_CARRIER FE_HAS_VITERBI FE_HAS_SYNC
frontend: 8FRONTEND DEVICE: : Device or resource busy

It says device busy... but as far as I know no one is holding it at this moment (I killed all mythtv processes before starting this command)

Next I tried scan

scan -c -U
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
dumping lists (19 services)
[000-0068] (0x006 00: PCR == V V 0x1d22 A 0x1d23 (eng)
[001-0089] (0x0089) 00: PCR == V V 0x1822 A 0x1823 (eng) 0x1824 (esl)
[002-00d2] (0x00d2) 00: PCR == V V 0x1322 A 0x1323 (eng) 0x1324 (esl)
[003-00d4] (0x00d4) 00: PCR == V V 0x1522 A 0x1523 (eng)
[004-00d5] (0x00d5) 00: PCR == V V 0x1022 A 0x1023 (eng)
[005-00d9] (0x00d9) 00: PCR == V V 0x1122 A 0x1123 (eng) 0x1124 (esl) 0x1125 (fra)
[006-00de] (0x00de) 00: PCR == V V 0x1622 A 0x1623 (eng)
[007-00e0] (0x00e0) 00: PCR == V V 0x1122 A 0x1123 (eng) 0x1124 (esl) 0x1125 (fra)
[008-00e4] (0x00e4) 00: PCR == V V 0x1922 A 0x1923 (eng)
[009-0104] (0x0104) 00: PCR == V V 0x1222 A 0x1223 (eng)
[00a-0105] (0x0105) 00: PCR == V V 0x1422 A 0x1423 (eng) 0x1424 (esl)
[00b-012b] (0x012b) 00: PCR == V V 0x1b22 A 0x1b23 (eng)
[00c-01f5] (0x01f5) 00: PCR == V V 0x1722 A 0x1723 (eng)
[00d-1687] (0x1687) 00: PCR == V V 0x1122 A 0x1123 (eng) 0x1124 (esl) 0x1125 (fra)
[00e-16cc] (0x16cc) 00: PCR == V V 0x1422 A 0x1423 (eng) 0x1424 (esl)
[00f-24c3] (0x24c3) 00: PCR == V V 0x1c22 A 0x1c23 (eng)
[010-24c4] (0x24c4) 00: PCR == V V 0x1a22 A 0x1a23 (eng)
[011-2582] (0x2582) 00: PCR == V V 0x1122 A 0x1123 (eng) 0x1124 (esl) 0x1125 (fra)
[012-4a81] (0x4a81) 00: PCR 0x1fff


The channel I needed is Nasa TV in this list #4 with number 0xd5 (dec 213)
So it seems that dvbtune failed for some reason but I can somehow receive data from scan.

Next step I want to watch Nasa TV.
I tried:
dvbstream -f 1120 -s 20000 -p v -o 4130 4131 | mplayer -

and I can watch NasaTV.

The question is how to add this channel to myth tv. What ever I did with myth doesn't give me any channel ...
First I did full scan of transporter 12370000 (LOF 11250000). It actually locked transporter but returned empty table and didn't add any channel.
After that I created channel.config with only one NasaTVchannel:
[00d5]:12370:v:0:20000:4130:4131:213
and tried to import it to myth... the same result. Myth says it locked transporter but no one channel is found.

So I simply can't find any answer to this so far.
Or driver can't work correctly with Hauppauge Nova-S (see dvbtune device is busy)
Or mythtv for some reason can't find NasaTV
Maybe I can manually insert this channel into database by hand because dvbstream is working fine with channel?

Any idea?
Thank you.

PS I inserted this dvb card into windows PC and it worked like a charm with ProgDVB...

PSS I submitted this question to "Multimedia & Video" but didn't get any answer yet so decided to submit it to mythbuntu forum as well

---

