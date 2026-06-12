---
title: "Cannot play Divx files on Kubuntu, Tried the HowTo...."
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by Soglad on 2007-07-11
Hi, I've tried the HowTo on playing Divx files about 3 times now and I still can't play them. First time I couldn't get MediaPlayerConnectivity to recognize Divx files, then I got that working, but no matter what program I tell it to open with Firefox just keeps saying there's a missing plugin and tells me to search for one (which there isn't). I've installed multiple programs and tried getting MediaPlayerConnectivity to open them, but to no avail.

PLEASE help me here!

I hate having to use Windows for anything!

Soglad.

---

### Post by Gremlinzzz on 2007-07-11
You have to install mplayer plugin and uninstall totem plugin
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
good for all formats off line smplayer
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
codecs if you need em 
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
:guitar:

---

### Post by pinoyskull on 2007-07-11
or if you're not comfortable with CLI you can try installing Automatix and install the codecs from there :)

---

### Post by Gremlinzzz on 2007-07-11
I would feel uncomfortable using Automatix
:guitar:

---

### Post by compiledkernel on 2007-07-11
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

:)

---

