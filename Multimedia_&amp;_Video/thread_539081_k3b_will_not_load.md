---
title: "k3b will not load"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by Rumpty on 2007-08-30
I posted this query in General Help a couple of days ago, but there were no responses. Since then I've tried a fresh installation of Kubuntu Feisty i386, and there is the same problem when I try to load k3b, from the terminal, or from the menu. K3b does not appear.

The terminal output is:
 
 colin@ubuntuamd:~$ k3b
 kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
 (K3bDevice::HalConnection) initializing HAL >= 0.5
 Mapping udi /org/freedesktop/Hal/devices/storage_model_RICOH_C D_R/RW_MP7240A to device /dev/hdc
 /dev/hdc resolved to /dev/hdc
 /dev/hdc is block device (0)
 /dev/hdc seems to be cdrom
 (K3bDevice:evice) /dev/hdc: init()
 
 The CDROM will not then eject using the button on the front.
 
 The same hardware works fine in Dapper, Kubuntu AMD64.

Any ideas about the cause please?

---

### Post by kingofpain on 2007-08-31
[http://www.getdeb.net/release.php?id=1326](http://www.getdeb.net/release.php?id=1326)

Did you install all those three packages? (libk3b2,  k3b and  libk3b2-mp3)

---

### Post by Rumpty on 2007-08-31
> **kingofpain said:**
> [http://www.getdeb.net/release.php?id=1326](http://www.getdeb.net/release.php?id=1326)

Did you install all those three packages? (libk3b2,  k3b and  libk3b2-mp3)

libk3b2-mp3 wasn't installed, so I installed it. The other two were installed. K3b still will not run though. I did a purge uninstall and a re-install of it, but no change in the situation.

Thanks for your interest though.

---

