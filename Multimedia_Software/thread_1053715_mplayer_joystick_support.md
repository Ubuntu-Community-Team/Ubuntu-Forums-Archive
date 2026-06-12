---
title: "mplayer joystick support"
date: 2009-01-28
forum: Multimedia Software
---

### Post by master_d on 2009-01-28
I was wondering how to enable joystick support in mplayer.  it seems that the precompiled binary in the ubuntu repositories is compiled without joystick support.  Is there a different version which has joystick support compiled in?  If not what is the standard procedure for installing a package from source?  I'd like the package manager to be aware of the package after I install it from source.

---

### Post by andrew.46 on 2009-01-29
Hi,

I have not used a joystick under MPlayer but I believe if you follow this guide:

[Howto] Install the svn Mplayer under Intrepid Ibex
[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

and install this file *before* actually compiling the source code:

```
sudo apt-get install libjsw-dev
```

you might be in luck. I should stress that I have not actually run a joystick with MPlayer before so I am making a semi-educated guess :-).

Andrew

---

### Post by master_d on 2009-01-29
thanks for the reply.

here's what I did to get it working.  It's really not pretty.  I didn't know compiling from source would be so exasperating.

First install source libraries that you would like to have support for in mplayer.  I installed the following list.  You may install more or less.

```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0  libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils  libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all  libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev  liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev   libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev  libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev  libmjpegtools0 fakeroot libgtk2.0-dev libmpcdec-dev
```

next we need to get the mplayer source code.  You can download it off the mplayer site, but I decided to go with the latest version from subversion.
You can store the code wherever you want, but I think ubuntu recommends you put it in /usr/local/src

```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

```

I found out the hard way that you need to patch the source if you don't want gnome-screensaver to start while you are watching something with mplayer.  I downloaded the patch from [here]("http://ubuntuforums.org/showthread.php?t=668257") and you can apply the patch by running the following command

```
patch -p1 < mplayer-svn-gnome-screensaver.patch
```

next you need to run ./configure in the root of the mplayer source directory.  You can run ./configure --help to find out what options you can enable before compile time.  The key parameter to get joystick support is --enable-joystick so make sure you at least pass this parameter to ./configure

```
 sudo ./configure --prefix=/usr --enable-joystick --enable-runtime-cpudetection --enable-gui --enable-largefiles --enable-menu --confdir=/etc/mplayer
```

after that you need to compile the source.  

```
sudo make -j5
```
**if you want to use the -j parameter for multithreading in a multiple cpu environment, it's recommended that you use 1 + the number of cpu cores you have on your box.  So in my case I have 4 cores so the number becomes 5.  You can ignore this if you want, it just takes longer to compile without it.

after mplayer compiles without error you can use checkinstall to install it.

```
sudo checkinstall
```

follow the dialogs to install mplayer.  This will make it aware to your package manager.

phew ... that's it I hope

---

### Post by andrew.46 on 2009-01-29
Hi,

Glad to hear you have it all running, a few alarm bells though:

> **master_d said:**
> 
next you need to run ./configure in the root of the mplayer source directory.  You can run ./configure --help to find out what options you can enable before compile time.  The key parameter to get joystick support is --enable-joystick so make sure you at least pass this parameter to ./configure

```
 sudo ./configure --prefix=/usr --enable-joystick \
--enable-runtime-cpudetection --enable-gui --enable-largefiles \
--enable-menu --confdir=/etc/mplayer
```


You would not normally use '--enable-joystick' as MPlayer works best with auto-detection and in fact compilation will usually fail with such an option unless you also specify the path to header files. The option '--enable-runtime-cpudetection' is really only of use if you plan to distribute your package, on a single user system this option will significantly slow down startup of MPlayer every time you open an instance of the program. '--enable-largefiles' is the default for the svn MPlayer and does not need to be specified.

You did not like the guide I suggested?

Andrew

---

### Post by master_d on 2009-01-30
thanks for your advice andrew.

I actually had a working copy of mplayer before I even noticed you posted a guide.  I think I will use it tonight because mplayer is giving me some problems playing back AC3 audio streams.  For some reason if you adjust the volume on these streams it will turn the audio into static.  I will also run ./configure without --enable-joystick as you suggested and see if it can auto detect it.  Thanks again for your help!

---

### Post by mattsl on 2009-11-09
Recompiling actually is not necessary. Simply commenting out "nojoystick = yes" in /etc/mplayer/mplayer.conf should do. Like this:

```

#Disable joystick support
#It seems to cause very odd problems on laptops
#With accelerometers (See LP: #75925)
#nojoystick = yes # <--- comment out to activate joystick support

```

---

