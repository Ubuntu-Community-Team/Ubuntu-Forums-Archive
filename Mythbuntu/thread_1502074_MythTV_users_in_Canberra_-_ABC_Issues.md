---
title: "MythTV users in Canberra - ABC Issues"
date: 2010-06-05
forum: Mythbuntu
---

### Post by BigPacks on 2010-06-05
Has anybody got a ABC Digital to work with a HVR-2200 in Canberra (Australia) from Black Mountain Tower?

I've been reading through various forums, but I'm still can't get this working on a HVR-2200 (using the drivers from [http://www.kernellabs.com/hg/saa7164-stable/](http://www.kernellabs.com/hg/saa7164-stable/)) on a PC with Mythbuntu 10.04.

My TV signal is via a 4 way amplified splitter, which should be strong enough to work. With the other splitter outputs I can get ABC with my TV (newish Samsung), my 6 year old PVR and with another PC runing Mythbuntu 10.04 (containing a DViCO FusionHDTV DVB-T Dual Digital 4 PCI with virtually no tweaks at all for the entire Mythbuntu installation).

I've tried generating a *channels.conf* file using both PCs.

```

scan /usr/share/dvb/dvb-t/au-Canberra-Black-Mt -o zap -a 1 | tee channels.conf

```The DVICO PC produces the following file:
```

[B]ABC HDTV:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:528
ABC1:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:529
ABC2:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:530
ABC1:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:531
ABC3:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2311:2312:532
[/B]PRIME Canberra:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2374
PRIME HD:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:4600:0:2400
PRIME View 1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2401
7TWO on PRIME:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:4620:4621:2402
PRIME View 3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2403
WIN Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:502:652:1
WIN HD Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:542:0:10
GO! Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:522:672:2
SC10 Canberra:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:353:354:2055
One HD Canberra:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1711:0:2087
SC Ten:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:353:354:2119
SBS ONE:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:849
SBS TWO:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:850
SBS 3:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:851
SBS 4:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:852
SBS HD:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:853
SBS Radio 1:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:862
SBS Radio 2:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:863

```while the HVR-2200 PC produces the same, except with the ABC stuff missing.

I've tried importing the *channels.conf* file into the HVR-2200 PC, but it still can't find the ABC signals.  I've tried to manually enter the signals (see [here]("http://www.mythtvtalk.com/forum/hardware/12229-hvr-2200-not-picking-up-all-channels-2.html")) but no luck.  I've tried changing various MythTV Backend setup parameters but without much luck.  Currently they are:

Capture Card Setup -> Signal timeout (msec)-> 50000
Capture Card Setup -> Tuning timeout (msec)-> 60000
Capture Card Setup -> Recorder Options - DVB Tuning Delay (msec)-> 2000

I've tried using tzap to check the signals on the HVR-2200 PC.  For SBS, Win (9), Prime (7) & SCTen (10) they will all lock.  Here is a sample of the WIN HD Signal:

```

using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
reading channels from file 'channels.conf'
tuning to 219500000 Hz
video pid 0x021e, audio pid 0x0000
status 00 | signal ffff | snr 0000 | ber 000014dc | unc 00000000 | 
status 1f | signal fefe | snr 00f6 | ber 00008caa | unc 00000000 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008157 | unc 00000154 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008a48 | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 000080be | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008a48 | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008e74 | unc 00000254 | FE_HAS_LOCK

```BUT ABC won't lock

```

using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
reading channels from file 'channels.conf'
tuning to 205500000 Hz
video pid 0x090a, audio pid 0x0000
status 00 | signal adad | snr 002c | ber 00008e74 | unc 00000000 | 
status 00 | signal 3c3c | snr 000f | ber 00008e74 | unc 00000000 | 
status 00 | signal 8a8a | snr 0023 | ber 00008e74 | unc 00000000 | 
status 00 | signal 5151 | snr 0014 | ber 00008e74 | unc 00000000 | 
status 00 | signal ffff | snr 0000 | ber 00008e74 | unc 00000000 | 
status 00 | signal ffff | snr 0000 | ber 00008e74 | unc 00000000 | 
status 00 | signal 5858 | snr 0013 | ber 00008e74 | unc 00000000 | 

```Anybody got any ideas?

Thanks

---

### Post by TopEnder on 2010-06-10
> **BigPacks said:**
> Has anybody got a ABC Digital to work with a HVR-2200 in Canberra (Australia) from Black Mountain Tower?

I've been reading through various forums, but I'm still can't get this working on a HVR-2200 (using the drivers from [http://www.kernellabs.com/hg/saa7164-stable/](http://www.kernellabs.com/hg/saa7164-stable/)) on a PC with Mythbuntu 10.04.

My TV signal is via a 4 way amplified splitter, which should be strong enough to work. With the other splitter outputs I can get ABC with my TV (newish Samsung), my 6 year old PVR and with another PC runing Mythbuntu 10.04 (containing a DViCO FusionHDTV DVB-T Dual Digital 4 PCI with virtually no tweaks at all for the entire Mythbuntu installation).

I've tried generating a *channels.conf* file using both PCs.

