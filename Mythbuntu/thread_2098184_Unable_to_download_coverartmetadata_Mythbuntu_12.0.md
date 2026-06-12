---
title: "Unable to download coverart/metadata: Mythbuntu 12.04"
date: 2012-12-25
forum: Mythbuntu
---

### Post by neko on 2012-12-25
Hi,

I've just upgraded from Mythbuntu 11.04 (I think it was) to 12.04.

Prior to installing Mythbuntu 11.04, I was running Mythtv-0.23.  Coverart and movie details were downloading properly.  Since installing Mythbuntu 11.04, downloading video metadata has been broken.  I was hoping it might fix itself with the install of 12.04, but it has not.

Basically, in the Video Gallery, if I select "Retrieve All Details" for a movie, nothing happens.  If I run 'tail -f /var/log/mythtv/mythfrontend.log' nothing is appended to the log file.  Is this the correct log file to be looking in?

I found metadata grabber settings in the database.  They were referencing /usr/share/mythtv/mythvideo/scripts/tmdb.pl, which no longer exists.  So I updated these references to /usr/share/mythtv/metadata/Movie/tmdb.py, which does exist.

If I manually run ```
/usr/share/mythtv/metadata/Movie/tmdb.py -M "21 Jump Street"
``` this generates suitable-looking data:

```
<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <language>en</language>
    <title>21 Jump Street</title>
    <inetref>64688</inetref>
    <imdb>1232829</imdb>
    <userrating>7.4</userrating>
    <certifications>
      <certification locale="us" name="R"/>
    </certifications>
    <description>In high school, Schmidt (Jonah Hill) was a dork and Jenko (Channing Tatum) was the popular jock. After graduation, both of them joined the police force and ended up as partners riding bicycles in the city park. Since they are young and look like high school students, they are assigned to an undercover unit to infiltrate a drug ring that is supplying high school students synthetic drugs.</description>
    <releasedate>2012-03-12</releasedate>
    <images>
      <image type="coverart" url="http://cf2.imgobject.com/t/p/original/mH6xazzfGdszadd1Xy9JgdZYvn1.jpg" width="1000" height="1500" thumb="http://cf2.imgobject.com/t/p/w185/mH6xazzfGdszadd1Xy9JgdZYvn1.jpg"/>
      <image type="fanart" url="http://cf2.imgobject.com/t/p/original/dsBgguvHDDOsUi6h10UxDFZyHRA.jpg" width="1920" height="1080" thumb="http://cf2.imgobject.com/t/p/w300/dsBgguvHDDOsUi6h10UxDFZyHRA.jpg"/>
    </images>
    <lastupdated>Tue, 25 Dec 2012 16:43:01 GMT</lastupdated>
  </item>
</metadata>
```


Using "-D", however, produces:

```
/usr/share/mythtv/metadata/Movie/tmdb.py -D "21 Jump Street"
! Error: Unknown error during a Movie (21 Jump Street) information display
Error(Input object has no document: lxml.etree._ElementTree)
```


So can anyone please help with:
[LIST]
[*]Where is/should mythtv be dumping logs for the failed download attempts?
[*]Pointers to why mythtv is failing to download metadata?
[*]Why is the "-D" option failing?
[/LIST]

thanks,
Matt

---

### Post by neko on 2013-01-02
Solved - sort of...

While "Update all details" appears to do nothing, I found that metadata is properly downloaded if I:

[LIST=1]
[*]Move/remove those videos that don't have metadata.
[*]Get mythtv to rescan (thus removing the videos from the database.
[*]Return the video files to the appropriate directory.
[*]Get mythtv to rescan.  Videos are restored to the database and metadata is downloaded.
[/LIST]

---

