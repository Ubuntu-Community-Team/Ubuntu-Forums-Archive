---
title: "EasyTAG-2.2.0"
date: 2014-04-11
forum: Multimedia Software
---

### Post by ron998 on 2014-04-11
[SIZE=5]**_[SIZE=7][COLOR=#00ff00]EDIT[SIZE=4] (again)[/SIZE][/COLOR][/SIZE]_**[/SIZE][COLOR=#ff0000][SIZE=5]****[/SIZE][/COLOR][SIZE=3][COLOR=#000000]**_If you don't want to compile EasyTAG yourself, there's a PPA here --->_** [https://launchpad.net/~amigadave/+archive/ppa?field.series_filter=](https://launchpad.net/~amigadave/+archive/ppa?field.series_filter=)[/COLOR][/SIZE][COLOR=#ff0000][SIZE=5][B][U]

I'm not going to update this thread any more now that PPA is available.


EDIT[/U][/B][/SIZE][/COLOR]
EasyTAG-2.2.[COLOR=#ff0000]2[/COLOR] was released on May 9 2014
I've edited the post below from 2.2.0 to 2.2.[COLOR=#ff0000]2[/COLOR].
The procedure is the same.

Hi
**EasyTAG** in the **_Ubuntu-14.04_** repo is version 2.1.10.
But version 2.2.[COLOR=#ff0000]2[/COLOR] has just been released.
It's easy enough to compile.
These commands worked OK for me with 32-bit *buntu-14.04...

Install some packages.
```
sudo apt-get update; \
sudo apt-get -y install build-essential checkinstall; \
sudo apt-get -y build-dep easytag; \
sudo apt-get -y install libopus-dev libopusfile-dev
```

Make a build folder and go there.
```
cd ~/; sudo rm -rf easytag_build; mkdir easytag_build; cd easytag_build
```

Download and configure.
```
wget download.gnome.org/sources/easytag/2.2/easytag-2.2.[COLOR=#ff0000]2[/COLOR].tar.xz -qO- | tar -xJ; cd easytag-*; ./configure
```

Results should look something like this...

Configuration for EasyTAG 2.2.[COLOR=#ff0000]2[/COLOR] :
--------------------------------
MP3 file support ..........   : yes
ID3v2.3 tags support .... : yes (id3lib-3.8.3)
Ogg Vorbis file support . : yes
Ogg Speex file support ..: yes
Ogg Opus file support ... : yes
FLAC file support .........   : yes
MP4 file support ..........   : yes
WavPack support ......... : yes
NLS/gettext ................    : yes
Tests during make check .: yes
Install prefix ..........: /usr/local

If it's OK, go ahead...

Build and install.
```
make; \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname easytag \
--pkgversion 2.2.[COLOR=#ff0000]2[/COLOR] \
--backup=no --fstrans=no --default; sudo ldconfig
```

```
easytag --version
EasyTAG 2.2.[COLOR=#ff0000]2[/COLOR]
Website: [https://wiki.gnome.org/Apps/EasyTAG](https://wiki.gnome.org/Apps/EasyTAG)
```

---

### Post by andrew.46 on 2014-04-12
Great news about the new release! I usually head for easyTAG when commandline tagging is doing my head in :). And as you have mentioned looks like Trusty has just missed out...

---

### Post by shantiq on 2014-04-12
thanx Ron for update info also how do you guys rate [puddletag]("http://puddletag.sourceforge.net/screenshots.html") [in repo] in relation to easytag ...    ever since i discovered its existence   i  stopped using easytag  ...   it seems easier to handle to me    might be just a personal thing


[IMG]http://puddletag.sourceforge.net/_images/5.png[/IMG]

---

### Post by andrew.46 on 2014-04-12
> **shantiq said:**
> thanx Ron for update info also how do you guys rate [puddletag]("http://puddletag.sourceforge.net/screenshots.html") [in repo] in relation to easytag ...    ever since i discovered its existence   i  stopped using easytag  ...   it seems easier to handle to me    might be just a personal thing

For me, and I am not a *huge* user of either Puddletag or EasyTag, both are pretty much the same. Simply that I am more used to EasyTAG and by nature a little too lazy to investigate Puddletag in greater depth :).

---

### Post by howefield on 2014-06-08
Thread closed at authors request.

---

