---
title: "compiling vlc 2.2.6 errors"
date: 2017-08-01
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2017-08-01
Ubuntu 16.04. Tried to compile vlc 2.2.6 from source and got this error running the configure script
```
configure: error: libavutil versions 55 and later are not supported.

```
I installed libavutil from [https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media)

```
libavutil      55. 58.100 / 55. 58.100
  libavcodec     57. 89.100 / 57. 89.100
  libavformat    57. 71.100 / 57. 71.100
  libavdevice    57.  6.100 / 57.  6.100
  libavfilter     6. 82.100 /  6. 82.100
  libavresample   3.  5.  0 /  3.  5.  0
  libswscale      4.  6.100 /  4.  6.100
  libswresample   2.  7.100 /  2.  7.100
  libpostproc    54.  5.100 / 54.  5.100

```

Previously installed vlc-2.2.5 still works with no issue (also compiled)

Thanks

---

### Post by mc4man on 2017-08-01
Yeah, that's not going to work. You'd need to only use older ffmpeg dev's. 
Or statically link an older ffmpeg in your build. For example look at what's done in 17.04 & 17.10 ubuntu packages
[https://packages.ubuntu.com/artful/vlc](https://packages.ubuntu.com/artful/vlc)
Notice that there is no dep on ffmpeg shared libs, they provide & use an older ffmpeg statically linked in build (pretty uncommon for Debian/Ubuntu.

/Thoughts behind going shared in that ppa.
It's been 15+ months so I'd rather start looking at new source builds that could benefit from newer FFmpeg shared libs. As appropriate they would show up in the ppa. 
Atm there is only 1 - Audacious. It gains some benefit, most notable wmal support which is broken with ffmpeg-2.8.x Also I've given aud ability to play mpc8 whereas with default ffmpeg libs it can only play mpc7 

The ffmpeg shared there (ppa) will advance per FFmpeg release so likely ffmpeg-3.4.x will be coming shortly. At that point will probably add a release version only mpv that uses the shared ffmpeg libs. Git master will always be in other ppa & use latest git ffmpeg, ect.

I do provide a git master ffmpeg (static) elsewhere but as it predated 16.04 release I decided to let it co-exist with 16.04's ffmpeg package.There was a little push back about altering the binaries's names (via links, not in source) but that's the way I decided to go...
[https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test)

---

### Post by monkeybrain20122 on 2017-08-04
Hi, Thanks for the reply. I have compiled a local version of ffmpeg-2.8.12 in my $HOME. This is the version vlc.2.2.6 is linked to in Artful, but I am not able to make the configure script see it. I set my environment variables thus

```
export CPPFLAGS="-I$HOME/opt/ffmpeg/include"
export LDFLAGS="-L$HOME/opt/ffmpeg/lib"
export PKG_CONFIG_PATH="$HOME/opt/ffmeg/lib/pkgconfig"
```

But I still get the same error even though the libavutil version is 5.4 for this copy of ffmpeg.

Please advise. Thanks.

---

### Post by mc4man on 2017-08-04
Not sure if your exports are correct to ffmpeg install, maybe see below method..
Or just remove the currently installed ffmpeg dev files, then see if vlc uses the exports. 

Just to see tried here with some commands modified from [Andrew's guide]("https://ubuntuforums.org/showthread.php?t=2141949"). Had no issue with vlc using the local headers & includes 
(though I still think one shouldn't build vlc with packaged ffmpeg headers/includes installed if not using those ones..

That would then expose your next issue - this bug
[https://bugs.launchpad.net/ubuntu/+source/qtbase-opensource-src/+bug/1536843](https://bugs.launchpad.net/ubuntu/+source/qtbase-opensource-src/+bug/1536843)

Easy to fix - 
You open configure.ac & comment or remove the whole check, see screenshot, removed is highlighted. 
Then at the vlc source prompt run
```
./bootstrap
```
This will create a new configure file without the nonsense check.

In a nutshell - 
Removed all vlc packages first (generally best not to build with vlc installed (the ubuntu packaged version
I created a folder vlc_build & extracted both ffmpeg & vlc sources inside.
cd'd to the ffmpeg folder & ran
```
if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
            $ARCHOPTS \
            --enable-gpl \
            --enable-version3 \
            --enable-nonfree \
            --enable-libmp3lame \
            --enable-libopencore-amrnb \
            --enable-libopencore-amrwb \
            --enable-libvpx \
            --enable-libfdk-aac \
            --enable-libx265 \
            --disable-programs \
            --disable-doc \
            --disable-filters \
            --disable-avdevice \
            --disable-devices \
            --disable-avfilter \
            --disable-avresample && \
make -j 2 && make install-libs install-headers && make distclean
```
Once completed cd'd to the vlc folder, edited configure.ac & ran bootstrap
When done ran this
```
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local && make -j 2 && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING INSTALL NEWS README THANKS doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
--pkgversion "2.6.6" --fstrans=no --deldesc=yes --delspec=yes --default \
&& make distclean && sudo ldconfig
```

built, installed & runs ok... (some likely unimportant qt warnings if run from terminal.
Note andrews method does create a root owned .deb, no real matter.
Also note: decided to put 2.6 in that ppa, so if deciding to build locally with checkinstall then up the version slightly if keeping ppa, maybe --pkgversion "2.6.6.1" or whatever...

---

### Post by monkeybrain20122 on 2017-08-05
Hi, just found out you have added vlc to the xerius media ppa.  Just updated it and problem solved. Thanks a lot!

---

### Post by mc4man on 2017-08-05
> **monkeybrain20122 said:**
> Hi, just found out you have added vlc to the xerius media ppa.  Just updated it and problem solved. Thanks a lot!
Went with the embedded method so FFmpeg's is built in. 
There will be an update tonight, you can ignore unless you use vlc to autoplay audio cd's. 
(- I had added the extra desktop file, (vlc-cd.desktop) but forgot to add the binary (script) it needs to autoplay from any attached cd/dvd drive

---

