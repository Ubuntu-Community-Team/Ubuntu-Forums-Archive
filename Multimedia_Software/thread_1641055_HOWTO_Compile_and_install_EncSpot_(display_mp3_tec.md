---
title: "HOWTO: Compile and install EncSpot (display mp3 technical info)"
date: 2010-12-08
forum: Multimedia Software
---

### Post by lykeion on 2010-12-08
EncSpot is a Windows application by now gone GuerillaSoft.
Before GuerillaSoft vanished they released a console version under the New BSD license. 
Francis Russell adapted the sources to compile under most *nix-like environments.

EncSpot is a command-line utility to display technical info of MP3 files. This is some info you'll get.
MP3 info: Bitrate distribution (histogram), Type, Bitrate, Mode, Frequency, Frames, Length, Reservoir (average), Emphasis, Scalefac, Encoder
Lame info: Quality, Version, Revision, VBR method, LP filter, Psycho-acoustic model, Safe joint stereo, ATH type, ABR bitrate, Noise shaping, Stereo mode, Input frequency

This howto will show you how to build and install EncSpot. If you encounter any errors during the commands below you might have to install some packages (cmake, debhelper, etc).

Steps to build and install EncSpot
[LIST]
[*] Start a terminal
Applications > Accessories > Terminal
[*]Start in your home directory, download the sources archive (available from Francis Russell's homepage [uncharted backwaters]("http://www.unchartedbackwaters.co.uk/")) and extract it:
```
cd
wget http://www.unchartedbackwaters.co.uk/files/encspot/encspot-2.01+mtn20100426.tar.bz2
tar -jxvf encspot-2.01+mtn20100426.tar.bz2
```
[*]Enter sub-directory and build deb package
```
cd encspot-2.01+mtn20100426/
dpkg-buildpackage -b
```
[*]Install package
```
cd ..
sudo dpkg -i encspot_2.01+mtn20100426-1_i386.deb
```
[*]Use EncSpot
```
encspot audiofile.mp3
```
[/LIST]

---

### Post by Francis Russell on 2011-01-11
As the author of the above packaging, I'd just like to point out that it already incorporates Debian packaging scripts. All one needs to do to build a deb, as with all Debian/Ubuntu sources, is to run 'dpkg-buildpackage -b' in the main folder.

---

### Post by lykeion on 2011-01-12
Thanks for your comment, I've changed the howto accordingly.

---

