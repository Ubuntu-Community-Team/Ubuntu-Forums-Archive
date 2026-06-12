---
title: "mythtv cofig issues - now I can't install anything!"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by fazza on 2007-06-01
hi all
installed mythtv a while ago, along with all other plugins I could find for it. During installation, it asked me to configure it. It wanted to connect to a MySQL database - but I haven't got an account. I'm only 14, so I'm not allowed one. I canceled the configuration and let it carry on installing the other packages. Afterwards, whenever I attempted to install something, it would get half way through and ask me to config MythTV. I said no, and the installation continued. This obviously gets annoying when you leave it to install and come back later to find that it's barely done anything - it's waiting for you to set up mythtv. So I removed mythtv and mythtv-backend (I think they're called that) so it wouldn't keep on asking me to connect it to MySQL, (then I can just reinstall those two packages when I have an account) and now nothing will install or uninstall. When I run ```
sudo apt-get upgrade
```, I get the message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
So I run
```
sudo dpkg --configure -a
```
and get
Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
So then I run
```
 sudo dpkg-reconfigure --force mythtv-database
```
and I get the config window. When I exit this, having unsuccessfully configured it, I have
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database

Please help, as I can do nothing and cannot upgrade in case it goes wrong like it did with my other pc!
cheers

---

### Post by fazza on 2007-06-01
after going through the processes in my last message, the upgrade appears to begin to work...
but not quite enough:
```
sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2 curl democracyplayer democracyplayer-data digikam firestarter
  frostwire gimp gimp-data gimp-dbg gimp-helpbrowser gimp-python gimp-svg
  kdelibs-data kdelibs4c2a ktorrent libcurl3 libcurl3-gnutls libfreetype6
  libfreetype6-dev libgimp2.0 libpq4 libqt3-mt libqt3-mt-mysql libsmbclient
  libx11-6 libx11-data libx11-dev linux-headers-2.6.17-11
  linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic linux-libc-dev
  opera pmount samba-common smbclient tzdata wine
38 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/107MB of archives.
After unpacking 1066kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libx11-dev_2%3a1.0.3-0ubuntu4.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `kdelibs-data': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libx11-dev_2%3a1.0.3-0ubuntu4.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

thought I'd try removing the other issues... (libx11-dev_2%3a1.0.3-0ubuntu4.1_i386.deb).
And it tells me I have loads of packages no longer required.
```
 sudo apt-get remove libx11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog libsm-dev krdc krfb kppp libktnef1 konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev libice-dev kdeprint
  adept-manager kmplayer-konq-plugins x11proto-xext-dev ksvg kscreensaver
  mozilla-dev libatk1.0-dev libavahi-compat-libdnssd1 kio-locate libk3b2
  libpythonize0 x11proto-kb-dev libglib2.0-dev ksnapshot liblockdev1
  kdebluetooth kooka libkipi0 wlassistant libkcal2b x11proto-xinerama-dev
  libpango1.0-dev openoffice.org-kde adept-installer libkexif1
  kdegraphics-kfile-plugins libburn2 x11proto-render-dev konqueror-nsplugins
  gwenview libpoppler1-qt libtdb1 adept-updater kdepim-kio-plugins
  libqt4-qt3support hwdb-client-kde krita libxi-dev qca-tls libmimelib1c2a
  klipper libxrender-dev libqt4-core kontact libsqlite0 libcairo2-dev
  kdeadmin-kfile-plugins ksmserver ksysguard adept-batch koffice-data
  libxdmcp-dev kde-icons-mono libpng12-dev kmenuedit pykdeextensions
  libfontconfig1-dev adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  ksplash xtrans-dev libkleopatra1 skim kipi-plugins korganizer k3b
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal
  x11proto-core-dev libxcursor-dev python-qt4 ark libexif-dev libusb-dev
  libgphoto2-2-dev kcron libjasper-runtime adept-common libqt4-gui
  x11proto-randr-dev libksieve0 digikam libxt-dev libgtk2.0-dev kdm
  speedcrunch libxext-dev libkpimidentities1 libskim0 kpf bogofilter-bdb
  libkdepim1a kdnssd kdemultimedia-kfile-plugins katapult poster
  kdenetwork-filesharing kubuntu-docs knotes bogofilter zlib1g-dev
  kde-guidance x11proto-input-dev libqt4-sql libfreetype6-dev debtags
  x11proto-fixes-dev libgsl0 khelpcenter apt-index-watcher libxau-dev
  kaddressbook libkpimexchange1 kmailcvt rdiff-backup knetworkconf ksysguardd
  konq-plugins libkmime2 libxrandr-dev language-selector-qt libexpat1-dev
  qobex scim-qtimm kwalletmanager libxft-dev libx11-dev kopete libisofs2 karm
  kate kmail beep-media-player-dev libxfixes-dev keep koffice-libs
  adept-notifier bogofilter-common kde-guidance-powermanager libxinerama-dev
  kde-systemsettings librsync1 kmousetool kmag kdepim-kresources
  kdepim-wizards kmilo kmplayer-base python-kde3 kdepasswd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  beep-media-player-dev libcairo2-dev libgtk2.0-dev libpango1.0-dev libx11-dev
  libxcursor-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxrandr-dev libxrender-dev libxt-dev mozilla-dev
