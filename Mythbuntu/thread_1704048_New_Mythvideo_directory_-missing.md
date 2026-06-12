---
title: "New Mythvideo directory -missing"
date: 2011-03-10
forum: Mythbuntu
---

### Post by Chewiesw on 2011-03-10
Me again..

I have created a new folder called NewMovies  in /var/lib/mythtv/.  The permissions are set that the mythtv user has read/write and mythgroup has read.  I have placed “link” to the folder in video settings, pressed M and scanned for changes, but the NewMovies folder does exist when I go to watch videos. I am not using storage groups as I prefer to use VNC. How do I make this folder visible in Mythvideo or should I rather create the folder in /media?

---

### Post by tgm4883 on 2011-03-10
> **Chewiesw said:**
> Me again..

I have created a new folder called NewMovies  in /var/lib/mythtv/.  The permissions are set that the mythtv user has read/write and mythgroup has read.  I have placed “link” to the folder in video settings, pressed M and scanned for changes, but the NewMovies folder does exist when I go to watch videos. I am not using storage groups as I prefer to use VNC. How do I make this folder visible in Mythvideo or should I rather create the folder in /media?

How exactly did you create the "link"?

---

### Post by Chewiesw on 2011-03-10
the actual location of the file "/var/lib/myhttv/NewMovies" prefixed with : (without the quotes)

---

### Post by newlinux on 2011-03-10
You put this in the mythfrontend setup, in the media settings? Try taking out the colon (unless you have multiple directories separated by a colon). That failing, what does mythfrontend produce in its logs when you scan for changes?

---

### Post by Chewiesw on 2011-03-11
my frontend log. The folder name is actually Movies not NewMovies, however a strange thing happens when I scan for folders on first scan NewMovies disappears  and if you scan it again it re-appears 

```
2011-03-11 18:35:15.775 buildFileList directory = /var/lib/mythtv/videos
2011-03-11 18:35:15.775 MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
2011-03-11 18:35:15.789 buildFileList directory = /var/lib/mythtv/WatchedTv
2011-03-11 18:35:15.790 MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/WatchedTv)
2011-03-11 18:35:17.197 buildFileList directory = /var/lib/mythtv/TV_Series
2011-03-11 18:35:17.197 MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/TV_Series)
2011-03-11 18:35:18.234 buildFileList directory = /media/NewMovies
2011-03-11 18:35:18.235 MythVideo::ScanVideoDirectory Scanning (/media/NewMovies)
2011-03-11 18:35:18.235 buildFileList directory = /var/lib/mythtv/Movies
2011-03-11 18:35:18.236 MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/Movies)
```

---

