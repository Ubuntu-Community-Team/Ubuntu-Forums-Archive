---
title: "DVD's won't play"
date: 2009-06-15
forum: Multimedia Software
---

### Post by GMD on 2009-06-15
Hello,

My DVD mounts, but the player (Movie Player, Movie Player Gstreamer, Xine, and VLC Media Player) opens for a second or two and then closes, without playing the DVD.

I think I've gone through all the standard procedures for troubleshooting. My actions are listed below.

Thank-you in advance for any suggestions.


Actions:
 
Installed libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad, and gstreamer0.10-plugins-ugly packages.

Ran sudo /usr/share/doc/libdvdread4/install-css.sh

Ran sudo apt-get install libdvdread4

Ran sudo /usr/share/doc/libdvdread4/install-css.sh

Added Medibuntu to sources.list by running sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Added the GPG key by running sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Installed libdvdcss2 by running sudo apt-get install libdvdcss2

Installed the w32codecs by running sudo apt-get install w32codecs

Removed the swfdec-gnome package

Made sure mozilla-plugin-vlc, vlc, vlc-nox, and vlc-plugin-pulse are installed

Made sure totem, totem-common, totem-gstreamer, totem-mozilla, totem-plugins, totem-plugins-extra, and totem-xine are installed

---

### Post by mc4man on 2009-06-15
When players open and close quickly (crash) most times it's the audio and or video output being used.

I don't use jaunty but i'd say the defaults would be pusleaudio and Xv.

You could try opening vlc - tools - preferences and click the video icon, for 'output' maybe try X11 and click save.

otherwise start vlc from the terminal with this, open the dvd (media -> open disc) and look thru the output for some info,

```
vlc -vv
```

---

### Post by GMD on 2009-06-15
You're a star!

I changed the VLC video output from default to X11 and it worked.

Thanks!

---

