---
title: "TMDB and dots in the title"
date: 2011-04-24
forum: Mythbuntu
---

### Post by axelsvag on 2011-04-24
Yesterday a put a new movie in the video folder. This normally worked well but when I searched for in the front end no metadata was fetched. I ed in the log and it said this.
```
2011-04-24 07:31:23.622 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l sv -M True Grit
2011-04-24 07:31:24.522 No adequate match or multiple matches found for True Grit.  Update manually.
2011-04-24 07:31:24.561 No results found for True Grit 0 0
```

I then tried  running the py script manually and then I got this feedback
```
 /usr/share/mythtv/metadata/Movie/tmdb.py -l sv -M True Grit
! Error: There must be one value for any option. Your options are ([u'True', u'Grit'])

```

after that I tried running the script with the moviename "True Grit"  with dot between True and Grit and then I succesfully could retrieve the metadata.

```
/usr/share/mythtv/metadata/Movie/tmdb.py -l sv -M True.Grit
<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <language>en</language>
    <title>True Grit</title>
    <inetref>44264</inetref>
    <imdb>1403865</imdb>
    <userrating>8.2</userrating>
    <certifications>
      <certification locale="us" name="PG-13"/>
    </certifications>
    <description>Fjortonåriga Mattie Ross far har blivit skjuten till döds av ynkryggen Tom Chaney och hon är fast besluten att se till att rättvisa skipas och att mördaren får vad han förtjänar. Hon tar hjälp av en skjutglad, försupen U.S. Marshal, Rooster Cogburn, och de ger sig iväg - mot hans protester - för att få tag på Chaney. För att kunna hämnas sin far måste hon förfölja brottslingen in på Indianernas territorium och dessutom hitta honom fort, innan en TexasRanger vid namn LaBoeuf fångar honom först och för honom till Texas för att stå till svars för mordet på en annan man.</description>
    <releasedate>2010-12-22</releasedate>
    <images>
      <image type="coverart" url="http://cf1.imgobject.com/posters/d21/4d29257f7b9aa134cb002d21/true-grit-original.jpg" width="1000" height="1500" thumb="http://cf1.imgobject.com/posters/d21/4d29257f7b9aa134cb002d21/true-grit-cover.jpg"/>
      <image type="fanart" url="http://cf1.imgobject.com/backdrops/675/4d7670247b9aa17045001675/true-grit-original.jpg" width="1920" height="1080" thumb="http://cf1.imgobject.com/backdrops/675/4d7670247b9aa17045001675/true-grit-thumb.jpg"/>
    </images>
    <lastupdated>Thu, 21 Apr 2011 07:12:49 GMT</lastupdated>
  </item>
  <item>
    <language>en</language>
    <title>True Grit</title>
    <inetref>17529</inetref>
    <imdb>0065126</imdb>
    <userrating>8.0</userrating>
    <certifications>
      <certification locale="us" name="G"/>
    </certifications>
    <description>The murder of her father sends a teenage tomboy, Mattie Ross (Kim Darby), on a mission of "justice", which involves avenging her father's death. She recruits a tough old marshal, "Rooster" Cogburn (John Wayne), because he has "grit", and a reputation of getting the job done. The two are joined by a Texas Ranger, La Boeuf (Glen Campbell), who is looking for the same man (Jeff Corey) for a separate murder in Texas. Their odyssey takes them from Fort Smith, Arkansas, deep into the Indian Territory (present day Oklahoma) to find their man.</description>
    <releasedate>1969-12-28</releasedate>
    <images>
      <image type="coverart" url="http://cf1.imgobject.com/posters/208/4bc94fc9017a3c57fe023208/true-grit-original.jpg" width="1000" height="1402" thumb="http://cf1.imgobject.com/posters/208/4bc94fc9017a3c57fe023208/true-grit-cover.jpg"/>
      <image type="fanart" url="http://cf1.imgobject.com/backdrops/900/4d33ccea7b9aa177db007900/true-grit-original.jpg" width="1920" height="1080" thumb="http://cf1.imgobject.com/backdrops/900/4d33ccea7b9aa177db007900/true-grit-thumb.jpg"/>
    </images>
    <lastupdated>Mon, 18 Apr 2011 10:33:24 GMT</lastupdated>
  </item>
</metadata>

```

I then tried to rename the video with dots but the front end refuse to update the metadata. 

What is wrong? 

This seemed to worked perfectly a few weeks ago. 
I use the 0.24 myth with mythtbuntu 10.04 with fixes enabled

---

### Post by iamlindoro on 2011-05-06
Like the original log message says, multiple matches were found, and thus myth is unable to make an accurate guess automatically.  Update manually means you should update the item's metadata manually.  Highlight it, press W, and select the correct version of True Grit from the resulting menu.

---

### Post by nickrout on 2011-05-07
The other trouble is that once you have scanned a file once, it remembers the video by making a hash of it and comparing the hash value on subsequent scans. Therefore changing the name will not result in the file being rescanned, as the system thinks it has been already.

Solution: move the file out of your videos directory, scan (it is now deleted from the db), move it back, change the name to what you want, rescan.

---

### Post by axelsvag on 2011-05-18
Thank you your suggestions worked so the problem is solved.

---

