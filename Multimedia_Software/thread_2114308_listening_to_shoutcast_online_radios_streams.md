---
title: "listening to shoutcast online radios streams"
date: 2013-02-09
forum: Multimedia Software
---

### Post by 3nitysoftwares on 2013-02-09
Hi!

I'm developing a browser for shoutcast radios stations

                **Description**

                          Shoutcast Explorer is a small Open Source browser for shoutcast radios stations.

it find radios stations by genre , download radios stations playlists  and open the default associated program to start the listening.


it works on linux ubuntu/debian and windows .



                 **Homepage**

                          [https://sourceforge.net/projects/shoutcastexplor/](https://sourceforge.net/projects/shoutcastexplor/)



[IMG]http://doc.ubuntu-fr.org/_media/shoutcastexplorer.jpg[/IMG]


Installation:
you need to install this package: [http://sourceforge.net/projects/shoutcastexplor/files/Shoutcast%20Explorer%20v1/shoutcastexplorer.deb/download]("http://sourceforge.net/projects/shoutcastexplor/files/Shoutcast%20Explorer%20v1/shoutcastexplorer.deb/download")


to remove :
sudo apt-get remove ShoutcastExplorer


please share it ( if you find it interesting )  :D

---

### Post by tgalati4 on 2013-02-09
I'm running Linux Mint 14 Mate 64-bit (based on 12.10).  Installed OK with all dependencies satisfied.  Wouldn't load:

tgalati4@Mint14-Extensa ~ $ ShoutcastExplorer
ShoutcastExplorer: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

tgalati4@Mint14-Extensa ~ $ locate libX11
/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1
/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
/usr/lib/x86_64-linux-gnu/libX11.a
/usr/lib/x86_64-linux-gnu/libX11.so
/usr/lib/x86_64-linux-gnu/libX11.so.6
/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
/usr/share/doc/libx11-dev/libX11
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.html
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.html.db
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.pdf.db.gz
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.txt.gz
/usr/share/doc/libx11-dev/libX11/libX11.html
/usr/share/doc/libx11-dev/libX11/libX11.html.db
/usr/share/doc/libx11-dev/libX11/libX11.pdf.db.gz
/usr/share/doc/libx11-dev/libX11/libX11.txt.gz

---

### Post by 3nitysoftwares on 2013-02-09
> **tgalati4 said:**
> I'm running Linux Mint 14 Mate 64-bit (based on 12.10).  Installed OK with all dependencies satisfied.  Wouldn't load:

tgalati4@Mint14-Extensa ~ $ ShoutcastExplorer
ShoutcastExplorer: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

tgalati4@Mint14-Extensa ~ $ locate libX11
/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1
/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
/usr/lib/x86_64-linux-gnu/libX11.a
/usr/lib/x86_64-linux-gnu/libX11.so
/usr/lib/x86_64-linux-gnu/libX11.so.6
/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
/usr/share/doc/libx11-dev/libX11
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.html
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.html.db
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.pdf.db.gz
/usr/share/doc/libx11-dev/i18n/compose/libX11-keys.txt.gz
/usr/share/doc/libx11-dev/libX11/libX11.html
/usr/share/doc/libx11-dev/libX11/libX11.html.db
/usr/share/doc/libx11-dev/libX11/libX11.pdf.db.gz
/usr/share/doc/libx11-dev/libX11/libX11.txt.gz


[B]i found this : please check if you have linux mint 14 64b 12.10 :

[/B]
[http://news.softpedia.com/news/Linux-Mint-14-RC-Doesn-t-Run-32-bit-Applications-306325.shtml](http://news.softpedia.com/news/Linux-Mint-14-RC-Doesn-t-Run-32-bit-Applications-306325.shtml)

"** it seems that the distribution has a problem with 32-bit applications.**
 
 The Linux Mint developers have issued a note stating that the 32-bit support is not included the Linux Mint 14 "

you need to fix your system for multiarch support :

[COLOR=#008080]sudo dpkg --add-architecture i386
 apt update
[/COLOR]

---

### Post by 3nitysoftwares on 2013-02-09
please note actual package for shoutcast explorer is 32b(i386)_so you need multiarch active.


And i'll build a specific package for X64 systems in the week .

---

