---
title: "epg and xmltv"
date: 2010-11-21
forum: Mythbuntu
---

### Post by simonnev on 2010-11-21
I have now got a working mythtv system comprising of masterbackend, slave backend and another two frontends.. everything seems to be running fine recording live tv, watching my films, loving it. 

However I am trying to setup the epg using xmltv and the radio times grabber in the videosource setup, I mapped all the channels from the channel.ids etc and running mythfilldatabase tells me there is 13 days of data, takes quite a while too run using sky uk. Now this is where I am lost! the timeline or mythweb listings does not show data for sky channels except now and next, but if i search for a program ie something on national geographic it shows, the show I search for later that week so the data must be there, does anyone know how I should be populating the data for mythweb and the timeline channels? also i have seen data in a cache folder in xmltv..
googled quite a bit but seem to have drawn a blank
simon

---

### Post by ian dobson on 2010-11-21
Hi,

Your you sure you've setup the xmltv id's for the channels that don't work correctly. The items this/next usually just come through EIT (epg over the wire).

Regards
Ian Dobson

---

### Post by simonnev on 2010-11-21
thanks for your reply ian

I now seem to have made it worse data now missing for the bbc channels and fta ones, which definatly was getting the data from the xmltv, well at least i hope so.. the eit guide only shows 8 days but the xmltv showed 13 days in front..

Maybe your are right and some how i messed up the channel.ids part when mapping.. but what i dont understand is that data was pulled in and if you searched for a films say it returned with alot of film data from the channels that do not have eit only now and next... also the same if ran a search for accident investigation again it brought the data back..

I have been following this guide here [http://www.mythtv.org/wiki/Uk_xmltv](http://www.mythtv.org/wiki/Uk_xmltv) but i am at a loss at this stage:

****It isn't enough just to add a new channel's xmltvid in the channel table.

If the new xmltvid is known, either:

    * Add the new xmltvid to ~/.mythtv/<videosourcename>.xmltv in the form 'channel xmltvid'
    * Or re-run tv_grab_uk_rt --configure <videosourcename>.xmltv 

(where <videosourcename> is the name of the 'video source' you want the grabber to grab data for) [/I]

what is xmlvtid? also if i run tv_grab_uk_rt --configure <videosourcename>.xmltv i end up with a empty file 

thnx again simon

---

### Post by ian dobson on 2010-11-21
> **simonnev said:**
> thanks for your reply ian

what is xmlvtid? also if i run tv_grab_uk_rt --configure <videosourcename>.xmltv i end up with a empty file 

thnx again simon

An xmltvid is nothing more than a unique text used to identify a channel (for example 9.[www.teleboy.ch](www.teleboy.ch)). The grabber creates a xml file which mythtv reads using the xmltvid to know which channel to add the information to. So you need to make sure that the xmltvid entered into mythtv (in mythsetup for each channel) is the same as the id in the xmltv file. Here's a dump of part of my xmltv file I use:-

```

  <programme start="20101122060500" stop="20101122063500" channel="9.www.teleboy.ch">
    <title lang="de">Alle hassen Chris</title>
    <sub-title lang="de">Chris hasst den Beratungslehrer</sub-title>
    <desc lang="en">Am Ende des vergangenen Schuljahres musste Chris einen Test ablegen, den er allerdings nicht ernst genommen hat, was sich nun rÃ¤cht: Der Beratungslehrer Mr. Abbott ruft Chris zu sich und redet ihm ein, dass aus ihm nichts werden wird ... Da die Kinder mal wieder gewachsen sind, muss Julius neue Kleidung besorgen - und siehe da, im Secondhandshop findet er auch einige SchmuckstÃ¼cke fÃ¼r seine Liebsten - sehr zum Ã„rger von Rochelle.Brooklyn, New York, in den frÃ¼hen 80er Jahren. Chris ist 13 Jahre alt und voller Hoffnung, endlich ein cooler Teenager zu werden. Das Heranwachsen stellt sich allerdings als sehr kompliziert heraus. Chris' Hauptproblem: Er ist fast das einzige schwarze Kind an seiner Schule. Ausserdem muss er sich regelmÃ¤ssig mit seinen jÃ¼ngeren Geschwistern, Bruder Drew und Schwester Tanya, herumÃ¤rgern. Und auch das liebe Thema "Geld" sorgt immer wieder fÃ¼r Wirbel bei der Familie ...</desc>
    <category lang="de">Sitcom</category>
    <audio><stereo></stereo></audio>
    <video><aspect></aspect></video>
  </programme>

```

Note the channel= at the start. Sorry that the texts are in german but you get the idea.

Regards
Ian Dobson

---

### Post by simonnev on 2010-11-22
Could u clarify a little more.. strange things are happening regarding the ids no..

This is a section from my xmltv file that is generated after the grab i do 

[I]channel=bbcfour.bbc.co.uk
channel=hd.bbc.co.uk
channel=news.bbc.co.uk
channel=bbc1.bbc.co.uk
channel=hd.bbc1.bbc.co.uk[/I]
 
this file comes from running *tv_grab_uk_rt --configure* and then *cp ~/.xmltv/tv_grab_uk_rt.conf ~/.mythtv/Test.xmltv*

Now when i look in the channel info in mythweb the id no becomes the address  ie bbcfour.bbc.co.uk but on your file u have a number as well, do i take it, i then have too insert the corresponding number again but this time in the generated file so it becomes *channel=47.bbcfour.bbc.co.uk* 
 

thnx simon

fried brain on this.....

---

### Post by simonnev on 2010-11-22
ok looks like i got it running all i did is to copy and paste the ids string into the empty xmltv box and the guide shows up in the timeline...
simon

---

