---
title: "new VLC 0.9.9 in repositories?"
date: 2009-04-03
forum: Multimedia Software
---

### Post by bsmith1051 on 2009-04-03
Yesterday Videolan announced a new 0.9.9 'stable' version of VLC.  But you can't download it -- they simply point you to the "multiverse" repository.  Anyone know when/if it's going to be added?

---

### Post by calrogman on 2009-04-03
I'm afraid that, until vlc 0.9.9 is approved and packaged your only option is to download the source code and compile vlc yourself.  This shouldn't be too hard.

EDIT:  How silly of me, the source can be found [here]("http://www.videolan.org/vlc/download-sources.html"), and the instructions on compiling it are [here]("http://wiki.videolan.org/UnixCompile").

Good luck!

---

### Post by bsmith1051 on 2009-04-03
My question was simply: When will it be approved?

I know other apps, e.g. Firefox, get approved really fast.  Don't know how important VLC is, though.

---

### Post by calrogman on 2009-04-03
No one knows when it'll be approved, or if it will be approved (although I see no reason why it wouldn't be) but if you need it desperately the option to compile it yourself is always there.

---

### Post by andrew.46 on 2009-04-04
Hi,

It is a difficult one to compile but it can be done. I attach a gloating screenshot of my own successful effort :-). It is a great pity that there is not a guide on these forums for compiling the newest vlc, such guides are in place for FFmpeg and MPlayer but not vlc yet...

Andrew

---

### Post by madhi19 on 2009-04-04
Canonical need to come up with a list of app that get fast tract to the repo. Or maybe a beta repo option that let us install and run things like Firefox minefield at our own risk.

---

### Post by binbash on 2009-04-04
I saw a repo on jaunty forums for jaunty, it contains latest and beta versions of vlc but i do not know if there is a package for intrepid or not.You can browse jaunty forums and check out yourself

---

### Post by bsmith1051 on 2009-04-04
If you're running the beta of Jaunty then you can subscribe to _VLC_'s beta repository.  It's in the Developer's section of their web-site.  Unfortunately, the last time I tried the 1.0-beta it had a lot of UI bugs.

---

### Post by mc4man on 2009-04-05
Hopefully they will release a better version of vlc though there has been ample opportunity to do so in the last several months and it hasn't happened. Considering 0.9.4 is broken and has security flaws it's curious that there has been no update for intrepid.

There are several ppa's that offer 0.9.8a and 0.9.9 for intrepid though not without some minor build flaws or missing the embedded video that most people want.

Once you get the hang of it, it is extremely simple to build your own version on hardy or intrepid, intrepid being the easiest.

If so I'd suggest using 0.9.9a which works quite well with only a few 'breaks', mainly with accessing certain types of directories from vlc. (easy workarounds 

If interested I'll give you a few pointers to get you going, any configure and or make errors are very verbose and will be no problem to resolve.

