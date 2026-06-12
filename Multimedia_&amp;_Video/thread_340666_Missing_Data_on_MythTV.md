---
title: "Missing Data on MythTV"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2007-01-17
I can not seem to get the Weather Map to show up and always get a message saying **“Map unavailable”** Also, I added some new feeds and get **“Failed to retrieve news” **and **“No Cached News”**

---

### Post by Titus A Duxass on 2007-01-20
Did you set up the Information Centre using Utilities/Setup?

---

### Post by pombe on 2007-02-23
Little bit of forum necromancy, but I'm having the same problem.   Anyone know what the deal is yet?   Google has failed me, the documentation for mythnews and mythweather are pretty bad, but I appear to have directories with the right permissions in all the right places...

Is there another setupscreen for the information center that I'm not aware of?  the one in the setup/utils only sets location and C/F, not info storage location etc...

Corey

---

### Post by Titus A Duxass on 2007-02-24
You set up the information centre from the main set up screen.
You have to use the arrow keys to tab across to what you want etc?

It is not difficult just takes a bit of understanding and a bit of time.

---

### Post by pombe on 2007-02-24
Titus

When I go into my setup menu for mythweather the only choices are celcius/farenhiet, location and "agressiveness." In your setup menu does it give you a choice of where to save weather info?

The problem is probably that there is some directory that doesnt have the right permissions but I cant find it.  The messed up file is probably wherever the system is trying to store the weather/news and mythweb info (that doesnt work either).   I've used the find command to locate all directories named mythnews and mythweather and changed all those permissions/ownerships but it hasnt solved my problem.   I'm trying to Grep the error message to maybe findout what file is issueing it and whether it has any directory information, but it doesnt seem to be doing anything [grep "failed to retrieve news"  thats probably not right at all...]

Thanks for your help

Corey

---

### Post by AndrewWalker on 2007-05-01
I think mythweather is broken, it was working ok but it looks like out of the blue the web site the data is retrieved from has changed.

---

### Post by newlinux on 2007-05-01
Yep. According to the posts I've seen over at Mythtvtalk a fix is not in the workings yet...

---

### Post by Rever75 on 2007-05-11
So is myth-weather broken in feisty? I no longer get my weather showing.

---

### Post by newlinux on 2007-05-12
Mythweather is broken period (not just in feisty or ubuntu) unless you install the temporary patch from SVN.

---

### Post by Staudie on 2007-05-12
I tried the instructions here: but they didnt work
[http://www.mythtv.org/wiki/index.php/Using_mythweather-revamp_with_trunk_mythtv]("http://www.mythtv.org/wiki/index.php/Using_mythweather-revamp_with_trunk_mythtv")

-Staudie

---

### Post by KuruOujou on 2007-05-13
I also tried those instructions with no luck. Can anyone make like a deb or something for it?

---

### Post by rhpot1991 on 2007-05-31
I made an entry into the wiki on how to compile mythweather:
[https://help.ubuntu.com/community/MythWeather](https://help.ubuntu.com/community/MythWeather)

---

### Post by baekster on 2007-07-04
Followed your instruction but doesn't work.  I'm using Mythtv-wide-blue theme

I get a series of error messages that look like:

   2007-07-04 13:03:21.727 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/weather-ui.xml
   2007-07-04 13:03:22.074 Current Conditions is in database, but not theme file
   2007-07-04 13:03:22.074 18 Hour Forecast is in database, but not theme file
   2007-07-04 13:03:22.074 Six Day Forecast is in database, but not theme file

---

### Post by bengalsfan74 on 2007-07-19
The problem I've had (and been able to fix so far) has been that MythWeather is trying to access data from [http://w3.weather.com](http://w3.weather.com) which is no longer a functional link.

If you're using MythWeb and MythWeather, the best solution is to open handler.php in jed (or nano, whatever) from /var/www/mythweb/modules/weather/handler.php

Look down to about line 201, and change both instances of w3.weather.com to [www.weather.com](www.weather.com)

That started the fix for me. I don't get forecasts anymore, but at least I can get a radar map.

Its a start at least.

---

### Post by baekster on 2007-09-12
This worked for me as well!  Thank you so much!!!  I get the forecast and everything.  I'm using feisty and the updated mythtv version that can use scheduledirect.  

> **bengalsfan74 said:**
> The problem I've had (and been able to fix so far) has been that MythWeather is trying to access data from [http://w3.weather.com](http://w3.weather.com) which is no longer a functional link.

If you're using MythWeb and MythWeather, the best solution is to open handler.php in jed (or nano, whatever) from /var/www/mythweb/modules/weather/handler.php

Look down to about line 201, and change both instances of w3.weather.com to [www.weather.com](www.weather.com)

That started the fix for me. I don't get forecasts anymore, but at least I can get a radar map.

Its a start at least.

---

### Post by newlinux on 2007-09-12
> **baekster said:**
> This worked for me as well!  Thank you so much!!!  I get the forecast and everything.  I'm using feisty and the updated mythtv version that can use scheduledirect.

I'm using the updated myth as well, and this fix only give me the radar. maybe you can post your handler.php file? I'm on edgy.

---

### Post by rhpot1991 on 2007-09-12
It is my understanding that the ubuntu mythweather packages should work out of the box.  I can verify that the weekly builds from mythbuntu work out of the box.  The only problem I am having with the ubuntu mythtv packages is that I have ubuntu-mythtv-frontend upgrading constantly even though it is at the newest version (I have made a thread about this but no has replied).

---

### Post by newlinux on 2007-09-12
> **rhpot1991 said:**
> It is my understanding that the ubuntu mythweather packages should work out of the box.  I can verify that the weekly builds from mythbuntu work out of the box.  The only problem I am having with the ubuntu mythtv packages is that I have ubuntu-mythtv-frontend upgrading constantly even though it is at the newest version (I have made a thread about this but no has replied).

mythweather from the proposed feisty/edgy repo works out of the box, but the mythweb weather module doesn't for me and many others. The mythweather in the current multiverse repo is broken, but hopefully the proposed version will be okayed and moved into the multiverse.

I think mythubuntu uses an even more updated version of myth.

---

### Post by aidan_curtis on 2007-12-10
I'm having the same problem on mythbuntu on Xubuntu gutsy
I can get the radar map by editing /var/www/mythweb/modules/weather/handler.php
but gont get any data other than that in mythweb.
The myth weather on the tv works
Anyone figure out a fix?
Thanks

---

