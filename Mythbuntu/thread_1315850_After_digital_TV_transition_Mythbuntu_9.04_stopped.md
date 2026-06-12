---
title: "After digital TV transition Mythbuntu 9.04 stopped recording"
date: 2009-11-05
forum: Mythbuntu
---

### Post by mekanix on 2009-11-05
November 1st Denmark went digital and my Mythbuntu 9.04 stopped working.

My setup is Mythbuntu 9.04 + WinTV ministick which worked fine before november 1st. Had it tuned into MUX1 which had the local (danish) public free-to-air channels (DR1, DR2, TV2 and more) all MPEG2.

Then came november 1st where the analog channels stopped and all went digital and some channels got moved around. And I could no longer record/watch LiveTV. LiveTV just gives me a ms black screen and back to the menu. And no recordings occur.

I have "retuned" my DVB-tuner and it finds all the channels. MUX1 is still MPEG2 and free-to-air with DR1, DR2, TV2 etc.. And MUX2 is MPEG4 and free-to-air. Rest is commercial and encrypted.

I can't wrap my head around as to why. 

I've installed MeTV, which doesn't show anything (but does show all the EPG-data). Just for fun I set MeTV to record a channel and used VLC to watch the recording - perfect recording. Weird.

I've tried femon - though I don't really know how to read the output. But it seems that that it locks on to the channel. It gives me something like:

status SCVYL | signal 0057 | snr 001e | ber 00000000 | unc 00000000 | FE_HAS_LOCK

Is this good or bad.

Bottom line:
Before november 1st Mythbuntu had no problem tuning into MUX1 - after is does.
MeTV will not play but does record mpeg2 channels (which tells me the signal strenght is good enough)
femon reports low numbers, but does have lock.

Anyone got a clue?

- Bjarne

---

### Post by mekanix on 2009-11-05
Fixed.

In Myth Setup, when I go into "Channel Editor" and then "Edit Transport" MUX1 and MUX2 looks like this:

QPSK 0 Hz netid 8400 tid 1001
QPSK 0 Hz netid 8400 tid 1002

Setting the right frequency and MythTV works again.

Now, how the 0 Hz got there I have no clue.

- Bjarne

---

