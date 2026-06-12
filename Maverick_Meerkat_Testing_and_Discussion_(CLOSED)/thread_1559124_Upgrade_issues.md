---
title: "Upgrade issues"
date: 2010-08-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-08-23
Just installed alpha 3 in VirtualBox. Tried to upgrade. Hit a snag/error: ```
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details:
libgirepository1.0-1
```

I guess I will have to update my sources.list. Where can I find a sources.list I could just copy and paste? Current list is:```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100803.1)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ru.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

---

### Post by kansasnoob on 2010-08-23
Just at a quick glance I think your sources.list is fine, but look at my Synaptic Commit log from Aug 11:

> Commit Log for Wed Aug 11 06:30:41 2010


[B][COLOR="Red"]Removed the following packages:
libgirepository1.0-0[/COLOR][/B]

**[COLOR="Red"]Upgraded the following packages:[/COLOR]**
adobe-flashplugin (10.1.53.64-1lucid1) to 10.1.82.76-1maverick1
apparmor (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
apparmor-utils (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
bash (4.1-2ubuntu3) to 4.1-2ubuntu4
debhelper (7.4.20ubuntu6) to 8.0.0ubuntu1
foomatic-db (20100806-0ubuntu2) to 20100806-0ubuntu5
foomatic-db-engine (4.0.4-0ubuntu1) to 4.0.5-0ubuntu4
foomatic-filters (4.0.4-0ubuntu2) to 4.0.5-0ubuntu2
gconf-defaults-service (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
gconf2-common (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
[B][COLOR="Red"]gir1.0-freedesktop (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2
gir1.0-glib-2.0 (0.9.3-0ubuntu1) to 0.9.3-0ubuntu2[/COLOR][/B]
gnome-menus (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
gstreamer0.10-plugins-bad (0.10.19-1ubuntu2) to 0.10.19-1ubuntu3
gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3) to 0.90.3+git20100810-0ubuntu1
gtk2-engines-pixbuf (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
gwibber (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
gwibber-service (2.31.4-0ubuntu1) to 2.31.4-0ubuntu2
hpijs (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-cups (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-data (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
hplip-gui (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
indicator-application (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libapparmor-perl (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libapparmor1 (2.5.1~pre1393-0ubuntu3) to 2.5.1~pre1393-0ubuntu4
libappindicator0 (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libappindicator0.1-cil (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
libclutter-1.0-0 (1.2.12-0ubuntu3) to 1.2.12-0ubuntu4
libclutter-gtk-0.10-0 (0.10.4-1ubuntu1) to 0.10.4-1ubuntu2
libdbusmenu-glib1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libdbusmenu-gtk1 (0.3.9-0ubuntu1) to 0.3.9-0ubuntu2
libgail-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgail18 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgconf2-4 (2.31.7-0ubuntu2) to 2.31.7-0ubuntu3
libgdk-pixbuf2.0-0 (2.21.6-2ubuntu3) to 2.21.6-2ubuntu5
libgnome-menu2 (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
libgtk2.0-0 (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-bin (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libgtk2.0-common (2.21.5-1ubuntu5) to 2.21.5-1ubuntu6
libhpmud0 (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libindicate-gtk2 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libindicate4 (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
libjson-glib-1.0-0 (0.10.2-2ubuntu1) to 0.10.2-2ubuntu2
libqt4-dbus (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-designer (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-help (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-network (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-script (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-scripttools (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-sql-mysql (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-svg (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-test (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-webkit (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xml (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqt4-xmlpatterns (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtcore4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
libqtgui4 (4:4.7.0~beta2-0ubuntu3) to 4:4.7.0~beta2-0ubuntu4
librsvg2-2 (2.26.3-2) to 2.26.3-2ubuntu1
librsvg2-common (2.26.3-2) to 2.26.3-2ubuntu1
libsane-hpaio (3.10.6-0ubuntu1) to 3.10.6-1ubuntu1
libsoup-gnome2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libsoup2.4-1 (2.31.6-0ubuntu1) to 2.31.6-0ubuntu2
libtotem-plparser17 (2.30.2-1) to 2.30.2-1build1
libunique-1.0-0 (1.1.6-1ubuntu2) to 1.1.6-1ubuntu3
libwebkit-1.0-2 (1.2.3-1) to 1.2.3-1ubuntu1
libwebkit-1.0-common (1.2.3-1) to 1.2.3-1ubuntu1
libwnck-common (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
libwnck22 (1:2.30.3-0ubuntu1) to 1:2.30.3-0ubuntu2
openprinting-ppds (20100806-0ubuntu2) to 20100806-0ubuntu5
python-appindicator (0.2.3-0ubuntu1) to 0.2.3-0ubuntu2
python-gmenu (2.30.2-0ubuntu1) to 2.30.2-0ubuntu2
python-gobject (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-gobject-cairo (2.21.5-0ubuntu1) to 2.21.5-0ubuntu3
python-indicate (0.4.1-0ubuntu1) to 0.4.1-0ubuntu2
telepathy-butterfly (0.5.12-1) to 0.5.12-1ubuntu1
time (1.7-23build1) to 1.7-23ubuntu1
update-manager (1:0.142.5) to 1:0.142.7
update-manager-core (1:0.142.5) to 1:0.142.7
xterm (261-1ubuntu1) to 261-1ubuntu2

[B][COLOR="Red"]Installed the following packages:
libgirepository1.0-1 (0.9.3-0ubuntu2)[/COLOR][/B]


---

### Post by Stoneface on 2010-08-31
Thanks! Solved the issue by reconfiguring dpkg, apt-get install -f and doing a distribution upgrade. All seems to be working again now. Mentioned details in another thread [http://ubuntuforums.org/showthread.php?t=1564835](http://ubuntuforums.org/showthread.php?t=1564835) I started by accident as I forgot I had this one going.. :-)

---

