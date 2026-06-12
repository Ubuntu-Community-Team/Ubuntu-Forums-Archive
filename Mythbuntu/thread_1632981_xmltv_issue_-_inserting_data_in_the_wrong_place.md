---
title: "xmltv issue - inserting data in the wrong place"
date: 2010-11-28
forum: Mythbuntu
---

### Post by nunrgguy on 2010-11-28
Newly setup backend.
xmltv configured
Channels scanned and numbered
xmltv ids added to channels

.conf file renamed and put in correct location


mythfilldatabase run successfully

BUT THEN

xmltv ids removed by the script from my scanned channels and channels now set to on air guide

script has added channels to channel list with xmltv ids but with no corresponding tv signal - and listings data is attached to these channels, not my actual channels

What else needs to be configured for this to work correctly? My first install on 6(ish) used to do something like this and it's so long ago I can't now remember, or find, the fix.

MTIA

---

### Post by Chunk of Earth on 2010-11-29
I believe that will happen if your call signs don't match the ones in the SchedulesDirect database.

---

### Post by nunrgguy on 2010-11-29
Ah, OK I'll give that a go. Thanks :) 

It's the RT grabber I'm using but it should be the same setup. 

BTW for anyone else reading no guides I've seen re setting up xmltv mention editing the scanned call signs, they only mention inputting the xmltv ids so I'll give it a go and report back.

---

### Post by nunrgguy on 2010-11-30
Fathomed it - it wasn't that.
I needed to run 

mythfilldatabase --manual

first

Now all good.
One to remember when I have to set it up another couple of years in the future :)

---

