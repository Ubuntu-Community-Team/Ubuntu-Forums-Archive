---
title: "[SOLVED] Cannot install Flash player in Firefox!"
date: 2008-10-28
forum: Multimedia Software
---

### Post by psmaster on 2008-10-28
Just as the title says, I tried to install flash earlier and I have never been able to get it to work at all! Need help, my girlfriend is getting pissed at me because she wants to watch youtube videos :P

Any help would be greatly appreciated.

---

### Post by aysiu on 2008-10-28
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate libflash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` Warning: the first command may take a few minutes to execute.

---

### Post by jseabolt on 2008-10-29
> **psmaster said:**
> Just as the title says, I tried to install flash earlier and I have never been able to get it to work at all! Need help, my girlfriend is getting pissed at me because she wants to watch youtube videos :P

Any help would be greatly appreciated.

This being my 2nd day experimenting with Ubuntu, Flash Player so far is the only plug-in I've been able to install.

I went to YouTube and it said I needed the plug-in. I clicked on their link and it directed me to Adobe's website. 

At first I didn't think it worked because I didn't see the "movie" but when I went back to YouTube later I was able to watch videos.

The Adobe flash player plug-in is a bit flakey. It took me a few times to install it on a Windows 98 machine.

I don't know if that helps or not.

---

### Post by psmaster on 2008-10-29
Aysiu:

```

psmaster@conquest:~$ sudo updatedb
[sudo] password for psmaster: 
psmaster@conquest:~$ locate libflash
/home/psmaster/.mozilla/plugins/libflashplayer.so
/home/psmaster/Desktop/other/install_flash_player_10_linux/libflashplayer.so
/home/psmaster/Desktop/other/install_flash_player_9_linux/libflashplayer.so
/usr/lib/libflash.so.0
/usr/lib/libflash.so.0.13.0
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/mozilla/plugins/libflash-mozplugin.so
/usr/lib/mozilla-firefox/plugins/libflash-mozplugin.so
/usr/lib/openoffice/program/libflash680li.so
/usr/share/doc/libflash-mozplugin
/usr/share/doc/libflash0c2
/usr/share/doc/libflash-mozplugin/README
/usr/share/doc/libflash-mozplugin/README.Debian
/usr/share/doc/libflash-mozplugin/changelog.Debian.gz
/usr/share/doc/libflash-mozplugin/copyright
/usr/share/doc/libflash0c2/README
/usr/share/doc/libflash0c2/README.Debian
/usr/share/doc/libflash0c2/changelog.Debian.gz
/usr/share/doc/libflash0c2/copyright
/usr/share/lintian/overrides/libflash-mozplugin
/var/cache/apt/archives/libflash-mozplugin_0.4.13-9ubuntu1_i386.deb
/var/cache/apt/archives/libflash0c2_0.4.13-9ubuntu1_i386.deb
/var/lib/dpkg/info/libflash-mozplugin.list
/var/lib/dpkg/info/libflash-mozplugin.md5sums
/var/lib/dpkg/info/libflash-mozplugin.postinst
/var/lib/dpkg/info/libflash-mozplugin.postrm
/var/lib/dpkg/info/libflash-mozplugin.shlibs
/var/lib/dpkg/info/libflash0c2.list
/var/lib/dpkg/info/libflash0c2.md5sums
/var/lib/dpkg/info/libflash0c2.postinst
/var/lib/dpkg/info/libflash0c2.postrm
/var/lib/dpkg/info/libflash0c2.shlibs
psmaster@conquest:~$ uname -m
i686
psmaster@conquest:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
psmaster@conquest:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
psmaster@conquest:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
psmaster@conquest:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 176
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.6.0-2ubuntu1
Replaces: swf-player
Provides: swf-player
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.14), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), liboil0.3, libpango1.0-0 (>= 1.20.0), libswfdec-0.6-90
Conflicts: swf-player
Description: Mozilla plugin for SWF files (Macromedia Flash)
 A GTK+ and swfdec based Mozilla plugin for SWF files,
 commonly known as Macromedia Flash animations.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Swfdec player for Adobe/Macromedia Flash
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>

```

---

### Post by aysiu on 2008-10-29
Well, it seems you have three Flash plugins installed - one local Adobe, one universal Adobe, and one SWFdec.

So let's get rid of two of them: ```
sudo apt-get remove swfdec-mozilla
mv /home/psmaster/.mozilla/plugins/libflashplayer.so /home/psmaster/.local/share/Trash/files/
``` and then let's reinstall the universal one just to be sure: ```
sudo apt-get install --reinstall flashplugin-nonfree
``` Then close Firefox and reopen it and see if Flash is okay or not.

If it's not, I suspect it may have something to do with all that *mozplugin* stuff... not sure how to fix that, though.

---

### Post by gandaran on 2008-10-29
no wonder it won't work! with so many flash packages installed? this must be a record!
you can start removing some, open synaptic package manager, use the search box, type flash, see what come up installed.
packages you have to remove, libflash-mozplugin, swfdec-mozilla plugin and flasplugin-nonfree and libflashsupport if it's installed.
just leave the flash installed in home .mozilla folder, just make sure it's flash 10

---

### Post by aysiu on 2008-10-29
> **gandaran said:**
> no wonder it won't work! with so many flash packages installed? this must be a record!
you can start removing some, open synaptic package manager, use the search box, type flash, see what come up installed.
packages you have to remove, libflash-mozplugin, swfdec-mozilla plugin and flasplugin-nonfree and libflashsupport if it's installed.
just leave the flash installed in home .mozilla folder, just make sure it's flash 10
That could work also.

Do either what I suggested or what gandaran suggested.

Do not do both.

---

### Post by psmaster on 2008-10-29
It works! Thanks! I did what aysiu said to do because his was the first one I saw :P
I have only been using Linux since Ubuntu 7.04, so I am kind of a noob :P
Thanks guys!

---