0 upgraded, 0 newly installed, 15 to remove and 37 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 50.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing beep-media-player-dev (--remove):
 failed in buffer_read(fd): files list for package `kdelibs-data': Input/output error
Errors were encountered while processing:
 beep-media-player-dev
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so I tried
```
sudo apt-get remove beep-media-player-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc krfb kppp libktnef1 konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kdeprint adept-manager
  kmplayer-konq-plugins ksvg kscreensaver libatk1.0-dev
  libavahi-compat-libdnssd1 kio-locate libk3b2 libpythonize0 libglib2.0-dev
  ksnapshot liblockdev1 kdebluetooth kooka libkipi0 wlassistant libkcal2b
  x11proto-xinerama-dev libpango1.0-dev openoffice.org-kde adept-installer
                                                     [[continued...]]
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  beep-media-player-dev
0 upgraded, 0 newly installed, 1 to remove and 38 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 274kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing beep-media-player-dev (--remove):
 failed in buffer_read(fd): files list for package `kdelibs-data': Input/output error
Errors were encountered while processing:
 beep-media-player-dev
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

can't do anything to fix anything in any way at all.
:(

---

### Post by fenian on 2007-06-01
run

> sudo apt-get autoremove

Also it seem as though you have misunderstood what a Mysql database is.Mysql is a database server set up on your machine that stores information that mythtv uses to organize itself.Mythtv has two parts a backend-server which grabs program guide info,grabs video and stores mythtv info (among other things) and a frontend client that you use to watch tv or video,set up tv recording,listen to music,etc..

---

### Post by fazza on 2007-06-01
ok...
sounds like a good plan but last time I did autoremove, it removed lots of packages I needed and messed my computer up. Is that the only way to get round the problem? Also, I noticed that most of the packages it said it no longer needed were KDE packages. Would this be because apt-get and aptitude are gnome programs and pick the KDE packages up as ones it doesn't use?
As for the MySQL database, thanks, I never really did understand that. How can I set it up?
thanks again:)

---

### Post by barney_1 on 2007-06-01
First off, you need to fix your packages.  Using autoremove should not effect a stable installation of Ubuntu.  It would be better to use the autoremove and then fix any problems that arise:

```
sudo apt-get autoremove
```

Once that has completed successfully you should bring your whole system up to date:
```
sudo apt-get update
sudo apt-get upgrade
```

If that has completed successfully you can try installing mythtv again.  Because you have had mysql problems already perhaps you should purge mysql (assuming you aren't using it for anything else, you probably aren't but check around to make sure):

```
sudo apt-get remove --purge mysql-server
```

Then follow the community documentation to install mythtv on feisty:

[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

(make sure you read everything as you go through.)

---

### Post by fazza on 2007-06-01
what would happen to kde if I did autoremove?

---

### Post by fazza on 2007-06-03
look at the packages in autoremove!
```
kpdf ksystemlog krdc krfb kppp libktnef1 konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kdeprint adept-manager
  kmplayer-konq-plugins ksvg kscreensaver libavahi-compat-libdnssd1 kio-locate
  libk3b2 libpythonize0 ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant libkcal2b openoffice.org-kde adept-installer libkexif1
  kdegraphics-kfile-plugins libburn2 konqueror-nsplugins gwenview
  libpoppler1-qt libtdb1 adept-updater kdepim-kio-plugins libqt4-qt3support
  hwdb-client-kde krita qca-tls libmimelib1c2a klipper libqt4-core kontact
  libsqlite0 kdeadmin-kfile-plugins ksmserver ksysguard adept-batch
  koffice-data kde-icons-mono kmenuedit pykdeextensions adept
  ksplash-engine-moodin kubuntu-konqueror-shortcuts ksplash libkleopatra1 skim
  kipi-plugins korganizer k3b kdenetwork-kfile-plugins kbstate akregator
  kio-apt kwin-style-crystal python-qt4 ark libexif-dev libusb-dev
  libgphoto2-2-dev kcron libjasper-runtime adept-common libqt4-gui libksieve0
  digikam kdm speedcrunch libkpimidentities1 libskim0 kpf bogofilter-bdb
  libkdepim1a kdnssd kdemultimedia-kfile-plugins katapult poster
  kdenetwork-filesharing kubuntu-docs knotes bogofilter kde-guidance
  libqt4-sql debtags libgsl0 khelpcenter apt-index-watcher kaddressbook
  libkpimexchange1 kmailcvt rdiff-backup knetworkconf ksysguardd konq-plugins
  libkmime2 language-selector-qt qobex scim-qtimm kwalletmanager kopete
  libisofs2 karm kate kmail keep koffice-libs adept-notifier bogofilter-common
  kde-guidance-powermanager kde-systemsettings librsync1 kmousetool kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base python-kde3 kdepasswd

