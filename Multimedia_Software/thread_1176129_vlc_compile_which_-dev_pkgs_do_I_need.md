---
title: "vlc compile: which -dev pkgs do I need?"
date: 2009-06-02
forum: Multimedia Software
---

### Post by logos34 on 2009-06-02
version 0.9.9a, compiling on 64-bit 8.04 heron

Looks go for launch, except for these outstanding libs:

> checking for LIBV4L2... no
[COLOR="Red"]configure: WARNING: LibV4L2 support disabled because libv4l2 development headers were not found[/COLOR]
checking for new linux/videodev2.h... yes

checking for mpcdec/mpcdec.h... yes
[COLOR="Red"]configure: WARNING: only static linking is available, you must provide a gme-tree[/COLOR]

checking for CSRI... no
[COLOR="Red"]configure: WARNING: CSRI helper library not found
checking for LIBASS... no
configure: WARNING: LIBASS library not found[/COLOR]

checking for SVG... no
[COLOR="Red"]configure: WARNING: SVG library not found[/COLOR]
checking cascade/graphics/CascadeScreen.h usability... no
checking cascade/graphics/CascadeScreen.h presence... no
checking for cascade/graphics/CascadeScreen.h... no
[COLOR="Red"]configure: WARNING: Not building Roku HD1000 compatible video output
checking cascade/graphics/CascadeBitmap.h usability... no
checking cascade/graphics/CascadeBitmap.h presence... no
checking for cascade/graphics/CascadeBitmap.h... no
configure: WARNING: Not building Roku HD1000 compatible video output[/COLOR]

I can't figure out what development libs I need...Checked all the obvious ones...  Ideas anyone? Can I point it to ffmpeg codecs for 'mpcdec,h'? Where?

Here's my ./configure:

> $ auto-apt run ./configure --with-live555-tree=/usr/lib/live --enable-optimize-memory --enable-dc1394 --enable-dv --enable-dvdread --enable-v4l --enable-cddax --enable-pvr --enable-gnomevfs --enable-vcdx --enable-faad --enable-twolame --enable-real --enable-realrtsp --enable-flac --enable-theora --enable-dirac --enable-csri --enable-libass --enable-asademux --enable-xvmc --enable-svg --enable-snapshot --enable-mga --enable-svgalib --enable-directfb --enable-ggi --enable-aa --enable-caca --enable-esd --enable-jack --enable-cyberlink --enable-pda --enable-xosd --enable-fbosd --enable-mozilla

...

Enabled modules: a52 a52tofloat32 a52tospdif aa access_dv access_filter_bandwidth access_filter_dump access_filter_record access_filter_timeshift access_gnomevfs access_jack access_mmap access_realrtsp access_smb adjust adpcm alphamask alsa aout_file aout_sdl araw asademux asf atmo audio_format audioscrobbler avcodec avformat avi bandlimited_resampler blend blendbench bluescreen bonjour caca canvas cc cdda cddax cdg chain cinepak clone cmml colorthres converter_fixed converter_float crop croppadd cvdsub dbus dc1394 deinterlace dirac directfb dolby_surround_decoder dts dtstospdif dummy dvb dvb dvbsub dvdnav dvdread dynamicoverlay equalizer erase esd export extract faad fake fb fbosd flac float32_mixer fluidsynth folder freetype gaussianblur gestures ggi glx gnutls gradient grain grey_yuv gtk2_main h264 hal headphone_channel_mixer hotkeys http i420_rgb i420_rgb_mmx i420_rgb_sse2 i420_ymga i420_ymga_mmx i420_yuy2 i420_yuy2_mmx i420_yuy2_sse2 i422_i420 i422_yuy2 i422_yuy2_mmx i422_yuy2_sse2 id3tag image inhibit invert jack libmpeg2 linear_resampler live555 logger logo lpcm m4a m4v magnify marq memcpy memcpy3dn memcpymmx memcpymmxext mga mkv mod mono mosaic motion motionblur motiondetect mozilla mp4 mpc mpeg_audio mpga mpgatofixed32 mpgv mux_ogg mux_ts noise normvol notify nsc ogg opengl opengl osd_parser osdmenu oss panoramix param_eq pda playlist png podcast postproc probe_hal ps psychedelic pulse puzzle pvr qt4 rawvideo rc realaudio realvideo remoteosd ripple rotate rss rv32 sap scale scaletempo schroedinger screen screensaver sdl_image sharpen shout showintf signals simple_channel_mixer skins2 snapshot spatializer spdif_mixer speex spudec stats subsdec subsusf svcdsub svgalib swscale t140 taglib telepathy telnet telx theora transform trivial_channel_mixer trivial_mixer trivial_resampler ts twolame ugly_resampler v4l v4l2 vcd vcdx visual vmem vorbis vout_sdl wall wave x11 x264 xml xosd xtag xvideo yuy2_i420 yuy2_i422 zvbi 