```

scan /usr/share/dvb/dvb-t/au-Canberra-Black-Mt -o zap -a 1 | tee channels.conf

```The DVICO PC produces the following file:
```

[B]ABC HDTV:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:528
ABC1:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:529
ABC2:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:530
ABC1:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:531
ABC3:205500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2311:2312:532
[/B]PRIME Canberra:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2374
PRIME HD:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:4600:0:2400
PRIME View 1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2401
7TWO on PRIME:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:4620:4621:2402
PRIME View 3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2740:2741:2403
WIN Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:502:652:1
WIN HD Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:542:0:10
GO! Canberra:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:522:672:2
SC10 Canberra:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:353:354:2055
One HD Canberra:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1711:0:2087
SC Ten:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:353:354:2119
SBS ONE:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:849
SBS TWO:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:850
SBS 3:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:851
SBS 4:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:852
SBS HD:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:853
SBS Radio 1:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:862
SBS Radio 2:543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:863

```while the HVR-2200 PC produces the same, except with the ABC stuff missing.

I've tried importing the *channels.conf* file into the HVR-2200 PC, but it still can't find the ABC signals.  I've tried to manually enter the signals (see [here]("http://www.mythtvtalk.com/forum/hardware/12229-hvr-2200-not-picking-up-all-channels-2.html")) but no luck.  I've tried changing various MythTV Backend setup parameters but without much luck.  Currently they are:

Capture Card Setup -> Signal timeout (msec)-> 50000
Capture Card Setup -> Tuning timeout (msec)-> 60000
Capture Card Setup -> Recorder Options - DVB Tuning Delay (msec)-> 2000

I've tried using tzap to check the signals on the HVR-2200 PC.  For SBS, Win (9), Prime (7) & SCTen (10) they will all lock.  Here is a sample of the WIN HD Signal:

```

using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
reading channels from file 'channels.conf'
tuning to 219500000 Hz
video pid 0x021e, audio pid 0x0000
status 00 | signal ffff | snr 0000 | ber 000014dc | unc 00000000 | 
status 1f | signal fefe | snr 00f6 | ber 00008caa | unc 00000000 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008157 | unc 00000154 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008a48 | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 000080be | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008a48 | unc 00000254 | FE_HAS_LOCK
status 1f | signal fefe | snr 00f6 | ber 00008e74 | unc 00000254 | FE_HAS_LOCK

```BUT ABC won't lock

```

using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
reading channels from file 'channels.conf'
tuning to 205500000 Hz
video pid 0x090a, audio pid 0x0000
status 00 | signal adad | snr 002c | ber 00008e74 | unc 00000000 | 
status 00 | signal 3c3c | snr 000f | ber 00008e74 | unc 00000000 | 
status 00 | signal 8a8a | snr 0023 | ber 00008e74 | unc 00000000 | 
status 00 | signal 5151 | snr 0014 | ber 00008e74 | unc 00000000 | 
status 00 | signal ffff | snr 0000 | ber 00008e74 | unc 00000000 | 
status 00 | signal ffff | snr 0000 | ber 00008e74 | unc 00000000 | 
status 00 | signal 5858 | snr 0013 | ber 00008e74 | unc 00000000 | 

```Anybody got any ideas?

Thanks
BigPacks, You could try installing either VLC Media Player or me-tv and see if your channels.conf file will work and obtain a lock on the ABC channels.    me-tv can also generate the channels.conf that may work with mythbuntu.  I never had much luck with setting-up and using mythbuntu, my preference for viewering or recording is either of the above.

---

### Post by funkydan2 on 2010-06-11
I'm in Sydney, but I also used to have trouble getting a lock on ABC.

Try this: In the backend setup go to 'Input Connections', then set 'Quick Tune' to 'Always'.

Worked for me, YMMV.

---

### Post by BigPacks on 2010-06-13
> **funkydan2 said:**
> I'm in Sydney, but I also used to have trouble getting a lock on ABC.

Try this: In the backend setup go to 'Input Connections', then set 'Quick Tune' to 'Always'.

Worked for me, YMMV.

Nope, didn't work.

Thanks for the idea.

---

### Post by BigPacks on 2010-06-13
> **TopEnder said:**
> BigPacks, You could try installing either VLC Media Player or me-tv and see if your channels.conf file will work and obtain a lock on the ABC channels.    me-tv can also generate the channels.conf that may work with mythbuntu.  I never had much luck with setting-up and using mythbuntu, my preference for viewering or recording is either of the above.

TopEnder,

I couldn't get the ABC channels to work with VLC (the other channels worked).

I'll try and give me-tv a go.  See if that helps.

Thanks

---

### Post by BigPacks on 2010-06-14
> **BigPacks said:**
> TopEnder,

I couldn't get the ABC channels to work with VLC (the other channels worked).

I'll try and give me-tv a go.  See if that helps.

Thanks

I managed to get MythTV to see ABC during a scan (via the Channel Editor in the Backend Setup), but when I try and watch ABC via Myth it won't lock.

I have my DVB Tuning Delay set to 2000 msec (max value).

Anybody got any ideas?

I can't get ABC to work properly with VLC either.  I wonder if it's a driver issue?

---

### Post by daveshep on 2011-07-29
why do you want ABC anyway? i thought you only watched neighbours, masterchef, biggest loser, so you think you can dance...

---

### Post by BigPacks on 2011-07-29
You forgot to mention Home and Away.

---

