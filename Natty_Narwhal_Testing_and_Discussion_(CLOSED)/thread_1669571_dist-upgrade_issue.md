---
title: "dist-upgrade issue"
date: 2011-01-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wnelson on 2011-01-17
01/17 dist-upgrade want's to remove lubuntu-desktop and install kubuntu-desktop?

---

### Post by cariboo on 2011-01-17
I've updated 4 systems today, and haven't seen anything like that.

---

### Post by wnelson on 2011-01-17
apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  lubuntu-desktop osmo
The following NEW packages will be installed:
  akonadi-server apturl-kde docbook-xml docbook-xsl docbook-xsl-doc-html
  exiv2 icoutils kdebase-runtime kdebase-runtime-data kdelibs-bin
  kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins
  kdesudo kdoctools kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libakonadiprotocolinternals1 libattica0
  libboost-program-options1.42.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-10
  libexiv2-9 libhupnp0 libilmbase6 libiodbc2 libkabc4 libkatepartinterfaces4
  libkcal4 libkcmutils4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkimap4
  libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4
  libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4
  libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4
  libktexteditor4 libmailtransport4 libmicroblog4 libmng1 libmysqlclient16
  libnepomuk4 libnepomukquery4a libnepomukutils4 libntrack-qt4-1 libntrack0
  libopenexr6 libphonon4 libplasma3 libpolkit-qt-1-1 libpulse-mainloop-glib0
  libqapt-runtime libqapt1 libqca2 libqt4-dbus libqt4-declarative
  libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libqtlocation1 libqtmultimediakit1 libqtsolutions-soap-2.7-1 libqtwebkit4
  librasqal2 librdf0 libreadline5 libsolid4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0 libxcb-shape0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x libxml2-utils mysql-client-core-5.1 mysql-common
  mysql-server-core-5.1 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-xine plasma-scriptengine-declarative
  plasma-scriptengine-javascript python-kde4 python-qt4 python-sip qapt-batch
  sgml-data shared-desktop-ontologies software-properties-kde soprano-daemon
  ttf-dejavu virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
The following packages have been kept back:
  geany python-webkit
The following packages will be upgraded:
  bluez chromium-browser chromium-browser-inspector chromium-browser-l10n
  cpp-4.5 desktop-file-utils firefox-4.0 firefox-4.0-core g++-4.5 gcc-4.5
  gcc-4.5-base gdb libbluetooth3 libdirac-encoder0 libgcc1 libgomp1
  liblircclient0 libproxy0 libstdc++6 libstdc++6-4.5-dev
  network-manager-gnome sylpheed sylpheed-i18n system-tools-backends
24 upgraded, 139 newly installed, 2 to remove and 2 not upgraded.
Need to get 151 MB of archives.
After this operation, 337 MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by VeeDubb on 2011-01-17
dist-upgrade is roughly the same as running a "Parial Upgrade" through the update manager, and should generally be avoided.


That being said, lubuntu-desktop is probably just a dummy package with a lot of dependencies just like ubuntu-desktop and kubuntu-desktop, so having it removed is no big deal as long as you remember to try and re-install it periodically.

The only other package being removed is osmo, which I'm not familiar with.  Check what it is, and if it's something important, don't run the dist-upgrade until the dependency issues are resolved.


*Edit. I'm noting a HUGE number of KDE packages being installed by the dist-upgrade, and I can't imagine why.  I wasn't under the impression that lubuntu was based on QT or KDE, so I'm not sure why so much KDE stuff would get pulled in by an upgrade.

Instead, you might try opening up synaptic, and updating and/or reinstalling the lubuntu-desktop package.

---

### Post by castrojo on 2011-01-18
> **VeeDubb said:**
> dist-upgrade is roughly the same as running a "Parial Upgrade" through the update manager, and should generally be avoided.

^^ this. Though generally speaking held packages work themselves out after a couple of days.

Doing a normal apt-get upgrade will keep you safe most of the time.

---

### Post by wnelson on 2011-01-18
I did aptitude forget-new. It removed some dependencies. I just did an upgrade.

---

