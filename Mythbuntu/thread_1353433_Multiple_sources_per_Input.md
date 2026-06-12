---
title: "Multiple sources per Input?"
date: 2009-12-12
forum: Mythbuntu
---

### Post by B34N on 2009-12-12
I have two tuner cards on my backend.  Both receive their signal from Comcast.  From Comcast I receive SD Clear QAM signals and HD local channels.  There isn't a single lineup on Schedules Direct that has both the SD and HD channels so I added two lineups.  (was this the right thing to do?)  I can set it up so that both cards can see the SD and HD channels but in order to get program information for the SD and HD, I setup two sources (one SD and one HD) and assigned one source to each card.  I would have preferred to assign the same two sources to each card.  Is that possible?  I feel like I'm doing something wrong.  Any guidance would be greatly appreciated.

FYI: I used scte65scan to map the SD Comcast channels so that I could get program info from Schedules Direct.  Worked like a charm.  If you are using Comcast and you are having problems mapping, try this program.

Thank you!

---

### Post by klc5555 on 2009-12-12
> **st8ofmi9d said:**
> I have two tuner cards on my backend.  Both receive their signal from Comcast.  From Comcast I receive SD Clear QAM signals and HD local channels.  There isn't a single lineup on Schedules Direct that has both the SD and HD channels so I added two lineups.  (was this the right thing to do?)  I can set it up so that both cards can see the SD and HD channels but in order to get program information for the SD and HD, I setup two sources (one SD and one HD) and assigned one source to each card.  I would have preferred to assign the same two sources to each card.  Is that possible?  I feel like I'm doing something wrong.  Any guidance would be greatly appreciated.

FYI: I used scte65scan to map the SD Comcast channels so that I could get program info from Schedules Direct.  Worked like a charm.  If you are using Comcast and you are having problems mapping, try this program.

Thank you!

You can mix-n-match pieces from various Schedules Direct "lineups" into one single input source, as necessary. I also use Comcast. I just dumped all the clear QAM SDs and the HD locals from various Schedules Direct "lineups" into one input source: "Digital", used by four QAM tuner cards. The clear QAM SD locals and HD locals broadcast the exact same schedule, and use the same XMLTV ID numbers. They don't need to be differentiated at the Schedules Direct level; they should be differentiated in Channel Editor by your assigning a slightly different callsign to them, e.g. (in my case) "WBZ-SD" and "WBZ-HD" and giving them a different virtual channel number that may (or may not) closely resemble Comcast's, e.g. "4" for SD and "804" for the HD. That's all Mythtv needs to keep them separated for scheduling purposes. 

If your SD locals and HD locals broadcast different content schedules, they will have different XMLTV ID numbers. So again they can be dumped into one single "Digital" source used by all your QAM tuners.

The clear QAM non-locals (like TNT or History, etc.) are also dumped into this one source. Heck, for a while Deutsche Welle was also clear QAM here on Comcast, but Schedules Direct only carried that XMLTV ID number under one of the Fios lineups; so that one Fios channel on a Fios lineup also got dumped into my one "Digital" input source with all the Comcast channels. It doesn't particularly matter to Schedules Direct or mythfilldatabase.

The non-locals which are not clear QAM but encrypted, and go through a STB or DTA  that in turn has to be tuned with an IR Blaster or similar will need to be handled separately, one individual source per tuner.

Also, if one tuner card could not, say, handle HD content or maybe could not successfully tune some channels the other cards could, then this different card would need to be placed on its own special input source.

---

### Post by B34N on 2009-12-13
> **klc5555 said:**
> You can mix-n-match pieces from various Schedules Direct "lineups" into one single input source, as necessary. I also use Comcast. I just dumped all the clear QAM SDs and the HD locals from various Schedules Direct "lineups" into one input source: "Digital", used by four QAM tuner cards. The clear QAM SD locals and HD locals broadcast the exact same schedule, and use the same XMLTV ID numbers. They don't need to be differentiated at the Schedules Direct level; they should be differentiated in Channel Editor by your assigning a slightly different callsign to them, e.g. (in my case) "WBZ-SD" and "WBZ-HD" and giving them a different virtual channel number that may (or may not) closely resemble Comcast's, e.g. "4" for SD and "804" for the HD. That's all Mythtv needs to keep them separated for scheduling purposes. 

Thank you for the response.  The channels don't have the same XMLTV ID.  As an example, KYW-SD is set to 853 and the "use on air guide XMLTV_ID" is not checked where as KYW-HD is set to 611 with the use on air option checked.  Are you saying that since the channels have the same content that should uncheck the use on air guide for the HD channel and change the ID to the same ID as the SD channel?

Is there an easy way to dump all of the XMLTV IDs to a file so that I can compare them?

---

### Post by B34N on 2009-12-13
Well I went through each and every channel.  I removed the check box from "use on air guide XMLTV_ID" for all of the channels.  Some already had the IDs for the others I took my best guess.  i was able to mouse over in the edit screen on SD to see what the ID should have been.  It's not perfect yet but the schedule should be pretty accurate.  I still have a lot of unknowns for the sub-channels but I don't think they really carry much content so I'm not concerned.

Is there a quick and easy way to backup and restore all the manual work that I've done to map the channels and download their icons?

---

