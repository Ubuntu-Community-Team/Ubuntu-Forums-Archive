---
title: "I am to dumb to install SuperCollider"
date: 2009-11-25
forum: Multimedia Software
---

### Post by osterchrisi on 2009-11-25
Hey!

I don't know what I'm doing wrong:
I added **ppa:supercollider/ppa** to my software sources and succesfully installed the gpg key. But when I try to update my software it says:
```
GPG error: http://ppa.launchpad.net karmic Release: Die folgenden Signaturen konnten nicht überprüft werden, weil ihr öffentlicher Schlüssel nicht verfügbar ist: NO_PUBKEY 26F4EF8440618B66Konnte http://ppa.launchpad.net/supercollider/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz nicht holen  404  Not Found
Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.
```

which means something like:

```
... The following signatures could not be approved because their public key is not available: ...
Some index files could not be downloaded, they were ignored or old ones were used instead.
```

Which step did I miss? I use Ubuntu Karmic.
Any help appreciated, thank you very much!!

---

### Post by ilil on 2009-11-26
Maybe some bug in Launchpad? Try to report about this to supercollider/ppa owner.

Anyway, you can install packages without signatures (just pass by those warnings)

---

### Post by Serious Black on 2010-02-03
I had the same problem. I think the repository does not provide packages for karmic, since the only listed packages are for hardy, intrepid and jaunty. Is compiling from source the only option then, or could I try to install the jaunty version without risking my system stability??

---

### Post by Da_MerV on 2010-02-12
I'm having the same issue. I don't believe they actually have a karmic release. Anyone have a solution?

---

### Post by calimerox on 2010-02-19
yeah, the same thing for me... but i remember that i had it once installed on another karmic system, so it should work somehow...

---

### Post by omegvermelho on 2010-10-02
Im running Lucid with KXStudio PPA (similar to UbuntuStudio but KDE based) i got the SCollider PPA from :

[https://launchpad.net/~supercollider/+archive/ppa/]("https://launchpad.net/%7Esupercollider/+archive/ppa/")

and it works fine, also you might want to check 

[http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html](http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html) 

its nice tutorial on how to use the SC-Gedit plugin....(altho there options for vim and acouple more iirc)

Anyway if i understand correctly you´re running Karmic so in your sources list you should add 
deb [http://ppa.launchpad.net/supercollider/ppa/ubuntu](http://ppa.launchpad.net/supercollider/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/supercollider/ppa/ubuntu](http://ppa.launchpad.net/supercollider/ppa/ubuntu) karmic main

(for any other distro check the dropdown menu)

---

