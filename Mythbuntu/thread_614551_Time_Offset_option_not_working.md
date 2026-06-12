---
title: "Time Offset option not working"
date: 2007-11-16
forum: Mythbuntu
---

### Post by prion on 2007-11-16
Is there a trick to using the time offset option for XMLTV listings in MythTV?  My listings at eight hours slow, but changing the time offset isn't affecting the scheduling guide in the fronted.  Has anyone used this before?  Is there a step I'm missing?  Thanks.

---

### Post by stevetv on 2007-11-16
what settings have you tried in the backend setup?

according to the wiki, the time offset for xmltv needs to be "none" if ur using sd.

i dont use sd.. i live in australia.. but whenever ive used "none" ive had problems.  so i use "auto".. maybe try that if u havent already.

---

### Post by prion on 2007-11-16
I'm not using SD, I am generating my own XML files with a scrapper I wrote.  That's something else, the time values in the XML file are right, but MythTV sets it eight hours slow.  I've tried a bunch of offset values, and none have any effect on the listing times in the mythTV frontend scheduling.  Is there a way to make the new listings overwrite the old ones?  Right now I'm using:

sudo mythfilldatabase --file 1 -1 listings.xml

---

