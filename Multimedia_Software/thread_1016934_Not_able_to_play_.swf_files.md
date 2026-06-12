---
title: "Not able to play *.swf files"
date: 2008-12-20
forum: Multimedia Software
---

### Post by alokmishra.besu on 2008-12-20
Hi

I've Ubuntu 7.04- the Feisty Fawn installed on my machine. My problem is that I'm not able to play any .swf files in Ubuntu. I've Shockwave Flash installed on my machine and I can play files on youtube on my firefox. But if I download any swf file from youtube or from any other site then i'm not able to play it on firefox. I even tried with Opera, but with no success. 

The following plugins for Shockwave Flash are already installed on my machine:
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/firefox/plugins/libflashplayer.so

Please advise.

---

### Post by gandaran on 2008-12-20
youtube videos are .flv files, flash videos, not .swf or shockwave flash,
and you can play .flv and some .swf in firefox, you just have to type the full file path in firefox url bar.
you can use a stand alone player like totem or vlc for playing downloaded .flv files or flash videos, for .swf files or shockwave you can also use a stand alone player like swfdec or gnash or better get the adobe stand alone player for shockwave.

---

### Post by alokmishra.besu on 2008-12-21
Thank you for the prompt reply. 
When i try to install gnash i get the following error:

[COLOR="Blue"]$ sudo apt-get install gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-kb-dev x11proto-xinerama-dev x11proto-render-dev libntfs-3g1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgnash0 libgtkglext1
The following NEW packages will be installed:
  gnash libgnash0 libgtkglext1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 110kB/1155kB of archives.
After unpacking 2974kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgtkglext1
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe libgtkglext1 1.0.6-2.1ubuntu1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
$[/COLOR]


Can anyone please help me get the proper repository for it. My source.list file is as follows:

[COLOR="Blue"]$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
$[/COLOR]

Thank you in advance.

---

### Post by alokmishra.besu on 2008-12-27
ok i installed gnash in my system....
but on playing any files its giving the following error

[COLOR="Blue"]$ gnash 1.swf 

** (gnash:6486): WARNING **: Couldn't find pixmap file: gnash_128_96.ico[/COLOR]

and a blank window is opening up without playing anything. 

is anything wrong with the 1.swf file or am i missing something? :confused:

---

### Post by gandaran on 2008-12-27
theres some kind of bug with gnash, get the adobe flash player [http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz), it works nicely
inside this package are three separate packages, the flash plugin for  browsers, which you don't need if you already have flash installed, the debugger  and released stand alone player, this flash player doesn't play .flv files or flash movies only shockwave .swf files.

---

### Post by Zila1 on 2008-12-27
I have the same problem  as alokmishra.besu.
 [http://download.macromedia.com/pub/f...nux_dev.tar.gz](http://download.macromedia.com/pub/f...nux_dev.tar.gz), it works nicely doesn't want to open. There's just a white window with and nothing happens

---

### Post by gandaran on 2008-12-27
> **Zila1 said:**
> I have the same problem  as alokmishra.besu.
 [http://download.macromedia.com/pub/f...nux_dev.tar.gz](http://download.macromedia.com/pub/f...nux_dev.tar.gz), it works nicely doesn't want to open. There's just a white window with and nothing happens
just double click the flashplayer file to open then go to archive » open, find your .swf files to add and click OK 
I don't know if this player can play all windows .swf files, I have a lot of .swf files but they are all made using ubuntu, no problem at all running them.

---

