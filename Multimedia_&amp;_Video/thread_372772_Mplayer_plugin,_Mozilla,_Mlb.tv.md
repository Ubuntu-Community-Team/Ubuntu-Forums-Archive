---
title: "Mplayer plugin, Mozilla, Mlb.tv"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by grogger13 on 2007-02-28
this was the first time since i have switched to linux that i used Mlb.tv and i notice that the volume control is not there as well as the video size looks skewed.

[IMG]http://i177.photobucket.com/albums/w214/grogger13/Screenshot-2.png[/IMG]

see the gray area under the video and only a couple of buttons,  Is there a better plug in that i can find or something i can do to make this player better, becuase the quality is noticable worse than on windows.  I dont want to boot into windows every time i want to watch baseball or other video.

---

### Post by wesley_of_course on 2007-03-02
Wesley here ;

 Have you tried ;      [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by grogger13 on 2007-03-11
on other videos i also still get the right part of the video cut off, i did install easyubunut.

---

### Post by lucky7 on 2007-03-18
I have tried pretty much everything I have found in these forums but I cannot even get video working for mlb.tv.  I have tried using easyubuntu, I have installed the mediaplayerconnectivity plugin for firefox, I have tried using gmplayer and mplayer, and all i get is the audio.  It doesn't even look like it is trying to play the video since there is some logo in the middle of screen (film strip with a music note in the corner and a stop or play symbol).

---

### Post by eltaito on 2007-04-03
This is my second year using mlb.tv on Ubuntu and I usually have a pretty easy time of getting live games to play.  This has worked for me from Breezy to Edgy:  FIrst make sure you have all the restricted formats installed, easily done with automatix or easyubuntu.......then install mplayer and the mozilla-mplayer plugin from synaptic if you haven't already......then I remove anything that has "totem" in the name from my firefox plugins folders (can't ever seem to get totem to do what I want and it sometimes interferes with the mozilla mplayerplug-in):

/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins

(not sure if you need to remove totem plugins from all of those but I'm from the "better safe than sorry" school of thought)

after that I edit my mplayerplug-in file :  **/etc/mplayerplug-in.conf  **  (sorry for leaving that out the first time around allst896  - thanks for pointing it out)

change "#noembed-0" to "noembed-1" (uncomment and change value to 1).  -this allows mplayer to open the video stream in an external window instead of embedded in mlb's default flash window which seems to have all sorts of problems for me.....

I also uncomment #vo=xv,x11" (just remove the "#") and "#autosync"

This should let you view live games in an external re-sizable window

hope this method works for you


**LETS GO METS!**

--Some people have success simply using the [MediaPlayerConnectivity]("https://addons.mozilla.org/en-US/firefox/addon/446") plug-in for firefox but it has never worked well with mlb.tv for me....so I don't really recommend it.

---

### Post by allst896 on 2007-04-08
Where is the mplayer plug-in directory located?

Thanks.

---

### Post by allst896 on 2007-04-08
--

---

### Post by eltaito on 2007-04-11
sorry for the late reply.....haven't been paying attention...once baseball starts up I tend to get a little too absorbed in the season...anyways I'm sorry I left that out......its kind of important...haha.....the mplayerplug-in file that i edited is located at:

/etc/mplayerplug-in.conf


I'll try and edit my above post to eliminate any confusion......I'll also try to check back more often if anyone has problems getting this method to work for them

---

### Post by gregalynch on 2008-03-30
I can't get firefox to even use the mplayer plugin for wmv or wma files.  when i try to change the settings under preferences it only lists 'windows media player plugin' as an option for the plugin to open these files.  any ideas on how i might fix this?

---

### Post by zwanzig on 2008-06-30
> **gregalynch said:**
> I can't get firefox to even use the mplayer plugin for wmv or wma files.  when i try to change the settings under preferences it only lists 'windows media player plugin' as an option for the plugin to open these files.  any ideas on how i might fix this?

try:
```

sudo apt-get remove totem-mozilla
sudo apt-get remove mozilla-plugin-vlc
sudo apt-get install mozilla-mplayer

```
and restart browser

---