libvlc configuration
--------------------
version               : 0.9.9a
system                : linux
architecture          : x86_64 mmx sse sse2
build flavour         : devel 
vlc aliases           : cvlc rvlc svlc qvlc
plugins/bindings      : mozilla

You can tune the compiler flags in vlc-config.
To build vlc and its plugins, type `./compile' or `make'.


---

### Post by andrew.46 on 2009-06-02
Hi Logos,

Still waiting for mc4man to write up a compiling guide for vlc in 'Tutorials and Tips' :-). I compile [vlc under slackware]("http://www.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild") and for this the following *external *packages are used:

```

$ find vlc_alien/build \( -name '*.bz2' -o -name '*.gz' \) -exec du -h '{}' \;
912K	vlc_alien/build/fluidsynth-1.0.9.tar.gz
840K	vlc_alien/build/liboil-0.3.16.tar.gz
744K	vlc_alien/build/goom-2k4-0-src.tar.gz
1.1M	vlc_alien/build/libupnp-1.6.6.tar.bz2
252K	vlc_alien/build/libmpcdec-1.2.6.tar.bz2
392K	vlc_alien/build/libdca-0.0.5.tar.bz2
864K	vlc_alien/build/schroedinger-1.0.7.tar.gz
284K	vlc_alien/build/libass-0.9.6.tar.bz2
992K	vlc_alien/build/vcdimager-0.7.23.tar.gz
392K	vlc_alien/build/libdc1394-1.2.2.tar.gz
1.9M	vlc_alien/build/libtheora-1.0.tar.gz
296K	vlc_alien/build/libdvbpsi5-0.1.6.tar.bz2
64K	vlc_alien/build/libebml-0.7.8.tar.bz2
3.1M	vlc_alien/build/ggi-2.2.2-bundle.src.tar.bz2
396K	vlc_alien/build/libraw1394-1.3.0.tar.gz
520K	vlc_alien/build/libmpeg2-0.5.1.tar.gz
668K	vlc_alien/build/faac-1.28.tar.gz
100K	vlc_alien/build/libdvdread-4.1.3.tar.bz2
1.1M	vlc_alien/build/speex-1.2rc1.tar.gz
2.7M	vlc_alien/build/ffmpeg-0.5.tar.bz2
352K	vlc_alien/build/libavc1394-0.5.3.tar.gz
108M	vlc_alien/build/qt-x11-opensource-src-4.4.3.tar.gz
240K	vlc_alien/build/a52dec-0.7.4.tar.gz
96K	vlc_alien/build/libmatroska-0.8.1.tar.bz2
2.2M	vlc_alien/build/libcdio-0.81.tar.gz
18M	vlc_alien/build/vlc-1.0.0-rc2.tar.bz2
2.4M	vlc_alien/build/x264-snapshot-20090526-2245.tar.bz2
568K	vlc_alien/build/libdv-1.0.0.tar.gz
352K	vlc_alien/build/libcddb-1.3.2.tar.bz2
116K	vlc_alien/build/libdvdnav-4.1.3.tar.bz2
224K	vlc_alien/build/amrwb-7.0.0.3.tar.bz2
228K	vlc_alien/build/amrnb-7.0.0.2.tar.bz2
204K	vlc_alien/build/libdaap-0.0.4.tar.bz2
244K	vlc_alien/build/libopendaap-0.4.0.tar.bz2
472K	vlc_alien/build/libshout-2.2.2.tar.gz
452K	vlc_alien/build/live555-latest.tar.gz
476K	vlc_alien/build/twolame-0.3.12.tar.gz
1.3M	vlc_alien/build/lame-398-2.tar.gz

```

and I guess at a bare minimum you would require all of the above but I will admit have not tried to compile this under Ubuntu...

Andrew

---

### Post by logos34 on 2009-06-02
thanks.  Don't get it, though, because I can't even find anything with 'csri'...I can't find any -dev libs for v4l(2), yet vlc is apparently enabling the modules...While for svg, I have libsvg-dev and libsvga1-dev installed, but that's not it...hmmm.  hopefully mc4man can answer this

probably should just leave well enough alone (vers. 0.8.6), but I have the fix-it-till-it-breaks urge...

---

### Post by ad_267 on 2009-06-02
Have you tried "sudo apt-get build-dep vlc"?

---

### Post by mc4man on 2009-06-02
A few quick points

