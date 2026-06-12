---
title: "Codecs"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Hydrokys on 2010-05-01
Just installed ubuntu 10.04 and would like some suggestions on a good video and audio player and maybe an idiots guide to installing all the codecs i need. I would like to find an audio player with some good visualizations. thanks.

---

### Post by 2hot6ft2 on 2010-05-01
I don't know which has the best visualizations since I don't use them.
Perhaps Amarok aor Amarok Nightly, LiVeS, or Exaile.

For the rest.
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

### Post by Hydrokys on 2010-05-01
ty very much. exactly what i needed thnx

---

### Post by 2hot6ft2 on 2010-05-01
> **Hydrokys said:**
> ty very much. exactly what i needed thnx
You're welcome. Enjoy.
:guitar:

---

### Post by conradin on 2010-05-01
I recommend VLC. not for the visualizations, I don't use those either, but for the fact it uses much less system resources than the totem player.

more vlc visualizations are available on-line from sources like the ones below
[http://www.filebuzz.com/findsoftware/Vlc_Visualizations/1.html](http://www.filebuzz.com/findsoftware/Vlc_Visualizations/1.html)
or
[http://linuxers.org/article/visualizations-vlc-11](http://linuxers.org/article/visualizations-vlc-11)

You can install codecs either in synaptic, or by going to the ubuntu software center under applications.

---

