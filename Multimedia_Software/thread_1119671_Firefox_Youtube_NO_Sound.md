---
title: "Firefox Youtube NO Sound"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Th1eF` on 2009-04-08
im running ubuntu 8.10 on amd64, when i have update to 8.10 i have no video and no sound when i was visiting the youtube.

a search on the net solve me the video problem 
the solution was:
wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh

but now i still have no sound.

is there any solution??

-thanks indeed

---

### Post by bumanie on 2009-04-08
This is what I used a few days ago to get flash working on 64bit. It is a lot of commands.
First remove flash previously installed
> sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper> sudo rm -f /usr/lib/mozilla/plugins/*flash*> sudo rm -f ~/.mozilla/plugins/*flash*> sudo rm -f /usr/lib/firefox/plugins/*flash*> sudo rm -f usr/lib/firefox-addons/plugins/*flash*> sudo rm -rfd /usr/lib/nspluginwrapperNext > cd ~> wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)> tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz> sudo cp libflashplayer.so /usr/lib/mozilla/plugins/Then > sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/> sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/xulrunner-addons/plugins/> sudo rm-rf libflashplayer.so> sudo rm -rf libflashplayer-10.0.d20.7.linux-86_64.so.tar.gzAnd as long as I have the correct syntax, you tube should work again once you restart firefox. Hope it works

---

### Post by connorh123 on 2009-04-08
A little off topic, but this applies to me, only I can't watch videos. It just shows up as as gray play button. Anyone else share this problem?

---

### Post by bumanie on 2009-04-08
for the above to work, you have to copy and paste the commands to a text document as firefox must be closed for this to work.

---

### Post by Th1eF` on 2009-04-08
yeaaaa....i can hear again...

thanks a lot 

bumanie :guitar: rocks

---

