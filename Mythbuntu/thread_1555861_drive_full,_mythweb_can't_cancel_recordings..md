---
title: "drive full, mythweb can't cancel recordings."
date: 2010-08-18
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-08-18
I didn't clean my mythbox out last weekend, so my drive just got filled to the brim. I scheduled 3 shows in mythweb to record yesterday and only one recorded and is stuck in transcoding commercial flagging, the other two say they are currently recording but it's way past the time when they were scheduled to record. Backend reports no tuners in use.  I click on edit for the two shows but nothing loads, so can't cancel them.

Wondering did my mythbox record them and they are in queue for commerical detection? or if the missed shows will cancel out?

---

### Post by winewood on 2010-08-19
I use Mythweb for EVERYTHING I can to make it easy on myself.
 
It will tell you the status of all recordings and what has been tagged/etc.  I would get this tool working to report to you what is happening.
 
If you manually deleted shows via command line, then im assuming (sorry im guessing) that a mythfill database may be in order to requery what shows you have removed from the database of shows.  If you programs are not auto-expiring, this may account for a full hard drive.  
 
The default setting is for all scheduled recordings to be eligible for auto-expiration; this can be changed in the Settings->TV Settings->General page by manipulating the "Auto Expire Default" checkbox.  [http://www.mythtv.org/docs/mythtv-HOWTO-12.html](http://www.mythtv.org/docs/mythtv-HOWTO-12.html)
 
I would make sure that the "Auto Expire Default" is checked.
 
If you want to give your hard drive a rest, when you stop watching your front end, back out to the menu, or it will record all live tv.  This is the fastest way to fill up a hard drive with useless data when you are not watching it.

---

