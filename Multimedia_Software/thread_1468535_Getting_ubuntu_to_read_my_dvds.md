---
title: "Getting ubuntu to read my dvds"
date: 2010-05-01
forum: Multimedia Software
---

### Post by cuewoz on 2010-05-01
Does anyone know what I should do to read a dvd disc that I recorded on my dvd recorder off the satelite decoder. When I look in winxp it shows the contents which is only a video_ts folder and no audio folder.

Inserting the same into the pc with ubuntu 9.10 running the drive reads the disc but I then cannot access the contents, which I want to convert to a divx file or similar.

Am I missing something? or will I have to use my Windows system for this?

Thanks in advance

---

### Post by 2hot6ft2 on 2010-05-01
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube....

Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept the Java terms of use since Oracle now owns Sun.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

VLC Player will be in Applications > Sound and Video > VLC

---

