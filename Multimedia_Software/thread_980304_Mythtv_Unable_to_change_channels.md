---
title: "Mythtv Unable to change channels"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Chuffinora on 2008-11-12
After running 0.20 on Drake/Feisty for ~2 years, I ran into a problem (Whole other story) and ended up upgrading to 8.10 and Myth 0.21.

I have it all working except for one major problem.  I cannot change channels,  pressing either remote (Hauppauge PVR-150) or keyboard,  gives a correct on screen display and pauses live TV, but the channel does not change.  Recordings are not tuning to the correct station either.

I have tried re-running mythtv-setup and deleting all video sources and capture cards and then setting them up again.

Running IRW indicates that the right commands are being sent.

This section from my mytbackend log indicates an irsend problem

2008-11-12 18:42:00.542 Current Schema Version: 1214
Starting up as the master server.
2008-11-12 18:42:00.800 New DB connection, total: 3
2008-11-12 18:42:00.803 Connected to database 'mythconverg' at host: localhost
irsend: command failed: SEND_ONCE blaster 8
irsend: unknown remote: "blaster"

I have searched and cannot find a similar issue reported.

---

