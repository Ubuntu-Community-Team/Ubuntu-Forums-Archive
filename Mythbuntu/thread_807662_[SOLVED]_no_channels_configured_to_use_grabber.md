---
title: "[SOLVED] no channels configured to use grabber"
date: 2008-05-26
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2008-05-26
I have recently upgraded to a hdhomerun, and am having a difficult time adding the new channel lineup.  Mythfilldatabase yields:

```

 mythfilldatabase --do-channel-updates
2008-05-26 01:07:16.794 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-26 01:07:16.796 Empty LocalHostName.
2008-05-26 01:07:16.796 Using localhost value of server
2008-05-26 01:07:16.813 New DB connection, total: 1
2008-05-26 01:07:16.820 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-26 01:07:16.824 Closing DB connection named 'DBManager0'
2008-05-26 01:07:16.826 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-26 01:07:16.838 mythfilldatabase: Listings Download Started
2008-05-26 01:07:16.840 New DB connection, total: 2
2008-05-26 01:07:16.842 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-26 01:07:16.844 Updating source #1 (Time Warner) with grabber schedulesdirect1
2008-05-26 01:07:16.845 No channels are configured to use grabber.
2008-05-26 01:07:16.845 

...etc...

```

My account with schedulesdirect is current, and I am in North America, so there should not be any issues with xmltv.  Any suggestions?  Thanks

---

### Post by tgm4883 on 2008-05-26
Did you add the tuner in mythtv setup?  Did you also have a lineup for your HDhomerun (step 3) and did you "attach" that lineup to the tuner (step 4)

---

### Post by a_posse_ad_esse on 2008-05-26
Yes to both.  The odd thing is that the grabber gets the lineup description from schedulesdirect, but not any of the channel numbers.

---

### Post by a_posse_ad_esse on 2008-05-27
I just tried removing and re-creating my lineup on schedulesdirect.  Same results as before.

---

### Post by tgm4883 on 2008-05-27
Interesting.  Did you also delete all the channels in the channel editor before re-grabbing the channels in the channel lineup setup?

---

### Post by a_posse_ad_esse on 2008-05-27
I guess I should better describe what happened.

I did a fresh install of the base system because my /boot/stage1 got overwritten during a hd test.  I backed up the database, and all of my recordings remained untouched on my RAID array.  When I had finished the install, I didn't look to see if I had deleted the channels, I simply went through the setup process as usual.

There are currently no channels present, but all other data, such as settings and recording names, remains intact.

---

### Post by a_posse_ad_esse on 2008-05-29
Yet another addendum:

I am able to scan for channels through the HDHomerun, and they insert into the database without issue.  There is not way to simply convert these channels to human readable format however, as they are QAM.

---

### Post by jubxie on 2008-05-30
I feel your pain. I can't get myth working to save my marriage!! No pvr for 3 days now. We can watch, but not schedule recordings. I am finding lots of people with this issue, but no answers. I'll post if I find anything, I hope you do the same. 


[http://ubuntuforums.org/showthread.php?t=810122&highlight=mythfilldatabase](http://ubuntuforums.org/showthread.php?t=810122&highlight=mythfilldatabase)

---

### Post by jubxie on 2008-05-30
Got it! I needed to add the xmlid for each channel as I am using QAM. I forgot I had done this on the last install. That was it! While watching a channel, press "E". I had to manually add the xmlid (found a list somewhere, if you live in seattle, as I think they are regional, I can post a list.

Credit where credit is due. 

[http://mysettopbox.tv/phpBB2/viewtopic.php?t=16178&postdays=0&postorder=asc&start=45](http://mysettopbox.tv/phpBB2/viewtopic.php?t=16178&postdays=0&postorder=asc&start=45)

---

### Post by tgm4883 on 2008-05-30
Interesting, I wasn't aware that you had to do that.

Just FYI, it may be faster to add it in mythweb.  Go to setup and channel and there is a column for xmlid

---

### Post by bah1976 on 2008-05-30
I had a similar issue - In south-suburban Chicago, I can get all stations via ATSC antenna except CBS (until they switch frequencies in february - anyway...) and I am pulling CBS in via QAM from my comcast line.  I had all program data except this QAM digital channel.  My SchedulesDirect profile for the QAM lineup has channel 189 as the digital CBS, but it's showing (and tuning) as 2.1 in Myth.  189 does not tune when I try to view that channel.  I think that was the cause of my problem.  So, I took the XMLID from channel 189 and put it in the blank XMLID for 2.1.  After that, mythfilldatabase populated program info for 2.1.  

In the process of all this, i found that if you hover the mouse over the channel name/number in your schedules direct account, it'll tell you what the id is - so you don't have to go searching for a list somewhere - it's in your SD account.

---

### Post by a_posse_ad_esse on 2008-05-30
I guess that I am a bit lost.  

I scanned for the available channels, and got listings such as

78#1
49_2

etc.  These don't match up to anything that I'm familiar with, and the names are all wrong, so I'm not sure I will be able to make any intelligent matching with xmltvids.  I also tried editing the channels during live tv, but that didn't work either (according to my current lineup, there are 5 NBCs).  Is there another way to do this?

---

### Post by a_posse_ad_esse on 2008-06-01
I guess that I'm confused by all of this.  My lineup has analog channels in it too, and I have been able to use them before.  Shouldn't the QAM channels just not show up rather than the whole thing?

I have noticed that xmltv grabs the channels through tv_grab_na_dd, but that doesn't help mythtv of course.

I wonder if this is primarily a grabber problem...

---

### Post by a_posse_ad_esse on 2008-06-02
It turns out that the HDHomerun has its own internal grabber.  This would be why setup was different than when I had my internal card...

Thanks for all of your help.

---

