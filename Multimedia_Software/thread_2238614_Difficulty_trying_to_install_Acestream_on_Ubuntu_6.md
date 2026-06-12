---
title: "Difficulty trying to install Acestream on Ubuntu 64 bit Trusty"
date: 2014-08-08
forum: Multimedia Software
---

### Post by gunna999 on 2014-08-08
Have been trying for a few weeks now to install Acestream without success. It is not available thru the software centre but I have found several guides on the install, unfortunately some of the software sources are no longer available and it seems that some of the files I need are missing. These include libav-extra/libavcodec-extra-53_0.8.10ubuntu0.12.04.1_amd64.deb.

 I have used the following guides : [http://acestreamguide.com/linux/](http://acestreamguide.com/linux/)    and   [http://ahmek.wordpress.com/2014/04/30/how-to-setup-acestream-in-ubuntu-14-04-64bit/](http://ahmek.wordpress.com/2014/04/30/how-to-setup-acestream-in-ubuntu-14-04-64bit/) and [http://forums.linuxmint.com/viewtopic.php?f=47&t=167991](http://forums.linuxmint.com/viewtopic.php?f=47&t=167991).

Has anyone had any success installing acestream on 64 bit trusty? Any help is appreciated.

---

### Post by robegue on 2014-08-23
In general, you can modify a deb file in order to remove dependency conflicts:

download the deb file with: aptitude download <package>

now open a terminal and follow these steps

mkdir tmp
cd tmp
dpkg-deb -x ../package.deb .   #note the final mark
dpkg-deb -e ../package.deb     #without mark

Now edit DEBIAN/control

and rebuild:

dpkg-deb -b . ../newpackage.deb   #note the initial mark

and install:

dpkg -i ../newpackage.deb


If you're lazy you may use my packages:

[http://dl.dropbox.com/u/10405722/acestream-ubuntu-trusty.tar.gz](http://dl.dropbox.com/u/10405722/acestream-ubuntu-trusty.tar.gz)

but remember that some dependencies have been removed, so you may need to install some package in order to make it work.
Good luck....

---

### Post by guccimucci on 2014-08-23
Sorry for interrupting, but as I have the same problem I'll post here.
I installed your packages and I now finally have AceStream on my computer, but it doesn't load any streams, it only says:  "Loading error.:

 [COLOR=#000000]Could not read the file acestream://73ba5f6bb6ec44c5882f9d3f91036959fbd135d8. Error message: bad bencoded data[/COLOR]"

---

### Post by deviant78 on 2014-10-09
> **guccimucci said:**
> Sorry for interrupting, but as I have the same problem I'll post here.
I installed your packages and I now finally have AceStream on my computer, but it doesn't load any streams, it only says:  "Loading error.:

 [COLOR=#000000]Could not read the file acestream://73ba5f6bb6ec44c5882f9d3f91036959fbd135d8. Error message: bad bencoded data[/COLOR]"

Did you manage to get past this error? This is where i'm stuck now.

---

### Post by dwpbike on 2014-11-02
bump.  after seeing joker in action, i'm interested in this.

---

### Post by awmian on 2014-11-08
Acestream for trusty is now available from repository. Here is the link to it:

[http://forum.torrentstream.org/index.php?topic=2969.0]("http://forum.torrentstream.org/index.php?topic=2969.0")

Make sure to remove previous versions if installed from a different repository.

Here's the link to the wiki:

[http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en]("http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en")

---

