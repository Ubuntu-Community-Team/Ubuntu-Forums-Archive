---
title: "Burning more than 74 Minutes on Audio CD?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by cforput on 2008-12-10
I have some old time radio shows that are in 16 to 32bit format so the amount of time per file size is much higher than music. I get about 30 minutes per 7MB file size. This means I can fit hundreds of minutes on a 700 MB CDR. The problem I am seeing is that when I try and burn them to my CDR (k3b, gnomebaker, etc) the programs still limit me to 74 - 90 minutes of music. I don't know much about how all this stuff works but is there a program that will burn the CDs with a greater amount of time on them?

---

### Post by Jose Catre-Vandis on 2008-12-10
The only real way around this is to burn mp3CDs and use a player (DVD players usually can) that can cope with this format. As you mention there are 90 minute CDRs available but nothing of much higher value. How do you want to listen to them, in the car, for example?

---

### Post by cforput on 2008-12-10
Both in the car and at home. My CD player in my truck doesn't recognize MP3 format so I will figure out something. Thanks

---

### Post by xtifr on 2008-12-10
For audio CD format, the amount of space consumed is a function of time.  CD audio is 16-bit stereo at 14.4k samples/sec, always, so one second of sound takes 4 x 14,400 bytes, no matter what.  Period, end statement.

It doesn't matter if your input files are compressed--they have to be uncompressed before they can be burnt.  If your signal is mono, it has to be converted to "two-channel mono".  If your audio files are 8-bit, they will be scaled up to 16-bit, and if they are 24- or 32-bit, they will be scaled down.

If your player(s) can handle *data *CD *ROM*s with audio files on them, then this restriction doesn't matter, but if you want to make standard *audio* CDs that can be played on any CD player, you only get 74 (or 80 or 90) minutes.

---

