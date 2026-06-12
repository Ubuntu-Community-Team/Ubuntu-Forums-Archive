---
title: "Can't get dvb-t on Kaffeine"
date: 2008-07-30
forum: Multimedia Software
---

### Post by ERnst W. on 2008-07-30
Hi,
my Kaffeine player acts kind of weired. Sometimes the player recognizes the TV-card, but most of the time it doesn't. I've started kaffeine on the Terminal and that's what it's been telling me:

kbuildsycoca...
kio (KMimeType): WARNING: KService::offers : Servicetype THumbCreator not found 
kio (KMimeType): WARNING: KService::offers : servicetype THumbCreator not found 

hope you can help me...please try to keep your answer simple because I'm quite new on Ubuntu.

---

### Post by ERnst W. on 2008-07-30
I just had this situation again that after I restarted the computer the TV-Card was suddenly there again. But after I hit the restart button again and the computer failed to shutdown probably (I had to turn it off by hand) the TV-card was gone again.now there are 2 new error messages:

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket


I also had another problem, the first time when the TV-card was recognized. I wasn't capable of searching for channels.
Additionally to the other error messages these here plopped up on the Terminal

LLCI slot found on /dev/dvb/adapter0/ca0DvbCam::probe(): no CA module present on /dev/dvb/adapter0/ca0
Using DVB-s device 0:0 "ST STV0299 DVB-S"
tuning DVB-S to 12551000 v 22000000
inv:2 fecH:5
DiSEqC:switch pos 0, 13V, hiband (index2)
FE_SET_TONE failed:Connection timed out
FE_SET_VOLTAGE failed: Input/output error
DiSEqC: e0 10 38 f1 00 00
FE_DISEQC_SEND_MASTER_CMD failed: Connection timed out
FE_DISEQC_SEND_MASTER_CMD failed: Connection timed out
FE_DISEQC_SEND_BURST failed: Connection timed out
FE_DISEQC_SEND_BURST failed: Connection timed out
FE_SET_TONE failed: Connection timed out
...............

Not able to lock to the signal on the given frequency
Front closed
dvbsi: Cant tune DVB
Transponders: 1
dvbsi: The end :)
channels found: 0

---

### Post by ERnst W. on 2008-07-31
The problem has changed again. It seems like the the problem was caused by a new soundcard. I took the soundcard out of my computer and now it recognizes the TV-Card again...

As soon as I try to search for channels, the whole system freezes.
This is what the Terminal tells me:

DvbCam:: probe(): LLCI slot found on /dev/dvb/adapter0/ca0
DvbCam:: probe(): no CA module present on /dev/dvb/adapter0/Ca0
using DVB device 0:0 "ST STV0299 DVB-S"
tuning DVB_S to 125510000 v 22000000
inv:2 fech:5
DiSEqC: switch pos 0, 13V, hiband (index 2)
DiSEqC: e0 10 38 00 00
. Locked.
Transponder: 1/1


It's seems like I'm missing a "Ca module"... can anybody tell me what that is and how to solve the problem??? I'm desperate for an answer:confused:, so if you need more informations, just ask.

---

