---
title: "One channel shows only &quot;DTV program&quot;"
date: 2011-08-01
forum: Mythbuntu
---

### Post by mathog on 2011-08-01
Channel 28.1 (KCET, Los Angeles, a PBS station) almost always shows just "DTV program" in the EPG.  Most of the other channels, including channels 28.2,28.3,and 28.4 all have actual programs listed.  The TV, used directly, shows program info on 28.1.  On rare occasions we will have a day when we see programs listed on 28.1.  

I tried running a repair script on the SQL database, which didn't help.  Then nuked all the channels, rescanned, recreated them.  We had a listing on 28.1 for half a day after that, then back to "DTV".

Anybody know what might be causing this?  Myth version 0.21, guide information from Schedules Direct.

Thanks.

---

### Post by agamotto on 2011-08-01
Generally, it means the station isn't supplying data to the SD service for the 'tv guide.'  There is an option in the backend setup for the ATSC card to add the EPG data from the station.  This usually works in situations like yours.

---

### Post by mathog on 2011-08-05
> **agamotto said:**
> Generally, it means the station isn't supplying data to the SD service for the 'tv guide.'  There is an option in the backend setup for the ATSC card to add the EPG data from the station.  This usually works in situations like yours.

I did a schedules direct data dump and the information for 28.1 looked more or less like it did for 28.2.  

Can you be a little more specific on where that "add EPG data" option is located?

Thanks.

---

### Post by agamotto on 2011-08-05
It should be in the 'backend setup,' where you first tell the system what cards you have.  Before you do the scanning for channels on the digital card, there should be a list of three boxes on the left you want to turn on the box that deals with filling EPG with station data, and turning off the one that says something about using the tuner all the time.  Sorry I can't be more specific, but I am travelling and nowhere near my Mythbox.

---

### Post by alldunn on 2011-10-06
I am having the same issue with 2 of my DTV channels showing "DTV Program".  I have verified that the Schedules Direct data does in fact contain valid data for those channels.  The weird thing about my situation is that it usually shows valid data on the guide after 12 or so hours of a Schedules Direct update.  For instance:  My guide data was updated just after 8:00am this morning and the guide shows "DTV Program" up until midnight tonight after which it reverts to the correct listings on both channels.  I have unchecked the EIT data download option as suggested [here]("http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295") to no avail.
I am curious if the problem here with the OP was resolved and if so, how?  If not, I would certainly appreciate any assistance in troubleshooting.

---