```
I need these

---

### Post by barney_1 on 2007-06-03
Yep, that does seem excessive for autoremove to have all of those packages selected.

I don't know what to tell you.  My feeling is your system can't be considered "stable" if the package management system is broken.  If I were you here's what I'd do:

Reinstall all Kubuntu packages:
```
sudo apt-get install kubuntu-desktop
sudo apt-get isntall kde
sudo apt-get install kde-core
```

Then I'd run the autoremove.
```
sudo apt-get autoremove
```

Then bring everything up-to-date:
```
sudo apt-get update
sudo apt-get upgrade
```

This should fix all of your problems.  But, use your head as you go through these commands.  Make sure you read what each message is and decide if that is really what you want.

---

### Post by superm1 on 2007-06-03
Just a word of warning, if you are getting INPUT/OUTPUT errors, this can be caused by file system corruption.  You might want to force a fsck on the file system.

```
touch /forcefsck 
```

and reboot.  

It will check your filesystem upon boot and make sure things are intact.

---

### Post by fazza on 2007-06-08
> **barney_1 said:**
> 
...Reinstall all Kubuntu packages:...


the standing issue is that I cannot install!:KS

---

### Post by barney_1 on 2007-06-08
You are correct, that is the standing issue.  How's that coming for you?

---

### Post by fazza on 2007-06-08
that means that I cannot reinstall the packages because none of the program works. I will try it though...

---

### Post by fazza on 2007-09-27
have recently attempted mysql installation from tar.gz file (is that source or binary?) but I still got the error about it not being able to find the socket in /var/run/mysqld.sock or something. I did actually find that file in /tmp and tried to copy and paste it to the right place, but it wouldn't go. I had the permsissions etc, but there wasn't even an error message. nothing happened.

---

