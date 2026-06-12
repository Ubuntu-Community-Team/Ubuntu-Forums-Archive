---
title: "Amarok crashes when trying to play any song"
date: 2011-05-31
forum: Multimedia Software
---

### Post by ADani on 2011-05-31
I'm on Ubuntu 10.04, Amarok version 2.3.0, Using KDE 4.4.2
Whenever I start Amarok and try to play any song, amarok crashes, smetimes a few seconds of the music can be heard even if the Amarok window is no longer there.
This is my yakuake code from starting Amarok to the crash, I don't really know where to start looking for an answer.
thanks

```
daniela@Daniela:~$ amarok
amarok(4068)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4068)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4068)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
amarok(4068)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/daniela/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
amarok(4068)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QGraphicsLinearLayout::removeAt: invalid index 1
amarok(4068)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
amarok(4068)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Object::connect: No such slot Plasma::WebView::urlChanged(const QUrl &)
amarok(4068)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4068)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) ,  QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
QMap((0, QMap((0, QVariant(QString, "Playlist Files on Disk") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Playlist Files on Disk") ) )  ) )  
Creating empty group:  "Playlist Files on Disk" 
QMap((0, QMap((0, QVariant(QString, "Internal Database") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Internal Database") ) )  ) )  
Creating empty group:  "Internal Database" 
QMap() 
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Local Podcasts") )  ) 
QMap((0, QMap((0, QVariant(QString, "Local Podcasts") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Local Podcasts") ) )  ) )  
Creating empty group:  "Local Podcasts" 
amarok(4068)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok(4068)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok(4068)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(4068)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
QMetaObject::invokeMethod: No such method App::loadCommandLineOptionsForNewInstance()
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
daniela@Daniela:~$ amarok(4068)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
amarok(4068)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/daniela/.local/share/mime/magic"
link XMLID_9_ hasn't been detected!
link XMLID_9_ hasn't been detected!
link XMLID_9_ hasn't been detected!
link XMLID_9_ hasn't been detected!
Could not resolve property : linearGradient5167
Could not resolve property : linearGradient3563
Could not resolve property : linearGradient3563-3
Could not resolve property : linearGradient3563-3
KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/daniela/.kde/socket-Daniela/kdeinit4__0
QSocketNotifier: Invalid socket 22 and type 'Read', disabling...

```

---

### Post by CJ_Hudson on 2011-07-18
That is a tricky one, Perhaps you require expert help?

---

### Post by ADani on 2011-07-18
Yes I'm afraid so. I've been trying some packages with the same result: more things break down.
Right now I think my best chance is formating and upgrading to kubuntu 11.04, because the current list of things broken is very broad:
Amarok still has the same problem
Yakuake sometimes does not launch automatically or it doesn't respond to de f12 call (in the config that is enabled)
Notifications boxes on the bottom right have no text
Creating new forders in usb sticks desn't work
...

thanks, I think I'm beyond help :(

---

### Post by SeijiSensei on 2011-07-20
If you're going to upgrade, I'd advise installing Kubuntu 10.10, then adding the Kubuntu "[backports]("https://launchpad.net/~kubuntu-ppa/+archive/backports")" repository and upgrading.  Kubuntu 11.04 has been buggy for me and for others (e.g., the [Phonon bug]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274")), while 10.10+backports has been rock solid.

I dumped Amarok for [Clementine]("http://www.clementine-player.org/") a while back.  Amarok2 has never worked well for me.  Clementine is a fork of Amarok 1.4 and works fine.

---

### Post by ADani on 2011-07-20
Thank you for the suggestion, I'll look into Clementine and reconsider upgrading.
thanks again

---

