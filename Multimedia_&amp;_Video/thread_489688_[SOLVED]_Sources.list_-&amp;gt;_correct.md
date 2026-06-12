---
title: "[SOLVED] Sources.list -&amp;gt; correct?"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by neburzaragoza on 2007-07-01
Hi,

i have some problems with some plugins in internet. Overall whan I try to listen music like in [here]("http://www.culturageneral.net/Juego/Test%20de%20Musica%20Clasica/").

I was checking my sources.list in my /etc/apt, and this is what I have

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://security.ubuntu.com/ubuntu breezy-security multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free

```

my Ubuntu version is 6.06 "dapper", but here I see a lot of "breezy" I was wondering whetherit's normal, and if you can give some advices, like changing every breezy to dapper, or what I miss to have a clean and active souces.list with the univers and multivers activ.

the problem is overal about the plugins, so here you have apictures with what I have (is the response of my mozille when I go to about:plugins)
[[img]http://img440.imageshack.us/img440/4815/aboutpluginssb7.th.png[/img]](http://img440.imageshack.us/my.php?image=aboutpluginssb7.png)

Thank you for your help ans suggestions.

---

### Post by Vajra Vrtti on 2007-07-01
If you are using Dapper there should be no references to Breeze.
Here is a tool to generate a correct sources.list:
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

---

### Post by neburzaragoza on 2007-07-02
Thank you for the answer.

Now I have a clean *sources.list*. Very useful your link xD

what about the plugins I need in order to listen to the music in mozilla, any idea?

thaks again.

---

### Post by Vajra Vrtti on 2007-07-02
Try the ***mozilla-mplayer*** package.
Install it with Synaptic.

---

