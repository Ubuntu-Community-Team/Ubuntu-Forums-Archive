---
title: "Two cards - two recordings of same show"
date: 2009-03-01
forum: Mythbuntu
---

### Post by Markus72 on 2009-03-01
Hi,

I have two DVBT cards and want to use a rule to record all Simpsons shows.
So I created a rule but it records the same show with both cards simultaneously.

The reason seems to be that one and the same show is selected twice by the rule because they have different starting times (it always differs by one minute).

That's strange, because I only use EIT - they should't differ at all.

MythTV should evenmore know that it's the same show only on two different cards, right?

What is misconfigured?

Thanks
Markus

---

### Post by Markus72 on 2009-03-02
no idea?

---

### Post by utar on 2009-03-02
Are you using 1 or 2 video sources in the backend?

---

### Post by Markus72 on 2009-03-02
Hi,

first, I used 1 but then I tried with two - same behavior.

Is one video source for two cards ok or are there restrictions?

Markus

---

### Post by utar on 2009-03-02
If both tuners are for the same channels then you should be using 1 video source.

Do you mean that the programme guide on each tuner differs from each other by 1 min?  This shouldn't happen, although even if it does I would expect Myth to realise it is the same programme.  Are you using EIT to populate the programme guide?  

Not in front of my box at the moment but I seem to remember somewhere you can select how myth detects duplicate programmes, e.g. by time, title, subtitle etc.  I would check how you have this set.  I would also double check the recording options to make sure you haven't any rerecord by default options selected.

---

### Post by Markus72 on 2009-03-02
Hi,

I'll configure it with one video source when I'm back home.

The different starting times sometimes differ one or more minutes. I wasn't able to identify a pattern yet.

I use both cards for the same channels. 

Markus

---

### Post by Harani on 2009-03-02
as the previous poster says you should only have the one Video source defined and then linked to two inputs.

I use this sort of setup with two DVB  "Freeview" USB tuner sticks

---

### Post by Markus72 on 2009-03-02
Hi,

reconfigured MythTv to only use one video source for both cards.
Plus I scanned for stations using only one card (scanned with both cards before).

It seems that those changes made the difference. No duplicates any more.

Thanks!
Markus

---

