---
title: "How do you transfer a TV schedule to another channel?"
date: 2012-02-16
forum: Mythbuntu
---

### Post by nhtrader on 2012-02-16
I'm having a problem with the MythTV's Program Guide. It will not show me the TV schedule for 2 out of 11 channels.

So I'm now trying to figure out how to reassign the TV schedule from another channel to the one that is missing. How do I coerce MythTV to show me the TV schedule from channel 7.1 (HD) to channel 7 (SD)?

What database or MythTV feature can I manipulate to accomplish this task?

---

### Post by nickrout on 2012-02-16
> **nhtrader said:**
> I'm having a problem with the MythTV's Program Guide. It will not show me the TV schedule for 2 out of 11 channels.

So I'm now trying to figure out how to reassign the TV schedule from another channel to the one that is missing. How do I coerce MythTV to show me the TV schedule from channel 7.1 (HD) to channel 7 (SD)?

What database or MythTV feature can I manipulate to accomplish this task?

If you are using xmltv I have told you how in the other thread. If you are using eit then the data should match up.

---

### Post by nickrout on 2012-02-17
Saw this today, [http://www.mythtv.org/wiki/Cross-eit.py](http://www.mythtv.org/wiki/Cross-eit.py) - it will export data from one or more channels which you can than import as xmltv data to match to another channel,

---

### Post by nhtrader on 2012-02-21
> **nickrout said:**
> Saw this today, [http://www.mythtv.org/wiki/Cross-eit.py](http://www.mythtv.org/wiki/Cross-eit.py) - it will export data from one or more channels which you can than import as xmltv data to match to another channel,

This looks like an exciting prospect. Thanks. 

I'll get into this soon. It looks like I'll need a few hours to figure out how to implement this.

---

### Post by nhtrader on 2012-10-25
> **nickrout said:**
> [http://www.mythtv.org/wiki/Cross-eit.py](http://www.mythtv.org/wiki/Cross-eit.py) - it will export data from one or more channels which you can than import as xmltv data to match to another channel,

I have two questions:

1. Is cross-eit.py compatible with v0.25?

2. Can't get mythfilldatabase to successfully display the imported XML file from cross-eit.py  Tried the command: mythfilldatabase --refresh +1 -v --file --sourceid 1 --xmlfile stationmissing.xml but this didn't work. By this I mean, no error messages were generated and by all accounts mythfilldatabase worked b/c this was displayed "mythfilldatabase run complete", but nothing changed on when the program schedule is displayed in MythTV FE.

Why isn't the program schedule showing the newly imported programs?

---

### Post by nickrout on 2012-10-25
You'll have to ask the author of cross-eit.py.

However I believe the invocation of mythfilldatabase has changed recently.

---

