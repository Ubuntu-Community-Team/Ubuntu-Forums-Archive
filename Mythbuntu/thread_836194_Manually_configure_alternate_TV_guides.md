---
title: "Manually configure alternate TV guides?"
date: 2008-06-21
forum: Mythbuntu
---

### Post by sr_guy on 2008-06-21
I found a few guides online that are pretty detailed and well laid out:

URL:[http://tv.msn.com/tv/guide/](http://tv.msn.com/tv/guide/)

URL:[http://tv.yahoo.com/listings](http://tv.yahoo.com/listings)

Is there a way to manually configure mythtv to pull guide data from these sites?

---

### Post by DrewMac on 2008-06-21
I don't think so.. the data is not made public and easy to grab. Unless you get get myth to screenscrape somehow, I don't think it is possible.

---

### Post by sr_guy on 2008-06-21
what about using a XMLTV gui to add guide content to myth's database?

---

### Post by DrewMac on 2008-06-21
But that will always have to be done manually; I didn't think you would always want to have to enter the guide data. Sorry for the misunderstanding.

---

### Post by DutchLoki on 2008-06-21
Should be no problem. Here in the netherlands we extract data from existing sites and format it into xmltv format to use with mythTV, which works great. 

The only downside is that sometimes the page structure changes, then you need to make minor changes to your grabber module. grabbers are updated regulary here, so you can beside scheduling a daily import also schedule a daily grabber update.

You can find alot of info about xmltv and importing it into mythTV. Only the grabber part needs some thought.

---

