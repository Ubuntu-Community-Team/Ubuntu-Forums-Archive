---
title: "Some assistance with writing a guide for building the git vlc under Ubuntu?"
date: 2010-01-29
forum: Multimedia Software
---

### Post by andrew.46 on 2010-01-29
[B][CENTER][COLOR="Blue"]===========================================================================
Please do not follow the information in this early version. The guide is
now published in 'Tutorials and Tips' at this address:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

===========================================================================[/COLOR][/CENTER][/B]

I am in the process of writing a guide that will illustrate how to compile the git vlc under Ubuntu. I am putting a very early version of this guide here as a 'work in progress' mostly so I can get both feedback and assistance on certain elements of the guide, in particular the compilation under 64bit systems as I do not have access to such a system. I would love people to experiment with this work and suggest improvements, bearing in mind that this guide is *not* complete and may fail completely on some systems. When work is complete this thread will be locked and marked as outdated, the full guide will subsequently appear in the 'Tutorials and Tips' section hopefully in April.


**[COLOR="Red"]+-------------- 'Working version' of Guide Below -------------------+[/COLOR]**

Howto: Build the development version of vlc under Ubuntu

This guide details how to install the development version of vlc using the 32bit version of Ubuntu's Karmic Koala. I intend to update the guide with each new release of Ubuntu and hopefully also at some stage incorporate a section devoted to the needs of 64bit Ubuntu.

Can I state clearly at the outset that there is absolutely no *need* for the average Ubuntu user to compile this development version of vlc and in fact I believe that 99% of Ubuntu users will be more than happy with the release version from either the Ubuntu Repository or from one of the several PPAs that package vlc so nicely. For those of you happy to be a little closer to the bleeding edge please read on...

===========================
**Some Preparation...**
===========================

There are many steps to take before actually laying hands on the source code for the development version of vlc and these steps are best taken strictly in sequence. Let me emphasize at the beginning that this guide at this stage is for the ***32bit Karmic Koala***, this will change when the 32bit Lucid Lynx is released.

**Basic Tools...**

The first steps are to install some compiling and installation software as well as the necessary software to access both subversion and git repositories:

```

sudo apt-get install build-essential subversion git-core checkinstall automake

```

The next step is to enable the Medibuntu repository:

**Medibuntu...**

Some useful material is contained in the Medibuntu Repository and this can be accessed as follows, we also install libdvdcss and its development library to enable playback of commercial dvds as well as the w32codecs to allow playback of some windows media. The following is a single command:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install -y libdvdcss-dev w32codecs

```

Next to download and compile the latest x264 libraries:

**x264...**

The x264 libraries allow encoding to the h264 format. The standard technique of compiling x264 and linking statically with *--with-x264-tree=PATH* failed at times for me so I have borrowed the following technique Slackware which installs a *local* copy of x264 to be linked statically by vlc:

```

$ sudo apt-get install yasm
$ mkdir -v $HOME/vlc_build && cd $HOME/vlc_build
$ git clone git://git.videolan.org/x264.git
$ cd $HOME/vlc_build/x264
$ ./configure --prefix=$HOME/vlc_build/vlcdeps/usr
$ make && make install
$ make distclean

```

The x264 libraries are being developed at an alarming pace and I would advise you to come back here every week or so and issue the command *git pull* from $HOME/vlc_build/x264 and the recompile and reinstall to get the latest version of x264. Next to use a similar technique with FFmpeg:

**FFmpeg...**

One of the most fundamental parts of the preparation for compiling the development version of vlc is compiling an up to date version of libavcodec, which is part of FFmpeg, for vlc usage. I demonstrate here a technique borrowed from Slackware where vlc is linked statically to a slightly odd looking FFmpeg installation, trust me it works...

```

$ sudo apt-get install libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev \
	libopencore-amrwb-dev zlib1g-dev
$ cd $HOME/vlc_build
$ svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
$ cd $HOME/vlc_build/ffmpeg
$ ./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
	      --enable-gpl \
              --enable-version3 \
              --enable-nonfree \
              --enable-postproc \
              --enable-pthreads \
              --enable-libfaac \
              --enable-libfaad \
              --enable-libmp3lame \
              --enable-libopencore-amrnb \
              --enable-libopencore-amrwb \
              --disable-ffmpeg \
              --disable-ffplay \
              --disable-ffserver \
              --disable-doc
$ make && make install-libs install-headers
$ make distclean

```

FFmpeg is also being developed at an alarming pace and I would advise that you return every week or so to issue the command *svn up* from $HOME/vlc_build/ffmpeg and then recompile and reinstall to get the latest version of FFmpeg. Next to compile the latest Live555 libraries:

**Live555...**

The latest Live555 libraries are needed as vlc will use these to read media streams. The following will remove the repository live555 libraries which are quite dated and then download, compile and install the newest libraries.

```

$ sudo apt-get remove liblivemedia-dev
$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo mv -v $HOME/live /usr/lib

```

The live555 libraries are updated every 2 months or so and I would suggest you download, compile and install the newest libraries *regularly*. Simply remove /usr/lib/live and all of its contents and repeat the process above.

**Development Files...**

There are about 60megs of additional development files required to successfully build vlc and give it greatly increased functionality:

```

sudo apt-get install libqt4-dev libhal-dev liblua5.1-0-dev libdvdread-dev \
libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev \
libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev \
libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev \
libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev \
libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev \
libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev \
libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev \
libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev \
libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev \
libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev \
libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev \
libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev \
liboggkate-dev libkate-dev libpango1.0-dev libcairo2-dev

```

Feel free to modify these libraries and add your own according to your own requirements, please suggest additions to this list and I will happily test and incorporate them. 

**A few extras...**

There are couple of extra libraries that are not actually available in the Ubuntu repository. The first is libtiger which is useful for rendering more ornate Kate streams:

```

$ cd $HOME/vlc_build
$ wget http://libtiger.googlecode.com/files/libtiger-0.3.3.tar.gz
$ tar xvf libtiger-0.3.3.tar.gz
$ cd libtiger-0.3.3
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname libtiger --pkgversion "0.3.3" --deldesc=yes \
                    --delspec=yes --default
$ make distclean

```

and the second is my old friend goom which has also somehow missed a place with Ubuntu:

```

$ cd $HOME/vlc_build
$ wget http://downloads.sourceforge.net/goom/goom-2k4-0-src.tar.gz
$ tar xvf goom-2k4-0-src.tar.gz
$ cd goom2k4-0
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname goom --pkgversion "2k4-0" --deldesc=yes \
                    --delspec=yes --default
$ make distclean

```

Neither of these libraries require further ./configure options in vlc, they will both be picked up and utilised automagically. Now to finally come to grips with the vlc source code:

===========================
**Building vlc......**
===========================

Now to download and build the git vlc. The tricky bit of sed work, neatly reversed at the end of the build process, simply allows Ubuntu to see an icon on the desktop menu.

```

$ cd $HOME/vlc_build
$ git clone git://git.videolan.org/vlc.git --depth 1
$ cd vlc
$ ./bootstrap
$ export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"
$ sed -i_bak 's/Icon=vlc/Icon\=\/usr\/local\/share\/vlc\/vlc48x48\.png/' \
       share/applications/vlc.desktop
