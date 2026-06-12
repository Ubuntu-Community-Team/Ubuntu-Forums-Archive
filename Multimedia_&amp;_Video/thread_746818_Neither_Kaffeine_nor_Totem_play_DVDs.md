---
title: "Neither Kaffeine nor Totem play DVDs"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by jdoge13 on 2008-04-05
When I try to open a DVD in Kaffeine I get the error:
09:46:48 PM: xine: couldn't find demux for >dvd://<
09:46:48 PM: xine: found input plugin : DVD Navigator

When I try it in Totem I get the error:
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media.

I have tried installing the program listed on this page
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
but it still doesn't seem to be working.  I have also tried adding the medibuntu repositories which does not work as well.  I'm using Ubuntu version 7.10 just fyi.  

Any Ideas?

---

### Post by warp99 on 2008-04-05
Put a DVD in the tray, open a terminal and type the following:

```
totem dvd://
```

What is the output?

---

### Post by jdoge13 on 2008-04-05
It works just fine when I do that.
Is there anyway to open them without using the terminal?
But it doesn't show the menu, it skips directly the movie.

---

### Post by warp99 on 2008-04-05
Open a terminal and try the following.

```
sudo apt-get install --reinstall totem-xine libxine1 
```

---

### Post by jdoge13 on 2008-04-06
It says it cannot find that package.

---

### Post by warp99 on 2008-04-06
Then you have a problem with your sources.list. Please do the following:

```
sudo cat /etc/apt/sources.list
```

and post the results to this thread.

---

### Post by jdoge13 on 2008-04-06
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

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

---

### Post by warp99 on 2008-04-06
Well you have all of the correct repositories enabled. The packages are in the repositories, I did verify them. Make sure you have a good internet connection first before you try to download and reinstall the packages. So try the following:

Check your internet connection

```
ping -c 10 google.com
```

if that's fine then:

```
sudo apt-get update
```

and then

```
sudo apt-get install --reinstall totem-xine libxine1 xine-ui
```

Edit:

Since you have the universe repositories enabled we should install the xine-ui package since there are some extra libraries that will help with Totem and Kaffiene.

---

### Post by jdoge13 on 2008-04-06
It still says it cannot find the package.  I just might be patient and wait for 8.04 to come out and see if that fixes the problem.  You never know.
Thanks anyways. :)

---

### Post by xc3RnbFO8P on 2008-04-06
Try to change **server** in Synaptic Package Manager> settings> Repositories>  Ubuntu software

---

