---
title: "flydvb trio"
date: 2008-09-02
forum: Multimedia Software
---

### Post by grechk on 2008-09-02
Excuse for my english, i'm italian.
Hello, i have a problem with card on object...
I use ubuntu 8.04 with kernel 2.6.24-19 (if it can serve install another kernel).
dvb-t and analog tv are perfect, dvb-s found channels in kaffeine and with "scan" but get this error:
DVR device not found
I have allready less various forum and internet site, but not found a solution...
I change frontend with:
sudo modprobe saa7134-dvb use_frontend=0 (dvb-t) or use_frontend=1 (dvb-s)
and channel scan with scan... found channel list...
use:
mplayer - < /dev/dvb/adapter0/dvr0
and get error:
/dev/dvb/adapter0/dvr0 nessun device
I go on directory /dev/dvb/adapter0/ and file dvr0 found.

I can not solve the problem.

Thank you

---