Your ffmpeg and x264 libs and -devs should be good,
 
 Temporally adding this repo as a source and running  an apt-get build-dep would prove useful. ( then remove (unless you want to use  his build instead

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

> 
configure: WARNING: LibV4L2 support disabled because libv4l2 development headers were not found


D.ck. in synaptic, otherwise upgrade to intrepid versions. (Always remove existing =dev before upgrading with Gdebi, install libv41 also

> checking for mpcdec/mpcdec.h... yes
configure: WARNING: only static linking is available, you must provide a gme-tree

Those 2 lines aren't related at all.




> onfigure: WARNING: SVG library not found

Probably the build-deps will resolve, if not search svg in synaptic, 2 likely suspects and the qt one

> checking cascade/graphics/CascadeScreen.h usability... no
checking cascade/graphics/CascadeScreen.h presence... no
checking for cascade/graphics/CascadeScreen.h... no
configure: WARNING: Not building Roku HD1000 compatible video output
checking cascade/graphics/CascadeBitmap.h usability... no
checking cascade/graphics/CascadeBitmap.h presence... no
checking for cascade/graphics/CascadeBitmap.h... no
configure: WARNING: Not building Roku HD1000 compatible video 
output
Ignore the above

From my .dsc ( versions are min. and generally outdated
> Vcs-Bzr: [https://code.launchpad.net/~motumedia/vlc/ubuntu](https://code.launchpad.net/~motumedia/vlc/ubuntu)
Build-Depends: debhelper (>= 6), dh-buildinfo, gettext, liba52-0.7.4-dev, libaa1-dev, libarts1-dev (>= 1.4.2), libasound2-dev (>= 0.9.0beta10a) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libass-dev, libaudiofile-dev, libavahi-client-dev, libavc1394-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libavcodec-dev (>= 0.cvs20060823), libavformat-dev (>= 0.cvs20060823), libcaca-dev (>= 0.99.beta4), libcdio-dev, libdc1394-13-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libdca-dev, libdvbpsi4-dev, libdvdnav-dev, libdvdread-dev (>= 0.9.5), libesd0-dev, libfaad-dev, libflac-dev (>= 1.1.2-3), libfreetype6-dev, libfribidi-dev, libggi2-dev, libgl1-mesa-dev, libglib2.0-0, libgnutls-dev (>= 1.2.8), libhal-dev (>= 0.5.5.1-3) [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libid3tag0-dev, libidl0, libimlib2-dev, libjack-dev, liblircclient-dev, liblivemedia-dev (>= 2008.07.24), liblua5.1-0-dev, libmad0-dev, libmatroska-dev (>= 0.8.0), libmodplug-dev, libmpcdec-dev, libmpeg2-4-dev, libncursesw5-dev, libnotify-dev, libogg-dev, libpng12-dev, libpostproc-dev (>= 0.cvs20060823), libpulse-dev, libqt4-dev, libraw1394-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386], libschroedinger-dev, libsdl-image1.2-dev, libsdl1.2-dev (>= 1.2.7+1.2.8cvs20041007-5.3), libshout3-dev, libsmbclient-dev, libspeex-dev, libsvga1-dev [amd64 i386], libswscale-dev, libsysfs-dev, libtag1-dev, libtar-dev, libtheora-dev, libtwolame-dev (>= 0.3.8), libvcdinfo-dev, libvorbis-dev, libx11-dev, libx264-dev, libxext-dev, libxml2-dev, libxpm-dev, libxt-dev, libxul-dev, libxv-dev, libxxf86dga-dev, libxxf86vm-dev, nasm, pkg-config, qt4-dev-tools, quilt, yasm [amd64 kfreebsd-amd64], zlib1g-dev


Some are package building tools


Your configure seems a little bloated, no need to enable things that are already by default.
Just enable what you really want//need that's not already by default, and disable only default enabled that you don't want or in a few possible cases prove problematic, at least withthe current hardy lib, -dev versions.

Many A/v libs can be bumped up to 8.10 or 9.04 ver's with no issues, some would be not advised without add. work. 

Hardy has been somewhat 'left in the dust' A/v wise, so above is worth checking when needed.

If you get a speex related build error, then disable in configure (and remove the -dev) or try upgaded versions.

My recent configure of 0.9.9a on hardy 32 bit (ignore blue, red wwith adrews live guide in mplayer thread

> ./configure  --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-caca --enable-faad --disable-kate --enable-twolame --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --enable-cddax --disable-fluidsynth -[COLOR="Red"]-with-live555-tree=/usr/lib/live[/COLOR] [COLOR="Blue"]--enable-loader[/COLOR] --with-tuning=native

You may find it quicker, when setting up the build env.,to just resume a failed make if possible, (after a certain point, if it fails, address what's missing and typing just make will pick up a bit before the fail.

When changing a config, run make distclean  and start over. Once your good, you could run the build again if desired and future builds should go smoothly.

Edit: get an updated yasm one way or the other
sometimes I --enable-static, no particular reason, makes for a slightly larger install, build folder.

---

### Post by logos34 on 2009-06-02
> **ad_267 said:**
> Have you tried "sudo apt-get build-dep vlc"?

yeah, been there, done that....That's usually the first thing I do.  I'm loaded to the gills with dev pkgs.  My / partition is really starting to bulge at the seams...Need a new hdd!

---

### Post by logos34 on 2009-06-02
> **mc4man said:**
> A few quick points


ok, thanks for the info...let me digest you post...But I've done a lot of that already...I checked the ./configure --help and tried to only enable stuff that wasn't already by default...Let me check each of your points

---

### Post by logos34 on 2009-06-02
> **mc4man said:**
> 
 Temporally adding this repo as a source and running  an apt-get build-dep would prove useful. ( then remove (unless you want to use  his build instead

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)


ok, that helped (i.e. hardy...jaunty says libass unsatisfiable deps)...Pulled up a few more pkgs:

libass-dev libass1 libdca-dev libdca0 libncursesw5-dev libshout3-dev libsvga1-dev libswscale-dev libx264-65
libx264-dev libxxf86dga-dev libxxf86vm-dev qt4-dev-tools

lemme install and try again.  still going through your post

---

### Post by mc4man on 2009-06-02
To remind something:
While it was possible to keep the 0.8.6.x vlc and run the 0.9.9a from build, I definitely had 2nd thoughts about that.
There was a point for a short while on my previous hardy install that something seemed off. You can try, worst  case just remove, uninstall both completely and do a build.

( My new hardy build wouldn't allow 0.8.6 so a moot point anyway, am running the rc and  recent 1.1 git, but will return to 0.9.9a shortly

Do make sure no repo -devs are installed from the** hardy** repo in regards to ffmpeg

> libx264-65
libx264-dev
If you built a new x264 to /usr/local recently then these are not needed, remove the -dev at a min.

Any issues then add to config
```
--with-x264-tree=/usr/include 
```

I get around the whole libx264 thing (build-dep vs. manual local install   by just going to debian-multimedia and installed the latest 67+  ver. (libx264 and it's matching -dev as a package to /usr

You can have multiple libx264 versions installed, but only one libx264-dev at a time. Match the -dev to the source or use highest to start

If you migrate to the d-m x264 then  remove the /local build.

---

### Post by logos34 on 2009-06-02
> **mc4man said:**
> 
Do make sure no repo -devs are installed from the** hardy** repo in regards to ffmpeg

I'llbe sure to check that...

alright, maybe I'll play it safe, uninstall 0.8.6 first before running 99 out of make folder...  

Some headway.  But still these:

> checking for LIBV4L2... no
configure: WARNING: LibV4L2 support disabled because libv4l2 development headers were not found

checking for CSRI... no
configure: WARNING: CSRI helper library not found

> auto-apt run ./configure [COLOR="Blue"]--disable-zvbi --disable-fluidsynth --with-tuning=native --enable-mozilla --with-mozilla-pkg=libxul-plugi[/COLOR]n --with-live555-tree=/usr/lib/live --enable-release --enable-switcher --enable-optimize-memory --enable-dc1394 --enable-dv --enable-dvdread --enable-v4l --enable-cddax --enable-pvr --enable-gnomevfs --enable-vcdx --enable-faad --enable-twolame --enable-real --enable-realrtsp --enable-flac --enable-theora --enable-dirac --enable-csri --enable-libass --enable-asademux --enable-xvmc --enable-svg --enable-snapshot --enable-mga --enable-svgalib --enable-directfb --enable-ggi --enable-aa --enable-caca --enable-esd --enable-jack --enable-cyberlink --enable-pda --enable-xosd --enable-fbosd

---

### Post by mc4man on 2009-06-02
> checking for LIBV4L2... no

I remember that happening, doesn't any longer, check in synaptic as mentioned, I have libv4l-0 0.5.8.1 and it's -dev (probably from jaunty though I may have added for the 1.x versions

check your modules after config run

gotta go...

[COLOR="Blue"]Edit;[/COLOR]
> CSRI

Don't even know what that is offhand

A small thought on that
Not everything can be enabled, nor should it. The individualizing of a build should just reflect what you can and will use.

The repo's and ppa's for various reasons don't enable some truly useful options and tend to enable everything thing else possible.

Some config. and or build errors, fails can be resolved by simply removing something you'll never use anyway

---

### Post by logos34 on 2009-06-02
I have the svn versions installed:

> Package: libx264-65
...
Version: 1:0.svn20081230-1~hardy1
Depends: libc6 (>= 2.7), libx11-6
Filename: pool/main/x/x264/libx264-65_0.svn20081230-1~hardy1_amd64.deb

> Package: libx264-dev
...
Version: 1:0.svn20071224-0.0ubuntu1
Depends: libx264-57 (= 1:0.svn20071224-0.0ubuntu1)
Filename: pool/multiverse/x/x264/libx264-dev_0.svn20071224-0.0ubuntu1_amd64.deb

From---> "[Install FFmpeg and x264 on Ubuntu Hardy Heron 8.04 LTS]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360")"

(build of **yasm** too from that guide)

Maybe I should lock all three?


Is that ok?

can't find anyhing remotely like:

libv4l-0 0.5.8.1

---

### Post by mc4man on 2009-06-02
> can't find anyhing remotely like:

libv4l-0 0.5.8.1 

[http://packages.ubuntu.com/jaunty/libv4l-0](http://packages.ubuntu.com/jaunty/libv4l-0)

(probably did for 1.x, has no deps' to speak of, try it and -dev or 8.10 and -dev

> (build of yasm too from that guide)

Any yasm better than hardy's will do, the one you have is good

> Package: libx264-dev
...
Version: 1:0.svn20071224-0.0ubuntu1
Depends: libx264-57 (= 1:0.svn20071224-0.0ubuntu1)

remove the -dev, leave the libx264-57, other apps, libs depend on it. As mentioned you can have multiple libx264-xx installed, the current libx264-dev should match the libx264-xx that's needed for your source.

In all likelihood libx264-65 would be ok for vlc 0.9.9a

---

### Post by logos34 on 2009-06-02
cool, i'll try it

---

### Post by mc4man on 2009-06-02
If you do add another hdd, here's a possibility, mainly aimed a multimedia install.
For a Lts hardy came at bad time A/v wise, but on the other hand for some hardware is much more suitable than 8.10 and particularly 9.04 which I think has some issue with the kernel, xorg and compiz

Any way while you can 'update' hardy thru builds to /usr/local and whatnot i decided to just update it from the start in a package method to /usr and not be bothered keeping track of local builds, updating them, ect.

For me it's worked out well and makes building current apps much easier.

The exception is mplayer which can be built on almost any install due to it's more sane approach to just about everything including ffmpeg

Here's the list that brought hardy 'up to date' If you did a 32 bit install to test, I have them all done, some can't be publicly redist., but privately can.

> ffmpeg preinstall
libdc1394-13_1.1.0-5ubuntu1_i386.deb
libfaac0_1.28-0.1_i386.deb
libfaad0_2.6.1-2ubuntu0.1_i386.deb
libgsm1_1.0.12-1_i386.deb
libschroedinger-1.0-0_1.0.1-2_i386.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb
libasound2_1.0.17a-0ubuntu4_i386.deb
libmp3lame0_3.98-0.0_i386.deb
libspeex1_1.2~beta4-2_i386.deb
libx264-67_0.svn20090413-0.0_i386.deb
libamrnb3_7.0.0.1-0.0+medibuntu1_i386.deb
libamrwb3_7.0.0.2-0.1+medibuntu1_i386.deb

built new source (unstripped
ffmpeg_0.svn20090303-1ubuntu6_i386.deb
ffmpeg-dbg_0.svn20090303-1ubuntu6_i386.deb
ffmpeg-doc_0.svn20090303-1ubuntu6_all.deb
libavcodec52_0.svn20090303-1ubuntu6_i386.deb
libavcodec-dev_0.svn20090303-1ubuntu6_i386.deb
libavdevice52_0.svn20090303-1ubuntu6_i386.deb
libavdevice-dev_0.svn20090303-1ubuntu6_i386.deb
libavfilter0_0.svn20090303-1ubuntu6_i386.deb
libavfilter-dev_0.svn20090303-1ubuntu6_i386.deb
libavformat52_0.svn20090303-1ubuntu6_i386.deb
libavformat-dev_0.svn20090303-1ubuntu6_i386.deb
libavutil49_0.svn20090303-1ubuntu6_i386.deb
libavutil-dev_0.svn20090303-1ubuntu6_i386.deb
libpostproc51_0.svn20090303-1ubuntu6_i386.deb
libpostproc-dev_0.svn20090303-1ubuntu6_i386.deb
libswscale0_0.svn20090303-1ubuntu6_i386.deb
libswscale-dev_0.svn20090303-1ubuntu6_i386.deb

built new source
libxine1_1.1.16.3-0ubuntu1_i386.deb
libxine1-bin_1.1.16.3-0ubuntu1_i386.deb
libxine1-console_1.1.16.3-0ubuntu1_i386.deb
libxine1-x_1.1.16.3-0ubuntu1_i386.deb
libxine1-dbg_1.1.16.3-0ubuntu1_i386.deb
libxine1-doc_1.1.16.3-0ubuntu1_all.deb
libxine1-ffmpeg_1.1.16.3-0ubuntu1_i386.deb
libxine1-gnome_1.1.16.3-0ubuntu1_i386.deb
libxine1-misc-plugins_1.1.16.3-0ubuntu1_i386.deb
libxine1-plugins_1.1.16.3-0ubuntu1_all.deb
libxine-dev_1.1.16.3-0ubuntu1_i386.deb
libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb

rebuilt off new libs
gstreamer0.10-plugins-ugly-multiverse_0.10.7-2_i386.deb
gstreamer0.10-plugins-ugly-multiverse-dbg_0.10.7-2_i386.deb
gstreamer0.10-plugins-ugly_0.10.7-3ubuntu2_i386.deb
gstreamer0.10-plugins-ugly-dbg_0.10.7-3ubuntu2_i386.deb
gstreamer0.10-plugins-ugly-doc_0.10.7-3ubuntu2_all.deb
gstreamer0.10-ffmpeg_0.10.3-7_i386.deb
gstreamer0.10-plugins-bad-multiverse_0.10.6-2_i386.deb
gstreamer0.10-plugins-bad-multiverse-dbg_0.10.6-2_i386.deb

rebuilt 
libmjpegtools0c2a_1.8.0-0.2ubuntu6_i386.deb
libmjpegtools-dev_1.8.0-0.2ubuntu6_i386.deb
libquicktime1_1.0.0+debian-6_i386.deb
libquicktime-dev_1.0.0+debian-6_i386.deb
mjpegtools_1.8.0-0.2ubuntu6_i386.deb
quicktime-utils_1.0.0+debian-6_i386.deb
quicktime-x11utils_1.0.0+debian-6_i386.deb


Other deps
liba52-0.7.4_0.7.4-11ubuntu1_i386.deb
libiso9660-5_0.78.2+dfsg1-2ubuntu1_i386.deb
libmad0_0.15.1b-2.1ubuntu1_i386.deb
libmodplug0c2_1%3a0.7-7_i386.deb
libmpcdec3_1.2.2-1build1_i386.deb
libvcdinfo0_0.7.23-4ubuntu1_i386.deb
libxcb-shape0_1.1-1ubuntu1_i386.deb
libxcb-shm0_1.1-1ubuntu1_i386.deb
libxcb-xv0_1.1-1ubuntu1_i386.deb


There are several additions and a couple of further upgrades for vlc 1.x and in general, plus add. updated -devs where applicable

---

### Post by logos34 on 2009-06-02
thanks for offer of 32-bit libs, but unfortunately I won't be getting an extra hdd anytime soon, and my x64 installation has consumed my drive.  No room even for another partition.

I'll try to pare down the options in ./configure, maybe the errors for libvl4 will go away...otherwise I don't know what to do because the jaunty pkg you suggested installed ok, but didn't help.

About the x264 stuff I got through fakeoutdoorsman's guide: I think they may have gotten updated when I added a ppa repo source (can't remember which, though)...also svn...is that ok?  should I lock those versions in synaptic?

---

### Post by logos34 on 2009-06-02
I give up.

using the following stripped-down ./configure:

> auto-apt run ./configure --disable-zvbi --disable-fluidsynth --with-tuning=native --enable-mozilla --with-live555-tree=/usr/lib/live --enable-release --enable-switcher --enable-shout --enable-optimize-memory --enable-dc1394 --enable-dv --enable-dvdread --enable-v4l --enable-cddax --enable-vcdx --enable-faad --enable-twolame --enable-real --enable-realrtsp --enable-flac --enable-theora --enable-dirac --enable-libass --enable-snapshot --enable-directfb --enable-ggi --enable-aa --enable-caca --enable-esd --enable-jack --disable-atmo --disable-gme --disable-libsysfs --disable-kate --disable-hd1000v --disable-visual --disable-remoteosd

I get this make error:
> 
/libavcodec_plugin.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `aasc_decoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[6]: *** [libavcodec_plugin.la] Error 1
make[6]: Leaving directory `/home/logos34/vlc-0.9.9a/modules/codec/avcodec'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/logos34/vlc-0.9.9a/modules/codec/avcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/logos34/vlc-0.9.9a/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/logos34/vlc-0.9.9a/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/logos34/vlc-0.9.9a/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/logos34/vlc-0.9.9a'
make: *** [all] Error 2

Can't get support for libv4l2 either, it seems

---

### Post by mc4man on 2009-06-02
> maybe the errors for libvl4 will go away

If it's during the configure it's not an error, just telling you yhe module won't be built.

Went back into a regular hardy install that builds vlc 0.9.9a fine. There is no libv4l package for hardy and no -dev package (there are a few that mention, but they're irrelevant.

Vlc builds fine without v4l, not sure i'd use in anyway in any capacity

A quick configure shows

> checking for alsa/asoundlib.h... yes
checking for main in -lasound... yes
checking linux/videodev2.h usability... yes
checking linux/videodev2.h presence... yes
checking for linux/videodev2.h... yes
[COLOR="Blue"]checking for LIBV4L2... no[/COLOR]
configure: WARNING: LibV4L2 [COLOR="Blue"]support disabled[/COLOR] because libv4l2 development headers were not found
checking for LIBCDIO... yes
checking for VCDINFO... yes
checking for LIBCDIO_PARANOIA... yes
checking for LIBCDDB... yes
checking for LIBCDIO... yes
checking for cdrom_msf0 in linux/cdrom.h... yes



Now I add libv4l-0 and the **-dev** (took from intrepid-updates this time) and now
[QUOTE
checking for alsa/asoundlib.h... yes
checking for main in -lasound... yes
checking linux/videodev2.h usability... yes
checking linux/videodev2.h presence... yes
checking for linux/videodev2.h... yes
[COLOR="Blue"]checking for LIBV4L2... yes[/COLOR]
checking for LIBCDIO... yes
checking for VCDINFO... yes
checking for LIBCDIO_PARANOIA... yes
checking for LIBCDDB... yes
checking for LIBCDIO... yes
checking for cdrom_msf0 in linux/cdrom.h... yes
[/QUOTE]

You should be able to enable, though I'm not to sure of it's value in being so.

As far as x264 don't worry, just make sure the dev matches the libx264-xx that's good for vlv 0.9  (at least 64

If you installed a recent x264 to /usr/local then  that will be used. (preempts packages in /usr
Personally I don't like competing -dev's in usr/ and /usr/local. but it won't matter if you do

I'd go ahead and build and see what shakes out


If you get an error it's usually verbose, if not post it and a dozen or so preceding lines

---

### Post by logos34 on 2009-06-02
> **mc4man said:**
> 
Vlc builds fine without v4l, not sure i'd use in anyway in any capacity

one less thing to worry about then
> 

Now I add libv4l-0 and the **-dev** (took from intrepid-updates this time) and now

can't do it on mine--deps unsatisfiable

> As far as x264 don't worry, just make sure the dev matches the libx264-xx that's good for vlv 0.9  (at least 64

alright.  I'll try a build tomorrow.

BTW--tried the 0.9.9a version in the ppa repo, but the gui has bugs ('preferences' won't open, 2 'settings').

---

### Post by mc4man on 2009-06-02
Do remove all the vlc packages from that ppa before building (just search vlc in synaptic and anything that has vlc in the name with a 0.9.9....ver.

> can't do it on mine--deps unsatisfiable

While it doesn't matter too much, that does surprise me, the only dep of libv4l-0 is "Depends: libc6 (>=2.4) and the only dep of the dev is libv4l-0 itself

---

### Post by logos34 on 2009-06-02
sorry, correction--says: "Error: a later version is already installed"

libv4l-0_0.5.0-3~intrepid1_amd64.deb

$ apt-cache show libv4l-0
Package: libv4l-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 256
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: libv4l
**Version: 0.5.8-1**

I already removed the ppa repo for 99a version

---

### Post by mc4man on 2009-06-02
Yeah, you installed the jaunty version, 
Just because it 'nags' me, did you install the -dev?  (in your case the jaunty version of "libv4l-dev"

If so and no go maybe it's a kernel thing (amd_64 vs i386

---

### Post by logos34 on 2009-06-02
I'm not sure what's going on here--don't even see a 'libv4l-dev' and I didn't know I installed the 9.04 vers.:

> $ apt-cache search v4l
kmplayer - media player for KDE
libpt-1.10.10-plugins-v4l - Portable Windows Library Video Plugin for Video4Linux
libpt-1.10.10-plugins-v4l2 - Portable Windows Library Video Plugin for Video4Linux v2
xserver-xorg-video-v4l - X.Org X server -- Video 4 Linux display driver
camserv - Stream live video out onto the web
dov4l - program to set and query settings of video4linux devices
gspca-source - source for the gspca v4l kernel module
kdetv - TV viewer for KDE
kradio - Comfortable Radio Application for KDE
libpt-1.11.2-plugins-v4l - Portable Windows Library Video Plugin for Video4Linux
libpt-1.11.2-plugins-v4l2 - Portable Windows Library Video Plugin for Video4Linux v2
libv4l-ruby1.8 - an extension library for capture pictures in Ruby using Video4Linux
libvideo-capture-v4l-perl - Perl interface to the Video4linux framegrabber interface
libvideo-ivtv-perl - Perl extension for using V4l2 in the ivtv perl scripts
ov511-source - Driver source for the OV511, a USB-only chip used in many webcams
v4l-conf - tool to configure video4linux drivers
vgrabbj - grabs a image from a camera and puts it in jpg/png format
xfce4-radio-plugin - v4l radio control plugin for the Xfce4 panel
avahi-autoipd - Avahi IPv4LL network address configuration daemon
motion - V4L capture program supporting motion detection
**libv4l-0** - Collection of video4linux support libraries

lemme yank it out and put in the two intrpeid versions you gave me...

---

### Post by logos34 on 2009-06-02
how did I end up with jaunty versions???

anyway the 8.10 versions went in...Maybe I'll do  build tonight...

---

### Post by mc4man on 2009-06-02
> how did I end up with jaunty versions???

maybe post 13

If you get an error during make don't worry, can be resolved, refer to post 5 about continuing the make. The first build on hardy sometimes is just about getting setup. (due to the # of somewhat outdated libs hardy uses, which really comes into play with vlc 1.x

---

### Post by logos34 on 2009-06-02
no go...I did make, same libavcodec error, then I uninstalled vlc 0.8.6.  Then ran sudo checkinstall, but failed deb build.  Back to same libavcodec error.
??

---

### Post by mc4man on 2009-06-03
Missed your post 17, was posting at same time I guess, was wondering what error you were referring to.

> relocation R_X86_64_32 against `aasc_decoder' can not be used when making a shared object; recompile with -fPIC

That appears to be a 64 bit specific error, which I never had to deal with.

3 things come to mind.
Do what it *appears* to suggest, add -fPic to your ffmeg configure and recompile, not exactly sure how you'd do so, maybe as a cflag added to ffmpeg's configure

```
--extra-cflags="-fPIC"
```

Or maybe check your ffmpeg configure and use --enable-shared, if not already (or if you did enable shared then don't

Or add this to your vlc configure (maybe it's suggesting to add to vlc ...?
--with-pic
and maybe
--enable-static


Probably one of these four or a combo of them would resolve, wouldn't have time to try a hardy 64 bit live cd till later this week.

(I'd probably start with vlc and add those 2 options, if no change then look at ffmpeg build


side notes

If you use --enable-shared you need to run sudo ldconfig afterwards

I've never used checkinstall on vlc, can't see how it would work properly, maybe I'll try sometime just to see

If you were on 32 bit you could have built vlc 10 times by now

---

### Post by mc4man on 2009-06-03
did a build of 0.9.9a on a livecd of 8.04 64 bit.

What you'll have to do is re-compile ffmpeg and add this to the configure
```
--extra-cflags="-fPIC" 
```

You'll want to see these show up alot during the ffmpeg build

-fPIC -DPIC
-fPIC

Then vlc should proceed nicely.

Due to an 8.04 live cd being a bit of a pita to do some things, stopped after a successful build and the vlc config. is short a couple of enables that I'd do normally.
What's in blue may or may not have an effect

ffmpeg config

> ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-libvorbis --enable-postproc --enable-avfilter --enable-avfilter-lavf [COLOR="Blue"]--enable-shared[/COLOR] --extra-cflags="-fPIC" 

vlc config

>  ./configure --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-caca --enable-faad --disable-kate --enable-twolame --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --enable-cddax --with-tuning=native 


Noting that for the embedded video the vlc source needs to be edited, line 216 in vlc-0.9.9a/modules/gui/qt4/qt4.cpp

lines 216-220 after edit
```
#if !defined (Q_WS_X11) || defined HAS_QT43
    add_submodule();
        set_capability( "vout window", 50 );
        set_callbacks( WindowOpen, WindowClose );
#endif

```

---

### Post by logos34 on 2009-06-04
followed your suggestions.  Got the latest snv ffmpeg:

> $ ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-libvorbis --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-shared --extra-cflags="-fPIC"

configure ok, but

make ends with error:
> /usr/bin/ld: /usr/local/lib/libx264.a(common.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libx264.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavcodec/libavcodec.so.52] Error 1

---

### Post by mc4man on 2009-06-04
Don't know if your referring to ffmpeg build or vlc, moot point probably.

The live cd install is gone but an oversimplified how to

Installed build packages and build-deps for x264, ffmpeg, vlc

Went into synaptic, searched ffmpeg and removed all -dev packages
Searched x264 and removed the -dev

Built x264 as such (taken from any of Andrew's mplayer how to's, you should **see -fPIC during  the build**

> git clone git://git.videolan.org/x264.git && cd x264

> ./configure --prefix=/usr --enable-shared && make

> sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" --maintainer "$USER" --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default

Configured and built ffmpeg as described in previous post
configured and built vlc as described

All went fine

---

### Post by logos34 on 2009-06-04
> **mc4man said:**
> Don't know if your referring to ffmpeg build or vlc, moot point probably.

ffmpeg

> 
Installed build packages and build-deps for x264, ffmpeg, vlc

Went into synaptic, searched ffmpeg and removed all -dev packages
Searched x264 and removed the -dev

removed x64-dev, I thought I had removed build-deps for ffmpeg and vlc day before yesterday (I'm running out of room on my / partition, so I'm having to remove them afterwards).  I'll check again

Built x264 as such (taken from any of Andrew's mplayer how to's, you should **see -fPIC during  the build**
well, I installed x264 using fakeoutdoorsman's guide (ffmpeg for hardy)

maybe I'll try once more

---

