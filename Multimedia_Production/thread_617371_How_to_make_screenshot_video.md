---
title: "How to make screenshot video"
date: 2007-11-19
forum: Multimedia Production
---

### Post by tdn on 2007-11-19
I have seen a lot of screen shot videos like these:
 * [http://digikam3rdparty.free.fr/TourMovies/lighttable.swf](http://digikam3rdparty.free.fr/TourMovies/lighttable.swf)
 * [http://media.rubyonrails.org/video/rails_take2_with_sound.mov](http://media.rubyonrails.org/video/rails_take2_with_sound.mov)
 * [http://www.kirix.com/screencast.html](http://www.kirix.com/screencast.html)
 * [http://www.youtube.com/watch?v=tLnv46Kk2rs](http://www.youtube.com/watch?v=tLnv46Kk2rs)

How do I create such screen shot videos in Ubuntu?
It would be nice to be able to create such videos so that I can make visual HOWTOs for Ubuntu.
Often people ask me "how do I do X", and if it is something that needs to be done from the command line, fine, I just write a simple HOWTO, but if it is something that needs interaction with the GUI, then it is a bit difficult to both write and follow a written HOWTO.

Thus, the ability to make screen shot videos would be great. How do I do it in Ubuntu?

---

### Post by yabbies on 2007-11-19
recordMyDesktop

```
sudo apt-get install gtk-recordmydesktop
```

---

### Post by tdn on 2007-11-19
Ok. Thanks.
I use KDE. What do you recommend for KDE?

---

### Post by tdn on 2007-11-19
> **yabbies said:**
> recordMyDesktop

```
sudo apt-get install gtk-recordmydesktop
```


I did just that and I got this error:

```

~/wc $ sudo apt-get install gtk-recordmydesktop
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpisock9 libcompfaceg1 libt1-5 libfltk1.1 libcinepaint0 libetpan10
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-media-common libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-media0 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7
  libgtop2-common libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras python-pyorbit recordmydesktop
Suggested packages:
  gda2-mysql gda2-postgres gda2-odbc gda2-sqlite gda2-freetds python-gnome2-desktop-doc python-gnome2-desktop-dbg python-gnome2-extras-doc python-gnome2-extras-dbg python-pyorbit-dbg
Recommended packages:
  gnome-media libgda2-bin
The following NEW packages will be installed:
  gnome-media-common gtk-recordmydesktop libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-media0 libgtksourceview-common libgtksourceview1.0-0
  libgtkspell0 libgtop2-7 libgtop2-common libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras python-pyorbit recordmydesktop
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 3834kB of archives.
After unpacking 19,8MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  gnome-media-common recordmydesktop libgda2-common libgda2-3 libgdl-1-common libgdl-1-0 libgksu1.2-1 libgksuui1.0-1 libgtkspell0 python-pyorbit libgnome-media0 libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-common libgtop2-7 libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras gtk-recordmydesktop
Install these packages without verification [y/N]? y
Get:1 http://dk.archive.ubuntu.com feisty/main gnome-media-common 2.18.0-0ubuntu1 [2110kB]
Get:2 http://dk.archive.ubuntu.com feisty/universe recordmydesktop 0.3.1-1 [41,0kB]
Get:3 http://dk.archive.ubuntu.com feisty/main libgda2-common 1.2.4-0ubuntu1 [81,0kB]
Get:4 http://dk.archive.ubuntu.com feisty/main libgda2-3 1.2.4-0ubuntu1 [230kB]
Get:5 http://dk.archive.ubuntu.com feisty/main libgdl-1-common 0.6.1-1 [20,8kB]
Get:6 http://dk.archive.ubuntu.com feisty/main libgdl-1-0 0.6.1-1 [85,5kB]
Get:7 http://dk.archive.ubuntu.com feisty/main libgksu1.2-1 1.3.8-1ubuntu3 [31,7kB]
Get:8 http://dk.archive.ubuntu.com feisty/main libgksuui1.0-1 1.0.7-1ubuntu3 [20,3kB]
Get:9 http://dk.archive.ubuntu.com feisty/main libgtkspell0 2.0.10-3 [13,1kB]
Get:10 http://dk.archive.ubuntu.com feisty/main python-pyorbit 2.14.2-0ubuntu3 [96,1kB]
Get:11 http://dk.archive.ubuntu.com feisty/main libgnome-media0 2.18.0-0ubuntu1 [122kB]
Get:12 http://dk.archive.ubuntu.com feisty/main libgtksourceview-common 1.8.5-0ubuntu1 [84,2kB]
Get:13 http://dk.archive.ubuntu.com feisty/main libgtksourceview1.0-0 1.8.5-0ubuntu1 [112kB]
Get:14 http://dk.archive.ubuntu.com feisty/main libgtop2-common 2.14.8-0ubuntu1 [38,1kB]
Get:15 http://dk.archive.ubuntu.com feisty/main libgtop2-7 2.14.8-0ubuntu1 [66,1kB]
Get:16 http://dk.archive.ubuntu.com feisty/main libnautilus-burn4 2.18.1-0ubuntu1 [89,3kB]
Get:17 http://dk.archive.ubuntu.com feisty/main libtotem-plparser1 2.18.1-0ubuntu3 [42,8kB]
Get:18 http://dk.archive.ubuntu.com feisty/main python-gnome2-desktop 2.18.0-0ubuntu3 [285kB]
Get:19 http://dk.archive.ubuntu.com feisty/main python-gnome2-extras 2.14.3-0ubuntu1 [227kB]
Get:20 http://dk.archive.ubuntu.com feisty/universe gtk-recordmydesktop 0.3.0r2-2 [38,3kB]
Fetched 3834kB in 15s (244kB/s)
Selecting previously deselected package gnome-media-common.
(Reading database ... 196728 files and directories currently installed.)
Unpacking gnome-media-common (from .../gnome-media-common_2.18.0-0ubuntu1_all.deb) ...
Selecting previously deselected package recordmydesktop.
Unpacking recordmydesktop (from .../recordmydesktop_0.3.1-1_i386.deb) ...
Selecting previously deselected package libgda2-common.
Unpacking libgda2-common (from .../libgda2-common_1.2.4-0ubuntu1_all.deb) ...
Selecting previously deselected package libgda2-3.
Unpacking libgda2-3 (from .../libgda2-3_1.2.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgdl-1-common.
Unpacking libgdl-1-common (from .../libgdl-1-common_0.6.1-1_all.deb) ...
Selecting previously deselected package libgdl-1-0.
Unpacking libgdl-1-0 (from .../libgdl-1-0_0.6.1-1_i386.deb) ...
Selecting previously deselected package libgksu1.2-1.
Unpacking libgksu1.2-1 (from .../libgksu1.2-1_1.3.8-1ubuntu3_i386.deb) ...
Selecting previously deselected package libgksuui1.0-1.
Unpacking libgksuui1.0-1 (from .../libgksuui1.0-1_1.0.7-1ubuntu3_i386.deb) ...
Selecting previously deselected package libgtkspell0.
Unpacking libgtkspell0 (from .../libgtkspell0_2.0.10-3_i386.deb) ...
Selecting previously deselected package python-pyorbit.
Unpacking python-pyorbit (from .../python-pyorbit_2.14.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package libgnome-media0.
Unpacking libgnome-media0 (from .../libgnome-media0_2.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtksourceview-common.
Unpacking libgtksourceview-common (from .../libgtksourceview-common_1.8.5-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtksourceview1.0-0.
Unpacking libgtksourceview1.0-0 (from .../libgtksourceview1.0-0_1.8.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtop2-common.
Unpacking libgtop2-common (from .../libgtop2-common_2.14.8-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtop2-7.
Unpacking libgtop2-7 (from .../libgtop2-7_2.14.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnautilus-burn4.
Unpacking libnautilus-burn4 (from .../libnautilus-burn4_2.18.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libtotem-plparser1.
Unpacking libtotem-plparser1 (from .../libtotem-plparser1_2.18.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-gnome2-desktop.
Unpacking python-gnome2-desktop (from .../python-gnome2-desktop_2.18.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-gnome2-extras.
Unpacking python-gnome2-extras (from .../python-gnome2-extras_2.14.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package gtk-recordmydesktop.
Unpacking gtk-recordmydesktop (from .../gtk-recordmydesktop_0.3.0r2-2_all.deb) ...
Setting up gnome-media-common (2.18.0-0ubuntu1) ...

Setting up recordmydesktop (0.3.1-1) ...
Setting up libgda2-common (1.2.4-0ubuntu1) ...
Setting up libgda2-3 (1.2.4-0ubuntu1) ...

Setting up libgksu1.2-1 (1.3.8-1ubuntu3) ...

Setting up libgksuui1.0-1 (1.0.7-1ubuntu3) ...

Setting up libgtkspell0 (2.0.10-3) ...

Setting up python-pyorbit (2.14.2-0ubuntu3) ...
Setting up libgnome-media0 (2.18.0-0ubuntu1) ...

Setting up libgtksourceview-common (1.8.5-0ubuntu1) ...
Setting up libgtksourceview1.0-0 (1.8.5-0ubuntu1) ...

Setting up libgtop2-common (2.14.8-0ubuntu1) ...
Setting up libgtop2-7 (2.14.8-0ubuntu1) ...

Setting up libnautilus-burn4 (2.18.1-0ubuntu1) ...

Setting up libtotem-plparser1 (2.18.1-0ubuntu3) ...

Setting up python-gnome2-desktop (2.18.0-0ubuntu3) ...

Setting up libgdl-1-common (0.6.1-1) ...
Setting up libgdl-1-0 (0.6.1-1) ...

Setting up python-gnome2-extras (2.14.3-0ubuntu1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up gtk-recordmydesktop (0.3.0r2-2) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file



```

---

### Post by theorganloft on 2007-11-20
> **tdn said:**
> I did just that and I got this error:

```

~/wc $ sudo apt-get install gtk-recordmydesktop
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpisock9 libcompfaceg1 libt1-5 libfltk1.1 libcinepaint0 libetpan10
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-media-common libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-media0 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7
  libgtop2-common libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras python-pyorbit recordmydesktop
Suggested packages:
  gda2-mysql gda2-postgres gda2-odbc gda2-sqlite gda2-freetds python-gnome2-desktop-doc python-gnome2-desktop-dbg python-gnome2-extras-doc python-gnome2-extras-dbg python-pyorbit-dbg
Recommended packages:
  gnome-media libgda2-bin
The following NEW packages will be installed:
  gnome-media-common gtk-recordmydesktop libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-media0 libgtksourceview-common libgtksourceview1.0-0
  libgtkspell0 libgtop2-7 libgtop2-common libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras python-pyorbit recordmydesktop
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 3834kB of archives.
After unpacking 19,8MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  gnome-media-common recordmydesktop libgda2-common libgda2-3 libgdl-1-common libgdl-1-0 libgksu1.2-1 libgksuui1.0-1 libgtkspell0 python-pyorbit libgnome-media0 libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-common libgtop2-7 libnautilus-burn4 libtotem-plparser1 python-gnome2-desktop python-gnome2-extras gtk-recordmydesktop
Install these packages without verification [y/N]? y
Get:1 http://dk.archive.ubuntu.com feisty/main gnome-media-common 2.18.0-0ubuntu1 [2110kB]
Get:2 http://dk.archive.ubuntu.com feisty/universe recordmydesktop 0.3.1-1 [41,0kB]
Get:3 http://dk.archive.ubuntu.com feisty/main libgda2-common 1.2.4-0ubuntu1 [81,0kB]
Get:4 http://dk.archive.ubuntu.com feisty/main libgda2-3 1.2.4-0ubuntu1 [230kB]
Get:5 http://dk.archive.ubuntu.com feisty/main libgdl-1-common 0.6.1-1 [20,8kB]
Get:6 http://dk.archive.ubuntu.com feisty/main libgdl-1-0 0.6.1-1 [85,5kB]
Get:7 http://dk.archive.ubuntu.com feisty/main libgksu1.2-1 1.3.8-1ubuntu3 [31,7kB]
Get:8 http://dk.archive.ubuntu.com feisty/main libgksuui1.0-1 1.0.7-1ubuntu3 [20,3kB]
Get:9 http://dk.archive.ubuntu.com feisty/main libgtkspell0 2.0.10-3 [13,1kB]
Get:10 http://dk.archive.ubuntu.com feisty/main python-pyorbit 2.14.2-0ubuntu3 [96,1kB]
Get:11 http://dk.archive.ubuntu.com feisty/main libgnome-media0 2.18.0-0ubuntu1 [122kB]
Get:12 http://dk.archive.ubuntu.com feisty/main libgtksourceview-common 1.8.5-0ubuntu1 [84,2kB]
Get:13 http://dk.archive.ubuntu.com feisty/main libgtksourceview1.0-0 1.8.5-0ubuntu1 [112kB]
Get:14 http://dk.archive.ubuntu.com feisty/main libgtop2-common 2.14.8-0ubuntu1 [38,1kB]
Get:15 http://dk.archive.ubuntu.com feisty/main libgtop2-7 2.14.8-0ubuntu1 [66,1kB]
Get:16 http://dk.archive.ubuntu.com feisty/main libnautilus-burn4 2.18.1-0ubuntu1 [89,3kB]
Get:17 http://dk.archive.ubuntu.com feisty/main libtotem-plparser1 2.18.1-0ubuntu3 [42,8kB]
Get:18 http://dk.archive.ubuntu.com feisty/main python-gnome2-desktop 2.18.0-0ubuntu3 [285kB]
Get:19 http://dk.archive.ubuntu.com feisty/main python-gnome2-extras 2.14.3-0ubuntu1 [227kB]
Get:20 http://dk.archive.ubuntu.com feisty/universe gtk-recordmydesktop 0.3.0r2-2 [38,3kB]
Fetched 3834kB in 15s (244kB/s)
Selecting previously deselected package gnome-media-common.
(Reading database ... 196728 files and directories currently installed.)
Unpacking gnome-media-common (from .../gnome-media-common_2.18.0-0ubuntu1_all.deb) ...
Selecting previously deselected package recordmydesktop.
Unpacking recordmydesktop (from .../recordmydesktop_0.3.1-1_i386.deb) ...
Selecting previously deselected package libgda2-common.
Unpacking libgda2-common (from .../libgda2-common_1.2.4-0ubuntu1_all.deb) ...
Selecting previously deselected package libgda2-3.
Unpacking libgda2-3 (from .../libgda2-3_1.2.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgdl-1-common.
Unpacking libgdl-1-common (from .../libgdl-1-common_0.6.1-1_all.deb) ...
Selecting previously deselected package libgdl-1-0.
Unpacking libgdl-1-0 (from .../libgdl-1-0_0.6.1-1_i386.deb) ...
Selecting previously deselected package libgksu1.2-1.
Unpacking libgksu1.2-1 (from .../libgksu1.2-1_1.3.8-1ubuntu3_i386.deb) ...
Selecting previously deselected package libgksuui1.0-1.
Unpacking libgksuui1.0-1 (from .../libgksuui1.0-1_1.0.7-1ubuntu3_i386.deb) ...
Selecting previously deselected package libgtkspell0.
Unpacking libgtkspell0 (from .../libgtkspell0_2.0.10-3_i386.deb) ...
Selecting previously deselected package python-pyorbit.
Unpacking python-pyorbit (from .../python-pyorbit_2.14.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package libgnome-media0.
Unpacking libgnome-media0 (from .../libgnome-media0_2.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtksourceview-common.
Unpacking libgtksourceview-common (from .../libgtksourceview-common_1.8.5-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtksourceview1.0-0.
Unpacking libgtksourceview1.0-0 (from .../libgtksourceview1.0-0_1.8.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtop2-common.
Unpacking libgtop2-common (from .../libgtop2-common_2.14.8-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtop2-7.
Unpacking libgtop2-7 (from .../libgtop2-7_2.14.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnautilus-burn4.
Unpacking libnautilus-burn4 (from .../libnautilus-burn4_2.18.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libtotem-plparser1.
Unpacking libtotem-plparser1 (from .../libtotem-plparser1_2.18.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-gnome2-desktop.
Unpacking python-gnome2-desktop (from .../python-gnome2-desktop_2.18.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-gnome2-extras.
Unpacking python-gnome2-extras (from .../python-gnome2-extras_2.14.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package gtk-recordmydesktop.
Unpacking gtk-recordmydesktop (from .../gtk-recordmydesktop_0.3.0r2-2_all.deb) ...
Setting up gnome-media-common (2.18.0-0ubuntu1) ...

Setting up recordmydesktop (0.3.1-1) ...
Setting up libgda2-common (1.2.4-0ubuntu1) ...
Setting up libgda2-3 (1.2.4-0ubuntu1) ...

Setting up libgksu1.2-1 (1.3.8-1ubuntu3) ...

Setting up libgksuui1.0-1 (1.0.7-1ubuntu3) ...

Setting up libgtkspell0 (2.0.10-3) ...

Setting up python-pyorbit (2.14.2-0ubuntu3) ...
Setting up libgnome-media0 (2.18.0-0ubuntu1) ...

Setting up libgtksourceview-common (1.8.5-0ubuntu1) ...
Setting up libgtksourceview1.0-0 (1.8.5-0ubuntu1) ...

Setting up libgtop2-common (2.14.8-0ubuntu1) ...
Setting up libgtop2-7 (2.14.8-0ubuntu1) ...

Setting up libnautilus-burn4 (2.18.1-0ubuntu1) ...

Setting up libtotem-plparser1 (2.18.1-0ubuntu3) ...

Setting up python-gnome2-desktop (2.18.0-0ubuntu3) ...

Setting up libgdl-1-common (0.6.1-1) ...
Setting up libgdl-1-0 (0.6.1-1) ...

Setting up python-gnome2-extras (2.14.3-0ubuntu1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up gtk-recordmydesktop (0.3.0r2-2) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file



```

I loaded mine from GetDeb and it works.  [http://www.getdeb.net/](http://www.getdeb.net/)

The only problem I am having is with the sound recording.  For Jack it says some library is missing.  :guitar:

---

### Post by loell on 2007-11-20
it is  advisable to remove gtk-recordmydesktop

by doing

```
sudo apt-get remove gtk-recordmydesktop
```


since you are in KDE install   qt-recordmydesktop

```
sudo apt-get install qt-recordmydesktop
```

---

### Post by tdn on 2007-11-20
loeil: Thank you.

---

### Post by tdn on 2007-11-20
> **loell said:**
> it is  advisable to remove gtk-recordmydesktop

by doing

```
sudo apt-get remove gtk-recordmydesktop
```


since you are in KDE install   qt-recordmydesktop

```
sudo apt-get install qt-recordmydesktop
```

The package qt-recordmydesktop does not exist.

---

### Post by loell on 2007-11-20
oh sorry, in ubuntu gutsy it is still named as **krecordmydesktop**

so just do


```
sudo apt-get install krecordmydesktop 
```

in future versions of ubuntu, the name will most probably be change as

qt-recordmydesktop.

---

### Post by tdn on 2007-11-20
> **loell said:**
> oh sorry, in ubuntu gutsy it is still named as **krecordmydesktop**

so just do


```
sudo apt-get install krecordmydesktop 
```

in future versions of ubuntu, the name will most probably be change as

qt-recordmydesktop.


I use Feisty:
Couldn't find any package whose name or description matched "krecordmydesktop"

---

### Post by loell on 2007-11-20
:( , yeah really not availabe in fiesty.

for what its worth, still you can use recordmydesktop in command line

and just press ctrl + c to stop the recording, you can also try **istanbul** , and **xvidcap** in fiesty.

---

### Post by tdn on 2007-11-20
> **loell said:**
> :( , yeah really not availabe in fiesty.

for what its worth, still you can use recordmydesktop in command line

and just press ctrl + c to stop the recording, you can also try **istanbul** , and **xvidcap** in fiesty.

I tried installing istanbul.
I got this error:

~/wc $ sudo aptitude install istanbul
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-x liboil0.3 libshout3 libsidplay1 python-gconf python-gnome2
  python-gnomecanvas python-gst0.10
The following NEW packages will be installed:
  gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-x istanbul liboil0.3 libshout3 libsidplay1 python-gconf python-gnome2
  python-gnomecanvas python-gst0.10
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 2619kB of archives. After unpacking 8462kB will be used.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Get:1 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main gstreamer0.10-alsa 0.10.12-0ubuntu1 [64,9kB]
Get:2 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main liboil0.3 0.3.10-1.1ubuntu1 [144kB]
Get:3 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main gstreamer0.10-plugins-base 0.10.12-0ubuntu1 [451kB]
Get:4 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main libshout3 2.2.2-1build1 [36,4kB]
Get:5 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main gstreamer0.10-plugins-good 0.10.5-1ubuntu2 [676kB]
Get:6 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/universe libsidplay1 1.36.59-4 [65,9kB]
Get:7 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/universe gstreamer0.10-plugins-ugly 0.10.5-0ubuntu2 [207kB]
Get:8 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main gstreamer0.10-x 0.10.12-0ubuntu1 [98,6kB]
Get:9 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main python-gst0.10 0.10.6-1ubuntu3 [373kB]
Get:10 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main python-gnomecanvas 2.18.0-0ubuntu1 [55,2kB]
Get:11 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main python-gconf 2.18.0-0ubuntu1 [71,3kB]
Get:12 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/main python-gnome2 2.18.0-0ubuntu1 [327kB]
Get:13 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) feisty/universe istanbul 0.2.1-3build1 [47,3kB]
Fetched 2619kB in 10s (239kB/s)
Selecting previously deselected package gstreamer0.10-alsa.
(Reading database ... 198205 files and directories currently installed.)
Unpacking gstreamer0.10-alsa (from .../gstreamer0.10-alsa_0.10.12-0ubuntu1_i386.deb) ...
Selecting previously deselected package liboil0.3.
Unpacking liboil0.3 (from .../liboil0.3_0.3.10-1.1ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-base.
Unpacking gstreamer0.10-plugins-base (from .../gstreamer0.10-plugins-base_0.10.12-0ubuntu1_i386.deb) ...
Selecting previously deselected package libshout3.
Unpacking libshout3 (from .../libshout3_2.2.2-1build1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-good.
Unpacking gstreamer0.10-plugins-good (from .../gstreamer0.10-plugins-good_0.10.5-1ubuntu2_i386.deb) ...
Selecting previously deselected package libsidplay1.
Unpacking libsidplay1 (from .../libsidplay1_1.36.59-4_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-x.
Unpacking gstreamer0.10-x (from .../gstreamer0.10-x_0.10.12-0ubuntu1_i386.deb) ...
Selecting previously deselected package python-gst0.10.
Unpacking python-gst0.10 (from .../python-gst0.10_0.10.6-1ubuntu3_i386.deb) ...
Selecting previously deselected package python-gnomecanvas.
Unpacking python-gnomecanvas (from .../python-gnomecanvas_2.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package python-gconf.
Unpacking python-gconf (from .../python-gconf_2.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package python-gnome2.
Unpacking python-gnome2 (from .../python-gnome2_2.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package istanbul.
Unpacking istanbul (from .../istanbul_0.2.1-3build1_i386.deb) ...
Setting up gstreamer0.10-alsa (0.10.12-0ubuntu1) ...
Setting up liboil0.3 (0.3.10-1.1ubuntu1) ...

Setting up gstreamer0.10-plugins-base (0.10.12-0ubuntu1) ...
Setting up libshout3 (2.2.2-1build1) ...

Setting up gstreamer0.10-plugins-good (0.10.5-1ubuntu2) ...

Setting up libsidplay1 (1.36.59-4) ...
Setting up gstreamer0.10-plugins-ugly (0.10.5-0ubuntu2) ...
Setting up gstreamer0.10-x (0.10.12-0ubuntu1) ...
Setting up python-gst0.10 (0.10.6-1ubuntu3) ...

Setting up python-gnomecanvas (2.18.0-0ubuntu1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up python-gconf (2.18.0-0ubuntu1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up python-gnome2 (2.18.0-0ubuntu1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up istanbul (0.2.1-3build1) ...
Compiling /var/lib/python-support/python2.5/Bio/Wise/dnal.py ...
  File "/var/lib/python-support/python2.5/Bio/Wise/dnal.py", line 5
    from __future__ import division
SyntaxError: from __future__ imports must occur at the beginning of the file


Shouldn't this be reported and fixed?
I see quite a few packages with Python programs that are broken this way.

---

### Post by loell on 2007-11-20
yeah, it seems that the dependency wasn't set properly ,


these are python programs which is suppose to depend on gnome libs.

but  you are in KDE, I think this has already been fixed in gutsy.

---

