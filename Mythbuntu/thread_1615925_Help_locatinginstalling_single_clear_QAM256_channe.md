---
title: "Help locating/installing single clear QAM256 channel using 'scan' utility"
date: 2010-11-07
forum: Mythbuntu
---

### Post by stratoscape on 2010-11-07
I spent the weekend converting my mythtv video source from ASTC/Antenna to Clear QAM over Cox cable connection. Successfully scanned in all the available channels except FOX.

I know where it is suppose to be as just I set up my friends just the other day and it was there, the channel is 69-25 which is channel 712 from my provider. I have rescanned all of the current transports several times and cannot find it.

My thoughts are it was one found in a previous scan and my be cached somewhere? I am trying to figure out how to use the scan utility to find it but this to is a challenge. I run it with -c and all I get is (below)

```
strato@godzuki:/usr/share/dvb/atsc$ scan -c
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x1ffb
dumping lists (4 services)
[0004]                   (0x0004) 00: PCR == V   V 0x03e9 A 0x03ea (eng)
[0005]                   (0x0005) 00: PCR == V   V 0x03fd A 0x03fe (eng)
[00de]                   (0x00de) 00: PCR == V   V 0x03f8 A 0x03f9 (eng)
[00f7]                   (0x00f7) 00: PCR == V   V 0x03f3 A 0x03f4 (eng)
Done.
strato@godzuki:/usr/share/dvb/atsc$ 

```

I have about 17 transports listed but it only show these (without tids) and I try to specify this and fails (below)

```
strato@godzuki:~$ scan us-Cable-Standard-center-frequencies-QAM256
scanning us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
strato@godzuki:~$ 

```

Just looking for a way to (A) locate/create proper transport so (B) can re-add the missing FOX channel.

thanks

---

