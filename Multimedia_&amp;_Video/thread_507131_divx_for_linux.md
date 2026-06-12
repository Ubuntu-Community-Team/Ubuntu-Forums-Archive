---
title: "divx for linux"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by armymedic42 on 2007-07-22
I need to install Divx on my computer, but the only link I've been able to find is [http://www.divx.com/divx/linux/](http://www.divx.com/divx/linux/) and it doesn't seem to exist anymore.  Can someone help?

---

### Post by grayhammer on 2007-07-22
Open a terminal window, then type (or cut and paste) the following:
```
sudo apt-get install ffmpeg gstreamer0.10-ffmpeg
```

This will allow you to watch divx video in totem.

For other players you will need the w32codecs package, which is not in the official repos.

Check here:
[http://medibuntu.sos-sts.com/index.php]("http://medibuntu.sos-sts.com/index.php")

Hope this helps!

---

### Post by Gremlinzzz on 2007-07-22
I use smplayer and the mplayer plugin you cant use two plugins so you would have to uninstall totems plugin.
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
heres where i get my win32 codecs from
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
to watch divx online you need to add these plugins paste them in the terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
if you need the configure setting s for mplayer and plugin it works best when set at X11 video &ALSA audio
:guitar:

i

---

### Post by grayhammer on 2007-07-22
> you cant use two plugins so you would have to uninstall totems plugin.

Strictly speaking, that's not exactly true.  You can have more than one plugin that handles the same type of content.  You can configure how Firefox handles what plugin load for which kind of content by accessing the "Content" tab in the Preferenced dialog, and clicking the "Manage" button.

---

### Post by Deco_21 on 2007-07-22
Try installing automatix that will help you a lot. 
Then try installing the code pack.

OR.

Terminal 

```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

```

---