$ ./configure --enable-loader \
	      --with-live555-tree=/usr/lib/live \
              --enable-real \
              --enable-realrtsp \
              --enable-aa \
              --enable-snapshot \
              --enable-merge-ffmpeg 
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname vlc --pkgversion "1.1.0-`date +%Y%m%d`" \
                    --deldesc=yes --delspec=yes --default
$ make distclean
$ mv -v share/applications/vlc.desktop_bak share/applications/vlc.desktop
$ sudo ldconfig

```

This process can take a long time, depending on the speed of your connection to the git repository and the processing speed of your computer when compiling but eventually you will have a copy of the development version of this great media player. It remains then to return to the vlc source code from time to time to run the command *git pull* and then recompile and reinstall to receive the latest additions and corrections to this great media player. And remember the most important thing: Have Fun!!

==========================
**Some Resources...**
==========================

[LIST]
[*][The VideoLan Forums]("http://forum.videolan.org/"): The definitve place to go to with queries and problems related to vlc. ALso announcements of new features, new versions etc.
[*][Welcome to VideoLAN's Wiki]("http://wiki.videolan.org/Main_Page"): 483 articles on many areas related to vlc as well as other software hosted by VideoLan such as the x264 encoder and the new VideoLAN Movie Creator (vlmc).
[*][The vlc SlackBuild of Eric Hameleers]("http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild"): An incredible installation script for vlc from the world of Slackware. I have pillaged many ideas from this script for which I thank Eric very, very much.
[/LIST]

---

### Post by Yellow Pasque on 2010-01-30
On a relatively fresh install of Lucid in a virtual machine, I get the following. Maybe it will help you ;) :
```
$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autotools-dev build-essential cvs debhelper dh-buildinfo diffstat dpkg-dev
  fakeroot g++ g++-4.4 gettext html2text intltool-debian liba52-0.7.4
  liba52-0.7.4-dev libaa1-dev libasound2-dev libass-dev libass4 libatk1.0-dev
  libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev
  libavahi-common-dev libavc1394-dev libavcodec-dev libavcodec52
  libavformat-dev libavformat52 libavutil-dev libavutil49 libcaca-dev
  libcairo2-dev libcddb2 libcddb2-dev libcdio-dev libcdio7 libdbus-1-dev
  libdbus-glib-1-dev libdca-dev libdca0 libdirectfb-dev libdirectfb-extra
  libdvbpsi5 libdvbpsi5-dev libdvdnav-dev libdvdnav4 libdvdread-dev
  libdvdread4 libebml-dev libebml0 libenca-dev libenca0 libesd0-dev
  libexpat1-dev libfaad-dev libfaad2 libflac-dev libfontconfig1-dev
  libfreetype6-dev libfribidi-dev libgcrypt11-dev libggi-target-x libggi2
  libggi2-dev libggimisc2 libggimisc2-dev libgii1 libgii1-dev libgii1-target-x
  libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev
  libgpg-error-dev libgsm1 libgtk2.0-dev libhal-dev libice-dev libid3tag0
  libid3tag0-dev libiso9660-5 libiso9660-7 libiso9660-dev libjack-dev libjack0
  libjpeg62-dev liblircclient-dev liblivemedia-dev libltdl-dev liblua5.1-0
  liblua5.1-0-dev libmad0 libmad0-dev libmail-sendmail-perl libmatroska-dev
  libmatroska0 libmodplug-dev libmodplug0c2 libmpcdec-dev libmpcdec3
  libmpeg2-4 libmpeg2-4-dev libmysqlclient16 libncurses5-dev libncursesw5-dev
  libnotify-dev libnspr4-dev libnss3-dev libogg-dev liboil0.3-dev
  libpango1.0-dev libphonon4 libpixman-1-dev libpng12-dev libpostproc-dev
  libpostproc51 libpthread-stubs0 libpthread-stubs0-dev libpulse-dev
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-dev libqt4-help
  libqt4-multimedia libqt4-network libqt4-opengl libqt4-opengl-dev
  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libraw1394-dev libreadline-dev
  libreadline6-dev librsvg2-dev libschroedinger-1.0-0 libschroedinger-dev
  libsdl-image1.2 libsdl-image1.2-dev libsdl1.2-dev libshout3-dev
  libslang2-dev libsm-dev libsmbclient-dev libspeex-dev libstdc++6-4.4-dev
  libsvga1 libsvga1-dev libswscale-dev libswscale0 libsys-hostname-long-perl
  libsysfs-dev libtag1-dev libtar libtar-dev libtasn1-3-dev libtheora-dev
  libtiff4-dev libtiffxx0c2 libtool libtwolame-dev libtwolame0 libudev-dev
  libupnp3 libupnp3-dev libv4l-dev libvcdinfo-dev libvcdinfo0 libvorbis-dev
  libx11-dev libx264-67 libx264-dev libxau-dev libxcb-keysyms1
  libxcb-keysyms1-dev libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxpm-dev
  libxrandr-dev libxrender-dev libxt-dev libxv-dev libxxf86dga-dev
  libxxf86vm-dev mesa-common-dev mysql-common nasm patch po-debconf qt4-qmake
  quilt x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-video-dev x11proto-xext-dev
  x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev xulrunner-1.9.1-dev xulrunner-dev yasm zlib1g-dev
0 upgraded, 231 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by andrew.46 on 2010-01-30
Hi Temujin,

> **Temüjin said:**
> On a relatively fresh install of Lucid in a virtual machine, I get the following. Maybe it will help you ;)

Thanks for that :). In fact the guide when the rough edges have been knocked off will initially be based on the Lucid Lynx, although only aiming for Karmic Koala at the moment.

Andrew

---

### Post by mc4man on 2010-01-30
I've only worked on getting 1.0.5 going on lucid, but taking those .deps and willowing down the list posted by Temüjin looks like this. ( there still may be some redundancies and or missing. - you'd be surprised by what just libqt4-dev supplies

The build deps are ATM the same for karmic and lucid

Put in alpha. order otherwise I tend to get lost very quickly... 
```

sudo apt-get install dpkg-dev liba52-0.7.4-dev libass-dev \
libavc1394-dev libcddb2-dev libcdio-dev libdca-dev libdvbpsi5-dev \
libdvdnav-dev libdvdread-dev libebml-dev libenca-dev libflac-dev \
libfluidsynth-dev libfribidi-dev libgcrypt11-dev libggi2-dev libggi-target-x  \
libggimisc2-dev libgii1-dev libgnomevfs2-dev libgnutls-dev libhal-dev libmad0-dev \
libid3tag0-dev libiso9660-dev libjack-dev liblircclient-dev liblua5.1-0-dev  \
libmatroska-dev libmodplug-dev libmpcdec-dev libmpeg2-4-dev libmtp-dev \
libmysqlclient16 libncursesw5-dev libnotify-dev libogg-dev libproxy-dev \
libpulse-dev libqt4-dev libqt4-sql-mysql libraw1394-dev librsvg2-dev \
libschroedinger-dev libsdl-image1.2-dev libshout3-dev libsmbclient-dev  \
libspeex-dev libsqlite3-dev libsvga1-dev libtag1-dev libtar-dev \
libtheora-dev libtiff4-dev libtwolame-dev libudev-dev libupnp3-dev \
libv4l-dev libvcdinfo-dev libvorbis-dev libX11-xcb-dev libxcb-keysyms1-dev \
libxcb-randr0-dev libxcb-shm0-dev libxcb-shape0-dev libxcb-xvmc0-dev \
libxcb-xv0-dev libxcb-xfixes0-dev libxml2-dev libxpm-dev libxv-dev libxxf86dga-dev  \
libzvbi-dev mysql-common x11proto-video-dev x11proto-xf86dga-dev xulrunner-dev
```

