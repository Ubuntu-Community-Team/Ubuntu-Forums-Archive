---
title: "Compro VideoMate DVB-T300 tuning problem in MythTV"
date: 2008-07-28
forum: Multimedia Software
---

### Post by simgrant on 2008-07-28
Using this thread:
[http://ubuntuforums.org/showthread.php?t=402783&highlight=angelman99]("http://ubuntuforums.org/showthread.php?t=402783&highlight=angelman99")
I have been able to get my Tuner card working in Mythbuntu with Kaffeine but not in MythTV. If MythTV tries to scan it won't find any channels. I was able to create the channels.conf file below using dvb-utils:
```
ABC HDTV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:560
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:561
ABC2:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:562
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:563
ABC3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:564
ABC DiG Radio:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2317:566
ABC DiG Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2318:567
Nine Digital:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:519:720:1072
Nine Digital HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:0:1073
Nine Guide:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:517:700:1074
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1585
TEN Digital:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1589
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1592
SBS HD:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:784
SBS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:785
SBS NEWS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:786
SBS 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:787
SBS RADIO 1:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:798
SBS RADIO 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:799

```

But when I choose scan type "Import channels.conf" and give the file /home/mythtv/channels.conf no channels are entered. I get:

```
Timeout Scanning 0 -- no signal
Timeout Scanning 1 -- no signal
Timeout Scanning 2 -- no signal
Timeout Scanning 3 -- no signal
```

Any ideas what I might be doing wrong?

---

### Post by simgrant on 2008-08-10
Still no luck :(

---

### Post by summatix on 2008-09-11
I am having the same problem. It was hard enough trying to get MythTV to recognise the card in the first place, and now it isn&#8217;t picking up any channels. It would be greatly appreciated if anyone could help.

---

### Post by summatix on 2008-09-28
Surely someone must have a solution to this.

---

### Post by Tom58 on 2008-09-28
> **summatix said:**
> Surely someone must have a solution to this.

I have a Compro T300 and the only success I had in getting it to work with MythTV was to tune into the SBS analogue channel here in Adelaide.  If I remember correctly I copied the channel.conf file rather than getting MythTv to scan for channels.

I was never able to get it to work with digital transmissions and eventually replaced it with a Leadtek 1000 which worked (almost)straight from the box.

Unfortunately I haven't been able to find any thread where someone was able to get the card to work with MythTV.

---

### Post by res_au on 2008-09-29
I have the same problem.. let us know if anyone figures it out.

Cheers

---

### Post by Tom55 on 2008-10-18
Cleaned off the OS and reinstalled Ubuntu 8.04 64
The system recognizes the Compro T300
Tzap give me frequency locks
Installed Kaffeine and did a channel scan.  Kaffeine found one channel (SBS).  This is strange as I get my weakest reception from SBS and frequently can't get any signal.  However it's the only channel that broadcasts on UHF.  The other four digital channels are VHF

The compro finds all the analogue channels using TVTime.

I'll have to keep playing around

Tom

---

