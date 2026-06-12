---
title: "dvd::rip missing dependencies!"
date: 2008-05-21
forum: Multimedia Software
---

### Post by pmq on 2008-05-21
I was using dvd::rip to rip and compress some of my favourite movies.
Unfortunately some of my favourite dvds are tartan extreme asia. Films like Ring, Ring 2 etc the original japanese versions they have english subtitles.
I bought them here in the uk however their region code is 0.
I tried ripping them but they stop 75% of the way through. I couldnt figure this out.
I checked the dependency and dvd::rip says i am missing the fooling required tools.


  Program              Version   
  -------------------------------
  dvd::rip             0.98.6    
  transcode            1.0.2     
  ImageMagick          6.2.4     
  ffmpeg               SVN-rUNKNOWN,
  xvid4conf            1.12      
  subtitle2pgm         not installed
  lsdvd                0.16      
  rar                  not installed
  mplayer              not installed
  ogmtools             1.5       
  dvdxchap             1.5       
  mjpegtools           not installed
  xine                 not installed
  fping                2.4       
  hal                  0.5.9     
  -------------------------------

Are the non installed files necessary for these kinds of movies?
I used synaptic manager to get them but they weren't listed. 

Any ideas?

Thanks

pmq

---

### Post by warp99 on 2008-05-21
> **pmq said:**
> I was using dvd::rip to rip and compress some of my favourite movies.
Unfortunately some of my favourite dvds are tartan extreme asia. Films like Ring, Ring 2 etc the original japanese versions they have english subtitles.
I bought them here in the uk however their region code is 0.
I tried ripping them but they stop 75% of the way through. I couldnt figure this out.
I checked the dependency and dvd::rip says i am missing the fooling required tools.


  Program              Version   
  -------------------------------
  dvd::rip             0.98.6    
  transcode            1.0.2     
  ImageMagick          6.2.4     
  ffmpeg               SVN-rUNKNOWN,
  xvid4conf            1.12      
  subtitle2pgm         not installed
  lsdvd                0.16      
  rar                  not installed
  mplayer              not installed
  ogmtools             1.5       
  dvdxchap             1.5       
  mjpegtools           not installed
  xine                 not installed
  fping                2.4       
  hal                  0.5.9     
  -------------------------------

Are the non installed files necessary for these kinds of movies?
I used synaptic manager to get them but they weren't listed. 

Any ideas?

Thanks

pmq

Do you have the universe and multiverse repositories enabled?

---

### Post by pmq on 2008-05-21
How do i check if the universe and multiverse repositories are enabled?

---

### Post by angryhomer17 on 2008-05-21
Open synaptic, go to Settings> Repositories. Under the Ubuntu Software tab make sure the following are checked:

Community-maintained Open Source software (universe)

Software restricted by copyright or legal issues (multiverse)

These are the second and fourth checkboxes.

---

### Post by pmq on 2008-05-21
Yes they are checked!

---

### Post by warp99 on 2008-05-21
> ~/ sudo apt-cache show dvdrip
Package: dvdrip
Priority: optional
Section: multiverse/graphics
Installed-Size: 2580
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 1:0.98.6-0.0ubuntu1
[b]Depends: libc6 (>= 2.5-5), perl (>= 5.6.0-16), transcode (>= 2:1.0.2-0.8'), gtk2-ex-formfactory-perl (>= 0.65), libevent-execflow-perl (>= 0.63), imagemagick, fping, liblocale-gettext-perl, libintl-perl (>= 1.16), eject, lsdvd, libevent-perl, ffmpeg, ogmtools (>= 0.972)
Recommends: xine-ui, subtitleripper, dvdrip-doc
Suggests: mjpegtools, mplayer, rar, hal[/b]
Conflicts: video-dvdrip (<= 0.50.18-0.0)
Filename: pool/multiverse/d/dvdrip/dvdrip_0.98.6-0.0ubuntu1_i386.deb
Size: 1112252
MD5sum: 1440b2d604ffa4838b6ad0b3ec2687d9
SHA1: a384e501047fcbdbfd4bb1850337eed496202b2d
SHA256: c8d6f64273af0d8eca5091b60c0f951d7b6e1374fe811f2f4efa504a84757b3a
Description: perl front end for transcode
 dvd::rip is a full featured DVD copy program written in Perl. It provides
 an easy to use but feature-rich Gtk+ GUI to control almost all aspects of
 the ripping and transcoding process. It uses the widely known video
 processing swissknife transcode and many other Open Source tools.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

You should have all of the dependencies met if you obtained the packages from the Ubuntu repositories. Now you may need to install the recommended packages and/or the suggested packages for additional features, but these are also in the standard repositories as well.

---

### Post by pmq on 2008-05-22
The information was very helpful.
I got the necessary tools installed and now i have the dvd's ripped.

In the rip tab:

Grab subtitle preview images : by language

Specify chapter mode: all

Once i applied these settings the rip worked fine.

pmq

---

