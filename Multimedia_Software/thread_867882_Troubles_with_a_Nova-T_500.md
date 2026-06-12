---
title: "Troubles with a Nova-T 500"
date: 2008-07-23
forum: Multimedia Software
---

### Post by forcemaster99 on 2008-07-23
Hi All,
I'm having some trouble installing a Hauppauge Nova-T 500 Dual DVB card. I have followed this [(Link)]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI") guide, but when it came to scanning for channels, I got a tuning failure.

```
root@MythTV:/home/myth# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Waltham > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Waltham
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 698000000 0 3 9 1 0 0 0
initial transponder 490000000 0 2 9 3 0 0 0
initial transponder 514000000 0 2 9 3 0 0 0
initial transponder 570000000 0 3 9 1 0 0 0
initial transponder 666000000 0 3 9 1 0 0 0
initial transponder 642000000 0 3 9 1 0 0 0
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 666000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 666000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```
I have installed the firmware, and the computer recognizes the card.

I have searched Google, and nothing I have found has worked.
My specs are:
AMD Athlon 64 X2 Dual Core Processor 5200+
2Gb RAM
NVidia GeForce 8600 GT

And I am running Ubuntu 8.04 (hardy) 2.6.24-19-generic 

Please Help.
Cheers

---

### Post by forcemaster99 on 2008-07-24
bump

---

### Post by xc3RnbFO8P on 2008-07-24
What kind of antenna do you use?
Did you try Kaffeine?

---

### Post by forcemaster99 on 2008-07-25
I've tried Kaffeine, and i get a 0% signal, and we just had a new digital aerial installed a few months ago.

---

### Post by xc3RnbFO8P on 2008-07-25
Here is what I found:
> If some Waltham Freeview channels are missing from your digital TV channel line up, start by checking your aerial. If you are getting Freeview reception problems on Waltham UHF channel 23 and 26 DTT multiplexes, and you're well inside the service area from the transmitter, it is likely that your existing TV aerial is unsuitable for Freeview. In this case, you'll need to buy a high gain wideband aerial and get it installed by a CAI registered aerial contractor. Alternatively, if you live in a good DTT signal area, you can try installing a loft aerial yourself. 
[http://www.stevelarkins.freeuk.com/waltham_tv_transmitter.htm]("http://www.stevelarkins.freeuk.com/waltham_tv_transmitter.htm")
Do you have a information about your aerial?

---

### Post by forcemaster99 on 2008-07-25
Sorry, I have no info on the aerial, but I know that it works, because I can get a signal on the TV, just not through the pc.

---

### Post by xc3RnbFO8P on 2008-07-25
Has your TV DVB-T tuner?

---

### Post by forcemaster99 on 2008-07-25
Well, I did a full system reinstall and started over, and it worked this time. I dunno what was wrong before.
Thanks anyway.

---

