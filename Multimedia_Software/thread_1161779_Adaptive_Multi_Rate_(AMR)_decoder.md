---
title: "Adaptive Multi Rate (AMR) decoder"
date: 2009-05-17
forum: Multimedia Software
---

### Post by James4 on 2009-05-17
hey there,
when I try to play 3gp file format with totem player it says it need needs to find the 'Adaptive Multi Rate (AMR) decoder' but after searching it says there was no package with that codec.
here is the screen shots of what's going on:

[IMG]http://i39.tinypic.com/1huphh.png[/IMG]

[IMG]http://i43.tinypic.com/jk7q81.png[/IMG]

[IMG]http://i40.tinypic.com/2ivzqcp.png[/IMG]

---

### Post by xc3RnbFO8P on 2009-05-17
Install Medibuntu:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
and in Synaptic Package Manager:
libamrwb3
libammb3
Mplayer
Mencoder

---

### Post by James4 on 2009-05-17
thanks pal, I could play my files using Mplayer but for totem player the problem still persists. I was wondering if there is any way to play such files with Totem Player?

---

### Post by xc3RnbFO8P on 2009-05-17
Im not sure , but try to install
**gstreamer** **bad** and **ugly**.

---

### Post by James4 on 2009-05-19
nope, didn't work.

---

### Post by tombox on 2009-05-20
> **James4 said:**
> nope, didn't work.

install RealPlayer 11 from medibuntu repository - it works with .amr files (from my nokia phone voice recorder files)

Synaptic -> sources -> packages.medibuntu.org/non-free -> realplayer (11.0.0-0.2medibuntu2)

---

### Post by candive on 2009-09-15
Google led me here.
Thank you very much &...
I Love Ubuntu more every day.
Chris.

---

### Post by fooey on 2009-11-04
> **candive said:**
> Google led me here.
Thank you very much &...
I Love Ubuntu more every day.
Chris.

wish you included witch solution fixed your problem ;)

---

### Post by mightyiam on 2009-12-22
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/93849](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/93849)

---

### Post by mc4man on 2009-12-22
amr support in gstreamer will be available in lucid thru the ugly plugin and the opencore libs though I wouldn't expect jaunty or karmic to be updated there.
Ironically the lucid ffmpeg does not support amr and unless some changes are made won't.

Is is quite easy and possible to build the new ugly plugin in karmic, just did and totem/rhythmbox now plays amr audio (3gp) with no issues

> configure: *** checking feature: amrnb library ***
configure: *** for plug-ins: amrnb ***
checking for AMRNB... yes
configure: *** These plugins will be built: amrnb

configure: *** checking feature: amrwb library ***
configure: *** for plug-ins: amrwbdec ***
checking for AMRWB... yes
configure: *** These plugins will be built: amrwbdec

