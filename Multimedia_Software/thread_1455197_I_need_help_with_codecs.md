---
title: "I need help with codecs"
date: 2010-04-15
forum: Multimedia Software
---

### Post by awjm on 2010-04-15
I know there is information out there but I don't know how to find it or exactly what I need. I've installed ripoff to rip CDs and I want to rip them to mp3.
I downloaded a codec package to do that but I have no idea what to do with the package. I'm not the most technical person so could you please explain simply?
Thanks a lot for any help!

---

### Post by WinterRain on 2010-04-15
Just do
```
sudo apt-get install ubuntu-restricted-extras
```
and you will be covered.

---

### Post by awjm on 2010-04-15
> **WinterRain said:**
> Just do
```
sudo apt-get install ubuntu-restricted-extras
```
and you will be covered.

What does that do?
Thanks in advance.

---

### Post by WinterRain on 2010-04-15
> **awjm said:**
> What does that do?
Thanks in advance.

That will give you needed codecs.

---

### Post by 2hot6ft2 on 2010-04-15
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
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to decline the Java terms of use since we'll install suns java next.
Next we want the sun version of Java since it works better and will pass the test on this page.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
It will say there is an update available but the main thing is it works.
```
sudo apt-get ininstall sun-java6-jre sun-java6-plugin
```
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

