---
title: "w_scan can't find any DVB-T channels"
date: 2009-09-02
forum: Multimedia Software
---

### Post by Lantizia on 2009-09-02
Hi,

I want to use Totem to watch digital TV here in the UK.  The codec is installed and all is good, I just need to generate a channel file as described here... [http://projects.gnome.org/totem/#dvb](http://projects.gnome.org/totem/#dvb)

So I've ran this... but get no channels at the end (and yeah it's plugged into the aerial!.. when I reboot into Windows it's fine).

Output of my lspci...
```
05:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
```

And finally what I ran and what I got at the end...
```
lantizia@ares ~ $ w_scan -X > ~/.gstreamer-0.10/dvb-channels.conf
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend LSI L64781 DVB-T supports
INVERSION_AUTO
QAM_AUTO not supported, trying QAM_64.
TRANSMISSION_MODE not supported, trying TRANSMISSION_MODE_8K.
GUARD_INTERVAL_AUTO not supported, trying GUARD_INTERVAL_1_8.
HIERARCHY_AUTO not supported, trying HIERARCHY_NONE.
FEC_AUTO not supported, trying FEC_NONE.
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
177500: 
184500: 
191500: 
198500: 
205500: 
212500: 
219500: 
226500: 
474000: 
482000: 
490000: 
498000: 
506000: 
514000: 
522000: 
530000: 
538000: 
546000: 
554000: 
562000: 
570000: 
578000: 
586000: 
594000: 
602000: 
610000: 
618000: 
626000: 
634000: 
642000: 
650000: 
658000: 
666000: 
674000: 
682000: 
690000: 
698000: 
706000: 
714000: 
722000: 
730000: 
738000: 
746000: 
754000: 
762000: 
770000: 
778000: 
786000: 
794000: 
802000: 
810000: 
818000: 
826000: 
834000: 
842000: 
850000: 
858000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.

```

Any ideas?

---

### Post by avacado on 2009-09-16
Lantizia
I have the same problem, I am awaiting a responce to yur query.
Looks my board produces less error messages than yours in searching

Avacado@avacado $ w_scan -x
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend Zarlink ZL10353 DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
177500: 
184500: 
AND so on, etc etc, ad nauseum.....but NO channels and then it dumps the file so I end up with no initScanFile depite the front end messages all on AUTO.

Please help

---

