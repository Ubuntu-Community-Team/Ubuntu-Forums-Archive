---
title: "Metadata URL Incorrect"
date: 2010-11-16
forum: Mythbuntu
---

### Post by tacman2k on 2010-11-16
I am having issues with retrieving metadata in mythtv.

I am running Ubuntu 10.10 with the 0.24 auto-build repository.

Take a look at the attached screenshot. It would appear as though the URL to the image file on "online" searches is broken...

[IMG]http://dl.dropbox.com/u/767194/Screenshot-1.png[/IMG]

Any help would be appreciated.

---

### Post by tacman2k on 2010-11-16
Playing around with the TMDB.py script reveals that some of the URLs retrieved are relative links instead of absolute:

```


patrick@bigbeefy:/usr/share/mythtv/metadata/Movie$ python tmdb.py -M "Beerfest"
<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <language>en</language>
    <title>Beerfest</title>
    <inetref>9988</inetref>
    <imdb>0486551</imdb>
    <userrating>5.8</userrating>
    <certifications>
      <certification locale="us" name="R"/>
    </certifications>
    <description>Two brothers travel to Germany for Oktoberfest, only to stumble upon secret, centuries-old competition described as a "Fight Club" with beer games.</description>
    <releasedate>2006-08-25</releasedate>
    <images>
      <image type="coverart" url="/posters/0fb/4cdec3617b9aa13c780000fb/beerfest-original.jpg" width="1000" height="1500" thumb="/posters/0fb/4cdec3617b9aa13c780000fb/beerfest-cover.jpg"/>
      <image type="fanart" url="/backdrops/57e/4bc92af8017a3c57fe01157e/beerfest-original.jpg" width="1920" height="1080" thumb="/backdrops/57e/4bc92af8017a3c57fe01157e/beerfest-thumb.jpg"/>
    </images>
    <lastupdated>Sat, 13 Nov 2010 16:57:22 GMT</lastupdated>
  </item>
</metadata>




```

Any ideas on how to fix the script?

---

### Post by tacman2k on 2010-11-16
Well after doing some searching I found an answer to my question in the TMDB forums:

[http://forums.themoviedb.org/topic/1494/api-images-missing-domain-name-in-url/](http://forums.themoviedb.org/topic/1494/api-images-missing-domain-name-in-url/)

---

