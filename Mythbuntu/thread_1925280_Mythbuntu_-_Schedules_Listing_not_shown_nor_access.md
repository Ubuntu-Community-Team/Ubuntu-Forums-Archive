---
title: "Mythbuntu - Schedules/ Listing not shown nor accessible on Frontend or MythTv Player"
date: 2012-02-14
forum: Mythbuntu
---

### Post by sparkrov on 2012-02-14
I wanted to post this in case anyone else is having a similar issue. After performing a channel scan update on my Mythtv backend, i noticed my frontend would not populate channel listing data nor display live tv. The MythTV Frontend returned the error "no capture cards defined." Also, when trying to connect to my backend from a Windows frontend via MythTv Player, the live channel listings would not populate (channel list was blank) although i noticed i was connected to the SQL database since past recordings were shown. It turns out several scanned channels in the lineup were not populating "over the air" and the *broken* EIT database was apparently preventing remote frontend access to any channels. After i removed these problematic channels from within the backend-setup channel editor, everything worked again! 
 
Hope this helps. Perhaps someone can explain better the cause for this?

-sparkrov

---

