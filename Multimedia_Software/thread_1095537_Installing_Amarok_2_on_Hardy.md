---
title: "Installing Amarok 2 on Hardy"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Go7enKs on 2009-03-13
Hi guys, been trying to install Amarok 2 on Hardy for 3 days...

I add [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main to my upgrades sources list. 

Then I get 1 new upgrade, a package called Lipcre3. When i try to install it Ubuntu warns me that it's not authenticated so I didn't do it.

Then I try to install amarok 2 with the command sudo apt-get install amarok-kde4 (as suggest the guides I found around internet) but I get an error message:
```
I seguenti pacchetti hanno dipendenze non soddisfatte:
  amarok-kde4: Dipende: kdebase-runtime (>= 4:4.1.2) ma non sta per essere installato
               Dipende: kdelibs5 (>= 4:4.1.2) ma non sta per essere installato
               Dipende: libc6 (>= 2.8~20080505) ma 2.7-10ubuntu4 sta per essere installato
               Dipende: libgcrypt11 (>= 1.4.0) ma 1.2.4-2ubuntu7 sta per essere installato
               Dipende: libmtp8 ma non è installabile
               Dipende: libphonon4 (> 4:4.2.0) ma non sta per essere installato
               Dipende: libqt4-dbus (>= 4.4.3) ma non è installabile
               Dipende: libqt4-network (>= 4.4.3) ma non è installabile
               Dipende: libqt4-opengl (>= 4.4.3) ma non è installabile
               Dipende: libqt4-script (>= 4.4.3) ma non è installabile
               Dipende: libqt4-sql (>= 4.4.3) ma 4.3.4-0ubuntu3 sta per essere installato
               Dipende: libqt4-svg (>= 4.4.3) ma non è installabile
               Dipende: libqt4-webkit (>= 4.4.3) ma non è installabile
               Dipende: libqt4-xml (>= 4.4.3) ma non è installabile
               Dipende: libqtcore4 (>= 4.4.3) ma non è installabile
               Dipende: libqtgui4 (>= 4.4.3) ma non è installabile
               Dipende: libstreamanalyzer0 (>= 0.5.11) ma non sta per essere installato
               Dipende: libstreams0 (>= 0.5.11) ma non sta per essere installato
               Dipende: libtag1c2a (>= 1.5) ma 1.4-8ubuntu1 sta per essere installato
               Dipende: phonon (> 4:4.2.0) ma non è installabile
E: Pacchetto non integro

```
It's in italian but well...at the beginning it says: "The following packages have dependencies not satisfied.

How can I install it? 

Thanks in advance.

---

### Post by Go7enKs on 2009-03-13
Sorry guys. Had a sudden inspiration and solved the problem.

---

### Post by inobe on 2009-03-13
what version of kde is hardy updated to ?

in opensuse i needed to have kde factory repo enabled, the allowed me to have kde 4.2.1, i also had amarok 2.

you may need to update kde desktop to resolve dependencies

> Dipende: kdebase-runtime (>= 4:4.1.2)

---

### Post by inobe on 2009-03-13
> **Go7enKs said:**
> Sorry guys. Had a sudden inspiration and solved the problem.

what did you do ?

---

