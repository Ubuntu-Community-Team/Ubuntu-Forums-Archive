---
title: "No TV Listings / Guide Data"
date: 2011-01-31
forum: Mythbuntu
---

### Post by gladbird on 2011-01-31
I just installed Ubuntu 10.10 and added Mythbuntu on top of it. Everything but the listings seems to be working fine.

I've got a SchedulesDirect account and mythfilldatabase appears to sucessfully complete but, still no listings. Here's the end of mythfilldatabase

```
2011-01-31 16:13:57.985 Grab complete.  Actual data from Sun Feb 13 07:00:00 201        1 to Mon Feb 14 07:00:00 2011 (UTC)
2011-01-31 16:13:57.985 Main temp tables populated.
2011-01-31 16:13:57.990 Did not find any new program data.
2011-01-31 16:13:57.990 Failed to fetch some program info
2011-01-31 16:13:57.991 mythfilldatabase: Failed to fetch some program info
2011-01-31 16:13:57.991 Adjusting program database end times.
2011-01-31 16:13:57.991     0 replacements made
2011-01-31 16:13:57.992 mythfilldatabase: Listings Download Finished
2011-01-31 16:13:57.992 Marking generic episodes.
2011-01-31 16:13:57.992     Found 0
2011-01-31 16:13:57.992 Fudging non-unique programids with multiple parts.
2011-01-31 16:13:57.993     Found 0
2011-01-31 16:13:57.993 Marking repeats.
2011-01-31 16:13:57.994     Found 0
2011-01-31 16:13:57.994 Unmarking new episode rebroadcast repeats.
2011-01-31 16:13:57.994     Found 0
2011-01-31 16:13:57.994 Marking episode first showings.
2011-01-31 16:13:57.995     Found 0
2011-01-31 16:13:57.995 Marking episode last showings.
2011-01-31 16:13:57.995     Found 0
2011-01-31 16:13:57.996 Grabbing next suggested grabbing time
2011-01-31 16:13:58.516 DataDirect: BlockedTime is: 2011-01-31T16:13:58
2011-01-31 16:13:58.516 DataDirect: NextSuggestedTime is: 2011-02-01T16:53:50
2011-01-31 16:13:58.518
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2011-01-31 16:13:58.521 MythContext: Connecting to backend server: 127.0.0.1:654        3 (try 1 of 1)
2011-01-31 16:13:58.522 Using protocol version 23056
2011-01-31 16:13:58.752 Received a remote 'Clear Cache' request
2011-01-31 16:13:59.752 mythfilldatabase run complete.
2011-01-31 16:13:59.752 DataDirect: Deleting temporary files
```

I did a little looking on SchedulesDirect's forum and saw a suggestion to run ```
tv_grab_na_dd --dd-data dd.xml --configure
``` then follow the prompts to see if it would download the listings. Indeed, the resulting dd.xml file contains all of the listings.

---

### Post by LowSky on 2011-01-31
did you do a channel scan?
Did you properly chose your channel data?
Are you use QAM or OTA?

---

### Post by gladbird on 2011-01-31
> **LowSky said:**
> did you do a channel scan?
Did you properly chose your channel data?
Are you use QAM or OTA?

Yes. Mythweb shows each channel, just no listings.

Yes. Otherwise it wouldn't connect to Schedules Direct.

OTA.Does it really matter which though? SD is getting the info, myth just doesn't seem to be inputting it.

---

### Post by LowSky on 2011-01-31
Actually If you pick the wrong data it can screw up channel info.

Have you checked channel listings on te frontend to make sure there are not data for a few hours from now. Sometimes data isn't available for the first 4-5 hours.

---

### Post by gladbird on 2011-01-31
The channel info is right...hmm, I can't figure it.

Yeah, I checked the channel listings in the future, (I remember having to do that about a year and a half ago when I was using Mythtv), still nothing.

I just reinstalled Ubuntu and re-ran the setup. I figured it was worth a shot since I hadn't done anything with the box and it's just a backend/media server. It's working now. Odd. Thanks for checking in. ):P

---

### Post by nickrout on 2011-02-03
In mythweb go to settings|TV|Channel Info and make sure it is all OK.

---

### Post by tpmikey on 2011-02-03
I am having same problem. When i run mythfilldatabase i get a bunch of errors. On my mythtvweb when i click on listings it gives a fatal error. 

SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]


The channels are showing up when i watch tv, but no luck with the schedule. Anyone have any ideas on whats the problem.

---

### Post by tpmikey on 2011-02-03
I was able to fix this same problem by running this perl script.

```
$ perl /usr/share/doc/mythtv-backend/contrib/maintenance/[optimize_mythdb.pl]("http://optimize_mythdb.pl/")

```

and then ran mythfilldatabase again.

---

