---
title: "Nasa Tv"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by Don DeGregori on 2008-02-11
How does one watch live NASA TV, that is the Space Shuttle and ISS? The mission is going on right now. I bring up the correct web pageonUbuntu, [http://www.nasa.gov/multimedia/nasatv/index.html](http://www.nasa.gov/multimedia/nasatv/index.html) and all I get is quick flash of a picture of working in space. I believe the problem is no codec available for Real Video Player in Linux or Ubuntu. Is there a work-around?

donde

---

### Post by solitaire on 2008-02-11
I've been watching it fine in my install (7.10)


Just tunes into Nasa TV and i'm getting the same as you

it's not your problem it's NASA's problem

try view in "movie player" that works for me

*note* 
NASA TV Is very unreliable at the best of times!!

---

### Post by gandaran on 2008-02-11
> **Don DeGregori said:**
> How does one watch live NASA TV, that is the Space Shuttle and ISS? The mission is going on right now. I bring up the correct web pageonUbuntu, [http://www.nasa.gov/multimedia/nasatv/index.html](http://www.nasa.gov/multimedia/nasatv/index.html) and all I get is quick flash of a picture of working in space. I believe the problem is no codec available for Real Video Player in Linux or Ubuntu. Is there a work-around?

donde

I use gxine, it works very well with real video, but you have to dig up the url and make a play list then just fire-up gxine and select nasa tv
I used to watch nasa tv with totem gstreamer, but it doesn't work anymore, nasa must have changed codecs.

---

### Post by solitaire on 2008-02-11
I'm using Totem gStreamer and it does work but very tempromental.
I was watching them trying to attach the arm to the new module this afternoon on the website, but it's not working for me now.

But works when i right click and view using "Media player"

---

### Post by Don DeGregori on 2008-02-15
I'm now getting NASA TV using TOTEM Movie Player with add-on of GStreamer 0.10.14 and GNOME. I use this URL to bring up the stream.

mms://209.73.189.102/bcenc202056?Stream &#8230; ent=149773

NASA TV sure make Linux people work at it ! I don't think Real Player or Microsoft likes us very well. I don't either !

Thanks all...donde

---

### Post by brodiepearce on 2008-02-20
Possibly not the ideal solution, but VLC works fine if you can get the URL for the stream you want.  (The 'Download Embedded' plugin for firefox gives you a list of all embedded objects).

---

### Post by Marinus777 on 2008-03-11
Try

```
http://www.nasa.gov/multimedia/nasatv/index.html?skipIntro=1
```

(that will skip the intro and therefore the verification script)

From the source you can get all stream url's;

```
http://www.nasa.gov/55644main_NASATV_Windows.asx
http://www.nasa.gov/ram/35037main_portal.ram
http://www.nasa.gov/qtl/151335main_NASA_TV_QT.qtl
```

Paste the .asx url in Open | 'Network'  - Customize

Good luck :)

---

### Post by guilbep on 2008-05-25
I have an other solution.. you can download the realplayer software for linux on their website.. hence you do that you have to go in the default location.  /opt/real/RealPlayer/plugins/  for example, and then copy all the .so (which are needed to firefox/mozilla to be a plugin) in the mozilla directory in you home directory .. for example  ~/.mozilla/plugins/  or /home/yourname/.mozilla/plugins (which is the same).. then restart firefox and you should see the web tv thing on their web site.

please forgive my bad english.. and if you have time correct me ! it'll be useful!

---

### Post by don_bubnekovich on 2008-05-31
I installed through Synaptic Package Manager Gecko-mediaplayer.  This allows me to see NASA TV from their website on Firefox2.  I also uninstalled all other media players except for VLC (don't know if this is required).  

The GNOME MPlayer that also gets downloaded as part of the Gecko install emulates QuickTime, RealPlayer & Windows Media Players.  NASA TV's website is looking for what player you are using prior to sending out the stream.  If it can't determine that it will send you to the help page.

---

