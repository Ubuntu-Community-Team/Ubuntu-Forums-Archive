---
title: "a Soundkonverter problem"
date: 2009-06-18
forum: Multimedia Software
---

### Post by dE_logics on 2009-06-18
There appears to be absolutely no types of format that it supports...I try to drag/add files and just wont get added!

Also in the settings>backends section, the encoders as just void!...there are no encoders selected, though there are many in the plugins section.

---

### Post by mc4man on 2009-06-18
What you want to look at in settings is the enviroment, what 'programs' have been found
Sk uses the the name, so for mp3 install lame, for flac install flac, for aac install faac, faad, ect. (vs. just having the lib's installed

You should also have a decent ffmpeg and mplayer installed

If you're using it to rip & encode audio cd's on ubuntu (gnome) see here
[http://ubuntuforums.org/showthread.php?p=7450119#post7450119](http://ubuntuforums.org/showthread.php?p=7450119#post7450119)

---

### Post by dE_logics on 2009-06-19
Oh...the programs found is empty.

How about the location...do we have to specify that?

---

### Post by ad_267 on 2009-06-19
```
apt-cache show soundkonverter
Package: soundkonverter
Priority: optional
Section: universe/kde
Installed-Size: 4212
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Architecture: i386
Version: 0.3.8-2ubuntu1
Depends: kdelibs4c2a (>= 4:3.5.9), libc6 (>= 2.4), libcdparanoia0 (>= 3.10.2+debian), libgcc1 (>= 1:4.1.1), libqt3-mt (>= 3:3.3.8-b), libstdc++6 (>= 4.2.1), libtag1c2a (>= 1.5)
Recommends: **cdda2wav, cdparanoia, faad, ffmpeg, flac, kdemultimedia-kio-plugins, mp3gain, mplayer, mppenc, speex, timidity, vorbis-tools, vorbisgain, wavpack**
Filename: pool/universe/s/soundkonverter/soundkonverter_0.3.8-2ubuntu1_i386.deb
Size: 1106890
MD5sum: 77433e278f95a598eb05b0ea8984e5ed
SHA1: 5899452b32cf7a18e7a1481a146526c63ee01b1a
SHA256: 87bc3279a9c597dbe49b76db2cff8db27182d36acc970b519496691aecbb72b9
Description: audio converter frontend for KDE
 soundKonverter is a frontend to various audio converters.
 .
 The key features are:
  - Audio conversion
  - Replay Gain calculation
  - CD ripping
 .
 soundKonverter supports reading and writing tags for many formats, so the tags
 are preserved when converting files.
 .
 See README.Debian for more informations on supported formats.
Homepage: http://www.kde-apps.org/content/show.php?content=29024
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

Looks like you should install some of the recommended packages, depending on what formats you want to use.

---

### Post by dE_logics on 2009-06-19
I have lame installed but in discription of the package in synaptic, it says "lame ain't an mp3 encoder"

I also have ffmpeg installed but it shows nothing.

---

### Post by dE_logics on 2009-06-19
> **ad_267 said:**
> ```
apt-cache show soundkonverter
Package: soundkonverter
Priority: optional
Section: universe/kde
Installed-Size: 4212
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Architecture: i386
Version: 0.3.8-2ubuntu1
Depends: kdelibs4c2a (>= 4:3.5.9), libc6 (>= 2.4), libcdparanoia0 (>= 3.10.2+debian), libgcc1 (>= 1:4.1.1), libqt3-mt (>= 3:3.3.8-b), libstdc++6 (>= 4.2.1), libtag1c2a (>= 1.5)
Recommends: **cdda2wav, cdparanoia, faad, ffmpeg, flac, kdemultimedia-kio-plugins, mp3gain, mplayer, mppenc, speex, timidity, vorbis-tools, vorbisgain, wavpack**
Filename: pool/universe/s/soundkonverter/soundkonverter_0.3.8-2ubuntu1_i386.deb
Size: 1106890
MD5sum: 77433e278f95a598eb05b0ea8984e5ed
SHA1: 5899452b32cf7a18e7a1481a146526c63ee01b1a
SHA256: 87bc3279a9c597dbe49b76db2cff8db27182d36acc970b519496691aecbb72b9
Description: audio converter frontend for KDE
 soundKonverter is a frontend to various audio converters.
 .
 The key features are:
  - Audio conversion
  - Replay Gain calculation
  - CD ripping
 .
 soundKonverter supports reading and writing tags for many formats, so the tags
 are preserved when converting files.
 .
 See README.Debian for more informations on supported formats.
Homepage: http://www.kde-apps.org/content/show.php?content=29024
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

Looks like you should install some of the recommended packages, depending on what formats you want to use.

No cdda2wav in the repose, rest are all installed.

---

### Post by dE_logics on 2009-06-20
So what do I conclude, is this a sound konverter bug?

---

### Post by mc4man on 2009-06-20
> So what do I conclude, is this a sound konverter bug? 

No, I'd say you have a local issue.
There's no way the 'programs found' can be empty, just installing soundkonveter will install many of the 'programs', though some of them may not be the best versions, most notably ffmpeg, mplayer.

Are you still using 8.10?

screen shows a live cd of jaunty, installed nothing but soundkonverter (which installed an add. 100 packages or so

While in 8.10 it may not by default install that much you'd certainly get a fair number and then fill in the rest as desired (from ubuntu repo's, or elsewhere depending on packages (programs

Pretty much the same for 8.10, most everything in screen is installed and or found by default

---

### Post by dE_logics on 2009-06-20
Yep, 8.10

Thanks, I needed that path.

---

