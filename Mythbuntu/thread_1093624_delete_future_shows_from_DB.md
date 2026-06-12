---
title: "delete future shows from DB"
date: 2009-03-11
forum: Mythbuntu
---

### Post by reformy on 2009-03-11
hi
For some weird reason, in one of the updates from EPG some of the shows were inserted to the DB with day and month switched (3/1/09 -> 1/3/09). Now i have a lot of shows months ahead that are not valid. How can i delete it?

thanks

---

### Post by newlinux on 2009-03-11
you can try mythfilldatabase --refresh-all if your epg source has corrected its information.

---

