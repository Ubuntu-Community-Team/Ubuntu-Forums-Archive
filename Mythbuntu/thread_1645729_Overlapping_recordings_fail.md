---
title: "Overlapping recordings fail"
date: 2010-12-14
forum: Mythbuntu
---

### Post by gdselzer on 2010-12-14
I have dual Hauppauge 850 tuners recording OTA.  I set most of my shows to start 2 minutes early and end 2 minutes late.  So two shows that are back to back end up overlapping and get picked up by different tuners.  I find that sometimes the second show will fail and other times it won't.  But if I try to do 3 shows in a row, the 3rd ALWAYS fails.

My wife is a little miffed at having missed the second Glee and I miss being able to watch The Office (Community, 30 Rock, Office.)  Much thanks if anyone can help me figure out how to troubleshoot this.

---

### Post by ian dobson on 2010-12-15
Hi,

When the recording fails was do you see in the backend log file (/var/log/mythtvbackend.log)?

Regards
Ian Dobson

---

### Post by gdselzer on 2010-12-15
Here are the relevant time frames from the log.  The first two shows recorded fine.  The third failed (shows up in the Watch List but there is no file.)

Thanks

---

### Post by gdselzer on 2010-12-24
Bump.  Anyone?

---

### Post by ian dobson on 2010-12-24
Hi,

Sorry there isn't anything interesting in the log files, it just says it can find the recording.

I've tried looking for a spec for the dual Hauppauge 850 but can't find anything. Could it be that the second tuner doesn't work?

Regards
Ian Dobson

---

### Post by gdselzer on 2010-12-24
I guess that depends on what you mean by "work."  As you can see in the logs, the first two shows are recorded by different tuners, and each of those shows turned out just fine.  So both tuners work once.  The problem arises when the tuner that recorded the first show (and has not been recording for 58 mins) must turn back on to record the third show.  I get a listing for the show in "watch recordings" but there is no file.  So in that way, it doesn't work.

As you point out, there is nothing fishy in the backend log.  As far as I can tell, this only happens when I go from Tuner 1 to Tuner 2 back to Tuner 1 (also seems to be Tuner 2 to 1 to 2 again.)

Any other thoughts on how to debug?

Thanks

---

### Post by ian dobson on 2010-12-24
Hi,

mythbackend support extra logging, maybe there's an option for extra logging information for tuning. 

```
 mythbackend --verbose help
Verbose debug levels.
 Accepts any combination (separated by comma) of:

 "  all          "  -  ALL available debug output
 "  most         "  -  Most debug (nodatabase,notimestamp,noextra)
 "  important    "  -  Errors or other very important messages
 "  general      "  -  General info
 "  record       "  -  Recording related messages
 "  playback     "  -  Playback related messages
 "  channel      "  -  Channel related messages
 "  osd          "  -  On-Screen Display related messages
 "  file         "  -  File and AutoExpire related messages
 "  schedule     "  -  Scheduling related messages
 "  network      "  -  Network protocol related messages
 "  commflag     "  -  Commercial Flagging related messages
 "  audio        "  -  Audio related messages
 "  libav        "  -  Enables libav debugging
 "  jobqueue     "  -  JobQueue related messages
 "  siparser     "  -  Siparser related messages
 "  eit          "  -  EIT related messages
 "  vbi          "  -  VBI related messages
 "  database     "  -  Display all SQL commands executed
 "  dsmcc        "  -  DSMCC carousel related messages
 "  mheg         "  -  MHEG debugging messages
 "  upnp         "  -  upnp debugging messages
 "  socket       "  -  socket debugging messages
 "  xmltv        "  -  xmltv output and related messages
 "  dvbcam       "  -  DVB CAM debugging messages
 "  media        "  -  Media Manager debugging messages
 "  idle         "  -  System idle messages
 "  channelscan  "  -  Channel Scanning messages
 "  extra        "  -  More detailed messages in selected levels
 "  timestamp    "  -  Conditional data driven messages
 "  none         "  -  NO debug output
```

so maybe -v record,extra

The logs could be quite large but atleast your'll have more info. Mythtv uses information from the sql database to display a list of programs recorded and only attempts to access the recording when you try and play it.

The only thing I can think of is maybe the tuning delay is too short. I've seen afew 0 byte recordings on my system (with my IP recorder) when it took too long to tune to the correct channel.

Regards
Ian Dobson

---

### Post by LowSky on 2010-12-24
Its a digital tuner, they can handle multiple feeds at once. go into the backend, choose capture cards, go down to the Recording options button, from there change max recordings to 2 or 3. do this for both 850 tuners.

Digital tuners can record mulitple shows at once from one feed as long as the shows are on the same encryption channel. So maybe this can help

---

### Post by gdselzer on 2011-03-21
I upgraded to Mythbuntu 10.04 and this issue no longer appears.  Go figure!  Thanks to all that lent a hand.

---

