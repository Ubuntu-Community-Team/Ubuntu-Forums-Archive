---
title: "Recordings that cancel just before recording"
date: 2012-01-28
forum: Mythbuntu
---

### Post by mathog on 2012-01-28
The oddest thing has started happening on our Myth 0.21 box.  Set a "record once" early in the day on an NBC station.  Shortly before the recording is to start, it switches in the upcoming recordings to white letters with an "N" and does not record.  The reason given is always:

> The showing will not be recorded because this rule does not match any showings in the current program schedule.

The thing is, it does match: name, time, station, all match perfectly.  It is possible to go to the program guide and schedule the show again, at which point there are two (apparently identical) entries, the newer one of which will record, the older one won't.

So far this has happened a couple of times with the "NBC Nightly News" and also last night for the "Chuck Versus Sarah" episode.  It always happens somewhere between half an  hour and nothing before the show is to start.  For that Chuck episode we happened to have the box on "upcoming recordings" and saw it go to "N" about 30 seconds before the recording was to start.

No corresponding errors in the back end logs, at least that I could see.  So far it has only happened on NBC.  The only other glitch recently was an attempt to record the "Touch" pilot, which resulted in a 1.6GB file, but plays back (showing the appropriate time counter and duration) as a soundless black square.  Probably not a related issue.

Anybody else seen this?

---

### Post by nickrout on 2012-01-28
Are you really expecting support for 0.21?

Are you using EIT data, which can change at random times?

---

### Post by mathog on 2012-01-28
> **nickrout said:**
> Are you really expecting support for 0.21?


It never hurts to ask.  

The 0.21 box works and the better half would not be pleased if I had to take it off line for an extended period, which is the most likely scenario for a major update (both the OS and MythTV are of the same era).

> **nickrout said:**
> Are you using EIT data, which can change at random times?

Good point.  Checked mythtv-setup and that tiny box was indeed checked.  We have schedules direct so the dvr doesn't absolutely need to have EIT enabled.  It is unchecked now.  Will see if the problem goes away.

Thanks.

---

