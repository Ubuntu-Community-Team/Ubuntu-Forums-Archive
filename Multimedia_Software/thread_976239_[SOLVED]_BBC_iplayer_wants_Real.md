---
title: "[SOLVED] BBC iplayer wants Real"
date: 2008-11-09
forum: Multimedia Software
---

### Post by gleble on 2008-11-09
BBC iplayer asks for Real Player but it is already installed. Is there a way I can make it recognise the Real Player?

---

### Post by gandaran on 2008-11-09
which real player you have installed, the one from medibuntu repo? 10 or 11?
you need some sort of plugin for firefox, all I know it only works if you install reaplayer 11 gold and use this guide to set up [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)
I tried it once and works, but I prefer using the mozilla mplayer plugin (remove or disable totem plugin if you install the mozilla mplayer plugin) mplayer is fully compatible with real audio and video.

---

### Post by gleble on 2008-11-11
I installed Real Player 11 Gold
I followed the guide that you linked to but no lu. The plugins are in the plugins folder but Real doesn't recognise them.

I have two installations of Hardy on my laptop. One (23G) plays the BBC i player fine and I notice has lots of plugins. The other one (52G) won't and only has the default plugin. How do I install the relevant plug ins on 52G

---

### Post by abulaafia on 2008-11-11
you also need to install the helix player and codec through Synaptic Package Manager. for some reason it then works. dont really know why :)

---

### Post by gleble on 2008-11-11
Which codec? Helix isn't installed on the working version. I've installed it but it doesn't help.

---

### Post by gandaran on 2008-11-11
> **gleble said:**
> Which codec? Helix isn't installed on the working version. I've installed it but it doesn't help.
helix won't help, cant you find out what mozilla player plugin is installed in the other drive? as I have said on the first post mplayer plugin handles real video and audio very well and is the recommended plugin for firefox
did you run all the commands on that guide for real player mozilla integration?  I tried it once and it did work!

---

### Post by gleble on 2008-11-11
I get this when I try your suggestion. Still no luck
```
neil@neil-laptop:~$ cd /usr/lib/firefox-addons/plugins
neil@neil-laptop:/usr/lib/firefox-addons/plugins$ 
neil@neil-laptop:/usr/lib/firefox-addons/plugins$  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
[sudo] password for neil: 
ln: creating symbolic link `nphelix.xpt': File exists
neil@neil-laptop:/usr/lib/firefox-addons/plugins$  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
ln: creating symbolic link `nphelix.so': File exists
neil@neil-laptop:/usr/lib/firefox-addons/plugins$  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
mv: cannot stat `/usr/lib/totem/gstreamer/libtotem-complex-plugin.so': No such file or directory
neil@neil-laptop:/usr/lib/firefox-addons/plugins$ 
```

---

### Post by gleble on 2008-11-11
Sorted. I looked at thee other installation and real was using libotem_complex_pluugin.so so I installed totem on this installation and suddenly real player started working. It's using nphelix.cs
Thanx for your help

---

### Post by milkwood on 2008-12-11
I'm surprised that Totem can play real audio file(it's a bit crappy though).
But It seems to be not able to play real video file though.
Thanks for your information.

---

