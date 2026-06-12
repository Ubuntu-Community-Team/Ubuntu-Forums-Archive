---
title: "Error playing DVB TV : &quot;dtv error: cannot access DVR: Operation not permitted&quot;"
date: 2019-01-06
forum: Multimedia Software
---

### Post by mistervic on 2019-01-06
Hi,


I would like to see TV on my PC with this config :

- Ubuntu 18.04
- Kernel 4.15.0-43-generic
- VLC 3.0.5
- w_scan version 20170107 (compiled for DVB API 5.10)
- DVB tuner : AvrMedia AverTV Volar HD 2


My **lsusb** echo is correct : Bus 005 Device 004: ID 07ca:a110 AVerMedia Technologies, Inc.


When I run **w_scan -f t -c FR -X > channels.conf** command  I get this file :
> C8(NTN):490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:120:130:513 
BFM TV(NTN):490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:320:330:515 CNEWS(NTN):490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:420:430:516
  […]   
25(MHD7):770000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:320:330:2563 RMC Découverte(MHD7):770000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:420:430:2564 
RMC STORY(MHD7):770000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:520:530:2565

This generation file is good !


When I run **vlc -vvv ~/channels.conf**  command I get this error for etch channel in terminal  :
> main stream debug: looking for access module matching "dvb-t": 26 candidates
[00007f461c0038a0] dtv stream error: cannot access DVR: Operation not permitted 
[00007f461c0038a0] dvb stream warning: unknown option (code-rate-hp=:code-rate-lp=0:modulation=64QAM:transmission=-1:guard=1/8:hierarchy=0)

I try to chang privileg with **sudo chmod -R 777 /dev/dvb** but I have same pb.


I Think than my driver work fine beacause I run this reception test [https://www.linuxtv.org/wiki/index.php/ ... on_quality]("https://www.linuxtv.org/wiki/index.php/Testing_reception_quality")
And the result is the next : 

> Starting...
================================================================================
Tunning channel C8(NTN) (490000000)
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
Version: 5.10       FE_CAN { DVB-T }
tuning to 490000000 Hz
video pid 0x0078, audio pid 0x0082
status 00 | signal 051e | snr 0000 | ber 00000000 | unc 00000000 | 
status 1f | signal fae0 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK (Ignoring to let tuner/decoder settle.(2)
status 1f | signal fae0 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK (Ignoring to let tuner/decoder settle.(1)
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0
Signal: 97%    BER 0    UNC 0

[...]

================================================================================
Tunning channel RMC STORY(MHD7) (770000000)
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
Version: 5.10       FE_CAN { DVB-T }
tuning to 770000000 Hz
video pid 0x0208, audio pid 0x0212
status 00 | signal ee13 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1f | signal ee13 | snr bfff | ber 00000000 | unc 00000000 | FE_HAS_LOCK (Ignoring to let tuner/decoder settle.(2)
status 1f | signal ee13 | snr dfff | ber 00000000 | unc 00000000 | FE_HAS_LOCK (Ignoring to let tuner/decoder settle.(1)
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0
Signal: 92%    BER 0    UNC 0

Summary statistics:
Frequency    Signal      Ber         Unc
=========    ========    ========    ========
490000000      98.0 %         0.0         0.0
498000000      98.0 %         0.0         0.0
538000000      98.2 %         0.0         0.0
642000000     100.0 %         0.0         0.0
666000000      98.1 %         0.0         0.0
770000000      93.0 %         0.0         0.0


   
Iposted same post on videolan forum : [URL="https://forum.videolan.org/viewtopic.php?f=13&t=146177&p=484591#"]https://forum.videolan.org/viewtopic.php?f=13&t=146177&p=484591#
[/URL]
Do you think that's a driver bug or vlc bug ?
Best regard

---

