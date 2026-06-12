---
title: "Loading channels from multiple sources"
date: 2009-11-28
forum: Mythbuntu
---

### Post by mars76 on 2009-11-28
Hi All,

   I ran Scheduled Direct initially which inserted the data into channel and program tables in MySQL DB.

  Later i used an XML Grabber to load the channel listings. Now the channel table has listings from both.

  When i go to mythtv frontend i only see the channels which were loaded using SchedulesDirect but not from an XML Grabber.

  If i go to mythweb i see all the channels ( from SD and XML Grabber). 

  I am not sure why mythtv is always using the chanid from schedulesdirect ( i mean the chanid number created in channel table when the channel was initially inserted into this table). Where is this info stored/configured ??

  I want to use the XML Grabber. Now i need to update the chanid (replace the ones form XML Grabber with the ones from SD in the program table in order for them to show up in Myth frontend program guide)

thanks
mars

---