(( very easy to build as a .deb and replace the current karmic ver.

---

### Post by patman0623 on 2009-12-27
> **mc4man said:**
> amr support in gstreamer will be available in lucid thru the ugly plugin and the opencore libs though I wouldn't expect jaunty or karmic to be updated there.
Ironically the lucid ffmpeg does not support amr and unless some changes are made won't.

Is is quite easy and possible to build the new ugly plugin in karmic, just did and totem/rhythmbox now plays amr audio (3gp) with no issues


(( very easy to build as a .deb and replace the current karmic ver.
By all means, please give instructions on how to do this.

---

### Post by mc4man on 2009-12-27
> give instructions on how to do this. 

Note edit - gstreamer ppa

Note that I haven't bothered to see if there were any ill/unexpected results though all seems fine. If for any reason seems unsuitable then just remove and re-install karmic package.

( over the last day or so, while testing some ways to keep totem-xine alive in karmic and lucid, have come to dislike totem-gstreamer and gstreamer in general even more than before, if that's even possible. ( do have totem-xine going good in karmic and for the moment lucid

Anyway...
As far as build-deps you're a bit on your own, never hurts to run
```
sudo apt-get install build-essential
```

this should help add a bit more
```
sudo apt-get build-dep gstreamer0.10-plugins-ugly
``` 

Also install if not already 
```
sudo apt-get install dpkg-dev fakeroot libopencore-amrnb-dev libopencore-amrwb-dev

```
Once you have the source look in /debian/control and or /debian/build-deps for list  if needed to d.ck.

```
mkdir gstugly && cd gstugly
```
 ```
wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gst-plugins-ugly0.10_0.10.13.orig.tar.gz
```

Edit: the next 2 wgets are good till the plugin updates in lucid, if it does, ck. ver. #'s [here]("http://packages.ubuntu.com/en/lucid/gstreamer0.10-plugins-ugly")

 ```
wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gst-plugins-ugly0.10_0.10.13-2.dsc

```
```
wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gst-plugins-ugly0.10_0.10.13-2.diff.gz

```

```
dpkg-source -x *.dsc
```
```
cd gst-plugins-ugly0.10-0.10.13
```
double ck. your build-deps, then (I use debuild, but this should suffice

```
dpkg-buildpackage -rfakeroot -D -us -uc
```

If there are any errors than you are missing some build-dep(s), correct and try again

from my build log (see no point in the x264 plugin (encoding
> 
configure: *** Plug-ins without external dependencies that will be built:
	asfdemux
	dvdlpcmdec
	dvdsub
	iec958
	mpegaudioparse
	mpegstream
	realmedia

configure: *** Plug-ins without external dependencies that will NOT be built:
	synaesthesia

configure: *** Plug-ins with dependencies that will be built:
	a52dec
	amrnb
	amrwbdec
	cdio
	dvdreadsrc
	lame
	mad
	mpeg2dec
	sid
	twolame

configure: *** Plug-ins with dependencies that will NOT be built:
	x264

If the build fails (shouldn't if all deps are installed ) then you could after squaring away the debs, either try the final build command again, or run a make distclean first or just delete the gst-plugins-ugly0.10-0.10.13 folder and at the ~/gstugly prompt start back at the dpkg-source command 

Just install (d.click on) the highlighted .deb in screen (did a quick test of commands here to ck.

edit: karmic sometimes needs a restart for things to take effect

no need to build - this ppa will give karmic the newer gstreamer plugins (inc. wma3

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by alveola on 2010-01-09
My solution for this problem is without compiling, backporting or apt-pinning.
Install two packages from Lucid: libcdio10 & gstreamer0.10-plugins-ugly, following the next steps:

1. Download these two packages for your architecture (i386/amd64):
[LIST]
[*][libcdio10]("http://packages.ubuntu.com/lucid/libcdio10")
[*][gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-ugly")
[/LIST]

2. Installation
a. (karmic)
```
sudo apt-get install libopencore-amrnb0 libopencore-amrwb0
```
b. (lucid)
```
sudo dpkg -i libcdio10_0.81-4_amd64.deb
sudo dpkg -i gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb
```

regards

---

### Post by thirdreplicator on 2010-01-11
This worked for me.  Thank you!!  (64-bit karmic koala)

***********

My solution for this problem is without compiling, backporting or apt-pinning.
Install two packages from Lucid: libcdio10 & gstreamer0.10-plugins-ugly, following the next steps:

1. Download these two packages for your architecture (i386/amd64):
libcdio10
gstreamer0.10-plugins-ugly

2. Installation
a. (karmic)
Code:
sudo apt-get install libopencore-amrnb0 libopencore-amrwb0
b. (lucid)
Code:
sudo dpkg -i libcdio10_0.81-4_amd64.deb
sudo dpkg -i gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb

---

### Post by marin123 on 2010-01-11
thanks man!! this worked for me too (karmic x64)

---

### Post by Yellow Pasque on 2010-01-12
Easiest way to get updated gstreamer for karmic: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by boddhisatva on 2010-01-24
**Thanks alveola!**
I tried all the other solutions and **none** helped, not even **realplayer** which either "played" the file with no sound, or crashed. I can now play my phone files in **Totem** (for the FIRST time, previously I converted them with Mobile Media Converter). And I'm going to **remove realplayer** and other trash :). Even MPlayer, which I don't use (and don't particularly like, though it may sound like blasphemy to some ;).

---

### Post by andrew.46 on 2010-01-24
Hi boddhisatva,

> **boddhisatva said:**
>  Even MPlayer, which I don't use (and don't particularly like, though it may sound like blasphemy to some ;).

Mind you it does not take much to get MPlayer to play these files:

```

andrew@skamandros~$ mplayer -ac help | grep amr
ffamrnb     ffmpeg    working   AMR Narrowband  [libopencore_amrnb]
ffamrwb     ffmpeg    working   AMR Wideband  [libopencore_amrwb]

```

Andrew

---

### Post by boddhisatva on 2010-01-24
Sorry Andrew, it ain't so, not here anyway.

1. Code:
```
pawel@pawel-desktop:~$ mplayer -ac help | grep amr

ffamrnb     ffmpeg    working   AMR Narrowband  [libamr_nb]
ffamrwb     ffmpeg    working   AMR Wideband  [libamr_wb]
```

2. MPlayer:

[IMG]http://img85.imageshack.us/img85/3383/screenshot2h.png[/IMG]

---

### Post by andrew.46 on 2010-01-25
Hi boddhisatva,

> **boddhisatva said:**
> Sorry Andrew, it ain't so, not here anyway

Try installing [libavcodec-extra-52]("http://packages.medibuntu.org/karmic/libavcodec-extra-52.html") from Medibuntu, this should enable amr playback for MPlayer under Karmic Koala. The following command will grab this package + MPlayer + SMPlayer:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && \
sudo apt-get -y install libavcodec-extra-52 mplayer-nogui smplayer

```

You would be well advised to also grab either w32codecs or w64codecs depending on the architecture of your Ubuntu installation (not necessary for amr playback). I attach a screenshot of my Karmic system happily playing this 3gp file:

```
wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

but I guess you have to imagine the sound :)

All the best,

Andrew

---

### Post by boddhisatva on 2010-01-25
Hi Andrew

Thanks for all the effort. I guess I'll stick with Totem as that's all I need - it plays everything so far. But I'm sure your info here will be useful for other people who have problems with the format. 

The video plays (with sound) in Totem. I like the song too. :)

---

### Post by omelette on 2010-01-27
Wee, it works!

With Ubuntu 8.04, I had to resort to recompiling Mplayer to listen to AMR/AWB - this is a far more 'civilised' approach :)

Thanks **alveola**!

---

### Post by omelette on 2010-01-27
Oops, there seems to be a problem with AWB playback, even though the wideband plugin is definitely installed.  Anyone know how to fix this?

---

### Post by andrew.46 on 2010-01-28
Hi omelette,

> **omelette said:**
> Oops, there seems to be a problem with AWB playback, even though the wideband plugin is definitely installed.  Anyone know how to fix this?

Can you post the file or give a link?

Andrew

---

### Post by omelette on 2010-01-28
> **andrew.46 said:**
> Hi omelette,



Can you post the file or give a link?

Andrew

Hi.  I was referring to **alveola's** post;


> **alveola said:**
> My solution for this problem is without compiling, backporting or apt-pinning.
Install two packages from Lucid: libcdio10 & gstreamer0.10-plugins-ugly, following the next steps:

1. Download these two packages for your architecture (i386/amd64):
[LIST]
[*][libcdio10]("http://packages.ubuntu.com/lucid/libcdio10")
[*][gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-ugly")
[/LIST]

2. Installation
a. (karmic)
```
sudo apt-get install libopencore-amrnb0 libopencore-amrwb0
```
b. (lucid)
```
sudo dpkg -i libcdio10_0.81-4_amd64.deb
sudo dpkg -i gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb
```

regards



On Karmic, after installing the stuff mentioned, Totem plays AMR flawlessly, but displays the now-familiar prompt to search for a suitable codec whenever an AWB file is double-clicked.  I tried (re)installing the good/bad/ugly plugins, as well as the 'ibopencore-amrnb0' and 'libopencore-amrwb0' codecs - no joy! :(

---

### Post by omelette on 2010-02-02
Bump!

Still wondering if there are Karmic users that managed to listen to AWB files (not AMR) via Totem?

---

### Post by gorg_karlo on 2010-02-16
> **alveola said:**
> My solution for this problem is without compiling, backporting or apt-pinning.
Install two packages from Lucid: libcdio10 & gstreamer0.10-plugins-ugly, following the next steps:

1. Download these two packages for your architecture (i386/amd64):
[LIST]
[*][libcdio10]("http://packages.ubuntu.com/lucid/libcdio10")
[*][gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-ugly")
[/LIST]

2. Installation
a. (karmic)
```
sudo apt-get install libopencore-amrnb0 libopencore-amrwb0
```
b. (lucid)
```
sudo dpkg -i libcdio10_0.81-4_amd64.deb
sudo dpkg -i gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb
```

regards

:popcorn:

Thanks a lot, your solution helped me to play videos captured from my new mobile phone that uses AMR encoding.

---

### Post by tedrogers on 2010-02-16
This did not work for me.

Instead I upload the file to youtube and then redownload it as an MP4!!

---

### Post by WhiteHorse on 2010-03-16
Easy way to add the developer version of Totem:
sudo add-apt-repository ppa:gwibber-daily/ppa
sudo apt-get update
sudo apt-get upgrade

---

### Post by SonicSteve on 2010-03-28
> **Temüjin said:**
> Easiest way to get updated gstreamer for karmic: [https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")


Awesome, you are so right. This worked perfectly! Sometimes these testing and develpers ppa's can be a bit a risky. This is by far the easiest way. 
32bit karmic.

---

### Post by thepisu on 2010-04-04
> **alveola said:**
> My solution for this problem is without compiling, backporting or apt-pinning.
Install two packages from Lucid: libcdio10 & gstreamer0.10-plugins-ugly, following the next steps:

1. Download these two packages for your architecture (i386/amd64):
[LIST]
[*][libcdio10]("http://packages.ubuntu.com/lucid/libcdio10")
[*][gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-ugly")
[/LIST]

2. Installation
a. (karmic)
```
sudo apt-get install libopencore-amrnb0 libopencore-amrwb0
```
b. (lucid)
```
sudo dpkg -i libcdio10_0.81-4_amd64.deb
sudo dpkg -i gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb
```

regards

Worked also for me (karmic 64 bit)

The only think is that the 13-2 version of gstreamer plugins is no more available on packages.ubuntu.com... and the new version have other dependencies and does not install on karmic. I download the 13-2 package here:

[http://launchpadlibrarian.net/35322853/gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb](http://launchpadlibrarian.net/35322853/gstreamer0.10-plugins-ugly_0.10.13-2_amd64.deb)

Thanks

---

### Post by isbiyanto on 2010-04-10
> **tombox said:**
> install RealPlayer 11 from medibuntu repository - it works with .amr files (from my nokia phone voice recorder files)

Synaptic -> sources -> packages.medibuntu.org/non-free -> realplayer (11.0.0-0.2medibuntu2)
working for me (karmic 32), thanks for all

---

### Post by alexandren on 2010-05-12
Quote:
Try installing libavcodec-extra-52 from Medibuntu, this should enable amr playback for MPlayer under Karmic Koala. The following command will grab this package + MPlayer + SMPlayer:

This really works! 
Only I did it through Synaptic. Look for the package libavcodec-extra-52 and mark it for installation. The libavcodec-52 was automatically uninstalled and a couple more dependencies will be added. Apply changes and that's it.
Now I can wach mp4 videos from my samsung phone. I've been looking for a solution to this problem for weeks.
Works with mplayer and gmplayer, no luck with totem, but I prefer gmplayer best anyway.

Thanks andrew.46

---

### Post by r3delmasry on 2010-09-25
nothing of all works for me
please help 
still 3gp and quick time files .mov doesn`t work 
please

---

### Post by boddhisatva on 2010-09-26
Which player do you use? If you use Totem, it should automatically look for codecs. Does it try to do that? Alternatively, you could try using VLC.

---

### Post by ionospheric on 2010-09-30
I just used ffmpeg to convert an AMR file to an MP3 file which totem can play without problems. I use WinFF as a GUI for ffmpeg for convenience. I already had Medibuntu enabled and installed some codecs, not sure which ones..

---

