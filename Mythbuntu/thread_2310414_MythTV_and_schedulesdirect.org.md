---
title: "MythTV and schedulesdirect.org"
date: 2016-01-18
forum: Mythbuntu
---

### Post by devlin3 on 2016-01-18
Hi there, and thank you in advance for taking the time to respond.

I am attempting to use a HDHomeRun Connect along with a digital antenna and MythTV to pick up local channels and record them on my Ubuntu laptop. I'm using Ubuntu version 140.04.3 LTS.

I am following these instructions to set up MythTV with my HDHomeRun Connect: [https://help.ubuntu.com/community/HDHomeRun/MythTV](https://help.ubuntu.com/community/HDHomeRun/MythTV). Step 10 dictates that I create an account with zap2it.com and create a listing. Step 11 dictates that I follow these instructions for the MythTV backend setup: 
> 11) Choose Video sources Change the configuration for **Digital Antenna** as follows: 
[TABLE]
[TR]
  [TD="colspan: 1, align: center"] [[IMG]https://help.ubuntu.com/moin_static193/light/img/attachimg[/IMG]]("https://help.ubuntu.com/community/HDHomeRun/MythTV?action=AttachFile&do=upload_form&ticket=00569dad6a.83d56fae83cb5deac599796de507ef283c322bf1&target=video_return_1.png") 
[/TD]
   [TD] Listings grabber: North America ([DataDirect]("https://help.ubuntu.com/community/DataDirect")) (Internal) 
[/TD]
 [/TR]
 [TR]
  [TD] User id: <login name for zap2it> 
[/TD]
 [/TR]
 [TR]
  [TD] Password: <password for zap2it> 
[/TD]
 [/TR]
 [TR]
  [TD] Retrieve lineups: <enter> 
[/TD]
 [/TR]
 [TR]
  [TD] Data direct lineup: <select correct listing> 
[/TD]
 [/TR]
 [TR]
  [TD] Finish <enter> 

[/TD]
[/TR]
[/TABLE]


However, the only listings grabber option I come across is: "North America (SchedulesDirect.org) (Internal)" 
My zap2it user ID and password don't seem to do much (perhaps I am overlooking something). I did some cursory research on ScheduleDirect.org and it is a paid service. Does MythTV only allow users to use scheduledirect.org instead of cap2it.com, thus requiring the yearly payment? Anything to shed light upon this would be helpful. Thank you very much.

---

### Post by ub-newbie on 2016-01-22
I don't have a Homerun, but since you seem to be trying to get your MythTV program guide working, I'll take a stab....

I think the instructions you are following are out of date?  The Zap2it.com web page was changed (perhaps mid-2014) and I'm not sure if the grabber in MythTV works with it any more.

MythTV can use a XML data file to populate your program guide.  
You might look into "zap2xml".  It can create a XML file of channel guide info for you to import into MythTV.
If you try zap2xml, make sure "libhtml-parser-perl", "libapache2-request-perl", and "libjson-perl" are installed on your system.  

Here is how you could run zap2xml: 
(qutes indicates you need to replace with your values i.e. "username" replaced with   Ronald)
```
perl zap2xml.pl -u "zap2it_user_name" -p "zap2it_password" -D -s 1
```

Then, to get MythTV to use the XML file to populate the channel guide:
```
mythfilldatabase --update --file --xmlfile "path_to_XML_file" --sourceid 1 -V all
```
Then I put these into 2 scripts (make them executable) and run them twice a week, zap2it on the hour, and mythfilldatabase about 30 min later.

Please look at the instructions for zap2xml and mythfilldatabase to understand all the options, the one's I use might not be the best for you.

NOTE:  Only the channels you have configured in your Zap2it account will be downloaded.

NOTE2:  Since I had previously used  MicroSo** Media Center XML files, I had to go into the MythTV database and make some changes to the "Channels" table, but you probably won't have to do that.

---

### Post by deadflowr on 2016-01-22
Moved to the *Mythbuntu* sub-forum

Though you may not necessarily be using mythbuntu, this is where those who use and understand myth will be.

---

### Post by tgm4883 on 2016-01-23
Zap2it no longer provides listing data. In the US, Schedules Direct is what you want to use. [http://www.schedulesdirect.org/](http://www.schedulesdirect.org/) It's really good data for $20/year

---

