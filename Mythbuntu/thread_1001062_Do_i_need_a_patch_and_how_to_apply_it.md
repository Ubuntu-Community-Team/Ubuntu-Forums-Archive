---
title: "Do i need a patch and how to apply it?"
date: 2008-12-03
forum: Mythbuntu
---

### Post by GileraGFR on 2008-12-03
Hi,

I have MythBuntu 8.10 installed as a primary backend and trying to use a AverTV DVB-T Super 007 card.

Everything seems to install ok but won't find any channels, just states no lock and keeps scanning. I've ran ```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
``` but it just states tuning failed.

The wiki [http://www.mythtv.org/wiki/index.php/Tuner_Card#Cards_that_work](http://www.mythtv.org/wiki/index.php/Tuner_Card#Cards_that_work) says its supported but on the linuxtv site [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#AVerMedia) it says its supported but using a patch.

It links to the patch here [http://lists.zerezo.com/video4linux/msg19205.html](http://lists.zerezo.com/video4linux/msg19205.html) but the patch states in a few lines the number saa7133 but the card is saa7134 according to the wiki so i don't even know if its right to use the patch.

If it is correct or just worth a try and won't damage anything a re-install won't fix can anyone help me apply the patch.

I know i haven't included any logs but if anyone asks i shall provide :)

Any help would be appreciated.
Thanks

---

### Post by ian dobson on 2008-12-03
Hi,

Try scanning with w_scan maybe it'll scan better.

Regards
Ian Dobson

---

### Post by GileraGFR on 2008-12-04
Thanks for your suggestion, I'll try it when i get home.

One other thing i was going to ask, the transmitter Moel y Parc which is closer to me than Winter Hill isn't listed in the examples folder to scan with. Does a file exist for Moel y Parc? 

Thanks

---

### Post by GileraGFR on 2008-12-04
Ian,

I don't seem to have w_scan on there, should it be?

Thanks

---

### Post by ian dobson on 2008-12-04
Hi,

You need to download and compile it yourself. See [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/) on how to do that.

Regards
Ian Dobson

---

### Post by GileraGFR on 2008-12-04
Ahh sweet thanks Ian, I should have searched first sorry.

I've not had any joy though:

```
root@leviathon:/home/gilera/w_scan-20081106# w_scan >> /etc/vdr/channels.conf
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_
frontend Philips TDA10046H DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO not supported, trying HIERARCHY_NONE.
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_
177500:
184500:
191500:
198500:
205500:
...
834000:
842000:
850000:
858000:
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.

```

I'm now thinking it has to be my card, have any other ideas or have i gone wrong somewhere?

Thanks

---

### Post by ian dobson on 2008-12-04
Hi,

Do you have a windows box that you could use to test the card. It could well be that the card is not good or you have a vary bad signal or somethings wrong with your wiring/antenna.

Regards
Ian Dobson

---

