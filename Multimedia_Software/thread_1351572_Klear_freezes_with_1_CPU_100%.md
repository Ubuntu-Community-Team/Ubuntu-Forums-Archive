---
title: "Klear freezes with 1 CPU 100%"
date: 2009-12-10
forum: Multimedia Software
---

### Post by Rschnauzer on 2009-12-10
Hallo, 
 
after changing Ubuntu Karmic to Ubuntu64 Klear freezes with one CPU at 100%
The process starts displaying TV picture and audio and than freezes. 
Process shows wait for futex_wait_queue_me and has to be killed. 

I use a DVB-S TV with a Medion MD-8828 with TV-Hybrid adapter CTX948 
(see: [http://www.creatix.de/produkte/multimedia/ctx948.htm](http://www.creatix.de/produkte/multimedia/ctx948.htm)) 
 
To aktivate DVB-S frontend I stored:  
options saa7134-dvb use_frontend=1  
in /etc/modprobe.d/modprobe.conv (DVB-T is default on frontend=0) 

With Ubuntu 32bit Klear works.
Has anybody an idea what to do or how to get additional information?

---

