---
title: "Mythweb and Frontend program guides are not in sync"
date: 2009-11-21
forum: Mythbuntu
---

### Post by mars76 on 2009-11-21
Hi All,

 I ran the mythfillbackend and now when i go to mythweb i see the program guide info proerly.

 How ever when i try toschedule a recording using mythfrontend i don't see anything in program guide.

 I tried scheduling recordings from mythweb and the recorded programs are not showing up in the upcoming recordings in mythweb and the tuner is not recording any of those schedules.

 I have 2.6.31-15 kernel running.
The version of myth i am running is : 2.0.22.0-fixes-22864

Thanks
mars

---

### Post by mars76 on 2009-11-21
After going through the mythconverge database it seems that i have duplicate entries for every channel in the channel table.

Earlier i used the trail version of SD to populate the channels. I ended up having two entries for every channel in the chnnael table. Some how mythfrontend only picking up the channel entered by SD , where as Mythweb shows both the channels.

Now i used the mc2xml to load the channel guide. The only difference i can make out between the rows entered by SD and mc2xml is the value for the column xmltvid.

I am not sure what will happen if i truncate the channel table and rerun the mc2xml script..

Does any one encountered this problem.

thaks
mars


> **mars76 said:**
> Hi All,

 I ran the mythfillbackend and now when i go to mythweb i see the program guide info proerly.

 How ever when i try toschedule a recording using mythfrontend i don't see anything in program guide.

 I tried scheduling recordings from mythweb and the recorded programs are not showing up in the upcoming recordings in mythweb and the tuner is not recording any of those schedules.

 I have 2.6.31-15 kernel running.
The version of myth i am running is : 2.0.22.0-fixes-22864

Thanks
mars

---

### Post by nickrout on 2009-11-21
> **mars76 said:**
> After going through the mythconverge database it seems that i have duplicate entries for every channel in the channel table.

Earlier i used the trail version of SD to populate the channels. I ended up having two entries for every channel in the chnnael table. Some how mythfrontend only picking up the channel entered by SD , where as Mythweb shows both the channels.

Now i used the mc2xml to load the channel guide. The only difference i can make out between the rows entered by SD and mc2xml is the value for the column xmltvid.

I am not sure what will happen if i truncate the channel table and rerun the mc2xml script..

Does any one encountered this problem.

thaks
mars

I usually find the best way of handling this sort of crap is through the channel settings page in mythweb (settings button at the top, choose TV on the left hand menu, channel info tab.

---

### Post by mars76 on 2009-11-21
Hi,

  I found a crude way of fixing the issues..

  I updated the "chanid" in program table with the chanid of SD from channel table and now i can schedule recordings.

  I am wondering why mythfrontend is always looking for chanid of SD inserted channels.

 Now i am running a SQL script in my mc2xml mythfilldatabase script.

mars..

---

