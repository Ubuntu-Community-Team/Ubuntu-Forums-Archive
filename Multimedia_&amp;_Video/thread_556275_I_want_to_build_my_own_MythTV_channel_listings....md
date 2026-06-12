---
title: "I want to build my own MythTV channel listings..."
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by prion on 2007-09-21
Now that the free MythTV listings data isn't free anymore, I'd like to write a program that grabs the data from an online listing service.  I can't find any information on

1) The form of the XML file

or 2) How to give my XML file to mythTV.

Does anyone know how to do this or where I can find some information?

Thanks!

---

### Post by prion on 2007-09-21
If a mythTV user could post a mythTV XML TV listing file here that would be a great help.  I'd be more than happy to post the edited template XML file for any other users that are writing their own listing-capture software.  I can't believe I am the only ubuntu-mythTV user who is having this problem.  I hope we can come together as a community to keep MythTV free and independent software.

_prion

---

### Post by jba6511 on 2007-09-22
I am doing what you want to do now. i use the zap2xml grabber from here zap2xml.110mb.com. I am not experienced with perl yet so I use the windows version and grab the xml listings from a command prompt in virtualbox. Once my xml listings are created, I place them in my home directory and run the following to fill the mythtv database: mythfilldatabase --file 1 -1 xmltv.xml
where xmltv.xml is the name of the xml file created. You also have to change your settings in mythtv to match the new non grabber video source. I got most of the info from here [http://www.mythtvtalk.com/forum/viewtopic.php?t=6271](http://www.mythtvtalk.com/forum/viewtopic.php?t=6271). Works well so far, but the only problem I am having is sometime the listings in  mythweb will show an episode that is 30 min is on for 2 hours when that is not the case. I think it is the listings file so I need to find another source other than the zap2xml. If you find a good one, please let me know.

---

### Post by jba6511 on 2007-09-22
well found a better alternative xml scrapper. [http://planetreplay.com/phpBB2/viewtopic.php?t=14314](http://planetreplay.com/phpBB2/viewtopic.php?t=14314)
I use  that in my xp virtual box session to generate the xml file and then just fill the mythtv database with it. I had a problem with duplicate settings (channels listed twice in mythweb) so I just deleted all my video source and readded. This time I did not search or add any channels in the channel editor. I then filled the myth db and everything is working fine.

---

### Post by prion on 2007-09-22
Thanks a lot, that forum entry is exactly what I needed.  If you have the wrong length information, you probably have a mistake in the xmltv.xml file for that program.  Their DTD is posted online [http://www,xmltv.org/](http://www,xmltv.org/)  I think the time attribute is 

<programme starttime = "YYYYMMDDHHMM endtime = "YYYYMMDDHHMM" id = "[channelID]">
...
</programme>

Where the times are in a YearMonthDayHourMinute format.

---

