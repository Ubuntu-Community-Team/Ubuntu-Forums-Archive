---
title: "mpd + Sonata, how open mp3 file?"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Stefan_xfce on 2008-03-23
Hi,
I'm looking for a feature-rich and slim player to play mp3's and web radio and I finally discovered mpd + Sonata, which looks really like what I'm looking for.
For internet radio it works really fine so far, since I am able to add new urls, but how can I get it to open a playlist or a single mp3 file??
Also, how can I make it the default when I double click on an audio file?

Thanks for you help,
 Stefan

---

### Post by sanus|art on 2008-05-28
I guess you've already found out how to do this, but for the sake of future searches on the matter I'll post this anyway.

Was looking to try sonata+MPD too.
installation:
```
sudo apt-get install mpd python-soappy libtag1-dev sonata -y
```And specify path to your music directory in:
```
sudo gedit /etc/mpd.conf
```
or copy the conf iguration file to your ~/
```
sudo cp /etc/mpd.conf ~/.mpdconf
```and then edit it.

---

