---
title: "dvb-s Most channels ok, some still not working"
date: 2010-01-29
forum: Mythbuntu
---

### Post by singedwings on 2010-01-29
I have mostly got to grips with the channel scanner in 9.10. I have managed (mostly) to successfully scan and setup my dvb-s channels, including getting the eit information. However I have several channels that I know should work but are not. These include BBC2 Eng, BBC Three & BBC Four.

The scan has found these channels and named them, but when I try to tune to them I cannot get a lock. Using phpmyadmin I have viewed the information in the database to try and get a clue as to what has caused this.

All the channels that are not working are all on the same multiplex, and this is the one transport that I entered manually to get the scan going when setting up all the channels.

Is this a bug, or is there any way to fine tune these channels? So near and yet still so far!

---

### Post by nickrout on 2010-01-29
at one point there was a bug that changed the polarity in the database from horizontal to vertical or viceversa. Check the polarity.

---

### Post by singedwings on 2010-01-30
I have managed to solve this. I deleted the transport that was not working properly, there were some differences in the list of transports between the one I had added myself and the ones added by the channel scan. Then I rescanned the channels using the 'scan existing tranports' with 'search for new transports' enabled.

After about 3 or 4 goes the channel scanner did not crash and hey presto the non functioning channels now work!

---

