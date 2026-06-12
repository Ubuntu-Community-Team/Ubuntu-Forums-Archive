---
title: "Rhythmbox style mediaplayer for DTS"
date: 2011-04-02
forum: Multimedia Software
---

### Post by plo on 2011-04-02
Hi!

I am looking for a Rhythmbox style mediaplayer that plays dts music.
VLC works excellent but it would be very nice with a GUI more suited for a music library (Artist/Album/Genre/..).

Any suggestions?

Note. I have a dual screen setup and I have the music on a separate 8" touch screen (MyhtTv on the other screen - the tv) so if there is a software handling both reular mp3/flac/ogg music and dts with a touch screen adapted gui that would be ideal.

---

### Post by krupier on 2011-08-10
Hi,

It's possible! Yesterday I found rhythmbox from Natty can play DTS files!

I'm just switched back to Maverick (wasn't very happy with Natty due to some bugs/features  and complete lack of support). Anyway, sitting on Ubuntu 10.10 can listen to DTS through gstreamer and that's what you wanted. 

For those on 10.10 here's how:
being root (sudo su)
```
mv -v /etc/apt/sources.list /etc/apt/sources.list.save && sed s/maverick/natty/g /etc/apt/sources.list.save > /etc/apt/sources.list
apt-get update
apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
mv -v /etc/apt/sources.list.save /etc/apt/sources.list
apt-get update
```Now, after this **evince**, **rhythmbox** and some other apps stopped working due to a bug (as I think) in **libjpeg62** which is found in */usr/lib/i386-linux-gnu* instead of /usr/lib/ so a _symlink is needed_:
```
ln -s /usr/lib/i386-linux-gnu/libjpeg.so.62.0.0 /usr/lib/libjpeg.so.6
```And that's all! Enjoy :-)

---