I've found that suggesting dpkg-dev for any build tends to take care of most of the needed build tools ( if so, maybe in the orig. build deps.., includes build-essential among other things

1.1 is going more to autodetect and enabled by default so the config is clearly getting smaller, ( on an individual level may be more reason to disable unneeded modules than anything else

Probably useful to review ./configure --help from time to time for changes, additions, ect.

I wonder about this
--enable-run-as-root
While some people may need for certain setups, most won't. Is there any issues that could arise by needlessly running vlc as root?
(considering many have this 'fascination' with running apps as root

This I've never seen in 1.0.X - curious, do you now what it's about?
--enable-merge-ffmpeg

In addition to or in lieu of --enable-release may be worth exploring if there is any advantage to 
--with-tuning=native

Glad to see your proceeding, should be good - as long as users understand some things may break or builds/installs may fail from time to time

Ex. - For a couple of days this week 1.1 would build fine, but wouldn't fully install (though it could be used). Should have been resolved by now, so patience may be a build dep of sorts

---

### Post by andrew.46 on 2010-01-30
Hi mc4man,

> **mc4man said:**
> I wonder about this
--enable-run-as-root
While some people may need for certain setups, most won't. Is there any issues that could arise by needlessly running vlc as root?

Good point, this is a carry-over from installing vlc on my other distro...

> This I've never seen in 1.0.X - curious, do you now what it's about?
--enable-merge-ffmpeg

More efficient compiling and runtime performance:

[http://mailman.videolan.org/pipermail/vlc-devel/2009-September/066759.html](http://mailman.videolan.org/pipermail/vlc-devel/2009-September/066759.html)

Andrew

---

### Post by mc4man on 2010-01-30
Well I'll give it a run exactly as posted (except root), shouldn't take to long. let you now if any issus, (not expecting any

---

### Post by SuperSonic4 on 2010-01-30
Compiling now on x86_64 (albeit on arch but most will be the same), I'll edit if there are any issues.

Also it may be helpful to point out that VLC will be installed /usr/local in case anyone looks for it. Might I suggest you add in ```
**--prefix=/usr/local**
``` or ```
sudo mkdir /opt/vlc
--prefix=/opt/vlc
```.

This way the git version can coincide with the repo version


edit I: oops forgot to compile ffmpeg with pic

---

### Post by andrew.46 on 2010-01-30
Hi mc4man,

> **mc4man said:**
> Well I'll give it a run exactly as posted (except root), shouldn't take to long. let you now if any issus, (not expecting any

Thanks very much for that, I am not on such sure ground with vlc as MPlayer but I learn fast :).

Andrew

---

### Post by andrew.46 on 2010-01-30
Hi SuperSonic,

> **SuperSonic4 said:**
> Compiling now on x86_64 (albeit on arch but most will be the same), I'll edit if there are any issues.

Excellent :). I do not have a 64bit system to test and I know the 64bit vlc can present a few problems especially linking with FFmpeg.

Andrew

---

### Post by mc4man on 2010-01-30
I do remember and see in this post that for 64 bit both x264 and ffmpeg needed fPIC
[http://ubuntuforums.org/showthread.php?t=1155698&highlight=fPIC&page=3](http://ubuntuforums.org/showthread.php?t=1155698&highlight=fPIC&page=3) #23

Edit:
all went well with the build, will give this git a test later, (this was done on karmic
As far as config, used what you posted (almost..)
The --enable-dvdread isn't needed though doesn't hurt (dvdread and dvnav modules will be built anyway
> ./configure --enable-loader --with-live555-tree=/usr/lib/live --enable-real --enable-realrtsp --enable-snapshot  --enable-release --enable-merge-ffmpeg --enable-aa --with-tuning=native

> Enabled modules: a52tofloat32 aa access_alsa access_dv access_gnomevfs access_jack access_mmap access_oss access_output_shout access_realrtsp access_smb alsa aout_sdl atmo audioscrobbler avcodec bonjour caca cdda dbus dc1394 dirac dmo dtstofloat32 dvb dvb dvdnav dvdread dynamicoverlay fb flac fluidsynth freetype globalhotkeys gnutls inhibit jack kate libass libmpeg2 live555 mediadirs mkv mod motion mpc mpgatofixed32 mtp mux_ogg mux_ts notify ogg oldhttp oldrc oldtelnet osd_parser osdmenu oss panoramix png postproc pulse qt4 realvideo remoteosd schroedinger screensaver sdl_image signals skins2 snapshot speex sqlite stream_out_raop svg swscale taglib telepathy telx theora ts twolame udev unzip upnp_intel v4l2 vcd visual vorbis vout_sdl x264 xcb_apps xcb_glx xcb_screen xcb_window xcb_x11 xcb_xv xdg_screensaver xml zip

Well done as usual

---

### Post by SuperSonic4 on 2010-01-30
> **andrew.46 said:**
> Hi SuperSonic,



Excellent :). I do not have a 64bit system to test and I know the 64bit vlc can present a few problems especially linking with FFmpeg. I chose this way because I wanted the x264 and ffmpeg libs for mplayer

Andrew

Yeah VLC won't compile on those instructions, probably because I'm using a different OS but I did get VLC to compile (besides some sound issues on my machine)

**x264**. Installing x264 git from videoLAN. This is in order to compile ffmpeg (and mplayer) with h264 encoding.

```
cd ~/svn
git clone git://git.videolan.org/x264 x264
cd x264
./configure --enable-shared --enable-visualize --enable-pic --enable-pthread --extra-ldflags='-fPIC' --prefix=/usr/local
make
sudo make install
```


**ffmpeg**.

```
cd ~/svn
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
./configure --enable-pthreads --enable-libx264 --extra-cflags='-fPIC' --enable-libfaac --enable-libfaad --enable-encoder=x264 --enable-gpl --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-encoder=libx264 --enable-encoder=h264 --enable-libvorbis --enable-libtheora --enable-libmp3lame --enable-libx264 --enable-pic --prefix=/usr/local --disable-ffplay --disable-ffserver --extra-ldflags='-fPIC'
make
sudo make install
```


**VLC**

```
cd ~/svn
git clone -v git://git.videolan.org/vlc.git --depth 1
./configure --program-suffix=-git --prefix=/usr/local --enable-run-as-root --enable-ogg --enable-mkv --disable-faad --enable-twolame --enable-x264 --disable-png --enable-libmpeg2 --enable-vorbis --enable-theora --enable-svg --enable-snapshot --enable-alsa --enable-access_alsa --enable-skins2 --enable-qt4 --enable-ncurses --enable-visual --enable-flac --with-tuning=native --disable-swscale
make
sudo make install
```

---

### Post by FakeOutdoorsman on 2010-01-30
> **SuperSonic4 said:**
> ...

**x264**. Installing x264 git from videoLAN. This is in order to compile ffmpeg (and mplayer) with h264 encoding.

```
cd ~/svn
git clone git://git.videolan.org/x264 x264
cd x264
./configure --enable-shared --enable-visualize --enable-pic --enable-pthread --extra-ldflags='-fPIC' --prefix=/usr/local
make
sudo make install
```

The *--enable-pthread* option is redundant because x264 detects this automatically.  Does -*-enable-visualize* even work anymore?  I believe it enables a debugging tool, but I'm not sure if it has been updated for a while.

Still waiting for a chance to try this guide on my co-workers brand new i7.  I'm also interested in what additional options, if any, are needed for x86_64.

---

### Post by mc4man on 2010-01-30
I think the only issue will be is linking a static ffmpeg with vlc on 64 bit install a problem or not
Kinda curious how these two configures resulted in a vlc build
> /configure --enable-pthreads --enable-libx264 --extra-cflags='-fPIC' --enable-libfaac --enable-libfaad --enable-encoder=x264 --enable-gpl --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-encoder=libx264 --enable-encoder=h264 --enable-libvorbis --enable-libtheora --enable-libmp3lame --enable-libx264 --enable-pic --prefix=/usr/local --disable-ffplay --disable-ffserver --extra-ldflags='-fPIC'

> /configure --program-suffix=-git --prefix=/usr/local --enable-run-as-root --enable-ogg --enable-mkv --disable-faad --enable-twolame --enable-x264 --disable-png --enable-libmpeg2 --enable-vorbis --enable-theora --enable-svg --enable-snapshot --enable-alsa --enable-access_alsa --enable-skins2 --enable-qt4 --enable-ncurses --enable-visual --enable-flac --with-tuning=native --disable-swscale
Only because ffmpeg was configured without postproc and postproc wasn't disabled in vlc.
In that case vlc should have failed the config outright...

Think I may do a 64 bit install before installing lucid on this laptop, can also revisit building a 32 bit mplayer

---

### Post by mc4man on 2010-01-31
From here I don't yet see vlc building off of a static ffmpeg on 64 bit. Maybe I missed something, but did try all the mentioned compiler options, combinations ect. and several not mentioned. Same result - no go.

Maybe there is some flags that will work...?

On the other hand it will build fine with a shared ffmpeg, no issues whatsoever.
The default karmic -dev's worked  though obviously there there is a bit of a loss there. (though many might not particularly care

It's a shame that it *appears lucid may* use the same -r as karmic, personally don't buy into the regression potential of moving ffmpeg forward, certainly not with ubuntu supported apps. (i guess the next month will show

Also went ahead and put in newer shared and -dev packages of ffmpeg and x264 (r20916, core 83) and everything works quite well - no ubuntu or gstreamer app is broken or regressed, and something like winff is quite happy there, vlc built and is running well - both 1.1 and 1.04

(though for 1.0.X's, a ffmpeg/x264 about a week eariler than the X release *may *be better if you use vlc for x264 transcoding, which myself never do or will.

Would try one more bug on lucid's ffmpeg ver. if there were other's to confirm and comment

---

### Post by FakeOutdoorsman on 2010-01-31
> **mc4man said:**
> Would try one more bug on lucid's ffmpeg ver. if there were other's to confirm and comment

I can confirm and comment.  Just need to install Lucid first...

---

### Post by andrew.46 on 2010-01-31
Hi mc4man,

> **mc4man said:**
> From here I don't yet see vlc building off of a static ffmpeg on 64 bit. Maybe I missed something, but did try all the mentioned compiler options, combinations ect. and several not mentioned. Same result - no go.

Hmmm... that is a pretty major stumbling block but it does demonstrate to me again the difficulty of catering for both 32bit and 64bit in one guide. One solution would be to abandon 64bit completely, I am not so keen on a shared FFmpeg for building vlc... I shall ruminate while undertaking a week of night work in my real life :).

Andrew

---

### Post by Yellow Pasque on 2010-01-31
> catering for both 32bit and 64bit in one guide. One solution would be to abandon 64bit completely Please don't. It would be better to use the Launchpad PPA system. Do you have a PPA?

---

### Post by andrew.46 on 2010-01-31
Hi Temujin,

> **Temüjin said:**
> Do you have a PPA?

I suspect a PPA would not really suit running the development version of vlc which really requires a rebuild every week or so. But no, I have not ever set one up.

**Edit:** Mind you it appears that a PPA has been setup for Karmic and Lucid that contains a very recent git snapshot of vlc:

WebUpd8 
[https://edge.launchpad.net/~nilarimogard/+archive/webupd8](https://edge.launchpad.net/~nilarimogard/+archive/webupd8)

Yet another nail in the coffin for this prospective guide :(.

Andrew

---

### Post by dr_latino999 on 2010-02-01
I've tested this guide out on a fresh install of 9.04-32 with VMware tools installed on a host ESXi 3.5 system and have some observations.

The installation appears to hit a hard patch here- ```

`/home/edwin/live' -> `/usr/lib/live'
Initialized empty Git repository in /home/edwin/vlc_build/vlc/.git/
remote: Counting objects: 32832, done.
remote: Compressing objects: 100% (21570/21570), done.
remote: Total 32832 (delta 24071), reused 16984 (delta 10885)
Receiving objects: 100% (32832/32832), 74.44 MiB | 1515 KiB/s, done.
Resolving deltas: 100% (24071/24071), done.
Checking out files: 100% (3630/3630), done.
+ dirname ./bootstrap
+ cd .
+ ACLOCAL_ARGS=-I m4 
+ test -d extras/contrib/build/bin
+ uname -s
+ test .Linux = .Darwin
+ pkg-config --version
+ PKGCONFIG=yes
+ export AUTOPOINT
+ test 
+ AUTOPOINT=autopoint
+ autopoint --dry-run --force
+ AUTOPOINT=true
+ echo
+ set +x
generating modules/**/Makefile.am
...........................................................................
+ echo
+ echo
+ cp -f INSTALL INSTALL.git
+ autoreconf --install --force --verbose -I m4
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 188.
Use of uninitialized value $libtoolize in pattern match (m//) at /usr/bin/autoreconf line 188.
autoreconf: Entering directory `.'
autoreconf: running: true --force
autoreconf: running: aclocal --force -I m4
configure.ac:436: error: m4_undefine: undefined macro: AC_DEPLIBS_CHECK_METHOD
configure.ac:436: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
VLC20100201: line 41: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@US904-32 ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ vlc ]
3 -  Version: [ 1.1.0-20100201 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ vlc ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ vlc ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

make: *** No rule to make target `distclean'.  Stop.
`share/applications/vlc.desktop_bak' -> `share/applications/vlc.desktop'
edwin@US904-32:~/Desktop$ 

```Also, I had to remove libxcb-keysyms-1-dev from the large list of packages to be installed, it was not present in the Jaunty cache. I changed it to libxcb-keysyms-0-dev.

Finally, the following code was changed due to an error in git.
**Original**
```
git clone **-v** git://git.videolan.org/vlc.git --depth 1
```**Modified**
```
git clone git://git.videolan.org/vlc.git --depth  1
```This is the script I used for the install:

```
#!/bin/bash
apt-get install build-essential subversion git-core checkinstall automake -y
wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
--output-document=/etc/apt/sources.list.d/medibuntu.list &&
apt-get -q update &&
apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
apt-get -q update &&
apt-get install libdvdcss-dev w32codecs yasm libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev zlib1g-dev libqt4-dev libhal-dev liblua5.1-0-dev libdvdread-dev libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev libupnp3-dev libx11-dev libxcb-keysyms0-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev -y
#i had to change libxcb-keysyms1-dev to libxcb-keysyms0-dev, 1 was not found in the cache
mkdir -v $HOME/vlc_build && cd $HOME/vlc_build
git clone git://git.videolan.org/x264.git
cd $HOME/vlc_build/x264
./configure --prefix=$HOME/vlc_build/vlcdeps/usr
make && make install
make distclean
cd $HOME/vlc_build
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd $HOME/vlc_build/ffmpeg
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
    --enable-gpl --enable-version3 --enable-nonfree --enable-postproc \
    --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame \
    --enable-libopencore-amrnb --enable-libopencore-amrwb \
    --disable-ffmpeg --disable-ffplay --disable-ffserver --disable-doc
make && make install-libs install-headers
make distclean
apt-get remove liblivemedia-dev
cd $HOME
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvf live555-latest.tar.gz
cd live
./genMakefiles linux
make
mv -v $HOME/live /usr/lib
cd $HOME/vlc_build
git clone git://git.videolan.org/vlc.git --depth 1
cd vlc
./bootstrap
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"
sed -i_bak 's/Icon=vlc/Icon\=\/usr\/local\/share\/vlc\/vlc48x48\.png/' \
       share/applications/vlc.desktop
./configure --enable-loader \
    --with-live555-tree=/usr/lib/live --enable-real --enable-aa \
        --enable-realrtsp --enable-snapshot --enable-merge-ffmpeg 
make
checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes --pkgname vlc \
    --pkgversion "1.1.0-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default
make distclean
mv -v share/applications/vlc.desktop_bak share/applications/vlc.desktop
ldconfig
```

---

### Post by andrew.46 on 2010-02-01
Hi dr_latino999,

Thanks for looking at this prospective guide. I have not really tested it under Jaunty and I will admit that my aim was to keep the guide abreast of the *current* Ubuntu flavour. The build error is I suspect the result of missing:

```
sudo apt-get install libtool
```

which I believe is normally dragged in as part of either automake or build-essential. The -v option I have removed from the git command as it does not contribute much. For your script I might suggest adding:

```
set -e
```

on the second line and this will prevent the script from continuing after a failure.

Thanks for your trouble,

Andrew

---

### Post by andrew.46 on 2010-02-01
Has anybody actually located any lua scripts to test out the new vlc 'extension' functionality?

Andrew

---

### Post by mc4man on 2010-02-01
> Has anybody actually located any lua scripts to test out the new vlc 'extension' functionality?


Never paid  any attention but taking the most obvious one I see - one of the youtube lua's - well a little disappointing.

While it works fine - vlc <youtube url>, it always gets the sd. low audio quality stream, even when given the hd url

As ex.
this url is sd
```
http://www.youtube.com/watch?v=6minna09s5g
```
and the same in hd
```
http://www.youtube.com/watch?v=6minna09s5g&hd=1
```

if you give vlc the later it still plays the former
> 
vlc [http://www.youtube.com/watch?v=6minna09s5g&hd=1](http://www.youtube.com/watch?v=6minna09s5g&hd=1)
............................
0x9db92a0] lua demux debug: Lua playlist script /usr/share/vlc/lua/playlist/youtube.lua's probe() function was successful
[0x9db92a0] main demux debug: using demux module "lua"
[0x9db92a0] main demux debug: TIMER module_need() : 58.725 ms - Total 58.725 ms / 1 intvls (Avg 58.725 ms)
[0xb7300ce8] main input debug: `[COLOR="Blue"]http://www.youtube.com/watch?v=6minna09s5g[/COLOR]' successfully opened


Possibly I'm missing something here, don't know this stuff to well - it appears that it reads embedded html which is the same on both sd and hd ..?

or maybe it needs a better script..
[http://wiki.videolan.org/Documentation:Play_HowTo/Building_Lua_Playlist_Scripts](http://wiki.videolan.org/Documentation:Play_HowTo/Building_Lua_Playlist_Scripts)

---

### Post by andrew.46 on 2010-02-02
Hi mc4man,

> **mc4man said:**
> Possibly I'm missing something here, don't know this stuff to well - it appears that it reads embedded html which is the same on both sd and hd ..?

These scripts do not appear to load in the ['Extensions' window ]("http://jpeg.dinauz.org/blog/index.php?post/2010/01/30/Extensions-in-VLC")of vlc 1.1.0-git despite placement in ~/.local/share/vlc/lua/extensions/. There must be another set of lua scripts?

BTW I have at least temporarily dumped the 64bit information for installing the git vlc. It is a little too frustrating for me to be unable to test and troubleshoot such an installation myself, and the installation sounds like it will be problematic at the least. 

All the best,

Andrew

---

### Post by mc4man on 2010-02-02
I was on 1.0.5 and didn't get what you meant by extensions, but found them here - they load up  - have to run so haven't looked at.
(am doing a cp of the /usr/local/share/vlc to ~/.local/share after install, then a mkdir for the extensions

[http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions/](http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions/)

Am running a 64 bit for a few weeks, though I'll probably go w/32 for lucid....

Tried the ppa - is fine and what you'd expect from a ppa vlc - missing a few things and uses the repo ffmpeg though for x264 is using a current 83
(while I have no use for vlc transcoding I couldn't get the ppa vlc to transcode anything...

Created a local repo and some new shared ffmpeg, x264 libs and built the 1.1 git - works fine (though it also has some difficulty trans...

Built a 32 mplayer which works quite fine though needed to use live555 created on 32 bit (though didn't test how or if vdpau can be used with a 32 bit build, may try on lucid

Tested an excellent [windows mplayer]("http://ubuntuforums.org/showthread.php?p=8752368#post8752368") cli build for extracting and playback - interesting

I think if I was to go 64 bit I'd go: 

new ffmpeg/x264 shared using local repo for ease of use
self built vlc(s)
64 bit mplayer (if no vdpau needed then a 32 bit
Sherpya win cli for dmo if using 64 bit mplayer

Edit:
what may prove to be an endeavor of some proportions would be, at some point, a "how to use vlc 1.1"

Re-edit:
am also seeing the plugins cache - ( plugins-04081e-3e8.dat.28941 ) is now being installed to /usr vs. ~/ , which makes it impossible for vlc to write to or reset if need be, wonder what that's about - I guess if vlc was run as root it could..? ( the ppa is enabling 'run as root'

---

### Post by andrew.46 on 2010-02-02
Hi mc4man,

> **mc4man said:**
> I was on 1.0.5 and didn't get what you meant by extensions, but found them here - they load up  - have to run so haven't looked at.
(am doing a cp of the /usr/local/share/vlc to ~/.local/share after install, then a mkdir for the extensions

[http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions/](http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions/)

Thanks for that, I shall load these up and have an explore :).


All the best,

Andrew

---

### Post by dr_latino999 on 2010-02-02
Rebuilt VLC under 10.04 today, which in itself was amazing that I was able to install the necessary VMtools for ESX for the gui to be half decent. I think VLC is working fine, but I can't test the transcoding features very well as it only has one Xeon (Pentium 4 architecture) allocated to the machine. Before I move the script over to a Core 2 Duo, does VLC natively transcode/encode with more than one thread if FFMPEG is installed?

---

### Post by Yellow Pasque on 2010-02-02
You probably need ffmpeg-mt (from git) for multi-threaded ffmpeg.

---

### Post by FakeOutdoorsman on 2010-02-02
> **Temüjin said:**
> You probably need ffmpeg-mt (from git) for multi-threaded ffmpeg.

Some encoders in regular FFmpeg can take advantage of the *-threads* option, although I'm unsure what options VLC uses when encoding.

---

### Post by SuperSonic4 on 2010-02-02
For the extensions I saved the .lua file direct to ~/.local/share/vlc/lua/extensions/

```
mkdir -p ~/.local/share/vlc/lua/extensions/
mv *.lua ~/.local/share/vlc/lua/extensions/
```

After recompiling both are to be found in View and Tools --> Plugins/Extensions

As I'm using Arch I cannot be sure about dependencies but I can't see anything wrong with the OP's guide.

For today at least my VLC is up and running using the latest git. I have installed it into /usr/local. I used this method as the installed packages can be used in other compilations such as mplayer

For some reason I had to compile ffmpeg first or disable lavf in x264.

**Housekeeping**
```
mkdir -p ~/svn
```


**FFMPEG**
```
cd ~/svn
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
./configure --host-cflags='-fPIC' --extra-cflags='-fPIC' --arch=x86_64 --enable-libx264 --enable-libmp3lame   --enable-libfaac   --enable-libfaad --enable-libopencore-amrnb --enable-encoder=libx264 --enable-encoder=h264 --prefix=/usr/local --enable-encoder=x264 --disable-ffplay --disable-ffserver --enable-postproc --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-swscale --enable-encoder=xvid --enable-avcodec
make
sudo make install
```


**x264**
```
cd ~/svn
git clone git://git.videolan.org/x264.git x264
./configure --enable-pthread --extra-cflags='-fPIC' --extra-ldflags='-fPIC' --enable-pic --prefix=/usr/local --enable-shared
make
sudo make install
```


**VLC**
```
cd ~/svn
git clone git://git.videolan.org/vlc.git --depth 1
export PKG_CONFIG_PATH="/usr/local/lib/pkg-config"
./configure --enable-flac --prefix=/usr/local --program-suffix=-git --enable-postproc --enable-run-as-root --enable-lua --disable-notify --enable-live555 --enable-dvdread --disable-smb --enable-id3tag --enable-merge-ffmpeg --enable-swscale --enable-faad --enable-flac --enable-libmpeg2 --enable-x264 --disable-fribidi --disable-pulse --enable-alsa --enable-access_alsa --enable-ncurses --enable-qt4 --enable-mtp --disable-png
make
sudo make install
```

---

### Post by andrew.46 on 2010-02-02
Hi dr_latino,


> **dr_latino999 said:**
> Rebuilt VLC under 10.04 today, which in itself was amazing that I was able to install the necessary VMtools for ESX for the gui to be half decent. 

So the error message during ./bootstrap was resolved? You may need to write an 'update' script as well to update the FFmpeg and x264 libraries from time to time...

Andrew

---

### Post by andrew.46 on 2010-02-02
The new Extension manager will be a huge feature I suspect... I attach a screenshot of the movie database script which on my system works beautifully and might even justify all the compiling :).

Andrew

---

### Post by dr_latino999 on 2010-02-02
> **andrew.46 said:**
> Hi dr_latino,




So the error message during ./bootstrap was resolved? You may need to write an 'update' script as well to update the FFmpeg and x264 libraries from time to time...

Andrew
That is correct, the problem went away under 10.04 and 9.10 testing. I can't vouch for the encoders yet since I haven't been able to finish compiling it on something larger than a P4 (everyone else in the office has at least 1 Quad :mad:).

Is VLC installed to the same location as repo versions using your instructions? Also, are they other things we should be looking for while testing 1.1.0?

EDIT: Last question, I am running it on my laptop - the script - and it crashed; my laptop is running x64 9.10. What happened to the x64 instructions above?

---

### Post by SuperSonic4 on 2010-02-02
> **dr_latino999 said:**
> Is VLC installed to the same location as repo versions using your instructions? Also, are they other things we should be looking for while testing 1.1.0?

No, unless checkinstall has something to do with it. The installer will send it to /usr/local. In my instructions (for x86_64 but untested) it installs to /usr/local.

You can specify it's installation location by adding *--prefix=PATH* in the configure line where PATH is wherever you want it to be. /usr/local is always good I find.

> EDIT: Last question, I am running it on my laptop - the script - and it crashed; my laptop is running x64 9.10. What happened to the x64 instructions above?

The OP removed them as he is unable to test them on his own PC. My instructions in my immediately prior post are for x86_64

---

### Post by Yellow Pasque on 2010-02-02
andrew, I used to like installing stuff directly from source too, but then I came to realize it wasn't the way to go when trying to guide other users. .deb packaging exists for a reason.

mc4man, I am interested in creating .deb packages in a PPA to make it extremely easy for users to get all their multimedia running. I'm going to start with that PPA version of VLC and see if I can add in the missing features.

---

### Post by SuperSonic4 on 2010-02-02
> **Temüjin said:**
> andrew, I used to like installing stuff directly from source too, but then I came to realize it wasn't the way to go when trying to guide other users. .deb packaging exists for a reason.

mc4man, I am interested in creating .deb packages in a PPA to make it extremely easy for users to get all their multimedia running. I'm going to start with that PPA version of VLC and see if I can add in the missing features.

The reason for these guides is that it will be an enormous strain on your bandwidth due to the sheer frequency of git/svn updates. Perhaps a weekly snapshot would be a good idea?

---

### Post by mc4man on 2010-02-02
@Temüjin
While I generally build vlc as a package set for myself, I also can do some things I'm not sure a ppa will afford (though am curious about if you can.

Noting that the ck. install also works quite fine, again for personal use. (it has some limitations that most would find irrelevant, as may many would find my reasons to do as a package set.

What is at the heart of the "get all their multimedia running" is that you need a higher version of ffmpeg for both the git and point releases.( -r 19778 at a min. from my vantage point

(there are some other libs that may also be of benefit with newer versions - more so with the 1.1 git than 1.0.5 or earlier.

My assumption is that a launchpad ppa will not let you use a statically linked ffmpeg (and not possible for 64 bit anyway), so then the ppa would need to also provide the ffmpeg libraires, shared and -dev's.

So if that's the case - no static ffmpeg,( and or other libs), then it would need to be done as to not break existing apps, plugins ect., or if it did then provide suitable replacements.


> I used to like installing stuff directly from source....


I think there's plus's and minus here to, though there is a lot users can learn from building sources, even if the bork it at first and there are times when building is the only way.
(or if not only then possibly the best way.

---

### Post by mc4man on 2010-02-02
> although I'm unsure what options VLC uses when encoding.
@ FO
I'm not sure either, never have used vlc for that to much, but doing a quick trancode of an .avi w/ the default setting's shows this

> Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x1:0x11 / me=hex / subme=5 / psy=1 / psy_rd=0.0:0.0 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=0 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=0 / threads=3 / sliced_threads=0 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=1 / wpredp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=5 / rc=cbr / mbtree=1 / bitrate=800 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / vbv_maxrate=800 / vbv_bufsize=6673 / ip_ratio=1.40 / aq=1:1.00

@ Andrew - 
> The new Extension manager will be a huge feature I suspect...

Looks interesting, the whole playlist/media window is also starting to take shape.

As far as 64 bit, I'd be somewhat careful installing ffmmpeg shared libs into the system, sooner or later it will be an issue if you keep updating them.

Plus if not done as a debian package set (talking about ubuntu here), then ffmpeg itself (and the headers), will be tied to the shared libs, can be a bit restrictive or a potential mess at some point if you want a new ffmpeg to use. (ffmpeg itself

---

### Post by Yellow Pasque on 2010-02-02
> **mc4man said:**
> My assumption is that a launchpad ppa will not let you use a statically linked ffmpeg.
I don't see why one couldn't put the library in a PPA and then link to it statically in the build (then users wouldn't need to download the shared libs, but of course, the resulting binary would be larger). The PPA build system defaults to using packages existing within the PPA to satisfy dependencies before going to the Ubuntu repos.

> I think there's plus's and minus here to, though there is a lot users can learn from building sources, even if the bork it at first and there are times when building is the only way (or if not only then possibly the best way.

When I said that people should use .deb pakaging, I was including checkinstall (e.g.) in that. Building from source is a great learning experience, but littering stuff in your root is a violation of Debian policy and could make life more difficult.

EDIT: I'll attempt the VLC+ffmpeg build tomorrow when I'm less drunk and more caffeinated :)

---

### Post by FakeOutdoorsman on 2010-02-02
> **mc4man said:**
> @ FO
I'm not sure either, never have used vlc for that to much, but doing a quick trancode of an .avi w/ the default setting's shows this
```
Encoding settings : ... threads=3 ...
```

With mc4man's evidence, I'm going to risk a guess that VLC does in fact use FFmpeg's threads option.  3 threads: are you using a Pentium 4?

---

### Post by andrew.46 on 2010-02-03
Hi dr_latino,

> **dr_latino999 said:**
> Is VLC installed to the same location as repo versions using your instructions? Also, are they other things we should be looking for while testing 1.1.0?

By default the installation will go to /usr/local which is pretty standard for applications that you compile yourself under Ubuntu. But you can decide yourself where you place the files. As for things to look for that would include changes to the ./configure options, new required dependencies, compilation breakages, new features, more breakages and then again more breakages :).

> EDIT: Last question, I am running it on my laptop - the script - and it crashed; my laptop is running x64 9.10. What happened to the x64 instructions above?

I did not realise when I posted the original instructions that there would be some substantial difficulty with the 64bit vlc. There are several 64bit users in this thread who I suspect can help out, for myself I like to write guides about what I know and can test personally rather than what I am guessing and inferring from other guides.

All the best,

Andrew

---

### Post by andrew.46 on 2010-02-03
Hi Temüjin,

> **Temüjin said:**
> andrew, I used to like installing stuff directly from source too, but then I came to realize it wasn't the way to go when trying to guide other users. .deb packaging exists for a reason.

I agree with you completely, I believe that if you are installing from source there should be a substantial effort made to integrate the resulting package into the systems package management system. Since I have no interest in formal debian package creation checkinstall is an ideal tool for this purpose and I have used it extensively for this purpose in many of the guides I have written. It creates easy installation and removal of packages such as vlc, allows for a backup debian installation to be created and with attention to version numbering fits reasonably neatly into the overall package management of a user's system.

I do not use it for x264 and FFmpeg in this particular guide as these libraries are not installed to the system at large and will be used only for static linking by vlc. Removal is simply a matter of deleting $HOME/vlc_build/vlcdeps. This avoids the somewhat thorny problem of different requirements and installations of these 2 important applications.

> I am interested in creating .deb packages in a PPA to make it extremely easy for users to get all their multimedia running. I'm going to start with that PPA version of VLC and see if I can add in the missing features.

It would be great to have a few choices with vlc-git PPAs and I would love to able to include a link to such a PPA in the preamble to this guide to perhaps forestall those who are not *really* ready to compile software like vlc 'by hand'.

BTW this guide is maturing a little faster than I expected, I suspect I shall be ready for submission to 'Tutorials and Tips' in a weeks time. Thanks to all for comments and advice :).

All the best,

Andrew

---

### Post by dr_latino999 on 2010-02-03
> **andrew.46 said:**
> Hi dr_latino,

I did not realise when I posted the original instructions that there would be some substantial difficulty with the 64bit vlc. There are several 64bit users in this thread who I suspect can help out, for myself I like to write guides about what I know and can test personally rather than what I am guessing and inferring from other guides.

All the best,

Andrew
Ok, that makes sense. Now I don't know about the substantial difficulty with x64, as I only modified a few items in my original script to build x64 VLC on 9.10. If someone else running x64 wants to test it out and give some feedback then we would be peachy on that aspect allowing for a comprehensive x32/x64 guide.

```
#!/bin/bash
#VLC x64, tested in Ubuntu 9.10 on 20100203
set -e
apt-get install build-essential subversion git-core checkinstall automake libtool -y
wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
--output-document=/etc/apt/sources.list.d/medibuntu.list &&
apt-get -q update &&
apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
apt-get -q update &&
apt-get install libdvdcss-dev w64codecs yasm libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev zlib1g-dev libqt4-dev libhal-dev liblua5.1-0-dev libdvdread-dev libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev -y

mkdir -p ~/svn

cd ~/svn
git clone git://git.videolan.org/x264.git x264
cd ~/svn/x264/
./configure --enable-pthread --extra-cflags='-fPIC' --extra-ldflags='-fPIC' --enable-pic --prefix=/usr/local --enable-shared
make
make install

cd ~/svn
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ~/svn/ffmpeg/
./configure --host-cflags='-fPIC' --extra-cflags='-fPIC' --arch=x86_64 --enable-libx264 --enable-libmp3lame   --enable-libfaac   --enable-libfaad --enable-libopencore-amrnb --enable-encoder=libx264 --enable-encoder=h264 --prefix=/usr/local --enable-encoder=x264 --disable-ffplay --disable-ffserver --enable-postproc --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-swscale --enable-encoder=xvid --enable-avcodec
make
make install

apt-get remove liblivemedia-dev
cd ~/svn
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvf live555-latest.tar.gz
cd live
./genMakefiles linux
make
mv -v ~/svn/live /usr/lib

cd ~/svn
git clone git://git.videolan.org/vlc.git --depth 1
cd ~/svn/vlc/
./bootstrap
sed -i_bak 's/Icon=vlc/Icon\=\/usr\/local\/share\/vlc\/vlc48x48\.png/' \
       share/applications/vlc.desktop
export PKG_CONFIG_PATH="/usr/local/lib/pkg-config"
./configure --enable-flac --prefix=/usr/local --program-suffix=-git --enable-postproc --enable-run-as-root --enable-lua --disable-notify --enable-live555 --enable-dvdread --disable-smb --enable-id3tag --enable-merge-ffmpeg --enable-swscale --enable-faad --enable-flac --enable-libmpeg2 --enable-x264 --disable-fribidi --disable-pulse --enable-alsa --enable-access_alsa --enable-ncurses --enable-qt4 --enable-mtp --disable-png
make
checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes --pkgname vlc \
    --pkgversion "1.1.0-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default
make install
make distclean
mv -v share/applications/vlc.desktop_bak share/applications/vlc.desktop
ldconfig
```I'm sure I missed something or other in there, but I was able to get it up and running tested with a .mkv 720 file. I did run into two problems, completely removing a repository version of VLC from this system, and getting the system links to work. Both the program list and Alt+F2 (VLC) return invalid file locations, but I can use VLC if I navigate to /usr/local/bin. When I enter the version command:
```
cvlc --version
```I still return this output.
```
edwin@XPS-M1530-U910:~/Desktop$ cvlc --version
VLC media player 1.0.2 Goldeneye
VLC version 1.0.2 Goldeneye
Compiled by buildd@yellow.buildd
Compiler: gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

---

### Post by andrew.46 on 2010-02-03
I have added in the required development libraries and libtiger, which had to be compiled from source, to enable kate support for vlc. A [testing url is here]("http://people.xiph.org/~oggk/elephants_dream/elephantsdream-with-subtitles.ogg").

Gratuitous screenshot attached as usual :). Added in goom as well, this is a favourite of mine.

Andrew

---

### Post by mc4man on 2010-02-03
> ...to enable kate support for vlc

Is there an advantage to using libtiger over libkate?
(figuring there probably is

Ed is an interesting film, there must be half a dozen or so different codec versions, useful for testing and comparisions, ect.

(the 1080p wmv ver. (vc1), shows pretty clearly how superior ffmpeg is to dmo for vc1

---

### Post by andrew.46 on 2010-02-04
Hi mc4man,

> **mc4man said:**
> Is there an advantage to using libtiger over libkate?


I guess the options to turn tiger rendering off and on should provide an interesting test which I will admit I have not undertaken yet due to a spell of night work :(. And there is of course the issue that these particular streams are not all that common but my aim was to illustrate a fully kitted out vlc I guess...

All the best,

Andrew

---

### Post by andrew.46 on 2010-02-04
I have submitted this guide to 'Tutorials and Tips' on February 4th 2010 so I will no longer be adding to this 'Working version'. Thank you very much to all of those who have assisted in putting this quite complex guide together. See you in 'Tutorials and Tips' in a couple of days...

All the best,

Andrew

---

### Post by SuperSonic4 on 2010-02-04
> **dr_latino999 said:**
> Ok, that makes sense. Now I don't know about the substantial difficulty with x64, as I only modified a few items in my original script to build x64 VLC on 9.10. If someone else running x64 wants to test it out and give some feedback then we would be peachy on that aspect allowing for a comprehensive x32/x64 guide.

```
#!/bin/bash
#VLC x64, tested in Ubuntu 9.10 on 20100203
set -e
apt-get install build-essential subversion git-core checkinstall automake libtool -y
wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
--output-document=/etc/apt/sources.list.d/medibuntu.list &&
apt-get -q update &&
apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
apt-get -q update &&
apt-get install libdvdcss-dev w64codecs yasm libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev zlib1g-dev libqt4-dev libhal-dev liblua5.1-0-dev libdvdread-dev libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev -y

mkdir -p ~/svn

cd ~/svn
git clone git://git.videolan.org/x264.git x264
cd ~/svn/x264/
./configure --enable-pthread --extra-cflags='-fPIC' --extra-ldflags='-fPIC' --enable-pic --prefix=/usr/local --enable-shared
make
make install

cd ~/svn
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ~/svn/ffmpeg/
./configure --host-cflags='-fPIC' --extra-cflags='-fPIC' --arch=x86_64 --enable-libx264 --enable-libmp3lame   --enable-libfaac   --enable-libfaad --enable-libopencore-amrnb --enable-encoder=libx264 --enable-encoder=h264 --prefix=/usr/local --enable-encoder=x264 --disable-ffplay --disable-ffserver --enable-postproc --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-swscale --enable-encoder=xvid --enable-avcodec
make
make install

apt-get remove liblivemedia-dev
cd ~/svn
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvf live555-latest.tar.gz
cd live
./genMakefiles linux
make
mv -v ~/svn/live /usr/lib

cd ~/svn
git clone git://git.videolan.org/vlc.git --depth 1
cd ~/svn/vlc/
./bootstrap
sed -i_bak 's/Icon=vlc/Icon\=\/usr\/local\/share\/vlc\/vlc48x48\.png/' \
       share/applications/vlc.desktop
export PKG_CONFIG_PATH="/usr/local/lib/pkg-config"
./configure --enable-flac --prefix=/usr/local --program-suffix=-git --enable-postproc --enable-run-as-root --enable-lua --disable-notify --enable-live555 --enable-dvdread --disable-smb --enable-id3tag --enable-merge-ffmpeg --enable-swscale --enable-faad --enable-flac --enable-libmpeg2 --enable-x264 --disable-fribidi --disable-pulse --enable-alsa --enable-access_alsa --enable-ncurses --enable-qt4 --enable-mtp --disable-png
make
checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes --pkgname vlc \
    --pkgversion "1.1.0-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default
make install
make distclean
mv -v share/applications/vlc.desktop_bak share/applications/vlc.desktop
ldconfig
```I'm sure I missed something or other in there, but I was able to get it up and running tested with a .mkv 720 file. I did run into two problems, completely removing a repository version of VLC from this system, and getting the system links to work. Both the program list and Alt+F2 (VLC) return invalid file locations, but I can use VLC if I navigate to /usr/local/bin. When I enter the version command:
```
cvlc --version
```I still return this output.
```
edwin@XPS-M1530-U910:~/Desktop$ cvlc --version
VLC media player 1.0.2 Goldeneye
VLC version 1.0.2 Goldeneye
Compiled by buildd@yellow.buildd
Compiler: gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

It could be because /usr/local might not be in your path, what is the output of ```
echo $PATH
```.

Alternatively using the absolute path might work ```
/usr/local/bin/cvlc
```

---

### Post by frt975 on 2010-02-05
Could you take the $'s out? They make copy-pasting a pain.
Thanks

---

### Post by andrew.46 on 2010-02-05
Hi frt,

> **frt975 said:**
> Could you take the $'s out? They make copy-pasting a pain.

I have left the prompt indicators out on those blocks of code that can be copied and pasted as a single command but retained them where multiple *individual* commands are required.

Andrew

---

### Post by andrew.46 on 2010-02-06
The 'official' guide is now published:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

See you all there :).

Andrew

---

