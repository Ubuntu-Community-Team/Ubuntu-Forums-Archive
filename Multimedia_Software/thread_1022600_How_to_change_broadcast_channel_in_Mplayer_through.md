---
title: "How to change broadcast channel in Mplayer through terminal command"
date: 2008-12-27
forum: Multimedia Software
---

### Post by sofasurfer on 2008-12-27
I can watch tv with Mplayer by using this command... mplayer dvb://.

I can change channels by hitting the 'k' or 'h' key.

Here is my Mplayer channels.conf.atsc list...

```

WDCQ-DT·:479028615:8VSB:49:52:3
WDCQ-DT·:479028615:8VSB:65:68:4
WDCQ-DT·:479028615:8VSB:81:84:5
WDCQ-DT·:479028615:8VSB:97:100:6
WNEM Digital Television:521028615:8VSB:49:52:3
WNEM HDTV:521028615:8VSB:65:68:4
WFUM HD:557028615:8VSB:49:52:1
WFUM SD:557028615:8VSB:65:68:2
WEYI High Def:569028615:8VSB:65:68:4
WEYI Digital Television:569028615:8VSB:49:52:3
WJRT-HD·:605028615:8VSB:49:52:1
WJRT-S1:605028615:8VSB:65:68:2
WJRT-S2:605028615:8VSB:81:84:3
WAQP High Definition:677028615:8VSB:49:52:3
WAQP Standard Definition:677028615:8VSB:65:68:4

```

Suppose I want to start Mplayer on a specific channel, such as 'WEYI High Def'. I see this line in the list above 'WEYI High Def:569028615:8VSB:65:68:4'. 

Which information do I add to 'mplayer dvb://' in order to start mplayer on WEYI?

I tried differant combinations but I always end up with this... 
"Failed to open dvb://677028615.
Exiting... (End of file)"

---

### Post by itix on 2008-12-29
Doesn't mplayer have a manual entry? Try *man mplayer* and see if it gives you any info.

I can't check for you since I don't have mplayer installed on my system.

---

