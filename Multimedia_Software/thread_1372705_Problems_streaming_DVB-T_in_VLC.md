---
title: "Problems streaming DVB-T in VLC"
date: 2010-01-04
forum: Multimedia Software
---

### Post by bgrade on 2010-01-04
Hi,

  I have also posted this on the VLC forums [http://forum.videolan.org/viewtopic.php?f=13&t=70114](http://forum.videolan.org/viewtopic.php?f=13&t=70114).

  I am having problems playing DVB with VLC. Kaffeine seems to play the tv correctly. But i can not get VLC to play or stream the content. 

uname - a
Linux meg 2.6.31-16-server #53-Ubuntu SMP Tue Dec 8 05:08:02 UTC 2009 x86_64 GNU/Linux

channels.conf 
Nine HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_N
ONE:513:0:1112

tzap seems to lock onto the signal correctly.

tom@meg:~$ tzap "Nine HD"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
reading channels from file '/home/tom/.tzap/channels.conf'
tuning to 191625000 Hz
video pid 0x0201, audio pid 0x0000
status 07 | signal 6724 | snr 0000 | ber 001fffff | unc 00000000 | 
status 1f | signal 6263 | snr 0000 | ber 00001640 | unc 00000024 | FE_HAS_LOCK
status 1f | signal 629c | snr 0000 | ber 00001940 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 62a6 | snr 0000 | ber 00001ed0 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 62ae | snr 0000 | ber 00001c70 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 629a | snr 0000 | ber 00001860 | unc 00000000 | FE_HAS_LOCK
^C

but VLC will keep repeating 

[0x8da008] dvb access debug: frontend has acquired signal
[0x8da008] dvb access warning: no lock, tuning again
[0x8da008] dvb access debug: using inversion=2
[0x8da008] dvb access debug: using bandwidth=7
[0x8da008] dvb access debug: using fec=4
[0x8da008] dvb access debug: using fec=0
[0x8da008] dvb access debug: using transmission=8
[0x8da008] dvb access debug: using guard=16
[0x8da008] dvb access debug: using hierarchy=-1
[0x8da008] dvb access debug: frontend has acquired signal

after the command

vlc-wrapper -vvv --ts-es-id-pid --color --program=512 dvb:// :dvb-budget-mode=1 :dvb-code-rate-hp=3 :dvb-code-rate-lp=3 :dvb-qam=64 :dvb-guard=16 :dvb-hierarchy=-1 :dvb-transmission=8 :dvb-frequency=191625000 :dvb-bandwidth=7 --sout '#transcode{scale=1,fps=29.97,width=320,height=240,vcodec=WMV1,acodec=mp3,vb=512,ab=128,channels=1}:std{access=http,mux=asf,dst=0.0.0.0:8090}' --ttl 12

has anyone else seen this problem?

---

