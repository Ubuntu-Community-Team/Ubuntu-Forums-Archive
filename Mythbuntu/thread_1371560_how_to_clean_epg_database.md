---
title: "how to clean epg database?"
date: 2010-01-03
forum: Mythbuntu
---

### Post by orduek on 2010-01-03
Hi,
I'm using Mythbuntu 9.04 and an external epg grabber (megaepg).
I use a cron job to updater the epg using this command to update the database:
```
mythfilldatabase <sourceid> --file filename.xml 
```
everything works out great but now one of the channels has some wrong information in it. when looking at the xml file I see different information. But - when I try to update it using the command stated above, nothing is changed.
Is there a way to reset the epg data or, otherwise, to tell mythfilldatabase to override the existing data?

---

### Post by azmyth on 2010-01-03
mythfilldatabase --refresh-all

---

### Post by orduek on 2010-01-04
it didn't help :(
using refresh-all and still - the old data is in that channel.
can I clear the database and fill it again?

---

