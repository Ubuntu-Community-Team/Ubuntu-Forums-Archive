---
title: "Installing Amarok or VLC"
date: 2009-06-19
forum: Multimedia Software
---

### Post by n.hinton on 2009-06-19
I am new to ubuntu and would appreciate advice. I used to use VLC Media player in windows and thought I would give it a try in ubuntu however synaptic said it would impact on other packages followed by a long list of items that mean nothing to me, so cancelled that idea. Then tried Amarok as I believe it has a graphic equalizer and was presented with an even longer list of packages that would be affected by installing. I haven't installed either packages yet as I have no idea what the affected packages are or do and what the implications of installing would be. Again any advice very much appreciated.

---

### Post by andrew.46 on 2009-06-19
Hi n.hinton,

> **n.hinton said:**
> I am new to ubuntu and would appreciate advice. I used to use VLC Media player in windows and thought I would give it a try in ubuntu however synaptic said it would impact on other packages followed by a long list of items that mean nothing to me, so cancelled that idea.

What the package manager is trying to tell you is that along with vlc, or with Amarok, a long list of requirements will *also* be downloaded and installed. These extra packages are required for both programs to install and run effectively and it should be quite safe to install them.

All the best,

Andrew

---

### Post by SuperSonic4 on 2009-06-19
Amarok will haul a lot of added programs because it's based on Qt whereas Ubuntu is based on gtk. 

If you've not added the medibuntu repos then I suggest you add those and take their version of vlc for it compiles with non-free codecs

---

### Post by andrew.46 on 2009-06-19
Hi SuperSonic,

> **SuperSonic4 said:**
> If you've not added the medibuntu repos then I suggest you add those and take their version of vlc for it compiles with non-free codecs

Hmmmm...... are you *sure* that Medibuntu carries vlc?

Andrew

---

