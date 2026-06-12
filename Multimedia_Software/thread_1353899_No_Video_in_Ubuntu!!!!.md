---
title: "No Video in Ubuntu!!!!"
date: 2009-12-13
forum: Multimedia Software
---

### Post by stormsurge on 2009-12-13
Hey guys! I'm a new Ubuntu 9.10 user and I have a video problem in Ubuntu. I just noticed that I can't play my videos with any media players. At first, I can play my videos but now I can't. I tried Totem, VLC and Kaffein... All of these can't play my videos. Can anyone please help me? Thanks!

---

### Post by markbuntu on 2009-12-13
Try this

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by stormsurge on 2009-12-14
Thanks! I'll see if this could address my problem. Its just weird because for the last 2 weeks of my fresh installation, I did not have any problems with my video then suddenly I encountered this. 
 
To give you a brief background on what particularly is my problem, everytime I double-click (or open) a video file, my video player opens then it immediately closes. 
 
Thank you!

---

### Post by stormsurge on 2009-12-14
By the way, its weird...

I can play my videos in RhythmBox. 

When I play .avi files from a CD here are the results:
1. VLC - Plays audio only
2. Totem - Quits unexpectedly

When playing .mp4 files from my HD, both players quits unexpectedly.

I hope that someone can provide a quick and easy solution on this. Thanks!

---

### Post by fancypiper on 2009-12-14
This guide helped me get multimedia going.  Flash support can be spotty, depending upon the site.

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

If you have a 64 bit processer, try this script for installing flash.
```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

### Post by sdowney717 on 2009-12-14
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

make sure ubuntu restricted extras are installed

---

