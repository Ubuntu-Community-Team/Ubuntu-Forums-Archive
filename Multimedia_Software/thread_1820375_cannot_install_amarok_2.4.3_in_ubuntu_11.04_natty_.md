---
title: "cannot install amarok 2.4.3 in ubuntu 11.04 natty narwhal?"
date: 2011-08-07
forum: Multimedia Software
---

### Post by NattyNoobCake on 2011-08-07
help! i'm a comlpete newbie to ubuntu (started 3 days ago)
i need to install amarok but nothing works :confused:
i tried doing sudo apt-get install amarok but that gave me this error

```
The following packages have unmet dependencies:
 amarok : Depends: libavcodec53 (>= 4:0.7-1) but it is not installable or
                   libavcodec-extra-53 (>= 4:0.7-1) but it is not installable
          Depends: libavformat53 (>= 4:0.7-1) but it is not installable or
                   libavformat-extra-53 (>= 4:0.7-1) but it is not installable
E: Broken packages
user@user:~$ sudo dpkg -i songbird_1.4.1-x86_64-skyzim.deb
dpkg: error processing songbird_1.4.1-x86_64-skyzim.deb (--install):
 cannot access archive: No such file or directory

```


then i tried going to software center and installing from there but that didn't work either becuase it says 

"Package dependencies cannot be resolved"
"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

and the details are:

```
The following packages have unmet dependencies:

amarok: Depends: amarok-common (= 2:2.4.3-natty~ppa1kde47) but 2:2.4.3-natty~ppa1kde47 is to be installed
        Depends: amarok-utils (= 2:2.4.3-natty~ppa1kde47) but 2:2.4.3-natty~ppa1kde47 is to be installed
        Depends: libavcodec-extra-53 (>= 4:0.7-1) but it is not going to be installed
        Depends: libavformat-extra-53 (>= 4:0.7-1) but it is not going to be installed
        Depends: libkcmutils4 (>= 4:4.4.95) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkdecore5 (>= 4:4.4.95) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkdeui5 (>= 4:4.5.2) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkdewebkit5 (>= 4:4.4.0) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkdnssd4 (>= 4:4.3.4) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkfile4 (>= 4:4.4.0) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libkio5 (>= 4:4.3.4) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libknewstuff3-4 (>= 4:4.4.0) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libphonon4 (>= 4:4.7.0really4.4.4) but 4:4.7.0really4.5.0-0ubuntu3 is to be installed
        Depends: libplasma3 (>= 4:4.5.86) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-script (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-sql (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-svg (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-xml (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqtgui4 (>= 4:4.6.2) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libsolid4 (>= 4:4.3.4) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed
        Depends: libthreadweaver4 (>= 4:4.3.4) but 4:4.7.0-0ubuntu1~natty1~ppa1 is to be installed

```

i really don't know what to do :( can someone help?

---

