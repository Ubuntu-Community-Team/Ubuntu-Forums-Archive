---
title: "Totem cant play wmv files"
date: 2010-09-26
forum: Multimedia Software
---

### Post by walwal on 2010-09-26
im using ubuntu lucid and totem cant play wmv files. i tried my files using vlc and gxine, they both work but not totem.
plz help.

---

### Post by 0N3 on 2010-09-26
Have you ubuntu-restricted-extras installed?

sudo apt-get install ubuntu-restricted-extras

---

### Post by 0N3 on 2010-09-26
This might also be worth a look @ 

[http://gnome-look.org/content/show.php/Ubuntu+Multimedia+Script(i386%2Bamd64)?content=129011](http://gnome-look.org/content/show.php/Ubuntu+Multimedia+Script(i386%2Bamd64)?content=129011)

---

### Post by walwal on 2010-09-26
yeah i have all the codecs installed but still have a problem with wmv videos in totem.

---

### Post by nidfix on 2010-11-13
I faced the same issue since I upgraded to 10.10 my x86 unit (while no issue on the x64). After investigations it seems that gstreamer0.10-pitfdll package provided (0.9.1.1+cvs20080215-1ubuntu2) does not like some codecs delivered in W32codec package causing totem to use a codec that eventually fails.
Therefore removing one or the other solved the issue. As the gstreamer package is installed "by default" so far I removed w32codec package.

I hope that will help you.

---

### Post by mc4man on 2010-11-13
> As the gstreamer package is installed "by default" so far I removed w32codec package.

It's a dependency of ubuntu-restricted-addons metapackage (u-r-e), and at this point the pitfdll package is of little to no value and can in some instances be a hindrance.
If one had any players that can use w32codecs then better to dump the pitfdll plugin instead which needs w32codecs anyway..

Filed a bug request some time ago to remove it from the metapackage's dep list - another minor issue that will not be 'fixed'
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-addons/+bug/621857](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-addons/+bug/621857)

---

### Post by manu14807 on 2011-06-12
you can try this worked for me in ubuntu 10.10
go to 
[http://mplayer.rut.org/MPlayer/releases/codecs/](http://mplayer.rut.org/MPlayer/releases/codecs/)
download all all-20071007.tar.bz2
then extract it.
then go to terminal and type
sudo mkdir /usr/lib/codecs
and then copy all contents of  all-20071007 to /usr/lib/codecs/  (only copying wmsdmod.dll will also do)
sudo cp  'path to  all-20071007'/*  /usr/lib/codecs/

then play it using mplayer(or smplayer). It will work.

---

### Post by AmirGooran on 2012-03-22
I have the same problem,but root user can play wmv files with totem. I changed permission of some codec files,but nothing happened.:mad:
any suggestions?

---

