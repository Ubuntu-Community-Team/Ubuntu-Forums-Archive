---
title: "How put totem -xine in lucid"
date: 2010-07-07
forum: Multimedia Software
---

### Post by lcnrj on 2010-07-07
How put totem -xine in lucid
I try [http://www.uluga.ubuntuforums.org/showthread.php?p=8710182](http://www.uluga.ubuntuforums.org/showthread.php?p=8710182)
but I get error. Any other way?

1-with the karmic sources.list and installed the karmic libtotem plparser12-and-libtotem plparser-dev
2-with the lucid sources.list lucid and sudo apt-get install python-support liblircclient-dev libglib2.0-dev \
libirman-dev gnome-pkg-tools libxine-dev libglade2-dev libxml-parser-perl \
libxml2-dev gstreamer0.10-tools librsvg2-dev shared-mime-info libhal-dev \
libtrackerclient-dev libssl-dev gtk-doc-tools-common librsvg2 iso-codes \
libmusicbrainz4-dev gnome-icon-theme intltool dpkg-dev libx11-dev libcairo2-dev \
libdbus-glib-1-dev autotools-dev libgconf2-dev libgtk2.0-dev \
libXtst-dev-dev libxrandr libxxf86vm-dev gnome-doc-utils python-dev python-xdg \
python-apt python-rdflib python-gtk2-dev python-dev python-GObject-gst0.10 \
python-gdbm checkinstall libxine1 libxine1-ffmpeg

---

### Post by lcnrj on 2010-07-07
3 - mkdir totemx_build && cd totemx_build
4-wget [http://ftp.acc.umu.se/pub/GNOME/sources/totem/2.26/totem-2.26.5.tar.gz](http://ftp.acc.umu.se/pub/GNOME/sources/totem/2.26/totem-2.26.5.tar.gz)
5-tar xzvf totem-2.26.5.tar.gz
6-cd totem-2.26.5
7-./configure --enable-xine --disable-browser-plugins --disable-nautilus --with-plugins=none --disable-shared  --enable-xine --disable-browser-plugins --disable-nautilus --with-plugins=none --disable-shared --disable-schemas-install
8-make
9-sudo checkinstall --backup=no --deldoc=yes --pkgname totem-xine --pkgversion 2.30.5 --provides totem-xine --default --deldoc=yes --exclude=/usr/local/share/icons/hicolor/icon-theme.cache --exclude=/usr/lib/python2.6/
10-make install

---

### Post by mc4man on 2010-07-07
I continue to use a totem-xine player, karmic thru maverick. 
(works perfectly in karmic, a minor give back or 2 in lucid and maverick.

To do so requires building the last released source - totem-2.26.5

If you want to do so I'll link to a how to with minor explanation, takes about 15 min, or so

(Though if so, you should  return your sources and packages to normal for lucid..,.

---

### Post by mc4man on 2010-07-07
Since the post previous is using part of the how to here's the link.

It's important to get the right libtotem-plparser-dev  installed - read first half carefully

Note that this page is a bit scattered, using for myself actually

[http://ubuntuforums.org/showthread.php?p=8710182](http://ubuntuforums.org/showthread.php?p=8710182)

I see you've tried it - post your error if you'd like, I've no issue - just did on Maverick, have on lucid

---

### Post by lcnrj on 2010-07-12
log is too big so if you can seen in  [http://oldrockmustard.blogspot.com/2010/07/try-3-totem-xine-in-lucid.html]("http://oldrockmustard.blogspot.com/2010/07/try-3-totem-xine-in-lucid.html")

---

### Post by lcnrj on 2010-07-12
and please in > sudo apt-get install python-support libglib2.0-dev liblircclient-dev \
libirman-dev gnome-pkg-tools libxine-dev libglade2-dev libxml-parser-perl \
libxml2-dev  gstreamer0.10-tools librsvg2-dev shared-mime-info libhal-dev  \
libssl-dev gtk-doc-tools librsvg2-common iso-codes \
libmusicbrainz4-dev gnome-icon-theme intltool dpkg-dev libx11-dev libcairo2-dev \
libdbus-glib-1-dev autotools-dev libgconf2-dev libgtk2.0-dev \
libxtst-dev libxrandr-dev libxxf86vm-dev gnome-doc-utils python-dev python-xdg \
python-apt python-rdflib python-gtk2-dev python-gobject-dev python-gst0.10 \
python-gdbm libxine1 checkinstall libxine1-ffmpeg libtrackerclient-dev
It is with karmic sources.list or some other.

---

### Post by mc4man on 2010-07-12
Whatever possessed you to change your sources to karmic I'm not sure, there was nothing in that post suggesting that.

That post was orig. early in the lucid development when the older libtotem-plparser and -dev where available. (12)
Then lucid updated so I edited in to install  the karmic versions, nothing about changing sources to do so.

Seeing as though there was no interest anyway I only edited in some add. changes, comments every once and a while for maverick ect., though after your post added a 'preamble'.

I think your best bet is to go back to lucid sources, update and upgrade to set your packages right and forget about totem-xine.


If you wish to pursue this still then start over from beginning, read carefully and as far as libtotem-plparser - 

Install build-deps **first**
Then 

Install libtotem-plparser **manually** from link provided - don't remove the lucid version.

Remove the lucid version of libtotem-plparser-dev, (if installed) and **manually** install the karmic version from the link provided.

After done you can let libtotem-plparser-dev be updated to lucid version or just remove - doesn't matter

---