### Post by oboedad55 on 2011-08-07
Are you running Ubuntu or Kubuntu? Is it a normal or wubi install? If you're using regular Ubuntu there are nice alternatives to Amarok that are lighter and won't pull in so many dependencies. Rhythmbox works well as does Clementine which you can get here: 
[http://www.ubuntugeek.com/install-latest-clementine-music-player-in-ubuntu-10-1010-04-using-ppa.html](http://www.ubuntugeek.com/install-latest-clementine-music-player-in-ubuntu-10-1010-04-using-ppa.html)

---

### Post by mc4man on 2011-08-07
Likely related to [the ppa you've enabled]("https://launchpad.net/~philip5/+archive/kubuntu-backports") which says  - 
> PPA description

Same as the "extra" PPA but rebuilt packages against the Kubuntu teams backports PPA.

Do you also have "Kubuntu teams backports PPA" enabled?

---

### Post by dniMretsaM on 2011-08-07
Clementine is a fork or Amarok (1.x.x), so you might like that. Or you could try Banshee (Rhythmbox and Banshee are almost identical). They are a little lighter weight. Banshee/Rhythmbox won't add a bunch of KDE lib's either.

---

### Post by NattyNoobCake on 2011-08-07
I am using Ubuntu but i recently tried downloaded KDE or something to try the Kubuntu desktop environment. Even thought i went back to ubuntu, i never deleted that. maybe that's the problem. how would i fix that?

---

### Post by dniMretsaM on 2011-08-07
No, that shouldn't cause any problems. If you want to remove it though, just run this:
```
sudo apt-get remove akonadi-server akregator amarok amarok-common  amarok-utils appmenu-qt apport-kde apturl-kde ark bluedevil cdparanoia   cdrdao docbook-xsl dolphin dragonplayer freespacenotifier gdebi-core  gdebi-kde gnupg-agent gnupg2 gpgsm   gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data  kaddressbook kamera kate kcalc kde-config-gtk   kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin  kdebase-data kdebase-runtime kdebase-runtime-data   kdebase-workspace kdebase-workspace-bin kdebase-workspace-data  kdebase-workspace-kgreet-plugins kdegames-card-data   kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin  kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins   kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources  kdepim-runtime kdepim-strigi-plugins kdepim-wizards   kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4  kinfocenter klipper kmag kmail kmix kmousetool knm-runtime   knotes konsole kontact kopete kopete-message-indicator korganizer  kpackagekit kpat kppp krdc krfb krosspython ksnapshot   ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data  kubuntu-debug-installer kubuntu-default-settings   kubuntu-desktop kubuntu-docs kubuntu-firefox-installer  kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings   kubuntu-notification-helper kvkbd kwalletmanager language-selector-kde  libakonadi-contact4 libakonadi-kabc4   libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4  libakonadiprotocolinternals1 libao-common libao4 libasyncns0 libattica0   libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6  libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdiscid0   libdmtx0a libepub0 libflac++6 libgif4 libgpgme++2 libgps19 libibus-qt1  libilmbase6 libindicate-qt1 libiodbc2 libk3b6   libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4  libkcalutils4 libkcddb4 libkcmutils4 libkdcraw9   libkde3support4 libkdecorations4 libkdecore5 libkdegames5 libkdepim4  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4   libkemoticons4 libkephal4a libkexiv2-9 libkfile4 libkholidays4  libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5   libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4  libkmime4 libknewstuff2-4 libknewstuff3-4   libknotifyconfig4 libkntlm4 libkonq5-templates libkonq5a  libkontactinterface4 libkopete4 libkparts4 libkpgp4   libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4  libkpty4 libkresources4 libkrosscore4 libksba8   libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4  libktexteditor4 libktnef4 libktorrent-l10n libktorrent2   libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4  libkxmlrpcclient4 liblastfm0 libloudmouth1-0   libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4  libmimelib4 libmng1 libmpcdec6 libmsn0.3 libmusicbrainz3-6   libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4  libntrack-qt4-1 libntrack0 libokularcore1 libopenexr6   libotr2 libpackagekit-glib2-14 libpackagekit-qt14 libphonon4  libplasma-geolocation-interface4 libplasma3 libplasmaclock4b   libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3  libpowerdevilcore0 libprocesscore4b libprocessui4a libqalculate5   libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1  libqimageblitz4 libqjson0 libqt4-dbus libqt4-declarative   libqt4-designer libqt4-help libqt4-network libqt4-opengl  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql   libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml  libqt4-xmlpatterns libqtassistantclient4 libqtcore4   libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network  libqtscript4-sql libqtscript4-uitools libqtscript4-xml   libqtwebkit4 libreadline5 libreoffice-kde libreoffice-style-oxygen  libsolid4 libsolidcontrol4a libsolidcontrolifaces4a   libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4  libtag-extras1 libtaskmanager4b libthreadweaver4   libvirtodbc0 libvncserver0 libweather-ion6 libzip1  mysql-client-core-5.1 mysql-common mysql-server-core-5.1   nepomukcontroller network-manager-pptp-kde ntrack-module-libnl-0  odbcinst odbcinst1debian2 okular okular-extra-backends   oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete  packagekit packagekit-backend-aptcc partitionmanager   phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4  plasma-dataengines-addons plasma-dataengines-workspace   plasma-desktop plasma-netbook plasma-scriptengine-declarative  plasma-scriptengine-javascript plasma-scriptengine-python   plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel  plasma-widget-kimpanel-backend-ibus   plasma-widget-menubar plasma-widget-message-indicator  plasma-widget-networkmanagement plasma-widget-quickaccess   plasma-widgets-addons plasma-widgets-workspace  plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1   printer-applet python-kde4 python-packagekit python-pyudev python-qt4  python-qt4-dbus python-sip qapt-batch quassel   quassel-data rekonq shared-desktop-ontologies software-properties-kde  soprano-daemon system-config-printer-kde   systemsettings update-manager-kde usb-creator-kde userconfig  virtuoso-minimal virtuoso-opensource-6.1-bin   virtuoso-opensource-6.1-common && sudo apt-get install  ubuntu-desktop
```

Note that this is for 11.04. See [this](http://www.psychocats.net/ubuntu/puregnome) page for more details.

---

### Post by NattyNoobCake on 2011-08-07
thanks a lot!
but i want to be able to install amarok too :(
how do i do this?

---

