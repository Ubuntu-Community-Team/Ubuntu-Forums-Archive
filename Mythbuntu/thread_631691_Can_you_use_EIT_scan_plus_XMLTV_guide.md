---
title: "Can you use EIT scan plus XMLTV guide?"
date: 2007-12-04
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-12-04
Can mythtv combine guide data from the on-air EPG as well as downloaded XMLTV data?  If so, how does it handle it?

I ask because, in the mythtv setup, it let's you tick 'EIT scan' but I haven't tried it yet - I've just been using XMLTV data, but now, our digital TV stations are finally starting to transmit EPG data properly.

---

### Post by Lester_Burnham on 2007-12-05
Hi,

I think when you do a scan, you will see duplicate channels, so one should have an xmltv ID and the other should be EIT based. I can't remember exactly.

Worth a try though.

Lester

---

### Post by twkisner on 2007-12-05
> **ubnewbie2 said:**
> Can mythtv combine guide data from the on-air EPG as well as downloaded XMLTV data?  If so, how does it handle it?

I ask because, in the mythtv setup, it let's you tick 'EIT scan' but I haven't tried it yet - I've just been using XMLTV data, but now, our digital TV stations are finally starting to transmit EPG data properly.

I've had them both on before, but I don't recommend it.  I didn't have duplicate channels, but EIT data is spotty at best (at least where I live).  It instantly said I had 3,000 days of schedule data, and the EIT data isn't as desciptive as what I get from DataDirect/Schedules direct.  I think Myth gives presidence to EIT data in the databse (since it is supposed to be up-to-the-minute current).

---

### Post by ubnewbie2 on 2007-12-05
> **twkisner said:**
> I've had them both on before, but I don't recommend it.  I didn't have duplicate channels, but EIT data is spotty at best (at least where I live).  It instantly said I had 3,000 days of schedule data, and the EIT data isn't as desciptive as what I get from DataDirect/Schedules direct.  I think Myth gives presidence to EIT data in the databse (since it is supposed to be up-to-the-minute current).

The quality of data is the main issue for me, but I am in Australia, so it may be different to your experience.

Just to clarify for myself then, you can just turn it on for all channels, and myth uses EIT data for the channels/timeslots whenever it can, then fills in the rest from the XMLTV data?

---

### Post by Lester_Burnham on 2007-12-06
Hi,

I'm in OZ too. You might have to be a test pilot.
I setup a quick knoppmyth box the other day for an EIT test, and the data looked passable.

I also receive channels from country and metro, so was thinking of doing the same as you are talking about, as I use IceTV for the metro stuff.

Good luck,
Lester

---

### Post by twkisner on 2007-12-06
> **ubnewbie2 said:**
> The quality of data is the main issue for me, but I am in Australia, so it may be different to your experience.

You might get better results from the TV stations in Austrialia.  I know it's just the stations in my area (Dallas, Texas).

> **ubnewbie2 said:**
> 
Just to clarify for myself then, you can just turn it on for all channels, and myth uses EIT data for the channels/timeslots whenever it can, then fills in the rest from the XMLTV data?

Yes, that is exactly how it was behaving.

---

### Post by ubnewbie2 on 2007-12-06
> **Lester_Burnham said:**
> Hi,

I'm in OZ too. You might have to be a test pilot.
I setup a quick knoppmyth box the other day for an EIT test, and the data looked passable.

I also receive channels from country and metro, so was thinking of doing the same as you are talking about, as I use IceTV for the metro stuff.

Good luck,
Lester

Looking at the guides on my digital TV, at least 3 seem to have a week's worth, from memory it was ABC, Nine, and Ten.  I read that Seven is about to do it too.

Last night I turned on EIT scan, and over the weekend, I'll see what happens if I turn on the individual "Use on air data" on a few channels.

---

### Post by Lester_Burnham on 2007-12-06
It will be good to see what you think of the quality of the data. I would play around as well, but I don't have the time for another week or two.

All stations are meant to have the EIT data sorted by January, I think.

---

### Post by ubnewbie2 on 2007-12-07
> **Lester_Burnham said:**
> It will be good to see what you think of the quality of the data. I would play around as well, but I don't have the time for another week or two.

All stations are meant to have the EIT data sorted by January, I think.

Looking good.  I turned on all channel 10, and the textual info seems greater than I was getting from Oztivo.

Interestingly, Channel 1 (10HD) is carrying a 'banner' message covering all timeslots saying

"Ch1 is now available in HD in preparation for the launch of the new TEN HD channel in December. View TEN on Ch10 on a standard d"

Which means I cannot schedule anything on that channel until they go live (on the 16th) but I can live with that.

I think I'll just turn them all on now.

---

