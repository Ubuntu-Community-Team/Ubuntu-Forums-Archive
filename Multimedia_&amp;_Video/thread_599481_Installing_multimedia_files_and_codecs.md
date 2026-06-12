---
title: "Installing multimedia files and codecs"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by geovino on 2007-11-01
I followed these instructions...
Synaptic

    *

      Go to Applications &#8594; Add/Remove...
    *

      Set Show: to All available applications
    *

      Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras and kubuntu-restricted-extras.

But I don't have a ubuntu-restricted-extras listed. where else can I go to install the codecs?

I used to used Automatix, but everyone says not to use it anymore.

---

### Post by taurus on 2007-11-01
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by geovino on 2007-11-01
> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

Here it is...

davek@davek-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
davek@davek-desktop:~$

---

### Post by geovino on 2007-11-01
Tried automatix again. But it wouldn't install the codecs. So I uninstalled it and remmed ot out in the sources.list and was able to get the libdvdcss and w32codecs installed. DVDs work but amarok still is looking for some file. What could it be?

Here's the error for amarok:
Error Loading Media
There is no available decoder.
[http://scfire-chi-aa03.stream.aol.com:80/stream/1018](http://scfire-chi-aa03.stream.aol.com:80/stream/1018)


Gutsy is better at finding the needed files, but some programs needs extra help. :)

---

### Post by SlCKB0Y on 2007-11-04
Top right corner of the Add/Remove software application. Make sure it says "All available applications"

---

### Post by geovino on 2007-11-04
Thanks I did that and uninstalled and reinstalled Amarok. but it still can't play. 

Amarok is no better than Exaile or Listen and they work. 

I uninstalled amarok for now. I don't really need it. 

I went to refresh synaptic after the uninstall and I get this error:

[http://archive.canonical.com/ubuntu/dists/gutsy/Release:](http://archive.canonical.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz:) 400 Bad Request
[http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz:) 400 Bad Request

What's this about?

---

### Post by Vn Tutor on 2007-11-04
I think that you have to install non-free multimedia codecs known as w32codecs and libdvdcss2 package. In [[COLOR="Blue"]this post[/COLOR]]("http://vntutor.blogspot.com/2007/10/play-dvd-and-listen-to-mp3-music-in.html"), you can know how to update your source.list file to setup these packages.

---

### Post by geovino on 2007-11-04
> **Vn Tutor said:**
> I think that you have to install non-free multimedia codecs known as w32codecs and libdvdcss2 package. In [[COLOR="Blue"]this post[/COLOR]]("http://vntutor.blogspot.com/2007/10/play-dvd-and-listen-to-mp3-music-in.html"), you can know how to update your source.list file to setup these packages.

Both of those files are installed already. I can play cds dvds, and live streaming on Exaile and Streamtuner-Xmms. So what would cause that error? A temporary server problem?

...Synaptic is reloading fine now.

---

