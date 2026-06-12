---
title: "Mythfilldatabase not updating schedule information"
date: 2013-10-09
forum: Mythbuntu
---

### Post by cedyathome on 2013-10-09
After I upgraded - using the Mythbuntu Control Center - from 0.25 to 0.26, I started getting this message & I notice that the schedule information is not being updated.

I see this message when I look at mythweb or the system status in the front end.

"mythfilldatabase ran, but did not insert any new data into the Guide for 1 of 1 sources. This can indicate a potential grabber failure."

When I run mythfilldatabase - even with the --dd-grab-all switch, I still have the same problem. It seems to download the information from schedulesdirect, then connects to the backend to insert the next scheduled run. I don't see any error messages.


Any ideas?
Where do I start to debug?

---

### Post by zetoune2 on 2013-10-09
Same problem over here except upgrading process. I did a fresh install with the latest ISO then I upgraded to 0.27. 
First mythfilldatabase did work, all others did not insert any data in the DB. I get the same message as cedyathome. "mythfilldatabase run ... failure"

---

### Post by cedyathome on 2013-10-09
This thread is the nearest to my issue that I've found. (Don't know how I missed it earlier)
[http://ubuntuforums.org/showthread.php?t=2153391&highlight=mythfilldatabase](http://ubuntuforums.org/showthread.php?t=2153391&highlight=mythfilldatabase)

I did a reboot and now, while I still see the error, I have 14 days of schedule data. Previously, it was only 11 days. Let's see if it runs without error tomorrow or at least keeps the data updated.

---

### Post by mtbdrew on 2013-10-24
I've done several resets and power cycles none of which have helped.

---

### Post by ceenvee703 on 2013-10-29
I was having a similar problem with mythfilldatabase not running automatically. Running it manually in a terminal window always worked. In order to troubleshoot the problem, I added a line via mythtv-setup to log errors... but I never had to check the log, because (or coincidentally?) once I added the line to log errors, mythfilldatabase started running automatically with no errors.

---

### Post by mtbdrew on 2013-10-31
> **ceenvee703 said:**
> I was having a similar problem with mythfilldatabase not running automatically. Running it manually in a terminal window always worked. In order to troubleshoot the problem, I added a line via mythtv-setup to log errors... but I never had to check the log, because (or coincidentally?) once I added the line to log errors, mythfilldatabase started running automatically with no errors.


What line did you add and where did you added it?

---

### Post by dave65 on 2013-12-01
I have had that error pop up when I ran mythfilldatabase and the grabber got data, but there was no NEW data...that is, there were no changes in the guide data. mythfilldatabase threw the error, but nothing actually failed...but programmatically it looked like something went wrong. In fact it was just an unnecessary guide pull.

Could that be what you are seeing?

--Dave

---

