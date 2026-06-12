---
title: "I Need To Link The Realplayer Plugins To Opera / Firefox."
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by tickmike on 2007-01-18
Hello All.
I have installed Firefox 2 and Opera 9.1 also Realplayer 10, on Edgy Eft.
Using the BBC news web site to test the video it wanted to use 'totem' so I have uninstalled it with 'synaptic'.
Realplayer needs the plugins to be installed.
I need to make some 'symlinks' from realplayer to the opera and firefox plugin folders.
would someone be so kind to give me -s code please for terminal.

Michael

---

### Post by stulesnett on 2007-01-19
I seem to having the same problems and now I've lost all audio:
I have tried the (Add/Remove) not successful,
I have used the locate command and the remove apt command but nothing.
Attached is the locate messages:
slesnett@dig-charlee:/srv$ sudo apt-get remove realplay
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package realplay
slesnett@dig-charlee:/srv$ locate realplay
/srv/share/hxsetup/share/icons/realplay_16x16.png
/srv/share/hxsetup/share/icons/realplay_32x32.png
/srv/share/hxsetup/share/icons/realplay_48x48.png
/srv/share/hxsetup/share/icons/realplay_192x192.png
/srv/share/hxsetup/share/realplay
/srv/share/hxsetup/share/realplay/logo.png
/srv/share/hxsetup/share/realplay/icon.png
/srv/share/hxsetup/share/realplay/prefs_general.png
/srv/share/hxsetup/share/realplay/setup_title.png
/srv/share/hxsetup/share/realplay/setup_welcome.png
/srv/share/hxsetup/share/realplay/embedded_logo.png
/srv/share/hxsetup/share/realplay.png
/srv/share/hxsetup/share/realplay.desktop
/srv/share/hxsetup/share/realplay.applications
/srv/share/hxsetup/share/realplay.keys
/srv/share/hxsetup/share/realplay.mime
/srv/share/hxsetup/share/realplay.xml
/srv/share/hxsetup/realplay.bin
/srv/share/hxsetup/realplay
/usr/share/icons/crystalsvg/16x16/apps/realplayer.png
/usr/share/icons/crystalsvg/32x32/apps/realplayer.png
/usr/share/icons/crystalsvg/scalable/apps/realplayer.svgz
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/realplay.png
/usr/share/icons/HighContrastLargePrint/48x48/apps/realplay.png
/usr/share/app-install/desktop/realplayer.desktop
/usr/share/app-install/desktop/realplay.desktop
/usr/share/app-install/icons/realplayer-icon.xpm
/usr/share/app-install/icons/realplay.png
/usr/share/ubuntu-docs/ubuntu/menus/C/realplayer.xml
/usr/lib/opera/plugins/share/icons/realplay_16x16.png
/usr/lib/opera/plugins/share/icons/realplay_32x32.png
/usr/lib/opera/plugins/share/icons/realplay_48x48.png
/usr/lib/opera/plugins/share/icons/realplay_192x192.png
/usr/lib/opera/plugins/share/realplay
/usr/lib/opera/plugins/share/realplay/logo.png
/usr/lib/opera/plugins/share/realplay/icon.png
/usr/lib/opera/plugins/share/realplay/prefs_general.png
/usr/lib/opera/plugins/share/realplay/setup_title.png
/usr/lib/opera/plugins/share/realplay/setup_welcome.png
/usr/lib/opera/plugins/share/realplay/embedded_logo.png
/usr/lib/opera/plugins/share/realplay.png
/usr/lib/opera/plugins/share/realplay.desktop
/usr/lib/opera/plugins/share/realplay.applications
/usr/lib/opera/plugins/share/realplay.keys
/usr/lib/opera/plugins/share/realplay.mime
/usr/lib/opera/plugins/share/realplay.xml
/usr/lib/opera/plugins/realplay.bin
/usr/lib/opera/plugins/realplay
/usr/lib/opera/plugins/realplay.bak
/home/slesnett/.realplayerrc
slesnett@dig-charlee:/srv$
---------------------------------------------------------------------
any help would be appreciated.

---

### Post by RomeReactor on 2007-01-19
stulesnett, try searching for RealPlayer in Synaptic, then uninstall it (choose **completely remove**). tickmike, sorry i can't help you with the links, as i don't have realplayer installed; however, have you considered installing the mozilla-mplayer plugin for Firefox?

---

### Post by tickmike on 2007-01-19
Hi .
Having made a mess installing Realplayer and ended up with it installed in various locations I had to use 

sudo gnome-search-tool

That opens search tool in root, I did a search for 'RealPlayer' and sent 163 files to the wastebin.

Then reinstalled   see 
   [http://www.debianadmin.com/install-opera-web-broweser-and-realplayer-10-in-ubuntu.html](http://www.debianadmin.com/install-opera-web-broweser-and-realplayer-10-in-ubuntu.html)

Hope this helps.

But this is not answering my question !,can anyone help me with symlinks..

---

### Post by RomeReactor on 2007-01-19
Well, to make a symlink, let's imagine this: i want to make a link from

```
/home/sho/.opera/plugins/libflashplayer.so
```

to:

```
/home/sho/.real/plugins
```

then i would write in a terminal:

```
ln -s /home/sho/.opera/plugins/libflashplayer.so /home/sho/.real/plugins
```

Just an example :D

---

### Post by stulesnett on 2007-01-20
Thanks people, I'll give them a try and let all know it worked.

Stu

---

