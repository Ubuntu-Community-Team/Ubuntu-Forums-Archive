---
title: "Mythnews/Mythflix (netflix) fail to download data"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by scsever on 2006-11-18
I have installed MythTV and plugins on Edgy as directed on the Ubuntu Documentation.  I've gone into the setup and selected some news links and also selected the top three Netflix options.  When I try to view either news or netflix I get two message on the screen "failed to retrieve news" and "no news in cache".  I am not having any problems getting weather data or displaying web pages with mythweb, and program guide data is current so I don't see any network problems.  So does anyone have any ideas on what could be the problem?  Any idea where the configuration data for either of these is?  I don't know what I would find in those files but figured I could look for clues.

Thanks,

---

### Post by superm1 on 2006-11-19
This is an area lacking in the documentation, as I've never used mythflix myself....

But from what i understand, you will need to configure netflix like this:

/usr/share/mythtv/mythflix/scripts/netflix.pl -L <userid> <passwd>

Did you already add your netflix username and password this way?

---

### Post by scsever on 2006-11-21
I don't have a netflix account but in the past (as little as 2 weeks ago)  have been able to browse the catagories by just selecting the catagories in setup.  Because news links are failing with the same problem as netflix I am sure there is something wrong other than not having user information.
I'll give it a try though.

Thanks,

---

### Post by mydogmax on 2006-12-11
I get an error in mythnew that says failed to retrieve, and mythweather will not display maps.  Has this been figured out yet?

---

### Post by woodoousa on 2006-12-17
Hy there,

Had the same problem and it took me about three weeks to figure it out, but I guess this works. 

Create a folder called MythNews in /home/mythtv/.mythtv/. Set the permissions to the myth user and group.

This should be it. MythNews will save the News in this folder from now on. Same should actually work for MythWeather.

:D

---

