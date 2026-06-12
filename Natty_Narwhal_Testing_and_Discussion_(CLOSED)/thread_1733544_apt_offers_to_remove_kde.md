---
title: "apt offers to remove kde?"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2011-04-19
Second time this has happened - this one happened about 20 minutes ago.  I think this is a repo issue, not a workstation issue -

```
wizard@wizard-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
 akonadiconsole akregator apport-kde apturl-kde ark bomber bovo compiz-kde
 debconf-kde-helper dolphin dragonplayer firefox-kde-support gdebi-kde
 granatier gwenview jockey-kde k3b kaddressbook kajongg kapman kate katomic
 kbattleship kblackbox kblocks kbounce kbreakout kcalc kde-config-touchpad
 kde-window-manager kdebase-apps kdebase-bin kdebase-runtime
 kdebase-workspace kdebase-workspace-bin kdegames kdelibs5 kdelibs5-plugins
 kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources
 kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdesudo kdiamond kdiff3
 kdm kdoctools kfind kfourinline kgoldrunner khelpcenter4 kigo killbots
 kinfocenter kipi-plugins kiriki kjumpingcube klickety klines klipper kmag
 kmahjongg kmail kmines kmix kmousetool knetwalk knotes kolf kollision
 konqueror konqueror-nsplugins konquest konsole kontact kopete
 kopete-message-indicator korganizer kpackagekit kpat kreversi ksame kshisen
 ksirk ksnapshot kspaceduel ksquares ksudoku ksysguard ksystemlog ktorrent
 ktron ktuberling kubrick kubuntu-debug-installer kubuntu-desktop
 kubuntu-firefox-installer kubuntu-konqueror-shortcuts
 kubuntu-notification-helper kvkbd kwalletmanager kwrite
 language-selector-kde libkdepim4 libkopete4 libmessagelist4 libmuonprivate1
 libreoffice-kde lskat muon muon-installer muon-notifier muon-updater
 nepomukcontroller okular palapeli partitionmanager
 plasma-dataengines-workspace plasma-desktop plasma-netbook
 plasma-scriptengine-python plasma-widget-facebook plasma-widget-kimpanel
 plasma-widgets-addons plasma-widgets-workspace polkit-kde-1 printer-applet
 python-kde4 qapt-batch quassel rekonq software-properties-kde
 system-config-printer-kde systemsettings update-manager-kde usb-creator-kde
 userconfig wicd-kde
The following packages will be upgraded:
 command-not-found command-not-found-data compiz compiz-core compiz-gnome
 compiz-plugins kdelibs-bin libdecoration0 libkatepartinterfaces4
 libkcmutils4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkimproxy4
 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff2-4
 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4
 libkpty4 libkrosscore4 libkrossui4 libktexteditor4 libkunitconversion4
 libkutils4 libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3
 libsolid4 libthreadweaver4
43 upgraded, 0 newly installed, 141 to remove and 0 not upgraded.
Need to get 12.3 MB of archives.
After this operation, 302 MB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by dino99 on 2011-04-19
ready for huge breakage ? :)

---

### Post by imigueldiaz on 2011-04-19
> **wizard10000 said:**
> Second time this has happened - this one happened about 20 minutes ago.  I think this is a repo issue, not a workstation issue -

```
wizard@wizard-desktop:~$ sudo apt-get dist-upgrade

```

Perhaps you should try a 

```
sudo aptitude safe-upgrade
```

instead, while they push the correct packages on repository :confused:

---

### Post by wizard10000 on 2011-04-19
> **dino99 said:**
> ready for huge breakage ? :)

:D

The first time it happened I ran it anyway just for the hell of it because I keep a daily dump of installed packages and can restore in about ten minutes.  It did indeed break everything  ;)

---

### Post by xebian on 2011-04-19
[QUOTE=wizard10000;10694698]:D

The first time it happened I ran it anyway just for the hell of it because I keep a daily dump of installed packages and can restore in about ten minutes.  It did indeed break everything  ;)[/QUOTE

Of course because it removed the very core of KDE.

---

### Post by wizard10000 on 2011-04-19
> **imigueldiaz said:**
> Perhaps you should try a 

```
sudo aptitude safe-upgrade
```

instead, while they push the correct packages on repository :confused:

I could, but I've gotten into the habit of watching exactly what apt offers to do - I just declined the upgrade.

I've heard you're not supposed to mix aptitude and apt on the same machine - and I prefer apt.  Just personal preference, though  ;)

I just updated from repos and the problem is fixed now.

---

