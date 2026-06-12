---
title: "DVB-T scan"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by moeFinley on 2006-10-17
I'm trying to tune my Nebula DigiTV card.  It all seems to be detected ok as a NxtWave NXT6000 in Kaffeine, but tuning fails.  The progress bar doesn't get off 0%.

When I do 'scan' in the terminal I get the following:

```

scanning uk-CaradonHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 578000000 0 3 0 1 0 0 0
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

What does this mean, is the hardware not setup properly or are the transmitter details wrong?

Thanks for any help

---

### Post by moeFinley on 2006-10-20
Please, has anyone got any help?

I switched to Linux about 5 months ago and this is one of the last things I need to get working (that and Pocket PC syncing).  Not that I'm going to switch back to Windows because of this, I'll have to buy a more compatible TV card or something which is still a pain in the arse. ](*,)

---

### Post by Jose Catre-Vandis on 2006-10-22
Make absolutely certain that you are pointing at the right transmitter

or

You will most likely need to update the dvb part of the kernel to get things working, and you may also need some firmware. To update v4l-dvb do the following:


```
sudo apt-get install mercurial
```

```
hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb
cd v4l-dvb 
sudo make clean 
sudo make distclean 
sudo make ( error message like leaving directory /2.6.15-23 etc..) 
sudo make install 
sudo make reload
```

Try scanning again

If you need firmware then visit [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

Firmwares go in the /lib/firmware directory. I don't know which one is / might be for your card.

---

