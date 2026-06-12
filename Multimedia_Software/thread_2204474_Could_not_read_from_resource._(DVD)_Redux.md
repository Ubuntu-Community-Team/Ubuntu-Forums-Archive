---
title: "Could not read from resource. (DVD) Redux"
date: 2014-02-08
forum: Multimedia Software
---

### Post by Bob Unitt on 2014-02-08
I'm on Ubuntu 10.04 (I know it's old but...). Trying to play a video DVD (Game of Thrones, as it happens). I can play other video DVD's on this PC and I can play this DVD on my TV. Trying to play this video on my PC gives me "An error occurred  Could not read from resource". I found an old closed thread "*Could not read from resource. (DVD)*" which points to a how-to to fix this issue ([Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")) - but it requires Medibuntu, which apparently no longer exists. What do I do instead ?

---

### Post by mikewhatever on 2014-02-08
Medibuntu used to host the decrypter for DVDs, but you probably already have it, since you've said other DVDs play ok. Anyway, it's now available from [http://download.videolan.org/](http://download.videolan.org/), and Ubuntu pulls it from there. It's usually done by running the following:
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
The problem could have something to do with the regeon settings, but I am not really sure. 
Ufortunately, DVDs are just ridiculous like that. Even worse, it's been intentionally desingned to be this way.

PS: I also have to say, that how to is really old. Don't you see the huje red letters up top?

---

### Post by Bob Unitt on 2014-02-09
> **mikewhatever said:**
> Medibuntu used to host the decrypter for DVDs, but you probably already have it, since you've said other DVDs play ok. Anyway, it's now available from [http://download.videolan.org/](http://download.videolan.org/), and Ubuntu pulls it from there. 
Any idea where on that site ? all I see is a hierarchy of folder-names.

> It's usually done by running the following: <sudo /usr/share/doc/libdvdread4/install-css.sh>
Unfortunately, that just tries to load Medibuntu again.

> The problem could have something to do with the regeon settings, but I am not really sure. 
Ufortunately, DVDs are just ridiculous like that. Even worse, it's been intentionally desingned to be this way.
I would have expected a different message in that case.

> PS: I also have to say, that how to is really old. Don't you see the huje red letters up top?
What directly follows those 'huge red letters' is an updated version of the instructions, the original version the red notice refers to is much further down the page.

---

### Post by Bucky Ball on 2014-02-09
*Thread moved to **Multimedia & Video**.*

---

### Post by Bob Unitt on 2014-02-09
Oops sorry, Moderator

---

### Post by mikewhatever on 2014-02-09
Right, 10.04 is unsupported, so the Medibuntu related stuff never got updated. The script now looks as follows, just in case you are interested:
> #!/bin/sh
# Shell script to install libdvdcss under Debian GNU Linux
# Many DVDs use css for encryption.  To play these discs, a special library 
# is needed to decode them, libdvdcss.  Due to legal problems, Debian and most
# Linux distibutions cannot distribute libdvdcss
# Use this shell script to install the libdvdcss under DEBIAN GNU/Linux
# --------------------------------------------------------------------------
# Refer url for more info:
# Copyright info -  [http://www.dtek.chalmers.se/~dvd/](http://www.dtek.chalmers.se/~dvd/)
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit [http://bash.cyberciti.biz/](http://bash.cyberciti.biz/) for more information.
# -------------------------------------------------------------------------
# Addition of checking for current version.  Gene Cumm <gene.cumm@gmail.com>
# -------------------------------------------------------------------------

set -e

if [ ! -w /etc/passwd ]; then
    echo "Super-user privileges are required.  Please run this with 'sudo'." >&2
    exit 1
fi

sitert=http://download.videolan.org/
site=${sitert}pub/debian/stable/
arch=$(dpkg --print-architecture)

soname=2
uversion=1.2.13
available="i386 amd64"
version=${uversion}-0

do_dyn=T
dist=$(lsb_release -cs)

if ! type wget > /dev/null ; then
    echo "Install wget and run this script again" >&2
    exit 1
fi

CSSTMP=$(mktemp -t -d dvdcss-XXXXXX)

# Attempt to dymanically fetch the current version
# dep: grep sed
if [ "$do_dyn" = "T" ];then
    for a in grep sed head; do
	if ! type "$a" > /dev/null ; then
	    echo "Can not find ${a}; Needed for dymanic fetch"
	    do_dyn=F
	fi
    done
fi
if [ "$do_dyn" = "T" ];then
    set +e	# prevent this from stopping everything
    wget "${site}/Packages" -O "$CSSTMP"/Packages && \
	url=${site}$(grep "Filename: .*libdvdcss${soname}.*${arch}.*\.deb" "$CSSTMP"/Packages|sed  's/Filename: //'|head -n 1) && \
	wget "${url}" -O "$CSSTMP"/libdvdcss.deb && \
	dpkg -i "$CSSTMP"/libdvdcss.deb && \
	exit 0
    echo "Dynamic fetch failed; Falling back to static fetch"
    set -e	# undo
else
	echo "Skipping dynamic fetch"
fi

for a in $available; do
    if [  "$a" = "$arch" ]; then
	wget ${site}libdvdcss${soname}_${version}_${arch}.deb -O "$CSSTMP"/libdvdcss.deb
	dpkg -i "$CSSTMP"/libdvdcss.deb
	exit $?
    fi
done

echo "No prebuilt binary available.  Will try to build and install it."
echo "You need to have build-essential, debhelper and fakeroot installed."
echo "If not, interrupt now, install them and rerun this script."
echo ""
echo "This is higly experimental, look out for what happens below."
echo "If you want to stop, interrupt now (control-c), else press"
echo "return to proceed"
read dum

if ! type dh_testdir > /dev/null || ! type fakeroot > /dev/null; then
    echo "Attempting to install build-essential, debhelper and fakeroot..." >&2
    apt-get update && apt-get install build-essential debhelper fakeroot
fi

if ! type dh_testdir > /dev/null || ! type fakeroot > /dev/null || 
! type make > /dev/null ; then
    echo "Failed to install build-essential, debhelper and fakeroot, exiting now." >&2
    exit 1
fi

cd "$CSSTMP"
wget ${site}libdvdcss_${uversion}.orig.tar.gz
wget ${site}libdvdcss_${version}.debian.tar.gz
wget ${site}libdvdcss_${version}.dsc
dpkg-source -x libdvdcss_${version}.dsc
cd libdvdcss-${uversion}
fakeroot ./debian/rules binary
dpkg -i ../libdvdcss${soname}_${version}_${arch}.deb

...and the package in question is in [http://download.videolan.org/debian/precise/](http://download.videolan.org/debian/precise/). I don't know if any of that is going to work on Lucid. Likely not, but as said above, it plays other DVDs, which means you must have the lib installed.

PS: Not sure what message you've expected, just don't try to be too reasonable while dealing with DVDs.

---

### Post by Bob Unitt on 2014-02-11
> **mikewhatever said:**
> Right, 10.04 is unsupported, so the Medibuntu related stuff never got updated. The script now looks as follows, just in case you are interested:
...and the package in question is in [http://download.videolan.org/debian/precise/](http://download.videolan.org/debian/precise/). I don't know if any of that is going to work on Lucid. Likely not, but as said above, it plays other DVDs, which means you must have the lib installed.
You, Sir, are a scholar and a gentleman - that script did the trick. Thank you.

*eta:* (it may be that it needed the procedures described in [http://www.videolan.org/developers/libdvdcss.html]("http://www.videolan.org/developers/libdvdcss.html"), which I'd done previous to this script but had no effect on it's own).

---

