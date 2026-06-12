---
title: "ATSC bad configuration ...."
date: 2011-09-17
forum: Multimedia Software
---

### Post by spacedvb on 2011-09-17
iI am trying to do a proyect. my server had 4 DVB ATSC card all driver installed properly No error

i install mumudvb all installtion with out error.

I am getting a strange error, that i know my config file is correct.

iptvatsc@iptvatsc-P43-ES3G:~/mumudvb$ mumudvb -d -vvv -s -c atsc0.conf
MuMuDVB Version 1.6
Latest version available from [http://mumudvb.braice.net/](http://mumudvb.braice.net/)

Bad value for autoconfiguration, autoconfiguration will not be run
Config issue : unknow symbol : atsc_modulation

Streaming. Freq 629000000
Using DVB card "Samsung S5H1409 QAM/8VSB Frontend"
Unknown FE type : 3. Aborting
ERROR tuning channel : Invalid argument 
Tunning issue, card 0
closing cleanly. Error 7

*********************************************
my config file is look like this:

card=0
autoconfiguration=full
freq=629000
atsc_modulation=vsb8

On my other ATSC server use ubuntu 11.04 and same dvb card i had same configuration and work perfectly.

any help..

DVB ATSC ; detected as fallow:
iptvatsc@iptvatsc-P43-ES3G:~$ sudo w_scan -fa -c US -X -o 7
w_scan version 20101001 (compiled for DVB API 5.2)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format czap/tzap/szap/xine
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> ATSC "Samsung S5H1409 QAM/8VSB Frontend": good :-)
    /dev/dvb/adapter1/frontend0 -> ATSC "Samsung S5H1409 QAM/8VSB Frontend": good :-)
    /dev/dvb/adapter2/frontend0 -> ATSC "LG Electronics LGDT3303 VSB/QAM Frontend": good :-)
    /dev/dvb/adapter3/frontend0 -> ATSC "Samsung S5H1409 QAM/8VSB Frontend": good :-)
Using ATSC frontend (adapter /dev/dvb/adapter0/frontend0)

---

### Post by branna on 2011-12-08
Greetings:

Did you ever find a solution for this problem? I'm getting similar errors.

---