### Post by mc4man on 2009-06-19
you may wish to say what version of ubuntu your using (8.04 ,8.10, 9.04

Also try to simulate installing one or the other from the terminal and post the output, , just doing to get list of what's to be "affected" (not actually installing

```
sudo apt-get -s install vlc
```

You may also wish to post your sources list if the simulate shows a number of packages being removed
```
cat /etc/apt/sources.list
```

---

### Post by markbuntu on 2009-06-19
Amarok and VLC are KDE/qt/xine based so a lot of KDE and qt and xine packages are needed if you are on the standard gnome desktop. It is a pretty large amount of stuff but its what is needed to run them.

---

### Post by n.hinton on 2009-06-21
> **mc4man said:**
> you may wish to say what version of ubuntu your using (8.04 ,8.10, 9.04

Also try to simulate installing one or the other from the terminal and post the output, , just doing to get list of what's to be "affected" (not actually installing

```
sudo apt-get -s install vlc
```

You may also wish to post your sources list if the simulate shows a number of packages being removed
```
cat /etc/apt/sources.list
```

result of first line = :
kingfisher@kingfisher-desktop:~$ sudo apt-get -s install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amarok-common exiv2 kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins khelpcenter4
  libaudio2 libclucene0ldbl libexiv2-5 libkcddb4 libloudmouth1-0 libphonon4
  libpq5 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqtcore4 libqtgui4 librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x phonon phonon-backend-xine qt4-qtconfig redland-utils
  soprano-daemon ttf-dejavu ttf-dejavu-extra
Suggested packages:
  libqt4-sql-sqlite libqt4-sql-psql kdebase lame nas libqt4-dev gxine xine-ui
  libxine1-doc libxine-doc libxine1-ffmpeg phonon-backend-vlc
  phonon-backend-mplayer
The following NEW packages will be installed
  amarok amarok-common exiv2 kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins khelpcenter4
  libaudio2 libclucene0ldbl libexiv2-5 libkcddb4 libloudmouth1-0 libphonon4
  libpq5 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqtcore4 libqtgui4 librasqal1 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x phonon phonon-backend-xine qt4-qtconfig redland-utils
  soprano-daemon ttf-dejavu ttf-dejavu-extra
0 upgraded, 54 newly installed, 0 to remove and 16 not upgraded.
Inst libqtcore4 (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-xml (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-dbus (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libaudio2 (1.9.1-5 Ubuntu:9.04/jaunty)
Inst libqtgui4 (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libphonon4 (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Inst libqt4-script (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-designer (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-network (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-sql (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-qt3support (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-svg (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libclucene0ldbl (0.9.20-3 Ubuntu:9.04/jaunty)
Inst libpq5 (8.3.7-1 Ubuntu:9.04/jaunty)
Inst librasqal1 (0.9.16-1 Ubuntu:9.04/jaunty)
Inst librdf0 (1.0.8-1 Ubuntu:9.04/jaunty)
Inst soprano-daemon (2.2.2+dfsg.1-1ubuntu1 Ubuntu:9.04/jaunty) []
Inst libsoprano4 (2.2.2+dfsg.1-1ubuntu1 Ubuntu:9.04/jaunty)
Inst libexiv2-5 (0.18-1ubuntu1 Ubuntu:9.04/jaunty)
Inst libstreams0 (0.6.4-0ubuntu2 Ubuntu:9.04/jaunty)
Inst libstreamanalyzer0 (0.6.4-0ubuntu2 Ubuntu:9.04/jaunty)
Inst kdelibs5-data (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty)
Inst kdelibs5 (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty) []
Inst kdelibs-bin (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty)
Inst libqt4-opengl (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-sql-mysql (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libqt4-test (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst libxine1-bin (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Inst libxine1-misc-plugins (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Inst libxcb-shape0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Inst libxcb-shm0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Inst libxcb-xv0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Inst libxine1-x (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Inst libxine1-console (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Inst libxine1 (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Inst phonon-backend-xine (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Inst phonon (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Inst libqt4-webkit (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst qt4-qtconfig (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Inst amarok-common (2:2.0.2mysql5.1.30-0ubuntu3 Ubuntu:9.04/jaunty)
Inst kdebase-runtime-bin-kde4 (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty) []
Inst kdebase-runtime-data-common (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty) []
Inst kdebase-runtime-data (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty) []
Inst kde-icons-oxygen (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty) []
Inst kdebase-runtime (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Inst libloudmouth1-0 (1.4.2-2 Ubuntu:9.04/jaunty)
Inst amarok (2:2.0.2mysql5.1.30-0ubuntu3 Ubuntu:9.04/jaunty)
Inst exiv2 (0.18-1ubuntu1 Ubuntu:9.04/jaunty)
Inst libkcddb4 (4:4.2.2-0ubuntu2 Ubuntu:9.04/jaunty)
Inst kdemultimedia-kio-plugins (4:4.2.2-0ubuntu2 Ubuntu:9.04/jaunty)
Inst khelpcenter4 (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Inst redland-utils (1.0.8-1 Ubuntu:9.04/jaunty)
Inst ttf-dejavu-extra (2.28-1 Ubuntu:9.04/jaunty)
Inst ttf-dejavu (2.28-1 Ubuntu:9.04/jaunty)
Conf libqtcore4 (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-xml (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-dbus (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libaudio2 (1.9.1-5 Ubuntu:9.04/jaunty)
Conf libqtgui4 (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libphonon4 (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Conf libqt4-script (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-designer (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-network (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-sql (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-qt3support (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-svg (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libclucene0ldbl (0.9.20-3 Ubuntu:9.04/jaunty)
Conf libpq5 (8.3.7-1 Ubuntu:9.04/jaunty)
Conf librasqal1 (0.9.16-1 Ubuntu:9.04/jaunty)
Conf librdf0 (1.0.8-1 Ubuntu:9.04/jaunty)
Conf libsoprano4 (2.2.2+dfsg.1-1ubuntu1 Ubuntu:9.04/jaunty)
Conf soprano-daemon (2.2.2+dfsg.1-1ubuntu1 Ubuntu:9.04/jaunty)
Conf libexiv2-5 (0.18-1ubuntu1 Ubuntu:9.04/jaunty)
Conf libstreams0 (0.6.4-0ubuntu2 Ubuntu:9.04/jaunty)
Conf libstreamanalyzer0 (0.6.4-0ubuntu2 Ubuntu:9.04/jaunty)
Conf kdelibs5-data (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty)
Conf kdelibs-bin (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty)
Conf kdelibs5 (4:4.2.2-0ubuntu5 Ubuntu:9.04/jaunty)
Conf libqt4-opengl (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-sql-mysql (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libqt4-test (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf libxine1-bin (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Conf libxine1-misc-plugins (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Conf libxcb-shape0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Conf libxcb-shm0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Conf libxcb-xv0 (1.1.93-0ubuntu3 Ubuntu:9.04/jaunty)
Conf libxine1-x (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Conf libxine1-console (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Conf libxine1 (1.1.16.3-0ubuntu1 Ubuntu:9.04/jaunty)
Conf phonon-backend-xine (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Conf phonon (4:4.3.1-0ubuntu3 Ubuntu:9.04/jaunty)
Conf libqt4-webkit (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf qt4-qtconfig (4.5.0-0ubuntu4.1 Ubuntu:9.04/jaunty-updates)
Conf amarok-common (2:2.0.2mysql5.1.30-0ubuntu3 Ubuntu:9.04/jaunty)
Conf kdebase-runtime-data-common (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf kdebase-runtime-data (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf kde-icons-oxygen (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf kdebase-runtime (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf kdebase-runtime-bin-kde4 (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf libloudmouth1-0 (1.4.2-2 Ubuntu:9.04/jaunty)
Conf amarok (2:2.0.2mysql5.1.30-0ubuntu3 Ubuntu:9.04/jaunty)
Conf exiv2 (0.18-1ubuntu1 Ubuntu:9.04/jaunty)
Conf libkcddb4 (4:4.2.2-0ubuntu2 Ubuntu:9.04/jaunty)
Conf kdemultimedia-kio-plugins (4:4.2.2-0ubuntu2 Ubuntu:9.04/jaunty)
Conf khelpcenter4 (4:4.2.2-0ubuntu1 Ubuntu:9.04/jaunty)
Conf redland-utils (1.0.8-1 Ubuntu:9.04/jaunty)
Conf ttf-dejavu-extra (2.28-1 Ubuntu:9.04/jaunty)
Conf ttf-dejavu (2.28-1 Ubuntu:9.04/jaunty)

resulsts of second line = :

kingfisher@kingfisher-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by mc4man on 2009-06-21
You're fine, go ahead and install if you want them. Only suggested to simulate because you said "packages that would be *affected* by installing" (as in possibly removing

You may like the new amarok2, or may not, many people don't. If not there are several threads on how to install the older version in jaunty (1.4)

Same thing goes for vlc, in jaunty the patch that allowed the video and controls to be in same window was not applied like it was in Intrepid.

Again several ways to get it back if it's a concern.

you might as well try them both (the jaunty versions) and decide for yourself

Edit: after installing amarok run this to get better audio format support

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by n.hinton on 2009-06-21
wow thanks so much for your help, guess what i was looking for was a winamp in ububtu, many thanks to you that know your way around ubuntu
best regards
neil

---

