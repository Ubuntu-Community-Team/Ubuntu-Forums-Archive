---
title: "MP3 tag editor with CDDB lookup"
date: 2012-05-06
forum: Multimedia Software
---

### Post by bones12 on 2012-05-06
I have a number of mp3 files which have tag information for the artist and title, but not the album.

I would like to find an editor that would fill in the missing album information. I've tried Easytag but have not been able to make it work. 

In the Preferences I have for the automatic search 
freedb.freedb.org  port: 80   CGI Path: /~cddb/cddb.cgi

on the manual search I have 
[www.gnudb.org](www.gnudb.org)    port: 80     CGI Path: /~cddb/cddb.cgi

---

### Post by Nickolai_Leschov on 2012-05-15
I would like to know of a good mp3 tag editor, too!

I have around 150 audio recordings from the conference, which I need to tag properly. How is this best done these days?

---

### Post by Nickolai_Leschov on 2012-05-27
I happily use Puddletag:

```
sudo add-apt-repository ppa:webupd8team/puddletag
sudo apt-get update
sudo apt-get install puddletag
```

(ppa [via webupd8]("http://www.webupd8.org/2011/01/puddletag-audio-tag-editor-gets-ubuntu.html"))

---

