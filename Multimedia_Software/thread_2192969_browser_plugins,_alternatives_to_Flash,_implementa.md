---
title: "browser plugins, alternatives to Flash, implementation"
date: 2013-12-10
forum: Multimedia Software
---

### Post by edcompsci on 2013-12-10
Okay so I have tried everything, I think.


browser-plugin-packagekit
VLC
totem-mozilla
browser-plugin-gnash
gxineplugin
gnome-codec-install
libxine1-all-plugins
libxine2-all plugins
libjpf-java
libjs-gordan
xmms2-plugin-flv
avidemux-plugins-common
mozilla-plugin-swfdec
flashplugin-nonfree-extras
mozplugger.so

and hal

and once again Amazon Intant Video isn't working on my laptop. The hal fix worked on my desktop, just not on my Dell laptop.  

questions:
Does having all of these installed effect whether or not any of them work, I mean, do they interfere with each other?
When using one of these .so files, how to I get firefox to use it, when going into Edit-Preferences-Applications and choosing 'other' never chooses what I browse to?

I am on Raring, will moving to Saucy fix this?  Also I am really on Linux Mint 15 (which is built on Raring) with Mate, does this make any difference?


```
sudo apt-get install hal
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe/[all subdirectories]

```

seems to do  nothing where it works on my desktop.  These preprobe and information directories seem to never get anything put in them by the hal command, so what are they for?

```
terminalprompt:~$ ls /usr/lib/mozilla/plugins
gxineplugin.so                         libtotem-gmp-plugin.so
libflashplayer.so                      libtotem-mully-plugin.so
libjavaplugin.so                       libtotem-narrowspace-plugin.so
librhythmbox-itms-detection-plugin.so  packagekit-plugin.so
libtotem-cone-plugin.so


```

---

### Post by edcompsci on 2013-12-10
not solved from anything.  Are we doomed from Amazon Instant Video and crackle now?

---

