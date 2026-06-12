---
title: "coming from Suse 10.1"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by heracles on 2006-12-13
I have just installed Ubuntu after leaving Suse Linux. I must say the wireless support in Ubuntu is excellent .No tweaking it worked from the start. Dual monitors also no problem. I am left with running video on the net. I do a lot of it so its quite important. Any suggestions as how I set up to run all video files on the net gratefully received.

---

### Post by fnf on 2006-12-13
It's more of a matter of personal preference to choose which player/encoder. I use mplayer and mencoder for everything media related. The source is updated frequently so you'll want to compile it from SVN repository.

Sure you'd want a separate movie editor, but mencoder does its job well enough :) .

Ubuntu has mplayer package included, if you don't want any hassle. Also checkout the [Ubuntu Guides]("http://ubuntuguide.org/").

---

### Post by heracles on 2006-12-13
Thanks for that reply. Unfortunately as I got further on the UBUNTU site it pointed out that as I have a 64 bit version I need a workaround at the moment.

---

### Post by fnf on 2006-12-13
You may want to compile it then, that's actually prefered way as the stock mplayer is pretty old now. In particular, it can't play WVM9 or some kind of rare formats.

Detailed instruction and the SVN repository can be found at the [MPlayer Headquarter]("http://www.mplayerhq.hu/design7/news.html").

In case you haven't played much with Debian's package manager (Apt), you can install a package using the front-end *Synaptic*, or ```
$sudo apt-get install <package_name>
```.

---

### Post by heracles on 2006-12-14
thanks I shall give it a go

---

### Post by heracles on 2006-12-14
I have tried to compile and downloaded all the packages listed on Mplayer site. When I try to install with apt .I get  "Couldn't find package w32codecs_20061022-0.0_i386.deb "or a similar message to every package I install. Except that is for KM Player base which also says" KMplayer base is newest version"

---

### Post by fnf on 2006-12-14
Aside from mplayer, there're several more mentioned in UbuntuGuides (e.g VLC, Totem/xine with gstreamer), but I like the simplicity of mplayer ;) no need to install any additional codecs if you compile from source, to play almost every formats. You may want to try them first if they suit you anyway.
--------

You probably downloaded these packages from the [Unofficial packages]("http://www.mplayerhq.hu/design7/projects.html#unofficial_packages") page, the Ubuntu's packages are the ones you would get if you do '**apt-get install mplayer**' from the console, which is *1.0pre8* (from *June*!).

The stock mplayer is pretty good (can play most DivX, FLV, MOV, AVI formats) , except for the fact that if you do wish to play WMV, Real Media and random seeking on these files you'd need later versions.

The steps below are based on the [mplayer documentation]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#install"), basically you'll only need to install the dependencies, after that it's really straight forward (and pretty much the same for any other Linux packages) to install mplayer itself:

From the console, install the commonly required packages for compilation:
```
sudo apt-get install build-essential svn checkinstall
```
Install mplayer's dependencies:
```
sudo apt-get install xserver-xorg-dev libxv-dev libasound2-dev zlib1g-dev
```
Depending on your need, you'll want to install more development packages listed in the doc, this should be enough for most people though. **apt-cache show <package_name>** to get information on each package.

cd to the directory you want to place the source then:
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

```
Create a copy of the source to satify Debian's versioning system and in case things don't work out:
```
cp -R mplayer mplayer-svn-1337 (replace 1337 with any number ;)
cd mplayer-svn-1337
```
Alright, if you want to install without the cover of Debian's package manager (meaning it'll be difficult to remove mplayer later on), just invoke those:
```
./configure
make
sudo make install
```
checkinstall on the other hand is able to create packages for Debian, RedHat and Slackware package manager by monitoring the installation process, this is more preferable, you can install and remove the created package at your pleasure:
```
./configure
make
checkinstall --install=no (answer a few questions)
sudo dpkg --install <newly created mplayer package>
```

Let me know if there's any problem.

---

