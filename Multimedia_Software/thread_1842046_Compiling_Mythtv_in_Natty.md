---
title: "Compiling Mythtv in Natty"
date: 2011-09-10
forum: Multimedia Software
---

### Post by Gustra on 2011-09-10
Hi forum,

I have just upgraded my backend server from 10.04 to 11.04 and having problems with mythtv-backend not listening on the configured port 6543. I found two possible solution after googling (adding server host ip to /etc/hosts, and checking LostHostName), but none of these have worked. mythtv-backend refuses to listen on the configured port. Since I'm a developer I thought I'd simply add some traces to the source and recompile, but that's where it stops:

```
gunnar@lynx:/opt/build$ sudo apt-get build-dep mythtv
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
gunnar@lynx:/opt/build$ apt-get source mythtv
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
OBSERVERA: paketering av "mythtv" hanteras i versionshanteringssystemet "Bzr" på:
bzr+ssh://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-fixes
Använd:
bzr get bzr+ssh://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-fixes
för att hämta senaste (möjligen inte utgivna) uppdateringar av paketet.
Behöver hämta 98,5 MB källkodsarkiv.
Läs:1 http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ natty/multiverse mythtv 2:0.24.0+fixes.20110416.9ba3ece-0ubuntu1 (dsc) [3 366 B]
Läs:2 http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ natty/multiverse mythtv 2:0.24.0+fixes.20110416.9ba3ece-0ubuntu1 (tar) [98,4 MB]
Läs:3 http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ natty/multiverse mythtv 2:0.24.0+fixes.20110416.9ba3ece-0ubuntu1 (diff) [159 kB]
Hämtade 98,5 MB på 3min 54s (421 kB/s)                                                                                  
Packar inte upp redan uppackad källkod i mythtv-0.24.0+fixes.20110416.9ba3ece
gunnar@lynx:/opt/build$ cd mythtv-0.24.0+fixes.20110416.9ba3ece/
gunnar@lynx:/opt/build/mythtv-0.24.0+fixes.20110416.9ba3ece$ cd mythtv/
gunnar@lynx:/opt/build/mythtv-0.24.0+fixes.20110416.9ba3ece/mythtv$ ./configure
Error, no aligned memory allocator but SSE enabled, disable it or use --enable-memalign-hack.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
mythtv-dev@mythtv.org mailing list or IRC #mythtv on irc.freenode.net
Include the log file "config.ep" produced by configure as this will help
solving the problem.
gunnar@lynx:/opt/build/mythtv-0.24.0+fixes.20110416.9ba3ece/mythtv$ ./configure --enable-memalign-hack
ERROR! You must have FreeType installed to compile MythTV.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
mythtv-dev@mythtv.org mailing list or IRC #mythtv on irc.freenode.net
Include the log file "config.ep" produced by configure as this will help
solving the problem.
gunnar@lynx:/opt/build/mythtv-0.24.0+fixes.20110416.9ba3ece/mythtv$ sudo apt-get install libfreetype6
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
libfreetype6 är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.

```

How can I recreate the installed mythtv-backend binary? I have been unable to find any information searching the web and this forum. Where can I find the appropriate information.

BR
Gunnar

---

### Post by BicyclerBoy on 2011-09-10
Have a read in the source code install folder under ./mythtv/docs/mythtv-Howto*.html
You seem to be missing the Freetype  typeface/fonts package

This example is for mythtv 0.23 requiring libfaad for LATM AAC. I have not compiled from source for some time & I don't know where the following came from.
I don't have a backend-only example but I think you will get the idea..(--disable-frontend).

```

fe & be combined:
./configure --prefix=/usr --enable-gpl --enable-version3 --enable-nonfree --enable-libfaad
make
sudo checkinstall --pkgname=mythtv --pkgversion "4:SVN-r`LANG=C svn info |   grep Revision | awk '{ print $NF }'`" --backup=no --default --deldoc=yes

fe only:
./configure --prefix=/usr --enable-gpl --enable-version3 --enable-nonfree --enable-libfaad --disable-backend
make
sudo checkinstall --pkgname=mythtvfrontend --pkgversion "4:SVN-r`LANG=C svn info |   grep Revision | awk '{ print $NF }'`" --backup=no --default --deldoc=yes

```Use at your own risk, but it worked well for me..

The plugins & themes are separate config/make/checkinstall packages..

---

