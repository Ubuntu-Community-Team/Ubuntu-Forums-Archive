---
title: "Please explain useonairguide"
date: 2010-07-05
forum: Mythbuntu
---

### Post by iitywygms on 2010-07-05
I see this option in mythweb.  I assume it means I can get guide data ota.
I get all my tv signals ota.
Is this something I could use instead of schedules direct?  How does it work? how accurate is it?
Any other info someone can share?  google search does not come up with much.
Thanks.

---

### Post by jlagrone on 2010-07-05
Some stations broadcast a schedule in a similar manner to closed caption text.  This is the relevant page on the wiki.  [http://www.mythtv.org/wiki/EIT](http://www.mythtv.org/wiki/EIT)

It theoretically can be used to replace schedules direct if you are lucky.  In my experience some stations do not broadcast a schedule or they broadcast something that is too generic for general use (ie only telling you the simpsons is on at 6, but not which episode).  Also the schedules that are broadcast are often limited to a very short time frame, say 8 hours in advance, but it varies from station to station for me.

I don't know if there still is because I switched to cable, but there used to be an option to cross-reference the EIT data with that from schedules direct (or another source) which was very useful for getting last minute changes to the schedules (ie live events that run long would sometimes be reflected in the over the air data)

It's worth giving a try to see what you get if you have a few days with no or non-critical recordings.  I'd setup a new video source in mythbackend with the grabber option of transmitted guide only to test it that way you can just switch the source back if it does not work.

---

### Post by nickrout on 2010-07-05
EIT is a feature of DVB broadcasting. If you have access to Scedules Direct, you probably are not using DVB.

And in any event if you have access to SD, you probably have the best EPG data, EIT would likely be a downgrade.

---

### Post by iitywygms on 2010-07-06
I am going to turn on cross source eit in the backend, and check useonairguide in mythweb.  From my understanding, it will update the guide (last minute) if something changes like a sports show going longer or something like that right?
Sound correct?
Just playing around here so I hope nothing breaks.

---

### Post by jlagrone on 2010-07-06
It sounds right, but don't expect too much I find that it is seemingly random when the updates are provided and you may need a tuner not in use to scan for the scheduling changes (if any exist).  I don't remember if a tuner can scan the channel it is recording or not - it should be able to but whether it actually does or not is another story.

Also if you are using mythwelcome for automatic startup/shutdown, there were problems in the past with the EIT scanner blocking shutdown.  I think this has been fixed, but am not certain.

Just keep a close eye on it for a few days and make a note of what you changed just in case.

---

### Post by iitywygms on 2010-07-06
Already seeing some strange logs.
This is from my backend.

2010-07-05 22:05:43.849 DB Error (change_program):
Query was:
UPDATE program SET starttime = ?,     endtime   = ? WHERE chanid    = ? AND       starttime = ?
Bindings were:
:CHANID=1113, :NEWEND=2010-07-06T00:29:46, :NEWSTART=2010-07-05T23:59:46,
:OLDSTART=2010-07-05T23:30:00
Driver error was [2/1062]:
QMYSQL3: Unable to execute statement
Database error was:
Duplicate entry '1113-2010-07-05 23:59:46-0' for key 'PRIMARY'

Strange stuff already.
Anyone know if the above error is expected?

---

### Post by jlagrone on 2010-07-06
It's not expected.  Just for safeties sake, I would disable it as the potential gains are arguably negligible.  If you're having consistent problems with programs running long it would probably be safer to just tell the recording to go for an extra 30 min (or whatever is reasonable) past the end of the recording

---

### Post by nickrout on 2010-07-06
> **iitywygms said:**
> I am going to turn on cross source eit in the backend, and check useonairguide in mythweb.  From my understanding, it will update the guide (last minute) if something changes like a sports show going longer or something like that right?
Sound correct?
Just playing around here so I hope nothing breaks.

read my message above. No it will not do as you think afaik.

---

### Post by iitywygms on 2010-07-07
I decided to turn off the EIT/useonairguide stuff.
Yes, it did update some of the info in the guide.  Like episode numbers and stuff.  It also changed some of the lesser known channels info to general information, like DTV channel instead of what it was actually showing.
Schedules direct is the way to go imo.
The above error also disappeared when I shut every thing off.

---

