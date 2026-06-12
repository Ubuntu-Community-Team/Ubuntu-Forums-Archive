---
title: "Problems with media"
date: 2008-09-17
forum: Multimedia Software
---

### Post by cndrr_fan on 2008-09-17
Hello, 

Looking to get my laptop free of Windows. Only 4 things stand in my way:

1) Playing DVD movies

2) Watching online video (youtube, flash)

3) Listening to all music types (WMA, MP3)

4) Lack of knowledge of Ubuntu

I am currently using 7.10. Tried to follow the instructions on the helpful 
comprehensive multimedia and video howto

some of the sudo commands tell me cannot find file and the fix for that error tells me the same thing. 

Any suggestions?

---

### Post by wolfen69 on 2008-09-17
[This]("http://www.psychocats.net/ubuntu/") page will guide you. be patient and it will happen. we were all noobs at one time. welcome to ubuntu.

---

### Post by wolfen69 on 2008-09-17
OK, i've decided to help one on one. but the link i gave you is good. also see [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
open a terminal and: 
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```then ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```then ```
sudo apt-get install flashplugin-nonfree
``` then ```
sudo apt-get install libdvdcss2
```then ```
sudo apt-get install libflashsupport
``` i install vlc and mplayer to get the rest of the codecs. ```
sudo apt-get install vlc mplayer
``` of course, this is how *i* do it. other people may have other methods.

---

