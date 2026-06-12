---
title: "Channels cannot be found using DVB-S"
date: 2011-04-11
forum: Multimedia Software
---

### Post by natomb on 2011-04-11
Hello together,


I am setting up a MythTV environment to switch from Windows based MediaPortal (with a high number of disturbing bugs). Yet, I have three difficulties, which I want to discuss with you. They are:


- No audio via HDMI (see [http://ubuntuforums.org/showthread.php?p=10663374#post10663374](http://ubuntuforums.org/showthread.php?p=10663374#post10663374))
- Video resolution seems to change during video playback (see [http://ubuntuforums.org/showthread.php?p=10663380#post10663380](http://ubuntuforums.org/showthread.php?p=10663380#post10663380))
- Channels cannot be found via DVB-S


As you can see, I have created three posts to keep discussions focused.

Alltogether I have the following setup:

- AMD 5050e CPU
- 8 GByte RAM
- Biostar TA890GXE
- Samsung LE40M86BD, connected via HDMI (and only HDMI)
- Mythbuntu 10.10 with proprietary drivers installed
- Technisat Skystar HD2 DVB-S card (two times)


Now, here is the problem:

when I try to scan for any available satellite channels to use in Myth, I cannot find any channels. I have invoked "scan -V -l UNIVERSAL -s 1 -a 0 /usr/share/dvb/dvb-s/Astra-19.2E" with the following result:

```
scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:1:22000
DiSEqC: switch pos 1, 13V, hiband (index 6)
DVB-S IF freq is 1951500
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
>>> tune to: 12551:v:1:22000 (tuning failed)
DiSEqC: switch pos 1, 13V, hiband (index 6)
DVB-S IF freq is 1951500
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
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```The mantis drivers are loaded. In the Windows based MediaPortal I can scan approx. 900 channels.

Thank you for assistance
  Bjoern

---

### Post by bance on 2011-04-11
maybe try asking in the mythbuntu forums [_[COLOR=Red]here[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=301")

---

### Post by natomb on 2011-04-25
Hello,


Natty seems to do wonders. After my upgrade to Natty, I can detect DVB-S signals (approx. 600)

---

