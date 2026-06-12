---
title: "MythTV Channel Listings Swapped"
date: 2012-09-17
forum: Mythbuntu
---

### Post by Digicrat on 2012-09-17
I've been having some odd issues with my listings.  Specifically, the guide data between two particular channels seems to be [mostly] reversed - and I don't think it's a schedulesdirect issue.  

For a while, I've been having issues with it recording the wrong show.  In some cases, it showed the right description but the wrong program name -- and this is with QAM, which as far as I know isn't giving any in-line program descriptions.

I've verified the the XML TVids and channel names are correct (via MythWeb channel editor, the GUI within mythtv is unusable --but that's another issue for another day).  

As a test, however, I tried swapping the XMLTV IDs between the two channels.  Even after restarting myth and called mythfilldatabase, the listings remain reversed - hence why I don't believe it's a SD issue.  

Is there some sort of cache that needs to be manually cleared to force it to use the correct listing ID?  

Any help would be appreciated,
- David

---

### Post by nickrout on 2012-09-18
Do you have EIT enabled? It may be confusing things.

I don't think Schedules Direct will refresh everything unless you run ```
mythfilldatabase --dd-grab-all
``` so try that.

---

