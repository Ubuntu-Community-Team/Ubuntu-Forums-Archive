---
title: "weird dependency problem - ubuntu-restricted-extras &amp; gimp"
date: 2018-12-19
forum: Multimedia Software
---

### Post by paulorosario200080 on 2018-12-19
Hello,
So the other day, i installed ubuntu 18.10, it installed normally, i was impressed with the improvements and speed, and like any other user, i updated the system, changed some settings, installed my apps, etc... I then added the gimp repository (otto-kesselgulasch/gimp) because i wanted to get the latest gimp 2.10, and without the repository the store only shows gimp 2.8.

i also added the gimp repository because i don't like the snap or flatpak much.

i then installed ubuntu-restricted-extras, and later removed it.

i noticed when i installed ubuntu-restricted-extras, it showed that it would install additional packages, and now that i am removing ubuntu-restricted-extras, some of the additional packages were missing, they were not going to be removed along ubuntu-restricted-extras. so i had to remove them manually.

i went up on my terminal, and began to remove all of the packages that didn't want to leave.

it was going beautifully, until i found a package named libavcodec-extra-53 (and some other packages that i don't remember the name). this package tried to remove gimp too, and i didn't want it to remove gimp. why was it trying to remove gimp? with or without libavcodec-extra-53, gimp was working fine. why was it trying to pick on gimp? is it some dependency? is it a bug? i've had issues like this in the past, where i tried to remove one useless package, and it tried to remove the whole system, like gnome-control-center, packages like that, that make the system work. i used the remove and purge command btw. did i use the wrong command? is there some command that removes a package and all the related packages?

Thank you.

---

### Post by again? on 2018-12-20
```

```This is on Xubuntu 18.04
Gimp pulls in libavcodec[COLOR="#696969"]XX[/COLOR] or libavcodec-extra[COLOR="#696969"]XX[/COLOR] which contains additional codecs.

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends ubuntu-restricted-extras**
ubuntu-restricted-extras
  Depends: ubuntu-restricted-addons
  Recommends: libavcodec-extra
    libavcodec-extra57
  Recommends: ttf-mscorefonts-installer
  Recommends: unrar

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends ubuntu-restricted-addons**
ubuntu-restricted-addons
  Recommends: chromium-codecs-ffmpeg-extra
  Recommends: gstreamer1.0-fluendo-mp3
  Recommends: gstreamer1.0-libav
  Recommends: gstreamer1.0-plugins-ugly
  Recommends: gstreamer1.0-vaapi
```

In ubuntu, recommends are considered dependencies.
When you first installed gimp it would have pulled in libavcodec.
libavcodec would have been replaced with libavcodec-extra when you installed ubuntu-restricted-addons.
libavcodec-extra contains additional codecs so not really necessary to remove as you need one or the other for gimp.
Installing one removes the other...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install libavcodec57**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="#FF0000"]The following packages will be REMOVED[/COLOR]
  libavcodec-extra libavcodec-extra57
[COLOR="#FF0000"]The following NEW packages will be installed[/COLOR]
  libavcodec57
0 to upgrade, 1 to newly install, 2 to remove and 0 not to upgrade.
Need to get 0 B/4,592 kB of archives.
After this operation, 71.7 kB disk space will be freed.
Do you want to continue? [Y/n]
```

Odd though that you say you have libavcodec-extra-53 on 18.10. Should be 58.
I have 57 on 18.04
```

[B][COLOR="#006400"]glen@Bionic:~$[/COLOR] apt list --installed | grep -i libavcodec
[/B]
libavcodec-extra/bionic-updates,bionic-updates,bionic-security,bionic-security,now 7:3.4.4-0ubuntu0.18.04.1 all [installed]
libavcodec-extra[COLOR="#FF0000"]57[/COLOR]/bionic-updates,bionic-security,now 7:3.4.4-0ubuntu0.18.04.1 amd64 [installed]
```
[search packages ubuntu - libavcodec]("https://packages.ubuntu.com/search?keywords=libavcodec&searchon=names&suite=all&section=all")

Any errors when you run...
```
sudo apt update
sudo apt upgrade
```

---

