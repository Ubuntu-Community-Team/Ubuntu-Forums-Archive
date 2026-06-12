---
title: "sudo /usr/share/doc/libdvdread3/install-css.sh  error"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Chris2691 on 2008-06-14
Im running AMD64 Hardy and get the following error when I try to execute

sudo /usr/share/doc/libdvdread3/install-css.sh

No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--17:47:31--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz)
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.29.100
Connecting to [www.dtek.chalmers.se|129.16.29.100|:80](www.dtek.chalmers.se|129.16.29.100|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
17:47:31 ERROR 404: Not Found.

Has anyone an idea on how I can fix this ?

---

### Post by ad_267 on 2008-06-14
Read this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You need to install these first:
```
sudo apt-get install build-essential debhelper fakeroot
```

---

### Post by benediktf on 2008-06-14
I got the same error, though build-essential, debhelper and fakeroot had been installed.

On [http://www.dtek.chalmers.se/](http://www.dtek.chalmers.se/) it says that the site would be down for maintenance until June 18.
So I guess this will be worth trying end of next week again.

Cheers

---

### Post by toallpointswest on 2008-09-14
Bump, same problem.

---

### Post by mc4man on 2008-09-14
all that script does is install (or try to) an old version of libdvdcss2 that 99% of setups don't need.

go here and follow intsr. for adding medibuntu repo as a source and then install libdvdcss2. (if you install or have installed vlc then you should now be able to playback dvd thru vlc. mplayer, xine
Totem needs ubuntu-restricted-extras in addition

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

