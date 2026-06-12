---
title: "Can't open sopcast"
date: 2010-09-12
forum: Multimedia Software
---

### Post by Maestronaza on 2010-09-12
Sorry if I wrote in the other thread, that's why I am opening a new one.

I can't open sopcast, I guess it's because of the conflict with the newer versions of VLC...

Can you help me? 

I tried to uninstall vlc, sopcast, to install only sopcast, but I noticed it automatically installs also vlc...in other words, didn't find any solution by myself nor on the web.

Thanks in advance for help.
Naza

---

### Post by howefield on 2010-09-12
Did you add VLC with a repository ?

If you have, it needs to be removed along with the problem VLC version before installing the older one.

---

### Post by Maestronaza on 2010-09-12
well, if I open the file sources.list, I don't find it anymore. I found one and deleted it...Maybe there is some problem in that file? is it what you mean by repository?

Sorry for my ignorance

---

### Post by howefield on 2010-09-12
As long as you have uninstalled VLC and removed any repositories that you added to your software sources in order to install it, then reload your software sources, sop-cast will pull in the standard vlc for your Ubuntu version which will be 1.0.6 if you are running 10.04.

---

### Post by Maestronaza on 2010-09-12
I'll probably both annoy and bother you by this

This is the sources.list file:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty adunanza
deb-src [http://adurepo.altervista.org/ubuntu](http://adurepo.altervista.org/ubuntu) feisty adunanza

This is the state of the file when i tried to install sopcast and vlc again...but still, sopcast didn't open, and from the layout, I noticed vlc is the newer version.

The only possibility is to bother you more? :P

---

### Post by howefield on 2010-09-12
> **Maestronaza said:**
> I'll probably both annoy and bother you by this

Don't worry, you neither annoy or bother :)

> This is the state of the file when i tried to install sopcast and vlc again...but still, sopcast didn't open, and from the layout, I noticed vlc is the newer version.

When you open VLC, and go to the Help menu and choose About,...what is the version number ?

---

### Post by Maestronaza on 2010-09-12
installed now only vlc, version 1.1.4

---

### Post by howefield on 2010-09-12
What version of Ubuntu are you using ?

If 10.04 try this

Open a terminal and try these commands one at a time

```
sudo apt-get purge vlc
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get install vlc
```

---

### Post by Maestronaza on 2010-09-12
can install sopcast first? without installing vlc? or installing the right version of vlc which doens't conflict?

---

### Post by howefield on 2010-09-12
> **Maestronaza said:**
> can install sopcast first? without installing vlc? or installing the right version of vlc which doens't conflict?

I'm not sure I understand what you said there.

The version of VLC (1.0.6) that you get in a standard Lucid install works fine with sop-cast.

---

### Post by Maestronaza on 2010-09-12
can i install only sopcast now? then i will see about vlc :)

---

### Post by howefield on 2010-09-12
> **Maestronaza said:**
> can i install only sopcast now? then i will see about vlc :)

VLC is a dependancy of sop-cast, so I don't think you will be able to install sop-cast without also installing VLC.

---

### Post by Maestronaza on 2010-09-12
Damn! doesn't work :D 
I tried to install directly sopcast, and the vlc version installed was 1.1.4.

Then purged and cleaned, and installed vlc: version installed again 1.1.4.

I guess I should reinstall the os :D

---

### Post by ilabor on 2010-09-15
[http://ubuntuforums.org/showpost.php?p=9847168&postcount=422](http://ubuntuforums.org/showpost.php?p=9847168&postcount=422)

---

