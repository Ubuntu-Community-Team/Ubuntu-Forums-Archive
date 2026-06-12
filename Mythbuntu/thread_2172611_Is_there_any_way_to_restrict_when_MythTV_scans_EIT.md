---
title: "Is there any way to restrict when MythTV scans EIT?"
date: 2013-09-05
forum: Mythbuntu
---

### Post by zweiblumen on 2013-09-05
Hi,

I am a Mythbuntu user in the UK, and I have been using the Radio Times xmltv feed for my EPG data for several years. This feed is now deprecated, and its channel list is no longer being updated, so a number of newer channels have no EPG information. A replacement is apparently in the pipeline but I'm not counting on it. In addition, I have recently started recording radio shows, for which the Radio Times ironically has no data.

The EIT data in the UK is very good - 8 days of programming. However, I cannot use it, as whenever I turn on EIT (as I did recently to get the radio listings), I get the dreaded "No lock" error on a daily basis, requiring a backend restart.

I would like to solve this by running overnight EIT scans as a cron job, but I don't know where to begin. Stop the backend - change the EIT configuration - start the backend - Check when the scan is complete - stop the backend - turn off EIT again - restart the backend. Phew! 

Alternatively, if anyone knows of a way to grab the EIT data outside MythTV, convert it to XMLTV and feed it back into MythTV, that *might* be easier. I tried EPG Collector, as suggested [here]("http://www.mythtv.org/wiki/XMLTV"), but it's a .NET programme, and contrary to the wiki article it doesn't seem to work in mono as it uses COM.

In case it's relevant, I'm running the 32-bit version of Mythbuntu 12.04, MythTV version 0.25.

Any advice would be greatly appreciated.

---

