---
title: "Mythfilldatase and xmltv"
date: 2008-02-22
forum: Mythbuntu
---

### Post by axelsvag on 2008-02-22
I have a small but in the long end annoying problem with mythfilldatabase. I use the xmltv combiner with swedish and danish schedules. The setup works perfectly but the update has a life of its own. If I just accept the automatic mythfilldabase the mythtv runs mythfilldatabase every night, only the danish channelinfo get updated. And just the next two days. The swedish channels does not get updated at all. 
If I manually type ```
mythfilldatabase 
``` in a terminal the swedish channels get uppdated for 14 days as it supposed to and the danish channels get two days of schedule. If use the command ```
mythfilldatabase --refresh-all
```. The swedish channels get updated for 14 days as it supposed to and the danish channels get updated for 6 days as it supposed to. 
My question is now, how do I get the mythtv automatic command to make a complete update as I can when I use the ```
mythfilldatabase --refresh-all
``` ?

---

### Post by foxbuntu on 2008-02-22
In the frontend, Setup > General > 7th Page (last one) there is a line to add options to run mythfilldatabase. This should do what you need it to.

---

### Post by axelsvag on 2008-02-28
OK I tried to put the refresh all command in the menu but it does not seem to be any difference. It seems like mythtv do send the mythfilldatabase command but don´t get any data. If I write the command manually everything looks good. I know I have been reading about an issue with different permissions but I don´t understand if this have anything to do with my problem.

---

