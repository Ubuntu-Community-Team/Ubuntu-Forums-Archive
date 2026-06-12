---
title: "kaffeine 0.8.2 dapper package"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by mtron on 2006-10-11
**EDIT**: kaffeine 0.8.4 package is [here]("http://ubuntuforums.org/showpost.php?p=2462869&postcount=28")

due to the old version in the repositories i compiled version 0.8.2 from source and it works very nice.

backup your old profile in ~/.kde/share/apps/kaffeine if you wnat to roll back, than delete the old channel list (channels.dvb), and try my checkinstall package

at your own risk ;) 

it's compiled on a AMD Sempron 3000+ for ubuntu 6.06 with the xine engine only, cause i use it mainly for DVB which doesn't work with gstreamer. you'll need libxine1c2, libxine-extracodecs, w32codecs libdvdcss2

[kaffeine_0.8.2-ubuntu1_i386.deb - 4.36MB](http://mtron.co.nr/kaffeine_0.8.2-ubuntu1_i386.deb)

Screenshot of the DVB Tab:

[CENTER][IMG]http://michael.hoertnagl.googlepages.com/kaffeine.jpg[/IMG][/CENTER]

---

### Post by HuxleyHyperion on 2006-10-14
Thanks for this.  I tried to compile it myself, but being a newbie, I couldn't get it to work. Your .deb package worked perfectly.  Thanks!

---

### Post by mtron on 2006-10-15
glad it worked for you :p

---

### Post by el1 on 2006-10-16
it works fine, thanks dude :D

---

### Post by jdunn on 2006-10-18
Am I supposed to uninstall Kaffeine 0.7.1 first?  You didn't say anything about that.  I'm using Kubuntu Dapper and I'm reluctant to uninstall Kaffeine due to some defendancies...If I elect to remove Kaffeine, adept wants to remove other packages, including some part of the KDE desktop  :confused: .  I can't find channels.dvb anywhere.  I simply ran the install and received the following error:

sudo dpkg -i kaffeine_0.8.2-ubuntu1_i386.deb
Password:
dpkg-deb: unexpected end of file in version number in kaffeine_0.8.2-ubuntu1_i386.deb
dpkg: error processing kaffeine_0.8.2-ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 kaffeine_0.8.2-ubuntu1_i386.deb

I'm at the end of my rope with Kaffeine.  I get crash problems whenever I play DVDs on Kaffeine 0.7.1.  I've had this problem for months yet, I have no problems playing DVDs on KDE Media Player (KMplayer).  I've posted to the Ubuntu, Kubuntu and Kaffeine Sourceforge forums several times and have gotten no answers.  My next step is to petition KDE to change to a different default media player.  If that doesn't work, I'm switching to a different desktop manager and distro.  Gnome is beginning to look REALLY GOOD.

---

### Post by TransitMan on 2006-10-18
I uninstalled my Kaffeine player before installing 0.8.2.
It works flawlessly now.

---

### Post by jdunn on 2006-10-18
Well since everyone is saying this package works so great, I removed Kaffeine 0.7.1 and installed this 0.8.2 deb package.  I reinstalled the kaffeine-xine package from the repositories but Kaffeine is not seeing it.  why?

*update*
Okay, it found xine.  For some reason, I had to run Kaffeine a few times before it could find it.  I'm doing further tests.  So far, I can play DVDs but need to check on other formats

**update**
Thumbs up

---

### Post by jdunn on 2006-10-19
The Kaffeine 0.8.2 package works well but, I have a concern.  I used Adept to uninstall 0.7.1.  Before I performed the "update" i checked to see what other packages would be removed.  Among them were Kaffeine-xine, Kaffeine-mozilla and some kde package.  After installing 0.8.2, I reinstalled   Kaffeine-xine and Kaffeine-mozilla but I forgot what the 3rd kde package was.  Can some tell me?

---

### Post by easyease on 2006-10-19
I decide to bite the bullet last night and try out Edgy, the latest build of kaffeine is a joy to use under that. for some reason my dvb device uses about half the cpu it did under breezy using kaffeine.

---

### Post by mtron on 2006-10-19
Hi jdunn! 

uninstall the old package is a good idea, but in theory it should also work when you use the gtk package installer and "upgrade" & you only need the packages i listed in the first post:
libxine1c2, libxine-extracodecs, w32codecs, libdvdcss2

No kaffeine-xine (included in my package) is needed. kaffeine-mozilla from the repository is a browser plugin for firefox which i never tried.

There was a change in the channels database for DVB, so you need to re-scan your sats - if you have a DVB-S or whatever multimedia card that is supported by the v4l driver.

for every app it's a good way to start it via the terminal. The debug info is usually very easy to understand. If you have more problems, post the log here and i will try my best to help

DVB works very good here on dapper with the new kaffeine (much better than on any windows app i ever tried :D 

cpu usage on my Sempron 3000+ with the 2.6.15-27-k7 Kernel while watching DVB is between 20 and 30 %. Amazing! on Windows with ProgDVB & Mytheatre i came never under 40 - 50%

---

### Post by espinosa_cz on 2006-10-21
There is already a 0.8.2 package in Edgy Eft. 
Have you tried the backports repository?
Anyway I use Edgy, but Kaffeine doesn't show the DVB tab for me. Or it smartly recognized I have no DVB card?

---

### Post by mtron on 2006-10-23
> **espinosa_cz said:**
> Or it smartly recognized I have no DVB card?
Yup, if you don't have a DVB card, there won't be a DVB tab ;) 

The package from backports has many "debian & ubuntu" patches. the diff file is over 20 kb... and most important: DVB didn't work for me 
(this package has SoftCAM support :p )

---

### Post by chefweb on 2006-11-03
The download link is broken, can somebody upload the file again? Thanks

---

### Post by Eskas on 2006-11-04
I have trouble installing this package:
>sudo dpkg -i kaffeine_0.8.2-ubuntu1_i386.deb
dpkg-deb: `kaffeine_0.8.2-ubuntu1_i386.deb' is not a debian format archive
dpkg: error processing kaffeine_0.8.2-ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 kaffeine_0.8.2-ubuntu1_i386.deb

I have installed the prerequired packages libxine1c2, libxine-extracodecs, w32codecs libdvdcss2 installed.

Could this be because I have a i686 compiled kernel or is there a dependency missing? What's could else be wrong?

What version of the softcam plugin for Kaffeine is included in this package?

---

### Post by mtron on 2006-11-06
i would say you have a corrupt download file. re-download it, and use the gdebi package installer.

There is no softcam included in this package, cause it might be illegal in most countries of the world. google for kaffeine-sc-plugin.

Kaffeine 0.8.2 introduced CICAM support, what is used by the plugin.

---

### Post by Eskas on 2006-11-06
> **mtron said:**
> i would say you have a corrupt download file. re-download it, and use the gdebi package installer.

There is no softcam included in this package, cause it might be illegal in most countries of the world. google for kaffeine-sc-plugin.

Kaffeine 0.8.2 introduced CICAM support, what is used by the plugin.

I've tried to download the file many times now. There seems to be some trouble with the file on zSHARE. I've tried both gdebi and dpkg now, none of them recognize the .deb file as a package. Gdebi claims that the file is corrupt. Would you please upload it again or send me an email with the file. Thanks in advance!

---

### Post by mtron on 2006-11-06
heres a new link:

[http://mtron.co.nr/kaffeine_0.8.2-ubuntu1_i386.deb](http://mtron.co.nr/kaffeine_0.8.2-ubuntu1_i386.deb)

---

### Post by Eskas on 2006-11-07
Thanx alot, works great now!

---

### Post by megamaced on 2006-11-07
I compiled Kaffeine 0.8.2 and built a Debian package with checkinstall too. But the problem is that the screensaver starts every 5 minutes, which did not happen with the official kaffeine packages.

Does the screensaver start after a while whilst you are watching TV with your packaged version?

---

### Post by mtron on 2006-11-08
as far as i know kaffeine simulates the repeated press of the shift key in order to prevent the screensaver from starting.

The log reads fake keypress event every 5 - 10 minutes. my screensaver is set to be activated after 30 mins, so i never had a problem with it.

---

### Post by mtron on 2006-11-28
and **version 0.8.3 of kaffeine arrived! **

quick'n dirty checkinstall package for ubuntu dapper (6.06) 

kaffeine 0.8.3 (needs xine-lib 1.1) [kaffeine_0.8.3-ubuntu1_i386.deb - 4.36MB](http://www.zshare.net/download/kaffeine_0-8-3-ubuntu1_i386-deb.html)

Changelog Kaffeine 0.8.3:

* DVB: selectAll button in scandialog
* DVB: save channels list sort order
* DVB: added "Current channel" button in epg window
* DVB: OSD warning when timeshift hd<300MB
* DVB: auto rename channels when adding to list
* DVB: fixed scanning services sharing same pmt.
* DVB: added H/V (C band mutipoint) lnb settings.
* DVB: improved device detection.
* DVB: added : "int dvbSNR( int device )" dcop call.

* xine-part: shortcuts for delay/advance subtitles (ctrl+alt+right/left)
* xine-part: fixed wmv seeking.
* xine-part: save and restore video settings (hue,saturation,contrast,brightness)

* added: option to start in minimal mode + dcop call.
* added: "Open Dir" starts playing dvd from dir if dir points to a dvd image.
* added: playing dvd iso files.

* Disc: fixed crash trying to play while encoding
* Disc: Ask user for cddb close matches

* fixed: session issue.
* fixed: better screensaver disabling method (no interfering key presses anymore).
* fixed: crash when quit from systray.

---

### Post by megamaced on 2006-11-28
> **mtron said:**
> 
* fixed: better screensaver disabling method (no interfering key presses anymore).

Thank god

---

### Post by Castar on 2006-12-02
Thank you for the package!

---

### Post by raphoun on 2006-12-25
Great but are they a package for edgy?

---

### Post by vyoufinder on 2007-01-03
How do I remove Kaffeine?  I just barely installed it because I wanted ot play a dvd but it doesn't work.  now when I try to uninstall it won't let me and says to use something called Synaptics something or other.  I just want it gone but don't know how.  Also if anyone knows something that plays dvds on Ubuntu, I'm interested to know how.  there's got ot be a way right?  An easy way without installing a bunch of junk.  I'm a newbie so I don't know how to install or uninstall anything other than using the add/remove programs.


EDIT:  Ok, I figured it out.  Synaptics whatever is some sort of removal tool already installed in Ubuntu - got rid of it.  Anyone know how to make Totem movie player play a store-bought Hollywood dvd or is there another program that I need to install?  Is it even possible in Ubuntu?  Total newbie here but enjoying my freedom from Microsuck nonetheless.

---

### Post by mtron on 2007-01-04
> **mtron said:**
> you'll need libxine1c2, libxine-extracodecs, w32codecs libdvdcss2


if you install this packages, DVD playback will work. 

Read the wiki about [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")!

---

### Post by neztiti on 2007-04-06
great thanx

---

### Post by mtron on 2007-04-16
So, here we go with a new kaffeine Version:

**kaffeine 0.8.4 Changelog:**

* added: allow toggling (show / hide) panels by clicking tabs

* fixed: allow small window size in minimal mode

* fixed: removed readonly parts support
* fixed: improve screensaver disabling method again (old behaviour for non-kde environments)

* Playlist: menu option to not auto switch to player window
* Playlist: fix opening playlists
* Playlist: fix google fetcher
* Playlist: don't cut bottom font in rollingtitle.

* DVB: added osd browsing dcop calls
* DVB: added a "source" column in channels list.
* DVB: rotors support (usals and mem_pos)
* DVB: fixed multi devices usage.
* DVB: fixed devices probing
* DVB: added tuning timeout options
* DVB: fixed OSD epg bug with diseqc settings
* DVB: use klocale for datetime format

* gstreamer-part: port to gst 0.10

* xine-part: dragndrop subtitles files
* xine-part: support for xcb. Requires libxcb 1.0 and xine-lib 1.1.5. Fixes several issues.
* xine-part: reduced audio/sub combos sizes
* xine-part: add volume+/- to embedded context menu.
* xine-part: better "Track infos" box layout.
* xine-part: don't restore video settings if not previously saved

Again, here's a checkinstall package for **ubuntu dapper** of this version. So the same stuff appies..

> if you've never used kaffeine before, install the version from the Repositories first to get the necessary dependancies, and uninstall the old 0.7.1 package again. 

Next backup your old profile in ~/.kde/share/apps/kaffeine if you want to roll back, then delete the old channel list (channels.dvb) if present, and try my checkinstall package

it's compiled on a AMD Sempron 3000+ for ubuntu 6.06 with the xine engine only, cause i use it mainly for DVB which doesn't work with gstreamer. 

**For DVD and DVB playback you'll need these extra packages:**
sudo apt-get install libxine1c2 libxine-extracodecs w32codecs libdvdcss2

Due to the fact that dapper ships an old libxine (1.1.1) there's no xcb support in this package, also i stripped the gstreamer- part, cause it's not fully implemented.

[URL="http://mtrons.googlepages.com/kaffeine_0.8.4-ubuntu1_i386.deb"]
kaffeine_0.8.4-ubuntu1_i386.deb[/URL]
Size: 4.4 MB; OS: ubuntu LTS (dapper)
Notes: Package is build with prefix=/usr/local, so check that /usr/local/lib is present in the file  /etc/ld.so.conf and run "sudo ldconfig" after the install

---

### Post by Dexterp37 on 2007-05-05
Just tested it on my Ubuntu Edgy: it works fine, just had to tweak it, since it copies .desktop files to /usr/local/share/services. It complained for missing xine_part.desktop, so I copied them to /usr/share/services and it worked like a charm :)

---

### Post by megamaced on 2007-05-18
> **mtron said:**
> Due to the fact that dapper ships an old libxine (1.1.1) there's no xcb support in this package

What is xcb and does it matter that it's not compiled in?

---

### Post by mtron on 2007-05-20
it's mainly a fix for the embedded kaffeine player in konqueror. Kaffeine will still work with the old xlib based video out plugins, but then it might crash your Konqueror when playing embedded media

xcb is a  thread-safe replacement for xlib

You can give it a try right now:
1) install libxcb=>1.0 from source
2) install current xine-lib cvs (it contains xcb based video output plugins: xshm and xv)

more about xcb: [http://xcb.freedesktop.org/wiki/](http://xcb.freedesktop.org/wiki/)

---

### Post by megamaced on 2007-05-21
Thanks for the info.

I usually backport Kaffeine from the Feisty or Gutsy repos using [Prevu]("http://ubuntuforums.org/showthread.php?t=268687"). However Gutsy doesn't have a 0.8.4 package yet

---

### Post by josweet on 2007-12-29
Im  100% newbie to the linux scene after having so much trouble with windows i finally decided to change.
I think i have collected most of the needed linux software im gona need but this one..
I currently use "MyTheatre" in win so intend to use this as the equivilant to recieve me DVB broadcast.
Could someone please post a working link and give me any tips on getting it working.

---

### Post by mtron on 2008-02-03
i've build kaffeine 0.8.6 for gutsy (since the 0.8.6 supports epg plugins). Then i put some useful programs together and used falcon to create a repository.

The repo  contains:
[LIST]
[*]kaffeine 0.8.6 with gstreamer & xine engine,[SIZE="1"] [[http://kaffeine.kde.org/?q=node/19]](http://kaffeine.kde.org/?q=node/19])[/SIZE]
[*]atsc-converter: converts ATSC (a)scan channels.conf to kaffeine's channels.dvb format [SIZE="1"][[sourceforge    feature request]("https://sourceforge.net/tracker/?func=detail&atid=581409&aid=1658619&group_id=86937")][/SIZE]
[*]wscan a blindscanner for DVB-t and DVB-C that exports to kaffeine's channels.dvb format. you can also generate initial tuning data files for (dvb)scan [SIZE="1"][[howto]("http://edafe.org/vdr/wscan.html")][/SIZE]
[*]xine-lib 1.1.9 (hardy backport): newest xine-lib from hardy (ubuntu development version)
[/LIST]

to install see: [http://kaffeine.homelinux.com/](http://kaffeine.homelinux.com/)

---

