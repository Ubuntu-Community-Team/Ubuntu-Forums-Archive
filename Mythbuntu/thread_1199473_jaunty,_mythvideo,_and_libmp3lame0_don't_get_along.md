---
title: "jaunty, mythvideo, and libmp3lame0 don't get along"
date: 2009-06-29
forum: Mythbuntu
---

### Post by tedder on 2009-06-29
So I upgraded to Jaunty, and I can't get mythvideo installed. Here's what happens:

```
# apt-get install mythvideo
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythvideo: Depends: libmp3lame0 (>= 3.98) but it is not going to be installed
E: Broken packages

```

If I try to install libmp3lame0, I get the following:
```
# apt-get install libmp3lame0
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libmpich1.0gf kdelibs4c2a libartsc0 liblzo1 libopenal0a
  python-pexpect libdc1394-13 libgtk1.2 fftw2 kdelibs-data libmagick10
  liblualib50 libpostproc1d libxml-xql-perl libparse-yapp-perl dar libdar64-4
  feh libavahi-qt3-1 giblib1 libmjpegtools0c2a libdvdread3 libxml-simple-perl
  libgtk1.2-common pmount liblua50 libimlib2 libcucul0 feisty-gdm-themes
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  avidemux mencoder mplayer transcode
Suggested packages:
  w32codecs libdvdcss mplayer-doc ladspa-sdk pvm xvid4conf
Recommended packages:
  toolame transcode-doc
The following packages will be REMOVED:
  libavcodec1d libavformat1d liblame-dev liblame0 libmyth-0.20 libmyth-0.21-0
  mytharchive mythcontrols mythgallery mythmovies mythnews mythstream mythtv
  mythtv-backend mythtv-frontend mythtv-theme-mythbuntu mythtv-transcode-utils
  mythweather
The following NEW packages will be installed:
  libmp3lame0
The following packages will be upgraded:
  avidemux mencoder mplayer transcode
4 upgraded, 1 newly installed, 18 to remove and 1 not upgraded.
Need to get 14.1MB of archives.
After this operation, 74.2MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Obviously, I don't want to throw the baby out with the bathwater, so I tell it to abort. eek.

I have some multiverse and free/nonfree apt sources, which should have libmp3lame0 in them:
```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

deb http://packages.medibuntu.org/ jaunty free non-free

```


So what have I missed?

Thanks.

---

### Post by tedder on 2009-06-30
anybody? Bueller?

---

### Post by jyavenard on 2009-07-01
using synaptic.

before you upgrade mythtv, uninstall any liblame packages.
It doesn't matter if any mythtv packages are removed in the process ; the database is kept intact.

Then click apply 1

And *then* update/install mythtv...

it's just a conflict between libmp3lame and the previous version.

Usually it should have been upgraded automatically...

---

### Post by tedder on 2009-07-05
> **jyavenard said:**
> before you upgrade mythtv, uninstall any liblame packages.
It doesn't matter if any mythtv packages are removed in the process ; the database is kept intact.

Aha, that's what I needed to hear.

With some trepidation, I uninstalled liblame/lame, then reinstalled myth*. It all works now- hooray!

Thanks for your help.

---

