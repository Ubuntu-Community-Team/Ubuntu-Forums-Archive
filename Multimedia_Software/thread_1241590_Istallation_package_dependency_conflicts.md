---
title: "Istallation package dependency conflicts"
date: 2009-08-16
forum: Multimedia Software
---

### Post by hgraham on 2009-08-16
[COLOR="Blue"]Following the Multimedia and Video How To Sticky post using 9.04 64 bit I had problems installing some of the applications due to dependency problems.  My question is should I attempt to install these programs by uninstalling the interfering programs?  If I recall correctly, I went in circles trying to satisfy dependencies for various programs in the past.  Either some packages were not available or different programs caused dependency conflicts with other programs.  I appreciate your comments.
Howard

Below are most of the dependency problems I encountered[/COLOR]
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

All were installed except the following:
The following packages have unmet dependencies:
  gstreamer0.10-plugins-bad-multiverse: Depends: libmjpegtools-1.9 (>= 1:1.9.0) but it is not going to be installed
E: Broken packages

[COLOR="Blue"]Using synaptic I found that 
libmjpegtools-1.9 was dependent on libquicktime1 which in was dependent upon
  libavcodec51 and 
  libswscale0  which were both dependent on removing
      gstreamer0.10-ffmpeg
      libavformat-unstripped-52
      vlc
      vlc-nox
      vlc-plugin-esd  which are all installed
[/COLOR]




sudo apt-get install soundkonverter aacplusenc audacity alac-decoder cdparanoia ffmpeg flac lame vorbis-tools

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec51 (>= 3:20080706) but it is not going to be installed
          Depends: libavdevice52 (>= 3:20080706) but it is not going to be installed
          Depends: libavformat52 (>= 3:20080706) but it is not going to be installed
          Depends: libavutil49 (>= 3:20080706) but it is not going to be installed
          Depends: libswscale0 (>= 3:20080706) but it is not going to be installed
E: Broken packages

[COLOR="Blue"]However synaptic shows ffmpeg is installed but it has a star on it[/COLOR]





sudo apt-get install avidemux ffmpeg winff

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec51 (>= 3:20080706) but it is not going to be installed
          Depends: libavdevice52 (>= 3:20080706) but it is not going to be installed
          Depends: libavformat52 (>= 3:20080706) but it is not going to be installed
          Depends: libavutil49 (>= 3:20080706) but it is not going to be installed
          Depends: libswscale0 (>= 3:20080706) but it is not going to be installed
E: Broken packages


howard@howard-desktop:~$ sudo apt-get install dvdrip
The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:1.0.2-0.8) but it is not going to be installed
          Recommends: xine-ui but it is not going to be installed
          Recommends: subtitleripper but it is not going to be installed
E: Broken packages

---

### Post by mc4man on 2009-08-16
You should put your 'quotes' from terminal in a quote box, easier to read thru (highlight bllock of text and click on little quote icon in reply toolbar

> Using synaptic I found that
libmjpegtools-1.9 was dependent on libquicktime1 which in was dependent upon
[COLOR="Red"]libavcodec51[/COLOR]

It would appear you have 1 or more intrepid repos in your sources (most likely reason
Jaunty uses libavcodec52 (or libavcodec52-unstripped), no jaunty package would depend on or request libavcodec51 which is the default for intrepid


ck. or post sources
```
cat /etc/apt/sources.list
```

Plus ck. System -> Admin. -> Software sources -> Third party for any non jaunty sources
(( for instance medibuntu can be enabled but won't show up in sources.list, it's usually in /etc/apt/sources.list.d  due to wget command

---

### Post by hgraham on 2009-08-17
Here is my sources list.  I suppose part of my problem is that I really do not understand which packages are necessary or useful.  This gets more complicated when ffmpeg is involved.  I have not been able to discover such a list for 9.04 64 bit.  Anything you could suggest would be appreciated.
Howard

howard@howard-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

# howard add for ffmpeg lenny
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main

deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rainct/ppa/ubuntu](http://ppa.launchpad.net/rainct/ppa/ubuntu) jaunty main
deb [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) stable non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by mc4man on 2009-08-17
In general you should not use debian repo packages on an ubnutu install and never  add a debian repo as a source. (( particularity lenny which is well behind jaunty version wise

If you ever have a need for updated sources better to build and install your own.
You can add some packages from debian-multimedia safely if done directly and using sid versions. (or see note

Anyway I'd remove the below in red, either by commenting out as shown or deleting the lines, ( if deleting make sure all red is removed, maybe backspace a few lines to move blue up **(or see note**

The ones in blue appear ok for jaunty, though have no idea about the google one. It or any of the blue can be disabled in System -> Admin,,,, as described above if an issue. (the medibuntu ones are correct

After removing or commenting the lenny lines (a must do)
```
gksudo gedit /etc/apt/sources.list
```

 then run 

sudo apt-get update

After that open synaptic, click on custom filter -> broken and remove all the broken packages.

Then go ahead and  install whatever it was you wanted 

You may, while in synaptic, wish to install the the unstripped ffmpeg libraries ( search ffmpeg and scroll down, do after removing all broken ones.  (( libavcodec52-unstripped, libavformat52-unstripped,  ect.
```

# howard add for ffmpeg lenny
[COLOR="Red"]#deb http://www.debian-multimedia.org lenny main
#deb-src http://www.debian-multimedia.org lenny main[/COLOR]

[COLOR="Blue"]deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rainct/ppa/ubuntu jaunty main
deb http://dl.google.com/linux/deb stable non-free
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free [/COLOR]
```

Small note
I once, as a test, did add debian-multimedia as a source (in intrepid) using the sid version. 
It is possible possible to have it integrate without  issues, though I've since decided far better to build the  current ffmpeg source as debian package sets. (actually use the diff from debian-multimedia as a starting point.

If you wish to do so then change your lines in your sources list from lenny to sid (and do the apt-get update and fix, ect. as described
If you do so then it's best to disable the the 2 jaunty medibuntu sources

```
# howard add for ffmpeg [COLOR="Blue"]sid[/COLOR]
deb http://www.debian-multimedia.org sid main
deb-src http://www.debian-multimedia.org sid main

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rainct/ppa/ubuntu jaunty main
deb http://dl.google.com/linux/deb stable non-free
#deb http://packages.medibuntu.org/ jaunty free non-free
#deb-src http://packages.medibuntu.org/ jaunty free non-free 



```

---

### Post by hgraham on 2009-08-17
I followed your advice and did as you said.  I did not do the sid part.  I don't understand what that does.  I understand to change the source files to sid but don't you need to do more than just update.  Your suggestions did take the star off my ffmpeg entry in synaptic.  Don't we need the medibuntu with sid or does he contain it all?

Thanks so much for your interest.
Howard

---

