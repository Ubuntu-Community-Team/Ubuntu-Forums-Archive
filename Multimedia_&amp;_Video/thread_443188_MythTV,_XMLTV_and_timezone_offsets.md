---
title: "MythTV, XMLTV and timezone offsets"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by axcairns on 2007-05-14
Hey all,

I'm having trouble getting guide data via XMLTV on my Feisty MythTV install. No matter what I try the data is out by 8 hours which happens to be the timezone offset from UTC for Perth, Australia.

I have played around with the 'Time offset for XMLTV listings' setting in the General section of the backend setup. Neither 'Auto' or '+0800' seem to make any difference. Times still get inserted into the database as UTC, meaning that a show on at 8pm tonight Perth time is inserted with noon as the start time. 

Any ideas?

Thanks,


Allan

---

