---
title: "Can watch a channel live, but can not record it"
date: 2009-07-02
forum: Mythbuntu
---

### Post by Das Hammer on 2009-07-02
I have one channel that 100% always will not record. But the weird part is that I can watch it live all day long....which essentially IS recording it for timeshifting.

The guide data is present and correct. Time is ok. Scratching my head over this one. Oh, I also deleted all the tuner and redid everything...but it still persists.

This is a DVB-S channel. It also happens randomly on other DVB-S channels, but happens 100% of the time on this particular one.

The database has an entry for the recording and it shows up in the "recorded tv", but there is no file for the mpg.


backend log....I've highlighted the suspicious part.

[INDENT]2009-07-02 19:45:04.044 adding: mythbuntu as a client (events: 0)
2009-07-02 19:45:04.267 Reschedule requested for id 284.
2009-07-02 19:45:04.526 Scheduled 116 items in 0.2 = 0.02 match + 0.23 place
2009-07-02 19:45:04.583 TVRec(5): ASK_RECORDING 5 0 0 0
2009-07-02 19:45:04.762 TVRec(5): Changing from None to RecordingOnly
2009-07-02 19:45:04.765 TVRec(5): HW Tuner: 5->5
[COLOR="Red"][B]2009-07-02 19:45:04.848 DVBSM(0), Warning: Can not count Uncorrected Blocks
			eno: Operation not supported (95)[/B][/COLOR]
2009-07-02 19:45:04.872 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-07-02 19:45:04.875 Started recording: Tee-It-Up Ohio: channel 15010 on cardid 5, sourceid 15
2009-07-02 19:45:05.032 TVRec(6): ASK_RECORDING 6 0 0 0
2009-07-02 19:45:11.275 MainServer::HandleAnnounce Monitor
2009-07-02 19:45:11.325 adding: mythbuntu as a client (events: 0)[/INDENT]

---

### Post by Mister.Vash on 2009-07-04
What does the frontend log indicate during that same time?  It's possible that it would be including an error there as well, could be something like a 'video renderer not available' message or something odd like that.

I'm hoping the frontend does include additional messages, as I believe the one you are looking at it is more generic - it has logged a warning, it can't do something because of that warning - hopefully the frontend log will include an actual error, and if not that, then maybe the trigger for message in the backend log.

Quick question - where you are watching the live channel, does it let you pause, then skip back and forward?  I wasn't sure if you were just validating that you could see the channel, or actually do the time shifting

---

### Post by Das Hammer on 2009-07-04
There are no warnings or errors in the frontend log.

To answer your last question, yes, I can do all the timeshifting I want while watching the channel live. Watching it right now and can pause, skip back, skip forward, etc.

I went through the backend.log again and found nothing other than that warning in the first post followed by a slew of errors due to the file not being found (because I went to mythweb to look at my recorded programs).

I sure would like to fix this, but without something more obvious showing up in the log I don't know what to do.

Anyone else using a DVB-S card here in the US to watch Sportstime Ohio HD on 121W ???

---

