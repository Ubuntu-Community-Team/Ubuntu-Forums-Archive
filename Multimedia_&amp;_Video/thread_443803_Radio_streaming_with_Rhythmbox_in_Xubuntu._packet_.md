---
title: "Radio streaming with Rhythmbox in Xubuntu. packet needed?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by ciro314 on 2007-05-14
i have installed rhythmbox from add/remove on xubuntu feisty but radio stations (like [http://www.smgradio.com/core/audio/ogg/live.pls?service=vcbb](http://www.smgradio.com/core/audio/ogg/live.pls?service=vcbb)) do not work.

terminal returns no errors. rhytmbox shows: "playback error".which packet or packets are needed to listen to radio stations on rhythmbox?

thanks in advance.

---

### Post by scrooge_74 on 2007-05-14
Try adding radio stations manually, I have cases when those radio stations are off the net, sometimes perfectly working radio stations stop working for a few days then go back online.

I have even use just xmms to play radio stations

---

### Post by ciro314 on 2007-05-15
thanks for the reply but i only need to know whick packet is needed to listen to radio stations on rhythmbox.

---

### Post by wink on 2007-06-01
I am using plain Ubuntu (not K or X) and am encountering the same problem, the stations I've added result in error ":You do not have a decoder installed to handle this file. You might need to install the necessary plug-ins."

The question is WHICH plug-ins? Other than this "decoder" problem Rhythmbox works fine. Does  anyone have any ideas? 

wink

---

### Post by Gun_Smoke on 2007-11-02
Same here.. 

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.


I'm going to hunt this down.. I will post results.

---

### Post by Gremlinzzz on 2007-11-02
if your using feisty try exaile player and you made need these.
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
also make sure the shout cast plugin is enabled

---

### Post by Gremlinzzz on 2007-11-02
> **Gremlinzzz said:**
> if your using feisty try exaile player and you made need these.
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
also make sure the shout cast plugin is enabled

[http://www.exaile.org/](http://www.exaile.org/)
to get it just
sudo aptitude install exaile

---

### Post by Gun_Smoke on 2007-11-02
Exaile doesn't seem to be working much better.. It doesn't respond to any of the stations enter.

---

### Post by Gun_Smoke on 2007-11-02
Found it.  Missing some media codecs.

---

### Post by likeachild83 on 2007-11-13
I'm having the same problem with [this]("http://www.litefm.com/main.html") site.

---

### Post by Gun_Smoke on 2007-11-13
```
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine1-ffmpeg ogle ogle-gui ubuntu-restricted-extras
```

Add those and try again.. Everything works for me..

---

### Post by Tolak68 on 2008-03-29
Hi gun-smoke

where did you add that command to? Did you do it through shell or what?

New to this mate, appreciate your help.

Thanks

Tolak

---

### Post by Gun_Smoke on 2008-03-29
yes.  aptitude install (cut and paste them all here)  

Or you apt-get if you have been using that.
so something like

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine1-ffmpeg ogle ogle-gui ubuntu-restricted-extras
```

But this was from November I see.. So who's to say what will work?

---

