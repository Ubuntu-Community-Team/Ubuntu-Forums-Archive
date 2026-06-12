---
title: "Release of VLC media player 1.0.0, codename &quot;Goldeneye&quot;"
date: 2009-07-07
forum: Multimedia Software
---

### Post by DustofDust on 2009-07-07
from the videolan mailing list

> Dear VLC users and VideoLAN community,

The VideoLAN project and the VLC developers are very pleased to announce
the immediate release of VLC media player 1.0.0, codename "Goldeneye".

This release introduces many new features and includes:
* Instant pausing and Frame-by-Frame support
* Live recording
* Finer speed controls
* New HD codecs (AES3, Dolby Digital Plus, TrueHD, Blu-Ray Linear PCM, Real Video 3.0 and 4.0, ...)
* New formats (Raw Dirac, M2TS, ...) and majors improvements in many formats...
* New Dirac encoder and MP3 fixed-point encoder
* Video scaling in fullscreen
* RTSP Trickplay support
* Zipped file playback
* Customizable toolbars
* Easier encoding GUI in Qt interface
* Better integration in Gtk environments
* MTP devices on linux
* AirTunes streaming
* New skin for skins2 interface, made by Martin Pöhlmann

You can download it now on [http://www.videolan.org/](http://www.videolan.org/).

The VideoLAN team needs your help to continue the project.
If you can share time, hardware or money, that would help us a lot.

You can find more details on this release on the NEWS and Changelog files
from the source packages.

Press requests should be forwarded to [email]videolan@videolan.org[/email]

For the VideoLAN project,

-- Jean-Baptiste Kempf [http://www.jbkempf.com/](http://www.jbkempf.com/)

hope ubuntu releases the packages soon!

---

### Post by LarryMi on 2009-07-07
Why do they say: "Download Now for Ubuntu Linux"?  This link takes you to a page that doesn't even list 9.04.  Nothing to download here.  And under the "How to Add repositories links", I can't find anything related to VLC.; however, the Donate links work.

---

### Post by DustofDust on 2009-07-07
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
> Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "multiverse" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).
Command line way

You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.

    % sudo apt-get update
    % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc



so it is the work of ubuntu to add it to the repositories, for this is the package management!

---

### Post by binbash on 2009-07-07
New features look cool!

---

### Post by Happy-Dude on 2009-07-07
what is zipped file playback?

---

### Post by jamsh on 2009-07-07
How do I get this??

---

### Post by Sealbhach on 2009-07-07
What is all this about Blu-Ray Linear PCM? Will it play my Blu Ray DVDs? I doubt that they have cracked the DRM...

.

---

### Post by mc4man on 2009-07-07
> How do I get this??
For jaunty keep an eye on this ppa, should be availabe soon
[https://edge.launchpad.net/~kow/+archive/ppa](https://edge.launchpad.net/~kow/+archive/ppa)
or available now
[https://edge.launchpad.net/~c-korn/+archive/vlc](https://edge.launchpad.net/~c-korn/+archive/vlc)

for intrepid search the ppa's in a day or 2
[https://edge.launchpad.net/ubuntu/+ppas?name_filter=vlc](https://edge.launchpad.net/ubuntu/+ppas?name_filter=vlc)

for hardy maybe a ppa, more likely build yourself

source
[http://download.videolan.org/pub/videolan/vlc/1.0.0/](http://download.videolan.org/pub/videolan/vlc/1.0.0/)

---

### Post by Sealbhach on 2009-07-07
> **jamsh said:**
> How do I get this??

There's no binary available for Ubuntu or Debian yet, as far as I can see. There's only the source code:

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

.

---

### Post by slumbergod on 2009-07-07
I upgraded using the c-korn PPA.

Version 1.0 works fine for me so far. Actually, so far it is better than the 0.9.9a version I had locked Jaunty on. Video playback seems smoother too.

The most important thing for me was that I had embedded controls in fullscreen mode and it does :)

---

### Post by andrew.46 on 2009-07-07
Hi Happy-Dude,

> **Happy-Dude said:**
> what is zipped file playback?

vlc will play directly from some archives without the need to manually decompress the file first. In my copy of vlc 1.0.0 this seems to only work with .zip files although I have not tested this extensively. I note with some interest that MPlayer seems to have more extensive support, have a look at 'Tip 2: Play from archives...' [on this page]("http://ubuntuforums.org/showthread.php?t=1154431").

Andrew

---

