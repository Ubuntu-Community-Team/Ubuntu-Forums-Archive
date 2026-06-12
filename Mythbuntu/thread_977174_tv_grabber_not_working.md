---
title: "tv grabber not working"
date: 2008-11-10
forum: Mythbuntu
---

### Post by mpulley on 2008-11-10
I'm using tv_grab_na_dtv (xmltv 0.5.53) and it won't grab the channels.  I'm able to select the time zone and enter my zip.  But once it goes to retrieve the channels, nothing happens.

~# tv_grab_na_dtv --configure
Which is your time zone?
Time Zone:
0: Eastern
1: Central
2: Mountain
3: Pacific
4: Alaska
5: Hawaii
Select one: [0,1,2,3,4,5 (default=0)] 3
Enter your zip code to include local channels.
Zip Code: [] 93041
Select the channels that you want to receive data for.
~# 

My configuration file has nothing but the zip and time zone.  

I also tried --debug,

~$ tv_grab_na_dtv --debug
Getting IDs for day 0 ............
Getting IDs for day 1 ............
Getting IDs for day 2 ............
Getting IDs for day 3 ............
Getting IDs for day 4 ............
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE tv SYSTEM "xmltv.dtd">
<tv source-info-url="http://www.directv.com/" source-info-name="DirecTV" generator-info-name="XMLTV" generator-info-url="http://www.xmltv.org/">
</tv>

It doesn't say what the error is, so I'm not sure where to go with it.  Anyone have any advice?  Thanks

---

