---
title: "music player crossfeed plugin bs2b"
date: 2010-03-24
forum: Multimedia Software
---

### Post by gracchus on 2010-03-24
I've been trying to get this plugin to work with karmic:[http://bs2b.sourceforge.net/](http://bs2b.sourceforge.net/)

I tried the xmms one but the flac plugin for xmms is missing the dependacy libflac7 and there is no source availible as far as I can tell.

I tried the audacious one but it isn't compatible with audacious-2.2 and audacious1.5.1 crashes with a segment fault on karmic.

I also found this repository:[https://launchpad.net/~lazka/+archive/dumpingplace]("https://launchpad.net/%7Elazka/+archive/dumpingplace")

It has a plugin called gstreamer0.10-bs2b which sounds like the same thing I've been working on but I tried a bunch of music players (hythmbox, audacious, xmms2, songbird, and quodlibet). None seem to have anyway to enable the plugin.  

Can I get some advice on a fix for this plugin with karmic.

---

### Post by coolcaseley67 on 2010-03-24
Hi  

-try looking for the plug-in va synaptic manger .
-gstreamer is avalbe by  synaptic manger .
- to enable the plug in rhythmbox in one of  the menu at the top choose plug-in's 

see if this helps :  [http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html](http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html)


hope it helps

---

### Post by alfredgina on 2010-03-24
does it support all music file types?


------------------

[frameless design]("http://showerdesignsource.com/frameless-shower-design/")

---

### Post by coolcaseley67 on 2010-03-24
Hi 

-what just to play anything ?
- use vlc player go to :[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
-  and install Ubuntu restricted extras 

hope it helps

---

### Post by lazka on 2010-03-24
> **gracchus said:**
> 
It has a plugin called gstreamer0.10-bs2b which sounds like the same thing I've been working on but I tried a bunch of music players (hythmbox, audacious, xmms2, songbird, and quodlibet). None seem to have anyway to enable the plugin.

Enable:
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed ! autoaudiosink"

```
Disable: 
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```

Works with all gstreamer players (Rhythmbox, Banshee, Quod Libet, Exaile(should work, but doesn't)). You probably have to restart the player after switching it on/off.

I will create a Quod Libet plugin in the next weeks...

HTH

---

### Post by coolcaseley67 on 2010-03-24
> **lazka said:**
> Enable:
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed ! autoaudiosink"

```Disable: 
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```Works with all gstreamer players (Rhythmbox, Banshee, Quod Libet, Exaile(should work, but doesn't)). You probably have to restart the player after switching it on/off.

HTH
  nice cool fix ! :popcorn:

---

### Post by gracchus on 2010-03-25
Thanks Lazka, I can deffinately tell a difference on songs with high stereo seperation.  They sound a lot better now.

---

### Post by Taemojitsu on 2010-08-24
> **gracchus]
I also found this repository:[https://launchpad.net/~lazka/+archive/dumpingplace](https://launchpad.net/~lazka/+archive/dumpingplace)

It has a plugin called gstreamer0.10-bs2b which sounds like the same thing I've been working on but I tried a bunch of music players (hythmbox, audacious, xmms2, songbird, and quodlibet). None seem to have anyway to enable the plugin. [/quote]
[QUOTE=lazka said:**
> Enable:
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed ! autoaudiosink"

```
Disable: 
```
gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```

Works with all gstreamer players (Rhythmbox, Banshee, Quod Libet, Exaile(should work, but doesn't)). You probably have to restart the player after switching it on/off.

I will create a Quod Libet plugin in the next weeks...

HTH
Thank you

---

