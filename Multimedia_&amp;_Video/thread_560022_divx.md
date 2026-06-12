---
title: "divx"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by alsehendo34 on 2007-09-25
I have the DivX® Web Player plugin installed in 7.04 ubuntu and firfox 2.0.0.6 but videos are just color blurs from [http://stage6.divx.com/](http://stage6.divx.com/).

Any ideas?

---

### Post by misfitpierce on 2007-09-25
EasyUbuntu can set up totem to play divx everything auto. Found in sig.

---

### Post by Gremlinzzz on 2007-09-25
i use mplayer plugin works good but if you want to use it i would uninstall other plugins like totem.once mplayer plugin is install put these commands in the terminal.
installing mplayer plugin
sudo apt-get install mozilla-mplayer
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

