---
title: "(Unknown)'s in EPG"
date: 2011-04-08
forum: Mythbuntu
---

### Post by sudanmas on 2011-04-08
I started seeing (unknown)'s in my EPG listings last week from ScheduleDirect.  The other channels have data in the EPG, but the trouble channel stop displaying program info three hours before the other channels ru out of data.  The errant channels don't refresh from that point on.  The odd things is that this happens only with 11 of my 20 subscribed channels.  I've tried:

o Removing The Channels from SD and removing channels from the channel editor then  re-adding from SD

o Removing the Video Sources and Input Connections and recreating them both of the aforementioned . 

o Adding only 1 channel from the offending list - the issue still occurs with that one channel 

o SD sent me a listings of what I'm pulling down nightly and the channel listing info is there

o  Running a mythconverg database check from the command line or from mythweb don't have any effect

I find it rather odd that this is only affecting certain channels?  Seems to me like a DB issue to me. 

I'm prepared to nuke mythconverg and reconfig from scratch, but I'd rather not if I can find an alternate solution.

Any suggestions as to what else I can try?

I'm running mythbuntu .23

Robert

---

### Post by sudanmas on 2011-04-09
I followed up with a bit more troubleshooting on my end.

I nuked my Mythconverg database and started reconfiguring from scratch.  Got everything reconfigured and ran mythfilldatabase.  Same problem.  11 of the 30 channels I have in my lineup  pull in 12 less hours of data then the remaining 19.

I'm almost suspecting at this point that there's something up with my schedulesdirect account, but I've deleted and recreated my lineup a half dozen times and that doesn't seem to fix the issue.  

I'm stumped as to where to go from here :-|

---

### Post by uncle hammy on 2011-04-10
So you're saying that 19 channels get 13 (for example) days worth of data, but 11 only get 12.5?

---

### Post by LowSky on 2011-04-10
Channel data does change sometimes and the broadcasters don't always update at the same time as others.

---

### Post by nickrout on 2011-04-11
why not report this to SD?

---

### Post by uncle hammy on 2011-04-11
Yeah, unless I'm missing a big piece, that's kind of my line of thought.  Though, in all honesty, I probably couldn't be paid to care enough about 12 hours of data on the tail end of 13 days to bother doing anything.  That's assuming there's anything to be done.  In all likelihood, the channels with "missing" data, probably only put out that much for SD to report.

---

### Post by sudanmas on 2011-04-14
The SD tech support guys were actually very helpful and responded within 24 hours to my question.

They confirmed that I was actually getting valid program data for all of my channels in all of the time slots, including the ones that were displaying 'unknown' in the EPG 

I got around it by adding --dd-grab-all to the mythfilldatabase command in the General section of mythtv-setup.

From that point on, all of my channels ran out of data at exactly the same time - 14 days after the last myth fill ran

---

