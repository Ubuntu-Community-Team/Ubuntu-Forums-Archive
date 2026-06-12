---
title: "[SOLVED] adobe flash player"
date: 2008-09-28
forum: Multimedia Software
---

### Post by vandreaddita on 2008-09-28
hey guys, im a total noob here, im trying to install adobe flash player, so i can watch videos on youtube, how do i install this thing, i downloaded the .tar.gz

---

### Post by aysiu on 2008-09-28
> **vandreaddita said:**
> hey guys, im a total noob here, im trying to install adobe flash player, so i can watch videos on youtube, how do i install this thing, i downloaded the .tar.gz
Delete the .tar.gz and follow this tutorial:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Post back here if you have further questions or run into problems.

---

### Post by vandreaddita on 2008-09-28
well the instructions didnt really help, cause it said i already have nonfree installed.

---

### Post by aysiu on 2008-09-28
> **vandreaddita said:**
> well the instructions didnt really help, cause it said i already have nonfree installed.
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? The second command may take a few minutes to execute. Be patient. ```
uname -m
sudo updatedb
locate libflash
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
```

---

### Post by frankleeee on 2008-09-28
> **vandreaddita said:**
> well the instructions didnt really help, cause it said i already have nonfree installed.

Have you installed Ubuntu restricted extras in add remove, if your using gstreamer you might add those there as well and vlc.

---

### Post by vandreaddita on 2008-09-28
james@Jamesbeast:~$ uname-m
bash: uname-m: command not found
james@Jamesbeast:~$ uname -m
i686
james@Jamesbeast:~$ sudo updatedb
james@Jamesbeast:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so
/home/james/Desktop/install_flash_player_9_linux/libflashplayer.so
james@Jamesbeast:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
james@Jamesbeast:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 156
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.48.0.2+really0ubuntu12
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplugin (<< 6), xfs (<< 1:1.0.1-5), flashplayer-mozilla
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
james@Jamesbeast:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
james@Jamesbeast:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
james@Jamesbeast:~$

---

### Post by aysiu on 2008-09-28
You're using Ubuntu 7.10, and there used to be a bug that had Flash not actually install (some MD5sum mismatch error) even if it said it was installed, and you appear to be a victim of that.

Try installing Flash manually, then. These instructions should help with that:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by vandreaddita on 2008-09-28
> **aysiu said:**
> You're using Ubuntu 7.10, and there used to be a bug that had Flash not actually install (some MD5sum mismatch error) even if it said it was installed, and you appear to be a victim of that.

Try installing Flash manually, then. These instructions should help with that:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

worked like a charm, thanks

---

