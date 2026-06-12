---
title: "I cannot install libavcodec-extra-53"
date: 2014-12-11
forum: Multimedia Software
---

### Post by umbothor-9 on 2014-12-11
Ubuntu 12.04.1. I cannot install libavcodec-extra-53.

```


sudo apt-get install libavcodec-extra-53
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 libavcodec-extra-53 : Dipende: libavutil-extra-51 (< 4:0.8.16ubuntu0.12.04.1-99) ma la versione 7:2.2.1-2~precise1 sta per essere installata
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati.


```

and...

```


sudo apt-get install -f

Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.

```


Suggestion?

---

### Post by mc4man on 2014-12-11
Clearly you've used a ppa providing ffmpeg libraires before. Maybe you disabled it?
(- one possibility would be this questionable  ppa - [https://launchpad.net/~archivematica/+archive/ubuntu/externals-dev](https://launchpad.net/~archivematica/+archive/ubuntu/externals-dev)
What do these 2 return?
 ```
apt-cache policy libavcodec*
```
```
apt-cache policy libavutil*
```

---

### Post by umbothor-9 on 2014-12-12
> **mc4man said:**
> Clearly you've used a ppa providing ffmpeg libraires before. Maybe you disabled it?
(- one possibility would be this questionable  ppa - [https://launchpad.net/~archivematica/+archive/ubuntu/externals-dev](https://launchpad.net/~archivematica/+archive/ubuntu/externals-dev)
What do these 2 return?
 ```
apt-cache policy libavcodec*
```
```
apt-cache policy libavutil*
```


In order:

```

apt-cache policy ffmpeg

ffmpeg:
  Installato: 5:201412100724-git-1
  Candidato:  5:201412100724-git-1
  Tabella versione:
 *** 5:201412100724-git-1 0
        100 /var/lib/dpkg/status
     4:0.8.16-0ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     4:0.8.1-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/main i386 Packages




```







```
 apt-cache policy libavcodec*
libavcodec-extra-52:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
libavcodec-extra-53:
  Installato: (nessuno)
  Candidato:  4:0.8.16ubuntu0.12.04.1
  Tabella versione:
     4:0.8.16ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
     4:0.8.10ubuntu0.12.04.1 0
        100 /var/lib/dpkg/status
     4:0.8.1ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
libavcodec-extra-55:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
     7:2.2.1-2~precise1 0
        100 /var/lib/dpkg/status
libavcodec-dev:
  Installato: (nessuno)
  Candidato:  4:0.8.16-0ubuntu0.12.04.1
  Tabella versione:
     4:0.8.16-0ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     4:0.8.1-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libavcodec52:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
libavcodec53:
  Installato: 4:0.8.16-0ubuntu0.12.04.1
  Candidato:  4:0.8.16-0ubuntu0.12.04.1
  Tabella versione:
 *** 4:0.8.16-0ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     4:0.8.1-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libavcodec55:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:

```

and...

```

apt-cache policy libavutil*

libavutil51:
  Installato: 4:0.8.16-0ubuntu0.12.04.1
  Candidato:  4:0.8.16-0ubuntu0.12.04.1
  Tabella versione:
 *** 4:0.8.16-0ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     4:0.8.1-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
libavutil52:
  Installato: 7:2.2.1-2~precise1
  Candidato:  7:2.2.1-2~precise1
  Tabella versione:
 *** 7:2.2.1-2~precise1 0
        100 /var/lib/dpkg/status
libavutil49:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
libavutil-extra-50:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
libavutil-extra-51:
  Installato: 7:2.2.1-2~precise1
  Candidato:  7:2.2.1-2~precise1
  Tabella versione:
 *** 7:2.2.1-2~precise1 0
        100 /var/lib/dpkg/status
     4:0.8.16ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
     4:0.8.1ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
libavutil-extra-52:
  Installato: (nessuno)
  Candidato:  (nessuno)
  Tabella versione:
libavutil-dev:
  Installato: (nessuno)
  Candidato:  4:0.8.16-0ubuntu0.12.04.1
  Tabella versione:
     4:0.8.16-0ubuntu0.12.04.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     4:0.8.1-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

---

### Post by mc4man on 2014-12-12
Try this simulation to ck., post results if not obvious it's ok to run without  the -s (simulate)
```
sudo apt-get -s purge libavutil-extra-51 libavutil52
```

As far as your ffmpeg package, it looks self built, not an issue unless you built as shared (or whoever built it
post 
```
apt-cache show ffmpeg
```

---

### Post by umbothor-9 on 2014-12-12
> **mc4man said:**
> Try this simulation to ck., post results if not obvious it's ok to run without  the -s (simulate)
```
sudo apt-get -s purge libavutil-extra-51 libavutil52
```

As far as your ffmpeg package, it looks self built, not an issue unless you built as shared (or whoever built it
post 
```
apt-cache show ffmpeg
```

```
sudo apt-get -s purge libavutil-extra-51 libavutil52
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  simplescreenrecorder-lib libstdc++5 python-pygoocanvas libboost-regex1.46.1
  sp-auth libgoocanvas-common libboost-program-options1.46.1 pv librecode0
  faac ogmtools lsdvd enca bombono-dvd-data libvlc-dev scons mkvtoolnix
  libmlt-data openshot-doc libgoocanvas3
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno RIMOSSI:
  bombono-dvd* frei0r-plugins* gmic* gnash* gnash-common* gpac*
  gpac-modules-base* gstreamer0.10-ffmpeg*
  gstreamer0.10-plugins-bad-multiverse* h264enc* libavutil-extra-51*
  libavutil52* libmjpegtools-1.9* libmlt++3* libmlt4* libopencv-calib3d2.3*
  libopencv-features2d2.3* libopencv-highgui2.3* libopencv-objdetect2.3*
  libpostproc-extra-52* libpostproc52* libquicktime2* libswscale-extra-2*
  libswscale2* melt* mencoder* mjpegtools* mplayer* openshot* python-mlt3*
  simplescreenrecorder* sopcast-player* vlc* vlc-nox* vlc-plugin-notify*
  vlc-plugin-pulse*
0 aggiornati, 0 installati, 36 da rimuovere e 0 non aggiornati.
Purg bombono-dvd [1.2.1-0ubuntu2]
Purg frei0r-plugins [1.1.22git20091109-1.1ubuntu1]
Purg gmic [1.5.0.8+dfsg-1]
Purg gnash [0.8.10-5ubuntu1.1]
Purg gnash-common [0.8.10-5ubuntu1.1]
Purg h264enc [9.3.7~dfsg-0ubuntu1]
Purg gpac [0.4.5+svn3462~dfsg0-1]
Purg gpac-modules-base [0.4.5+svn3462~dfsg0-1]
Purg gstreamer0.10-ffmpeg [0.10.13-1]
Purg gstreamer0.10-plugins-bad-multiverse [0.10.21-1]
Purg simplescreenrecorder [0.3.1-1~ppa1~precise1]
Purg vlc-plugin-notify [2.1.3-0~precise1]
Purg vlc-plugin-pulse [2.1.3-0~precise1]
Purg sopcast-player [0.8.5~ppa~precise1]
Purg vlc [2.1.3-0~precise1]
Purg vlc-nox [2.1.3-0~precise1]
Purg mencoder [2:1.0~rc4.dfsg1+svn34540-1]
Purg mplayer [2:1.0~rc4.dfsg1+svn34540-1]
Purg libopencv-objdetect2.3 [2.3.1-7]
Purg libopencv-calib3d2.3 [2.3.1-7]
Purg libopencv-features2d2.3 [2.3.1-7]
Purg libopencv-highgui2.3 [2.3.1-7]
Purg openshot [1.4.3-1]
Purg python-mlt3 [0.7.6+git20120204-2]
Purg melt [0.7.6+git20120204-2]
Purg libmlt++3 [0.7.6+git20120204-2]
Purg libmlt4 [0.7.6+git20120204-2]
Purg libavutil-extra-51 [7:2.2.1-2~precise1]
Purg libpostproc-extra-52 [7:2.2.1-2~precise1]
Purg libpostproc52 [7:2.2.1-2~precise1]
Purg mjpegtools [1:1.9.0-0.5ubuntu7]
Purg libmjpegtools-1.9 [1:1.9.0-0.5ubuntu7]
Purg libquicktime2 [2:1.2.3-4build2]
Purg libswscale-extra-2 [7:2.2.1-2~precise1]
Purg libswscale2 [7:2.2.1-2~precise1]
Purg libavutil52 [7:2.2.1-2~precise1]





```

```


apt-cache show ffmpeg

Package: ffmpeg
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 184472
Maintainer: root@thorkkk-Z68XP-UD3
Architecture: i386
Version: 5:201412100724-git-1
Provides: ffmpeg
Conffiles:
 /etc/ffserver.conf 1633e55171ce060948a42cb74860d806 obsolete
Description: Package created with checkinstall 1.6.2


Package: ffmpeg
Priority: extra
Section: oldlibs
Installed-Size: 74
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: all
Source: libav
Version: 4:0.8.16-0ubuntu0.12.04.1
Depends: libav-tools
Filename: pool/main/liba/libav/ffmpeg_0.8.16-0ubuntu0.12.04.1_all.deb
Size: 2224
MD5sum: eb15f09dbd85772cde17aac9630eef94
SHA1: 3024660cbd4c355afb1f4f060fa7ded81197fa59
SHA256: 21929f6fc36e390e497b5cff4a5fd1cc26741c62815cb3bbaf219d6fca71f570
Description-en: Multimedia player, server, encoder and transcoder (transitional package)
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package is only used for transitional purposes and can be safely
 removed when no other packages depend on this package.
Homepage: http://libav.org/
Description-md5: 7d289d6cf1350e7e0ddcc4c8f883c772
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntustudio-video


Package: ffmpeg
Priority: optional
Section: graphics
Installed-Size: 66
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: all
Source: libav
Version: 4:0.8.1-0ubuntu1
Depends: libav-tools
Filename: pool/main/liba/libav/ffmpeg_0.8.1-0ubuntu1_all.deb
Size: 2220
MD5sum: 121d8a3844610da5696580a3c0bacdda
SHA1: da37118c20b648110f33806256003f4194a1dce0
SHA256: ecee06069f911528017fd0ea292fc964863cee3933270816a415ad9d6d023a22
Description-en: Multimedia player, server, encoder and transcoder (transitional package)
 Libav is a complete, cross-platform solution to decode, encode, record,
 convert and stream audio and video.
 .
 This package is only used for transitional purposes and can be safely
 removed when no other packages depend on this package.
Homepage: http://libav.org/
Description-md5: 7d289d6cf1350e7e0ddcc4c8f883c772
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntustudio-video



```

---

### Post by mc4man on 2014-12-12
Well that's not going to work out in a nice fashion - try the sim again but just with 51 package to see if all those others are dependent on - 
```
sudo apt-get -s purge libavutil-extra-51
```

---

### Post by umbothor-9 on 2014-12-12
> **mc4man said:**
> Well that's not going to work out in a nice fashion - try the sim again but just with 51 package to see if all those others are dependent on - 
```
sudo apt-get -s purge libavutil-extra-51
```


```

sudo apt-get -s purge libavutil-extra-51


Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti saranno RIMOSSI:
  libavutil-extra-51*
0 aggiornati, 0 installati, 1 da rimuovere e 0 non aggiornati.
Purg libavutil-extra-51 [7:2.2.1-2~precise1]




```

---

### Post by mc4man on 2014-12-12
Well then go ahead & remove 
```
sudo apt-get  purge libavutil-extra-51
```
Then maybe you can install what you wanted

Overall you've got a bit of a mess though with those unknown? ppa packages
The best for that would be to find out which ppa they came from (do you remember?

---

### Post by umbothor-9 on 2014-12-12
Yeeeees, thank you.

---