Other than the build and run deps you'll only need a relatively current set of x264 and ffmpeg's libs. (there are some 'extra' features that can be enabled that would require a few add. packages if desired.

For ffmpeg, x264, fake outdoorsman has a good how to in the tips forum for building or if one prefers to stick with repo style packages this ppa will certainly suffice to upgrade ffmpeg, it's libs, x264, ect. (makes it a piece of cake for linking x264

[http://ubuntuforums.org/showthread.php?p=6827208#post6827208](http://ubuntuforums.org/showthread.php?p=6827208#post6827208)

Also as prep andrew.46 shows how to upgrade your live555 in his how to for mplayer for intrepid in the tips forum, worth doing.

If you get preped in those area's then it's just a matter of aquiring the build-deps, patching the source to extent desired, linking x264 so there's no problems, configuring to enable or disable as one may choose and building.

For a bit of info here are 2 sample configures showing how to link x264 so there are no make errors. In the first just a tree to where it's installed (in this case /usr
In the second, you can always build x264 in the extra's dir in the vlc source and link there (just a configure and make in the extras dir., no make install

> ./configure --with-live555-tree=/usr/lib/live --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-caca --enable-faad  --disable-kate  --enable-twolame --enable-realrtsp --enable-cddax --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --with-x264-tree=/usr/include

> ./configure --with-live555-tree=/usr/lib/live --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-faad  --disable-kate  --enable-twolame --enable-caca  --enable-realrtsp --enable-cddax --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --with-x264-tree=./extras/x264  

a configure as these will produce these modules (with proper build-deps, more can be added or some removed to personal preferences

> Enabled modules: a52 a52tofloat32 a52tospdif access_filter_bandwidth access_filter_dump access_filter_record access_filter_timeshift access_jack access_mmap access_realrtsp access_smb adjust adpcm alphamask alsa aout_file aout_sdl araw asf atmo audio_format audioscrobbler avcodec avformat avi bandlimited_resampler blend blendbench bluescreen bonjour caca canvas cc cdda cddax cdg chain cinepak clone cmml colorthres converter_fixed converter_float crop croppadd cvdsub dbus deinterlace dolby_surround_decoder dts dtstofloat32 dtstospdif dummy dvb dvb dvbsub dvdnav dvdread dynamicoverlay equalizer erase export extract faad fake fb flac float32_mixer folder freetype gaussianblur gestures glx gnutls gradient grain grey_yuv h264 hal headphone_channel_mixer hotkeys http i420_rgb i420_rgb_mmx i420_rgb_sse2 i420_ymga i420_ymga_mmx i420_yuy2 i420_yuy2_mmx i420_yuy2_sse2 i422_i420 i422_yuy2 i422_yuy2_mmx i422_yuy2_sse2 id3tag image inhibit invert jack libass libmpeg2 linear_resampler live555 logger logo lpcm m4a m4v magnify marq memcpy memcpy3dn memcpymmx memcpymmxext mkv mod mono mosaic motion motionblur motiondetect mozilla mp4 mpc mpeg_audio mpga mpgatofixed32 mpgv mux_ogg mux_ts noise normvol notify nsc ogg opengl opengl osd_parser osdmenu oss panoramix param_eq playlist png podcast postproc probe_hal ps psychedelic pulse puzzle qt4 rawvideo rc remoteosd ripple rotate rss rv32 sap scale scaletempo schroedinger screen screensaver sdl_image sharpen  showintf signals simple_channel_mixer skins2 spatializer spdif_mixer speex spudec stats subsdec subsusf svcdsub swscale t140 taglib telepathy telnet telx theora transform trivial_channel_mixer trivial_mixer trivial_resampler ts twolame ugly_resampler v4l2 vcd visual vmem vorbis vout_sdl wall wave x11 x264 xml xtag xvideo yuy2_i420 yuy2_i422 


---

### Post by rmoody on 2009-04-10
Here is what I did to install VLC 0.9.9a on a clean, updated install.

apt-get build-dep vlc
apt-get install paranoia*

wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvfz live555-latest.tar.gz
cd live
./genMakefiles linux
make
cd ..
sudo cp -r live /usr/lib

wget http://download.videolan.org/pub/videolan/vlc/0.9.9a/vlc-0.9.9a.tar.bz2
tar jxvf vlc-0.9.9a.tar.bz2
cd vlc-0.9.9a
./configure --with-live555-tree=/usr/lib/live --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-caca --enable-faad --disable-kate --enable-twolame --enable-realrtsp --enable-cddax --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --with-x264-tree=/usr/include
make
sudo make install


The only issue I had was that the icon on the Applications menu was blank.  So, I found that if you install VLC normally first (sudo apt-get install vlc) then install your compiled VLC, it will leave the icon correct.

Hope that helps.

---

### Post by mc4man on 2009-04-11
The only other thing you may wish to do is apply some ubuntu/debian patches first before building.
The available diffs are
> 400_enable_embedded_video.diff
052_as-needed.diff
101_certificates_paths.diff
102_dejavu_font.diff
104_notify.diff
200_osdmenu_paths.diff
300_manpage_syntax.diff
301_DVD_media.diff
401_detect_xinerama_fullscreen.diff

for just the 'embedded video' no need to apply the .diff, just as easy to edit the source, only 1 line needs to be changed. (before building

Navigate in the extracted source to /modules/gui/qt4/qt4.cpp, line 216
replace that line with this
```
#if !defined (Q_WS_X11) || defined HAS_QT43
```

(screen1 shows orig., screen2 the patched


In 8.10 a sudo make install is best way, what's mentioned above is true about the menu item though I'd make sure to totally remove the repo vlc and related *0.9.4* packages first before building

In *hardy* I like to kept the 0.8.6 version installed (not as capable but nothing's 'broken' )and just run 0.9.9a or 1.0 pre from build folders. (no sudo make install
It's easy to add the build folder vlc to the menu and add to the autorun/autoplay/r. click context choices. (in other words it can become just like any other 'installed' app (screen 3

---

### Post by madhi19 on 2009-04-17
Well this morning I ran the update manager on Jaunty beta since it no longer warn me of new update. I run it every other day now and guess what 0.9.9a is now out.

---

### Post by alphacrucis2 on 2009-04-17
> **madhi19 said:**
> Well this morning I ran the update manager on Jaunty beta since it no longer warn me of new update. I run it every other day now and guess what 0.9.9a is now out.


I tried it. They haven't included the patch that makes it play the video's in the main window.

---

### Post by john.soper on 2009-04-17
> **mc4man said:**
> There are several ppa's that offer 0.9.8a and 0.9.9 for intrepid though not without some minor build flaws or missing the embedded video that most people want.
Ok... I've tried to search the forums for an answer to this question but couldn't find one.

What's a PPA?

Thanks,
John

---

### Post by mc4man on 2009-04-17
> What's a PPA?
Personal Package Archives

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

A search page for ubuntu ppa's

[https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)

Usually you add the ppa to your sources, sometimes if there are no specific dependencies you can dl. the pakage directly.

Most are fairly good (safe), most times the builds are also good and easy to revert back if not pleased.
On rare occasions the ppa will also have updated 'core' libs like gcc, g++, ect. Once those are updated it's very hard to revert. (gcc ect. , not the package

From search on the ppa page for vlc

[https://edge.launchpad.net/ubuntu/+ppas?name_filter=vlc](https://edge.launchpad.net/ubuntu/+ppas?name_filter=vlc)

2 for jaunty (ect.
[https://edge.launchpad.net/~petski/+archive/ppa](https://edge.launchpad.net/~petski/+archive/ppa)
[https://edge.launchpad.net/~kow/+archive/ppa](https://edge.launchpad.net/~kow/+archive/ppa)

Building your own gives you the most control, the ppa's the quickest way

---

### Post by aamr on 2009-04-17
My man! You are a genius! I've been looking for that since a long long time ago, thanks a lot!

---

### Post by aamr on 2009-04-17
> **rmoody said:**
> Here is what I did to install VLC 0.9.9a on a clean, updated install.

apt-get build-dep vlc
apt-get install paranoia*

wget [http://www.live555.com/liveMedia/public/live555-latest.tar.gz](http://www.live555.com/liveMedia/public/live555-latest.tar.gz)
tar xvfz live555-latest.tar.gz
cd live
./genMakefiles linux
make
cd ..
sudo cp -r live /usr/lib

wget [http://download.videolan.org/pub/videolan/vlc/0.9.9a/vlc-0.9.9a.tar.bz2](http://download.videolan.org/pub/videolan/vlc/0.9.9a/vlc-0.9.9a.tar.bz2)
tar jxvf vlc-0.9.9a.tar.bz2
cd vlc-0.9.9a
./configure --with-live555-tree=/usr/lib/live --prefix=/usr --disable-zvbi --enable-flac --enable-libass --enable-caca --enable-faad --disable-kate --enable-twolame --enable-realrtsp --enable-cddax --enable-theora --enable-mozilla --with-mozilla-pkg=libxul-plugin --with-x264-tree=/usr/include
make
sudo make install


The only issue I had was that the icon on the Applications menu was blank.  So, I found that if you install VLC normally first (sudo apt-get install vlc) then install your compiled VLC, it will leave the icon correct.

Hope that helps.

IT HELPED IT HELPED AND GUESS WHAT? IT HELPED! Now I have VLC 0.9.9 working perfectly on my hardy :)

Just a small addition, I had to download the libx264-dev library as well to successfully complete the process (sudo apt-get install libx264-dev)

---

### Post by john.soper on 2009-04-18
> **mc4man said:**
> Personal Package Archives

mc4man... thanks for the helpful reply... you could have just said 'Personal Package Archives' and left it at that.  I really appreciate the details and pointers to further information.  This is what makes the Ubuntu forums a welcome place to us noobs.

John

---

### Post by meka4996 on 2009-05-09
... troubleshooting
if there is error during ./configure, like this one: error Cannot find libXpm libXt development packages
Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) -> search for package name-> click on hardy or intrepid or jaunty in the top..., then install all the packages shown... for example: Package libxpm-dev, Package libxpm4, Package libxpm4-dbg
so install those by $ sudo apt-get install libxpm-dev libxpm4 libxpm4-dbg

for me, I need to install the following packages... 
sudo apt-get install libtwolame-dev
sudo apt-get install qt4-dev-tools  libqt4-dev
sudo apt-get install libxpm-dev libxpm4 libxpm4-dbg
sudo apt-get install libxt-dev libxt6 libxt6-dbg

---

### Post by thrvers on 2009-05-31
hi guys (i'm using **hardy** and **vlc-0.9.9**), 
i've some error after ./configure (based on **@rmoody** tutorial). Like this:

configure: error: Cannot find development header for libtwolame...

configure: error: The skins2 module depends on a the Qt4 development package. Without it you won't be able to open any dialog box from the interface, which makes the skins2 interface rather useless. Install the Qt4 development package or alternatively you can also configure with: --disable-qt4 --disable-skins2.

what i must to do, to fixes this error ??


THX b4

---

### Post by andrew.46 on 2009-05-31
Hi thrvers,

> **thrvers said:**
> 

```
configure: error: Cannot find development header for libtwolame...

configure: error: The skins2 module depends on a the Qt4 development package.
```

You are missing a couple of dev files:

```
sudo apt-get install libqt4-dev libtwolame-dev
```

or you could hold off for a little while as vlc 1.0 rc2 is out now and I guess the final release won't be too far away.

Andrew

---

### Post by thrvers on 2009-06-01
it works **@andrew.46**..

but i run vlc doesn't appear window.
then i run in terminal, and still have error:

reza@reza-desktop:~$ vlc
vlc: error while loading shared libraries: libvlccore.so.0: cannot open shared object file: No such file or directory
reza@reza-desktop:~$

then i find that file on "/usr/lib", i still doesn't have "libvlccore.so.0" or "libvlccore.so".
what i missing, because in ./configure doesn't show error..

[sorry my bad english]

---

### Post by Arup on 2009-06-01
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

I added the repo from here and it installed version 1.0 rc2 and it works fine.

---

### Post by andrew.46 on 2009-06-01
Hi thrvers,

> **thrvers said:**
> 
```
reza@reza-desktop:~$ vlc
vlc: error while loading shared libraries: libvlccore.so.0: cannot open shared object file: No such file or directory
```


It would definitely be an easier option to use the PPA that Arup has suggested above. I had a quick look and he maintains a Hardy version which not all will do :-).

Andrew

---

### Post by thrvers on 2009-06-01
I uninstall **vlc_0.9.9** then try **@mc4man** link at PPA and found [vlc_0.9.9a-1~ppa1~hardy2]("https://edge.launchpad.net/~c-korn/+archive/vlc/+sourcepub/597598/+listing-archive-extra").

After install (from PPA) and have 4 broken package:
**vlc**, **vlc-nox**, **vlc-plugin-ggi** and **vlc-plugin-svgalib**

Then i try to install via terminal and found:
Dependency problem, package **libass1** and **libdca0** not installed (it's make 4 broken package).

(I've been search and that packages just for intrepid, jaunty and karmic, can i (force) use that for hardy??)

:(

---

### Post by thrvers on 2009-06-01
Yes, it's works :) .
I've been force Intrepid package (libass1 and libdca0) to Hardy.

THX all.... :D

---

