---
title: "Can't get embedded video in Firefox"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by themikeflynn on 2006-08-05
Today I set up Dapper Drake on my parents computer and haven't had many problems. I used Automatix, and it worked as expected, but the mplayer firefox mplayer plugin was ineffective. At video sites such as Compfused or Apple Movie Trailers with embedded video, all I get is the white blank box with the green jigsaw puzzle that says basically it doesn't have anything to play it with. I checked, and w32codecs are installed properly. So I tried reinstalling mplayer-plugin, but get the same thing. So then I tried the VLC-plugin, and then the totem-xine-firefox-plugin and get the same results.

I can't figure out why it isn't at least detected by Firefox. :-k I've searched here in these forums, and in Google, and have found people with similar problems. But they all end in something similar to "Eureka!" and I can't find their explanation.

Does anyone know what else I should do before I just ditch the computer and leave them without embedded video?

---

### Post by Shinzetsu on 2006-08-05
Click on the jigsaw and see what plugins it needs, then click the manual install button and itll take  you to a site

---

### Post by themikeflynn on 2006-08-06
Well that takes me to the Microsoft WMV download site which obviously isn't much help. Are there any other suggestions? My computers components are supported by Linux drivers so I don't see why this wouldn't be working.

---

### Post by crispy_420 on 2006-08-06
Sounds like you need to install the w32 codecs package. For that you will need some other repos. Search the forums for the PLF repos.

---

### Post by ermannobonifazi on 2006-08-06
I solved the probelm using mplayer plugin for mozilla.
Install mozilla-mplayer from apt-get or synaptic.
Check that you have under your firefox/plugin directory, usually /usr/share/firefox/plugin the following list:

playerplug-in-gmp.xpt  mplayerplug-in.so
mplayerplug-in-qt.so    mplayerplug-in-wmp.so
mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt

they usually are a symlink to /usr/lib/mozilla/plugin

---

### Post by markmaus on 2006-08-06
I'm having the same problem.  I can't play embedded video in firefox.  I have checked and I do have mozilla-mplayer installed and all of the sym-links are present in /usr/lib/firefox/plugin.  I used Automatix and installed all the audio-video stuff.  I can't play any video clips from here:
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)
I can play video from reuters:
[http://today.reuters.com/tv/videoChannel.aspx?storyId=f789a0035e3216372f253b63bcc3e13448971e96](http://today.reuters.com/tv/videoChannel.aspx?storyId=f789a0035e3216372f253b63bcc3e13448971e96)
Any help is appreciated.

---

### Post by markmaus on 2006-08-06
Also, when I try the Windows Media clips here:
[http://movies.yahoo.com/movie/1808411970/trailer](http://movies.yahoo.com/movie/1808411970/trailer)
I only get the audio portion (no video)

---

### Post by markmaus on 2006-08-06
This is wierd.  All of the types of streaming video work in Opera.  So I must have a problem in Firefox's setup.

---

