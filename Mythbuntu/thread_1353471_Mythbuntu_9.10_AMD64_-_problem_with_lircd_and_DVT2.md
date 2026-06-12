---
title: "Mythbuntu 9.10 AMD64 - problem with lircd and DVT2000H"
date: 2009-12-12
forum: Mythbuntu
---

### Post by asbjorn on 2009-12-12
Hi
I'm using Mythbuntu 9.10 AMD64 and DVT2000H.
I can successfully use evtest /dev/input/event6
Testing ... (interrupt to exit)
Event: time 1260438485.593709, type 1 (Key), code 377 (TV), value 1
Event: time 1260438485.593719, -------------- Report Sync ------------
Event: time 1260438485.783717, type 1 (Key), code 377 (TV), value 0
Event: time 1260438485.783726, -------------- Report Sync ------------

I can use irrecord -H dev/input -d /dev/input/event6  YG
that create a YG.conf file with the buttons I press.

When I use mode2 -d /dev/input/event6 -H devinput
I'm getting the following error (have tried with dev/input but with the
same error):
mode2: initializing '/dev/input/event6'
**This program does not work for this hardware yet**

When I use /usr/sbin/lircd -H dev/input -d /dev/input/event6 -n and irw
I get nothing. (I.e. nothing shows up under irw as it use to...)

I have tried with default and null instead of devinput but that does not
work.

Does anyone have a suggestion?
(I have also tried with a NOVA 500 T but I get the same problem.

Thankful for any suggestions.

(Have use google, read this forum and dozens of other sites...) 
Martin

---

### Post by jammln on 2010-01-21
I am having exactly this problem with my Nova-T.

Did you manage to solve this?

---

