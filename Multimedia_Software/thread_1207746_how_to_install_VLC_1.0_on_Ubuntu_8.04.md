---
title: "how to install VLC 1.0 on Ubuntu 8.04"
date: 2009-07-08
forum: Multimedia Software
---

### Post by 4zdenek on 2009-07-08
I would like to install VLC 1.0 on my Ubuntu 8.04 but it doesn't work. I have checked 'multiverse' in Open Synaptic (System -> Administration -> Synaptic Package Manager -> Settings -> Repositories) then reloaded but there is still only version 0.86. Shouldn't I add some line in Third-Party software tab or something?

---

### Post by smuggly on 2009-07-08
i dont think 1.0 will be in until 9.04 Jaunty.I THINK not Sure......smuggly

---

### Post by wojox on 2009-07-08
Try terminal

```
sudo apt-get update
```

```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

Smuggly may be right though.

---

### Post by nahoj on 2009-07-08
To install Ubuntu we have to add the following line to our / etc / apt / sources.list 

For Ubuntu 8.04 Hardy Heron
> deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) hardy main

To add the GPG key and we do not see the warning written in a terminal: 

> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xd739676f7613768d

We update the repositories: 
> sudo aptitude update 

We update the system: 
> sudo aptitude safe-upgrade 

If you have installed the program we will be updated, but installed it with: 
> sudo aptitude install vlc 

It is also advisable to install the package vlc-plugin-esd and mozilla-plugin-vlc with: 

> sudo aptitude install vlc-plugin-esd mozilla-plugin-vlc 

Visit:

[http://ubusof.blogspot.com](http://ubusof.blogspot.com)
[http://ubusof.blogspot.com/2009/07/al-fin-vlc-100.html](http://ubusof.blogspot.com/2009/07/al-fin-vlc-100.html)

---

### Post by mc4man on 2009-07-08
If you wish vlc 1.0 on hardy your best bet atm would be to build it. Otherwise wait and see if someone decides to do a ppa build for hardy.

While there are a couple of hurdles building vlc 1.0 on hardy, doing it as a package set presents several more.
I not sure if the ppa build process would make it easier or even more difficult. (am leaning towards more difficult.

out of curiousity I built 1.0.0 last night as a debian package set on hardy, it was quite a pita but doable.

 I did it on my main hardy install which has been modified to make building and running current media apps easier and better. So in that regard I couldn't upload the set as built, you'd have difficult time meeting the install dependencies.

If no hardy ppa for 1.0.0 comes around, I'll probably try a more generic build using the min. possible versions of required libraries in a 'cleaner' build env.

Even at a min. one would need to upgrade some libraries past hardy versions, for the most part there's no problem doing so on a 'stock' install.

Ex. of install deps for just 1.0.0 vlc-nox (as current here, would need to reduce/remove some versions (mainly the ffmpeg libs, some acodecs

> Package: vlc-nox
Source: vlc
Version: 1.0.0-1~ppa3
Architecture: i386
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Installed-Size: 7080
Depends: liba52-0.7.4, libasound2 (>> 1.0.17), libass1, libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10), libavcodec52 (>= 5:0.5+svn20090604), libavformat52 (>= 5:0.5+svn20090604), libavutil50 (>= 5:0.5+svn20090604), libc6 (>= 2.5), libcaca0 (>= 0.99.beta13b-1), libcddb2, libcdio-cdda0, libcdio-paranoia0, libcdio7, libcucul0 (>= 0.99.beta13b-1), libdbus-1-3 (>= 1.1.1), libdca0, libdvbpsi5, libdvdnav4 (>= 4.1.2), libdvdread4 (>= 4.1.3), libebml0, libfaad0 (>= 2.6.1), libflac8, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1-21), libgcrypt11 (>= 1.2.2), libgnutls13 (>= 2.0.4-0), libgpg-error0 (>= 1.4), libhal1 (>= 0.5.8.1), libiso9660-5, liblircclient0, liblua5.1-0, libmad0 (>= 0.15.1b), libmatroska0, libmodplug0c2 (>= 1:0.7-4.1), libmpcdec3, libmpeg2-4, libmtp8, libncursesw5 (>= 5.6+20071006-3), libogg0 (>= 1.1.0), libpng12-0 (>= 1.2.13-4), libpostproc51 (>= 5:0.5+svn20090604), libshout3, libsmbclient (>= 3.0.2a-1), libspeex1 (>= 1.2~beta3-1), libstdc++6 (>= 4.1.1-21), libswscale0 (>= 5:0.5+svn20090604), libsysfs2, libtag1c2a (>= 1.5), libtheora0 (>= 0.0.0.alpha7.dfsg-1.1), libtwolame0, libusb-0.1-4 (>= 2:0.1.12), libv4l-0 (>= 0.5.0), libvcdinfo0 (>> 0.7.23), libvlc2 (>= 0.9.1), libvlccore2 (>= 1.0.0~rc2), libvorbis0a (>= 1.2.0), libvorbisenc2 (>= 1.1.2), libxcb-keysyms0, libxcb1, libxml2 (>= 2.6.27), zlib1g (>= 1:1.2.3.3.dfsg-1)
Conflicts: vlc (<< 0.9.8a-3)
Replaces: vlc (<< 0.9.8a-3)

---

### Post by mc4man on 2009-07-11
Bit of info on getting 1.0 on hardy.
Fairly simple to build using only hardy and hardy-medibuntu libraries, only one lib needs to be updated - libx264
(for a personal build either build a current x264 to /local (static build), or use the 2 packages from debian-multimedia-sid (libx264-67, libx264-dev. 

A ppa would need to provide them plus libs for any blue below, otherwise fairly straightforward for a package build, so maybe some will show up

A number of plugins need to be disabled, though most can be enabled using more recent libraries from either intrepid or jaunty, (will install cleanly in 8.04

Additional disabled by default options may or may not work without updated libs (realrtsp, cddax, ect


A working configure for hardy, using only hardy libraries,(except libx264) blue can be enabled w/ updated libraries, red can be hacked to some extent.

 >  ./configure --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-faad --disable-kate --enable-twolame --enable-theora [COLOR="Red"]--disable-mozilla [/COLOR]--enable-loader [COLOR="Red"]--disable-nls[/COLOR] -[COLOR="Blue"]-disable-mod --disable-pulse --disable-dvbpsi  --disable-fluidsynth --disable-libv4l2 --disable-mtp  --disable-schroedinger -disable-taglib --disable-speex[/COLOR]


A slightly better functioning vlc could be had on 8.04 by building/installing a current set of ffmpeg libraries (shared install) and  by enabling some default disabled

modules (plugins) available on a stock hardy with above configure (except libx264

> Enabled modules: a52tofloat32 a52tospdif access_alsa access_mmap access_oss access_smb adjust alphamask alsa aout_file aout_sdl atmo audio_format audioscrobbler avcodec avformat bandlimited_resampler blend blendbench bluescreen bonjour canvas cdda chain clone cmml colorthres converter_float crop croppadd dbus deinterlace dmo dolby_surround_decoder dtstofloat32 dtstospdif dvdnav dvdread dynamicoverlay equalizer erase extract faad fake fb float32_mixer folder freetype gaussianblur gestures globalhotkeys glx gnutls gradient grain hal headphone_channel_mixer hotkeys http i420_rgb_mmx i420_rgb_sse2 i420_ymga i420_ymga_mmx i420_yuy2 i420_yuy2_mmx i420_yuy2_sse2 i422_i420 i422_yuy2 i422_yuy2_mmx i422_yuy2_sse2 inhibit invert libass libmpeg2 linear_resampler live555 logo magnify marq memcpy3dn memcpymmx memcpymmxext mkv mosaic motion motionblur motiondetect mpc mpgatofixed32 mux_ogg noise normvol notify ogg opengl opengl osd_parser osdmenu oss panoramix param_eq png podcast postproc probe_hal psychedelic puzzle qt4 rc remoteosd ripple rotate rss rv32 sap scale scaletempo scene screensaver sdl_image sharpen shout showintf signals simple_channel_mixer skins2 spatializer spdif_mixer stream_out_raop swscale telepathy telnet telx theora transform twolame unzip v4l2 vcd visual vmem vorbis vout_sdl wall wave x11 x11_screen x264 xml xvideo yuv yuvp yuy2_i420 yuy2_i422 zip 



---

