---
title: "Cant get DVB-S channels with kaffeine"
date: 2012-02-25
forum: Multimedia Software
---

### Post by tarekeldeeb on 2012-02-25
Hello all,

I have a home PC with a twinhan 1027 DVB-S card. I use it to watch sattelite channels, it successful with ubuntu 11.04 (can't remember if it was 32 or 64 bits OS). The kernel at this release had the correct driver, although it was (and still) seen as Fujitsu MB86A16 DVB-S. Then I turned back to windows since I found difficulties with network streaming.

Two days ago, I decided to give another try and stream with VLC, I installed ubuntu 11.10 x64 and installed all updates.

(1) The DVB-S card is still recognized, cxx88 module is used

```

$ dmesg | grep -i dvb 

[    7.096300] cx88[0]: subsystem: 1822:0023, board: Twinhan VP-1027 DVB-S [card=85,autodetected], frontend(s): 1
[    8.048186] input: cx88 IR (Twinhan VP-1027 DVB-S) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0/input4
[    8.048277] rc0: cx88 IR (Twinhan VP-1027 DVB-S) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0
[    8.399258] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[    8.399263] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.399267] cx88[0]/2: subsystem: 1822:0023, board: Twinhan VP-1027 DVB-S [card=85]
[    8.399271] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.617904] DVB: registering new adapter (cx88[0])
[    8.617909] DVB: registering adapter 0 frontend 0 (Fujitsu MB86A16 DVB-S)...
```

(2) I used to use kaffeine to scan and view DVB-S channels on NileSat. Now I continually fail to scan for channels using the GUI from Kaffeine. So I tried the simple "scan" program. The last part ending with "WARNING: >>> tuning failed!!!" is repeated till the end of the scan.

```
$ sudo scan -v /usr/share/dvb/dvb-s/Nilesat101+102-7.0W 
[sudo] password for home: 
scanning /usr/share/dvb/dvb-s/Nilesat101+102-7.0W
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 10719000 V 27500000 3
initial transponder 10723000 H 27500000 3
initial transponder 10758000 V 27500000 3
initial transponder 10775000 H 27500000 3
initial transponder 10796000 V 27500000 3
initial transponder 10892000 H 27500000 3
initial transponder 10911000 V 27500000 3
initial transponder 10930000 H 27500000 3
initial transponder 11317000 V 27500000 3
initial transponder 11747000 V 27500000 3
initial transponder 11766000 H 27500000 3
initial transponder 11785000 V 27500000 3
initial transponder 11804000 H 27500000 3
initial transponder 11823000 V 27500000 3
initial transponder 11843000 H 27500000 3
initial transponder 11862000 V 27500000 3
initial transponder 11881000 H 27500000 3
initial transponder 11900000 V 27500000 3
initial transponder 11919000 H 27500000 3
initial transponder 11938000 V 27500000 3
initial transponder 11958000 H 27500000 3
initial transponder 11977000 V 27600000 5
initial transponder 11996000 H 27500000 3
initial transponder 12015000 V 27500000 3
initial transponder 12034000 H 27500000 3
initial transponder 12054000 V 27500000 3
initial transponder 12073000 H 27500000 3
initial transponder 12130000 V 27500000 3
initial transponder 12149000 H 27500000 3
initial transponder 12207000 V 27500000 3
initial transponder 12226000 H 27500000 3
initial transponder 12284000 V 27500000 3
initial transponder 12303000 H 27500000 3
initial transponder 12341000 V 27500000 3
initial transponder 12360000 H 27500000 3
initial transponder 12380000 V 27500000 3
initial transponder 12399000 H 27500000 3
initial transponder 12418000 V 27500000 3
initial transponder 12476000 H 27500000 3
>>> tune to: 10719:v:0:27500
DiSEqC: switch pos 0, 13V, loband (index 0)
DVB-S IF freq is 969000
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 10719:v:0:27500 (tuning failed)
DiSEqC: switch pos 0, 13V, loband (index 0)
DVB-S IF freq is 969000
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!

```

(3) I had doubts about the GUI kaffeine, so I started scanning, then started the command "scan" which failed due to locked device, this seems good to me. At this try, kaffeine magically was able to scan for some channels!! The problem is that non can be displayed or read its EPG.


How can I trace the scanning and channel tuning errors?
NB: Windows XP can still scan/view channels

Thanks in advance,
Tarek

---

### Post by tarekeldeeb on 2012-02-25
I noticed something weird, when I scan with kaffeine I see the signal and quality both set to 100% which is unrealistic.
Anyway, I now see strange behaviour:

(1) instead of launching kaffeine normally, I did "sudo kaffeine" and I was finally able to scan and tune to the channels as well :)

But not so fast, about 10% of the channels only were found, and they were awfully noisy
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213252&stc=1&d=1330189441[/IMG]

(2) As a user (not sudo), I re-opened kaffeine and started a new scan. I reached the same result: little channels, and noisy.

Is there something missing? Bug on the SNR level? What did the sudo magically enable?


Jus wandering .. looking forward for a nice DVB-S experience with ubutu ..

---

### Post by tarekeldeeb on 2012-02-26
The problem still exists, to be clear, let me rephrase it:
* Not all channels are found in scan (~10% only)
* Many channels are noisy

On the other hand, windows XP can scan/view channels perfectly. 

So is this a 
- driver parameter issue?
- faulty default channels.conf ?
- Can I do a blind exhaustive scan?? some windows programs have this option.

Hope this thread finds helful readers ;)

---

