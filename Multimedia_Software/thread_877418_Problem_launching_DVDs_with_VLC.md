---
title: "Problem launching DVDs with VLC"
date: 2008-08-01
forum: Multimedia Software
---

### Post by silkstone on 2008-08-01
I've just installed vlc to play DVDs with menu support etc. I've used vlc on previous versions of Ubuntu, but have used Totem so far with Hardy. Totem has worked fine - insert a DVD and it starts and plays, although I usually have to use the file menu to get the main video to play as there is no menu support in totem-gstreamer.

I installed vlc like this...

sudo apt-get install vlc
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

(Some of those were already installed to play DVDs on Totem.)

I edited /etc/gnome/defaults.list to show 'vlc.desktop' instead of 'totem-desktop' in the appropriate video entries.

When I insert a DVD, vlc starts but hangs without even showing the video frame. Also, if I right-click on the DVD icon and select 'Play with vlc' the same thing happens - vlc starts but hangs, and I have to kill it.

However, if I start vlc first, and then go File > Play Disk and select the DVD disk, everything works fine.

Any ideas on why it won't autoplay?

---

### Post by mc4man on 2008-08-01
Try going to edit menus, expand sound and video on left side and on the right side r. click vlc -> properties -> launch command. Change it to > vlc %m.

Here's how i usually set up vlc
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by silkstone on 2008-08-01
Brilliant! That's all I needed - change vlc %U to vlc %m and it works just fine. Many thanks!

---

