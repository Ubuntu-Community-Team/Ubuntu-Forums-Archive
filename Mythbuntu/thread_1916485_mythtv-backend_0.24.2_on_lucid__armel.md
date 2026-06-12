---
title: "mythtv-backend 0.24.2 on lucid / armel?"
date: 2012-01-28
forum: Mythbuntu
---

### Post by coderchris on 2012-01-28
[LEFT]Hello!

I am trying to install mythtv-backend 0.24.2 on lucid. I followed the instructions from mythbuntu.org and have installed the repositories:

deb [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main

On the first look everything is cool with mythtv-backend-master for armel:

cubox@cubox:/$ sudo apt-cache policy mythtv-backend-master
mythtv-backend-master:
  Installiert: (keine)
  Kandidat: 2:0.24.2+fixes.20120127.10d5624-0ubuntu0mythbuntu1
  Versions-Tabelle:
[B]     2:0.24.2+fixes.20120127.10d5624-0ubuntu0mythbuntu1 0
        500 [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/) lucid/main Packages
[/B]     0.23.0+fixes24158-0ubuntu2 0
        500 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/multiverse Packages

but there is no mythtv-backend for armel:

cubox@cubox:/$ sudo apt-cache policy mythtv-backend
mythtv-backend:
  Installiert: (keine)
  Kandidat: 0.23.0+fixes24158-0ubuntu2
  Versions-Tabelle:
     0.23.0+fixes24158-0ubuntu2 0
        500 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/multiverse Packages
        100 /var/lib/dpkg/status

Will there be no armel support for mythtv-backend? But why is there a mythtv-backend-master?

I am stuck here with my brand new cubox (Marvel Armada 510, cool little gadget). What to do now?

Regards,
Christoph

[/LEFT]

---

### Post by nickrout on 2012-01-28
> **coderchris said:**
> [LEFT]Hello!

I am trying to install mythtv-backend 0.24.2 on lucid. I followed the instructions from mythbuntu.org and have installed the repositories:

deb [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main

On the first look everything is cool with mythtv-backend-master for armel:

cubox@cubox:/$ sudo apt-cache policy mythtv-backend-master
mythtv-backend-master:
  Installiert: (keine)
  Kandidat: 2:0.24.2+fixes.20120127.10d5624-0ubuntu0mythbuntu1
  Versions-Tabelle:
[B]     2:0.24.2+fixes.20120127.10d5624-0ubuntu0mythbuntu1 0
        500 [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu/) lucid/main Packages
[/B]     0.23.0+fixes24158-0ubuntu2 0
        500 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/multiverse Packages

but there is no mythtv-backend for armel:

cubox@cubox:/$ sudo apt-cache policy mythtv-backend
mythtv-backend:
  Installiert: (keine)
  Kandidat: 0.23.0+fixes24158-0ubuntu2
  Versions-Tabelle:
     0.23.0+fixes24158-0ubuntu2 0
        500 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/multiverse Packages
        100 /var/lib/dpkg/status

Will there be no armel support for mythtv-backend? But why is there a mythtv-backend-master?

I am stuck here with my brand new cubox (Marvel Armada 510, cool little gadget). What to do now?

Regards,
Christoph

[/LEFT]

I believe you will be better off with debian and the debina-multimedia repo.

---

### Post by coderchris on 2012-01-29
You may be right, and one thing I also want to try is wheezy armhf. But I like Ubuntu (all my other machines run ubuntu) and this is ubuntuforums.org... :)

So has anyone a idea what can be done?

Christoph

---

### Post by nickrout on 2012-01-29
> **coderchris said:**
> You may be right, and one thing I also want to try is wheezy armhf. But I like Ubuntu (all my other machines run ubuntu) and this is ubuntuforums.org... :)

So has anyone a idea what can be done?

Christoph


Well for a start the ubuntu myth ppa soes not get compiled for arm AFAIK.

In fact I don't think ubuntu on arm is all that mature, which is why I pointed to something I know works.

There are a few people on the mailing list running backend on arm, so I suggest you ask there.

---

