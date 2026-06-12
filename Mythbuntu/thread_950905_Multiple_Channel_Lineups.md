---
title: "Multiple Channel Lineups"
date: 2008-10-17
forum: Mythbuntu
---

### Post by sgtstadanko on 2008-10-17
I need to setup an extra channel lineup for my fw capture card.  All of my other tuners on the primary and secondaries use the one schedule direct lineup from my provider BH.  The problem is schedules direct will not allow you to create more than one lineup from the same source.  For instance..they have Brighthouse Digital - which has all the channels and Brighthouse analog - which has only the 2-90 in it.  I need to be able to have a secondary lineup that only contains HD in it so when i want to record or view and HD channel myth will swap over to the FW input. I cant move the other tuners over to the analog source because I will lose most of my channels.

Is there some kind of way around this.  To maybe tell myth to use the same cable source but on certain channels to only use the FW card?

Thanks

---

### Post by ian dobson on 2008-10-17
Hi,

One way would be to write a small script that copies the programs from one channel to another.

This SQL should almost do it (ie try it, I've not tested it):-

```
INSERT
  INTO
    program
SELECT
  'NewChannel'
  ,starttime
  ,endtime
  ,title
  ,subtitle
  ,description
  ,category
  ,category_type
  ,airdate
  ,stars
  ,previouslyshown
  ,title_pronounce
  ,stereo
  ,subtitled
  ,hdtv
  ,closecaptioned
  ,partnumber
  ,parttotal
  ,seriesid
  ,originalairdate
  ,showtype
  ,colorcode
  ,syndicatedepisodenumber
  ,programid
  ,manualid
  ,generic
  ,'listingsource'
  ,first
  ,last
  ,audioprop
  ,subtitletypes
  ,videoprop
FROM
  program
WHERE
  chanid = 'OLDCHANNEL'

```

I've not tested this but it should work.
Note the fields in '' need to be replaced with the correct values:-
NewChannel - Channel number that should contain the new program list
OLDCHANNEL - Channel number that contains the programs you want to copy
listingsource - Video Input number for the newchannels

Edit: Just tested the SQL query in myPHP and it worked :)

Regards
Ian Dobson

---

### Post by sgtstadanko on 2008-10-17
Thanks!

I actually found a hack method on the Myth-HowTo docs....

[http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4](http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4)

It involves changing your lineups at SD multiple times for each lineup and creating separate sources and retrieving listings after the edits. Then u run mythfilldatabase --remove-new-channels.  Not shure If i need to run this on my secondary as well (where the 3rd tuner and the HD FW is).

Your way sounds l33t3r though and I may work that if this doesnt get it.

Thanks again

---

### Post by newlinux on 2008-10-17
> **sgtstadanko said:**
> Thanks!

I actually found a hack method on the Myth-HowTo docs....

[http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4](http://mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4)

It involves changing your lineups at SD multiple times for each lineup and creating separate sources and retrieving listings after the edits. Then u run mythfilldatabase --remove-new-channels.  Not shure If i need to run this on my secondary as well (where the 3rd tuner and the HD FW is).

Your way sounds l33t3r though and I may work that if this doesnt get it.

Thanks again

This is what I was going to suggest. You only need to run mythfilldatabase on your master backend. All of the program info is stored in the database on the master so once that is updated it is updated for all tuners and sources across all secondary backends. Just make sure to change the call to mythfilldatabase to add --remove-new-channels in mythfrontend.

---

### Post by sgtstadanko on 2008-10-17
Thanks guys!

Its working sweet now.  Moves inputs like a charm.  Even picks up some channels the tivo hd with cable cards doesnt.  It wouldn't work at first so I had to go into the db and remove the all the hd channels that werent listed with the correct sourceid.

Thanks again.

---

### Post by sgtstadanko on 2008-10-18
Scratch that.  Last night when mythfilldatabase ran it re-added the HD channels back to the wrong sourceids, even though I added the --remove-new-channels flag in the setup.  I have three lineup cable-analog, cable-digital (has analog too) , HD (just HD channels).

Any ideas on how to fix this other than writing a sql script an putting it in cron?

---

### Post by newlinux on 2008-10-18
Where did you add --remove-new-channels flag? Did it call it with that flag and not work or did it just fail to call it with the flag? (should be able to tell from backend logs) At the very least you could just disable in mythfrontend the automatic running of mythfilldatabase and just create a cron job that calls it with the flag if the problem was that it called it without it. I have mythfilldatabase called with flags and in my setup they are always used...

---

### Post by sgtstadanko on 2008-10-18
I added it in Utilities,Setup, Setup, General in the field for flags to run mythfilldatabase with.  It is call mythfilldb.sh which contains:

```
#!/bin/bash

DATE=`date +%d%m%Y`
rm -rf /tmp/dd-\*xml >/dev/null 2>&1

/usr/bin/tv_grab_na_dd --config-file /var/mythdora/.xmltv/scheddirect_AL01494:X 
--days 13 --download-only --dd-data /tmp/dd-1-$DATE.xml
/usr/bin/mythfilldatabase --do-channel-updates --refresh-all --dd-file 1 -1 AL01
494:X /tmp/dd-1-$DATE.xml
/usr/bin/tv_grab_na_dd --config-file /var/mythdora/.xmltv/scheddirect_AL01494:X 
--days 13 --download-only --dd-data /tmp/dd-2-$DATE.xml
/usr/bin/mythfilldatabase --do-channel-updates --refresh-all --dd-file 2 -1 AL01
494:X /tmp/dd-2-$DATE.xml
```


So I don't know why its not adding that flag.  I edited the mythfilldb.sh to add it and removed it from the field in setup to see what happens.

---

### Post by sgtstadanko on 2008-10-18
hmmmm. added them back again?!

bahhhhh.  I am a lazy sysadmin.  

hdfix.sql it is.

thanks for the help though.

---

