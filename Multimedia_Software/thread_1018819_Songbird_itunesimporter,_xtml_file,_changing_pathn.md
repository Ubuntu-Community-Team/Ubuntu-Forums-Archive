---
title: "Songbird itunesimporter, xtml file, changing pathnames"
date: 2008-12-22
forum: Multimedia Software
---

### Post by shortman101n on 2008-12-22
Well I have gotten songbird to import my library from iTunes using the xml file. Ratings and playlists are intact. However I need help changing the pathnames, I do not know what to change them to that Songbird will recognize. Here is an original path example...

<key>Location</key><string>file://localhost/F:/My%20Music/iTunes/iTunes%20Music/Compilations/Nirvana/10%20Pennyroyal%20Tea.mp3</string>

My music is mounted at /media/Files/ and all the folders are the same. I do not know if I need to get rid of "file://" or "localhost" or what to change so it is recognized in ubuntu. I am already using the find replace command in gedit. I am very new to linux so if there are any ways that involve scripts or anything other than find and replace, I will probably need some extra instruction on how to use them or modify them. For example I found this script on...

[http://ubuntuforums.org/showthread.php?p=1983441](http://ubuntuforums.org/showthread.php?p=1983441)

#!/bin/bash
cp /media/data/documents/My\ Music/iTunes/iTunes\ Music\ Library.xml /tmp/
perl -pi -e 's/file\:\/\/localhost\/E\:\//\/media\//g' /tmp/iTunes\ Music\ Library.xml
echo "Use File>Import Library to import the library (found at /tmp/iTunes Music Library)";

but do not know how to modify it. Thanks for your help.

---

