---
title: "I can't play a movie.  Need to download Coral Player first"
date: 2010-12-16
forum: Multimedia Software
---

### Post by mdialogo on 2010-12-16
I've download an 700MB .AVI file but when I played it only play a minute and displayed that I need to download a Coral Player.  I just learned that Coral Player is a scam.

Does anyone know how to extract the movie out from this 700MB file, or there some kind of a decoder to convert this movie?  Any thoughts guys?

(sorry for my english)

---

### Post by Rodney9 on 2010-12-16
[http://www.ehow.com/how_4928098_convert-avi-mpeg-ubuntu.html](http://www.ehow.com/how_4928098_convert-avi-mpeg-ubuntu.html)
or google convert avi ubuntu

---

### Post by Script Warlock on 2010-12-23
don't get carried away with those exotic players with a fee, its a scam...

---

### Post by cascade9 on 2010-12-23
Delete the file and find it a different version. I'll bet you didnt pay for in, so you've lost nothing but time.

---

### Post by amsterdamharu on 2010-12-23
You can copy and paste the following commands in a terminal ( to start a terminal press alt + F2 -> type gnome-terminal -> click run )

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install non-free-codecs ffmpeg winff
```When that is done you can press alt + F2 -> type winff -> press run
This should start winff, you can add the file there, select what type to convert to and press the convert button. Any output with errors you can post here (copy from terminal and paste here).

---

### Post by mc4man on 2010-12-23
> how to extract the movie out from this 700MB file
It's possible or likely probable most of the 700mb are garbage - 
> Delete the file and ....

---

