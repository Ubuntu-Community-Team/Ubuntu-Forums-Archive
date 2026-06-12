---
title: "Manual recording get duplicated on same channel"
date: 2011-06-21
forum: Mythbuntu
---

### Post by dibuntux on 2011-06-21
I have XLMTV set for DVB-T channels. Some of those are replicated via sat, but no XLMTV is set on the relative DVB-S card.
If I set a manual recording on the DVB-S input, it get scheduled correctly, but the same recordings also appear on the equivalent channel on DVB-T: so I get 2 recordings of the same show, at best, or conflict, since I'm using a card which was supposed to record another show.
The scope is to use the DVB-S card so the DVB-T is free to record another channel. I tried with input priority to no avail.

Any Ideas? TIA

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by nickrout on 2011-06-22
you probably need to sort out your epg data for the -S card.

---

### Post by dibuntux on 2011-06-22
For that channel I do not get EPG data (do not know why, I do receive it for others). So I have to schedule a Manual recording.
Do you suggest that I use XLMTV for that channel too? TIA

---

### Post by nickrout on 2011-06-22
If your DVB-S and DVB-T access the same channels then they need the same listing source.

---

### Post by dibuntux on 2011-06-23
Mmmmh. Ok yesterday I was able to  manually record a show, scheduling via mythweb,  giving it a short different name from the one that was on the guide. There were no conflict and all tuners recorded correctly.

Now, on your input I changed the DVB-S source to get listings from XLMTV. I updated the database and got the schedule correctly on the DVB-S channels. Then I programmed a show to be recorded on DVB-T and it was duplicated on DVB-S.
If I go on upcoming recordings I see all duplicated shows to be recorded. If I delete the DVB-S upcoming recording, the DVB-T also get deleted.

How to solve this? TIA

---

### Post by dibuntux on 2011-06-23
Got it! Looked around on the net and another nick gave me the answer: "The two 'BBC2' channels (one on DVB-T, the other on DVB-S) need to
appear as one to the scheduler to avoid these duplicates. I have both
DVB-S and DVB-T on a test box, and get different callsigns for each
'version':

DVB-T - "BBC TWO"
DVB-S - "BBC 2 England"

If you update your groups of common channls (BBC1, BBC2, ITV, etc) on
your 2 video sources so that they each share the same CALLSIGN, and
the scheduler should treat them as the same, and should stop these
duplicate recordings from occurring.

If you also want such channels to only appear once in the EPG, you
should also update the channel number (channum) to be the same for
both channels.

Nick"

As soon as I changed the callsigns to be the same (they were different in upper & lower cases), the duplicated recordings disappeared from the schedule! Great!

Thanks a lot for your time and suggestions. Hope this helps others.

Dave

---

