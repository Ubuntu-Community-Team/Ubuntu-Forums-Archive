---
title: "please help me installing kaffeine + plugins"
date: 2008-07-17
forum: Multimedia Software
---

### Post by hexman2006 on 2008-07-17
please help me installing kaffeine + plugins in ubuntu 8.04 lts
and it would be great if the toutroial with pics

---

### Post by hexman2006 on 2008-07-18
where are you guys?
:(

---

### Post by xc3RnbFO8P on 2008-07-18
Is something not working in Kaffeine?

---

### Post by hexman2006 on 2008-07-18
yes I can't install Kaffeine 0.8.7 released
from this package [http://sourceforge.net/project/showfiles.php?group_id=86937&package_id=90404&release_id=611650](http://sourceforge.net/project/showfiles.php?group_id=86937&package_id=90404&release_id=611650)
and don't know how to install the plugins

---

### Post by xc3RnbFO8P on 2008-07-19
In Synaptic Package Manager:

> Settings> repositories> Ubuntu Software check all

Settings> repositories> Update> check all

In Terminal:

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
> sudo apt-get install libdvdcss2
> sudo apt-get install build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh
> sudo apt-get install w32codecs

In Synaptic Package Manager, install:
(search xine)
> libxine1
libxine1-all-plugins
libxine1-ffmpeg
libxine1-gnome
libxine1-misc-plugins
libxine1-x
libxine-dev

Extract the **Kaffeine 0.8.7** (on desktop)
then in terminal:

> sudo apt-get install build-essential
> cd /home/**your folder**/desktop/Kaffeine 0.8.7
> ./configure
> make
> sudo make install

---

