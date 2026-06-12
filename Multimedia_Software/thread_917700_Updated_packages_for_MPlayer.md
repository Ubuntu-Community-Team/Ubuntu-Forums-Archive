---
title: "Updated packages for MPlayer"
date: 2008-09-12
forum: Multimedia Software
---

### Post by rvm4000 on 2008-09-12
Introduction: one of the problems that a Ubuntu user may find when using [SMPlayer](http://smplayer.berlios.de) is that not all options in the application work. This is because the version of MPlayer in Ubuntu is quite old (1.0rc2 is almost a year old). For that reason I built updated packages for MPlayer. I have also added some patches to MPlayer, so it can work better with SMPlayer.

While these packages are intented to be used with SMPlayer, of course they can also be used alone. No need to install or use SMPlayer. Indeed I had care MPlayer would work "out of the box".

The mplayer package includes a configuration file (/etc/mplayer/mplayer.conf) which will make mplayer to try to use xv and alsa as default.

These are the main differences you'll find when used along with SMPlayer (compared to mplayer 1.0rc2):

 * the option to change the playback speed without altering the pitch will work (thanks to the new scaletempo filter)
 * the option to change the volume just before start to play will work too (thanks to the startupvol patch)
 * the audio equalizer will work as everybody would expect, when you move the controls you'll notice the change in the audio immediately, no need to click on the "Apply" button. (Thanks to the patcheq patch).
 * the options to change the size of the subtitles (in the Subtitles menu) will work better.
 * selection of subtitles works better now. Previously under some circumstances, it was possible that the selected subtitle in the SMPlayer menu and the subtitle actually selected by MPlayer may not match.
 * you can use "gl:yuv=2:force-pbo:ati-hack" as video output, which is as fast as xv. Also gl (without options) is faster than before.

For the ones interested in MPlayer only, these are the changes since 1.0rc2 (copied from the mplayer changelog):
> rc3:
    Decoders:
    * Nellymoser audio decoding via lavc
    * support for X8 frame (fixes "J-type picture is not supported" for WMV2)
    * support for DTS WAV/DTS-CD passthrough by ad_hwac3
    * Apple's raw YUV2 in MOV
    * LATM over LOAS AAC decoding via internal libfaad2
    * video game codecs: BFI video, Playstation MDEC video, ADPCM XA audio,
      EA Maxis XA ADPCM audio, RL2 video, Beam Software SIFF video, V.Flash PTX video
    * AVOption support for libavcodec-based decoders
    * image decoders: Sun rasterfile, PCX image
    * MLP decoder via lavc
    * use lavc ADPCM codecs by default

    Demuxers:
    * -lavfdopts cryptokey allows decrypting MXF and ASF files
    * support for wavpack in Matroska
    * demux_lavf permits program switching
    * AVOption support for lavf demuxing
    * prefer lavf musepack demuxer over libmpdemux
    * prefer lavf MOV demuxer over libmpdemux
    * support -slang in lavf demuxer
    * support nosound switching in lavf demuxer
    * support libass in lavf demuxer
    * support VOBsub in lavf demuxer
    * support MOV subtitle format
    * support for attachments in lavf demuxer
    * support for chapters in lavf demuxer
    * FLAC speedup in lavf demuxer

    Filters:
    * vf_ow new overcomplete wavelet denoiser
    * change vf_screenshot dependency from libpng to lavc
    * add af_scaletempo which maintains audio pitch when changing playback speed
    * fix multi-channel reordering

    Streaming:
    * tv:// support for Windows
    * fix teletext on some systems
    * DVD streams can switch angles
    * DVD still menus are now supported via dvdnav://
    * allow specifying the TV standard for each channel

    FFmpeg/libavcodec:
    * DNxHD (SMPTE VC-3) encoder
    * H.264 speedup and PAFF decoding
    * correctly decode more of the H.264 conformance testsuite
    * Nellymoser audio codec
    * VC-1/WMV3 MMX optimizations
    * VP3 decoder speedup
    * Split-Radix FFT (speedup multiple audio codecs)
    * MMX/SSE/ARM and other misc speedups

    libmpeg2:
    * enable Alpha/ARM optimizations in libmpeg2
    * SSE2-optimized IDCT routines from upstream libmpeg2

    Drivers:
    * replace PolypAudio by PulseAudio (-ao pulse)
    * add force-pbo suboption for faster output in vo_gl
    * add Nintendo Wii/GameCube video driver (-vo wii)
    * VIDIX driver for SuperH Mobile VEU hardware block.
    * support -border on vo_gl/gl2 in x11

    MEncoder:
    * check for system-wide configuration file in MEncoder
    * AVOption support for lavc encoders
    * AVOption support for lavf muxers

    Others:
    * many compiler warning fixes
    * basic support for Closed Captioning roll-up mode
    * reworked screensaver disabling support, most users will need to use
      -heartbeat-cmd due to screensaver authors failing to design a common API
    * grayscale decoding/encoding with FFmpeg disabled where it slowed down
      the color case
    * Linux AppleIR remote support
    * add options to disable some or all configuration files
    * support for DOS-style file:///x:/path paths
    * some new slave commands (check DOCS/tech/slave.txt)
    * misc fixes to libass
    * libdvdcss updated to 1.2.10, now same as upstream version

    Ports:
    * small crash with vo_macosx fixed
    * AC3/DTS passthrough for ao_macosx
    * fix frozen OSD on Mac OS X
    * vo_gl now works with -wid and nVidia drivers on Windows (this is a hack)
    * VIDIX on SuperH.
    * workarounds for AltiVec on Apple gcc 3.3 on Mac OS X dropped

mencoder has also been patched to support the -a.s.s option, so for instance you can use it to convert a mkv video to avi with embedded subtitles on the image which will look like exactly the same as when played with mplayer.

Apt repositories:
Packages for hardy, intrepid and jaunty, available at: 
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
or
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing) (experimental packages)

More info, and even instructions to build the packages yourself, [**here**](http://smplayer.berlios.de/forums/viewforum.php?id=9).

---

### Post by mc4man on 2008-09-12
the packages seem fine, smplayer is great, as far as the mplayer package

Will receive font error from cli, resolved by re-installing mplayer fonts

Cryptic error - see screen, has no real effect, saw it since rev.'s starting in april, am guessing mv = motion vectors ?

I'm surprised mplayer isn't using a patched dvdread by now (allows playback of most UDF 'butchered' titles), considering the latest libdvdnav4 does deal with this.
I use this patch atm.
[http://tobias.rautenkranz.ch/code/libdvdread_udf.patch](http://tobias.rautenkranz.ch/code/libdvdread_udf.patch)

Also on the mplayer side any rev. from april on I've tried the chapter end option seems non functional. (ex. option  '-chapter 5-5' will start on 5 and continue to end of title instead of ending at end of 5, any idea's.

---

### Post by rvm4000 on 2008-09-13
Seeking to chapters may not work if using a cache.

Add *-nocache* to command line and see if it works now.

---

### Post by mc4man on 2008-09-13
> Add -nocache
That question was pretty much off topic, but anyway the issue seems to be not seeking to but ending at. (and not a 'playback' use per se)
for instance pre april these work to either rip & convert or dump an audio stream in **chapter 5 only**


> mplayer -vc null -vo null -aid 128 -ao pcm:fast:waveheader:file=foo5.wav dvd://1 -chapter 5-5

> mplayer -vc null -vo null -aid 128 -dumpaudio dvd://1 -chapter 5-5


Since then the same comm. will start at chap. 5 but continue to the end of the title. (the -5 no longer has effect

If in the future you manage to include dvdnav support it would interesting to see if the endchapter option returns (I tried building it in w/ no success

---

### Post by rvm4000 on 2008-09-13
You can report the bug to [http://bugzilla.mplayerhq.hu/](http://bugzilla.mplayerhq.hu/)

---

### Post by rvm4000 on 2008-09-15
New version available: [SVN r27607](http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588&release_id=626231).

This time, instead of one big package, there are several packages: mplayer, mencoder and mplayer-doc.

And something new: mencoder is patched to support the option -a.s.s. That allows to reencode videos with embedded subtitles on the video which will look the same as when played on mplayer.

Here an example (taken from a script I use):

```
#!/bin/sh

FILE=../1x01.avi
SUBS=../1x01.srt
OUTPUT=output_video.avi

mencoder -noodml -o $OUTPUT \
  -oac copy \
  -ovc xvid \
  -xvidencopts bitrate=1000:max_bframes=2 \
  -keep-pts -vf-add a.s.s,harddup \
  -sub $SUBS -subcp latin1 \
  -a.s.s -a.s.s-color ffff4000 -a.s.s-border-color 00000000 \
  -a.s.s-force-style Bold=1,Outline=2,Shadow=3,Fontsize=16 \
  -fontconfig \
  -subcp ISO-8859-1 -a.s.s-line-spacing 0 -a.s.s  \
  $FILE
```

---

### Post by liyanricaoqiyue1314 on 2008-09-15
To the married-Niu.      If that is not a Jiangsu-door furniture carpenter, Mei Niu doomed to marry a village of pottery Bozi wife. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Bozi home village of Tao Tao willing to spend with her sister-Niu for the pro-Gege Mei-yun.      Peach blossom in full bloom one day. - Niu made a home in Jiangsu's Wang is said to be a carpenter, he is to help fight-Niu furniture for the dowry. [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Wang linked to 20, a carpenter, keep-the first, Meiqingmuxiu, Douren favorite. [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Niu Mei Mei Nanzi never seen this, just Piaoyi Yan echocardiography have the feeling, but also face slightly Fatang.      Fortunately, not being the King is busy working carpenter found. [Runescape quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)     At this time, coincides with Nongmang season. Meiyun to Lane busy farm work, cooking at home-Niu hospitality Wang carpenter.      Wang carpenter while living doing carpentry, with the side-Niu chat.      Wang Mei Niu carpenter asked a lot of problems. [AOC Power Leveling](http://www.aoc-power-leveling.org)     Wang Mei Niu was a carpenter asked Mianhongerchi,. Thanks to Wang carpenter only pay attention to work and do not pay attention to observe.      Niu and Wang Mei carpenter contact Shijianyichang, bolder gradually larger. One day, she assured Wang carpenter questions:      "You have mountains there?? "      "We are the Great Plains there," says Wang carpenter replied, "do not see Hill. Tianba are all big."      "You have Baogu family, Yang Yu eat?? "Wang Mei Niu asked carpenter.      "We have Baogu home, not Yang Yu, but we do not eat Baogu." Wang-work carpenter Bianyue, "that is used to feed the finishing pigs."      "That is what you eat? "Mei Niu continue to ask.      "We eat rice," Wang carpenter said, "so throughout the year."      "Rice Gouchi?? "Mei Niu asked.      "Gouchi year of 2003 miles." Wang carpenter said, "every year sold several tons of surplus grain."       - Niu did not know "several tons of surplus grain" is the span mean, it inconvenient to ask for fear their Mochu Xi Wang carpenter laugh. [Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Day night, thinking about the day-Niu Wang carpenter, then a sleepless night.       Three days later, Wang Mei Niu carpenter Datan to the marriage, on the sorry for her, advised her out of the poor mountain valley, the mountains to. [Buy Aoc Power Leveling](http://www.aoc-power-leveling.org)      "To the mountains, to Gansha? "Niu-inexplicably asked.       "When my daughter-in-law ah? "Wang Xiaoxiao carpenter surreptitious manner.       Niu Mei Zhang De Crimson's face, quickly turned back to thatched houses, heart kept jumping. [Buy Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Wang left carpenter tools, catch up with the entrance of housing.       "Really." Wang carpenter Mangshuo, "You beautiful, I love you, really like you!"       "You Bieluan said." Mei Wu Zhuolian Niu said, "I would not agree to the Columbia." [Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      "He did not take advantage of the home," Wang said Niu carpenter-advised, "Do you think escape."       "Does not work." Mei Niu shaking his head said, "I have miles to the brother-for-daughter-in-law, brother can not be left regardless." [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)      "My hands of the rich." Wang carpenter serious, "your brother to stay 5,000 yuan, he casually enough to marry the daughter-in-law." [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)      Niu Dian Ledian-head. [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      Wang entered the house carpenter, cling-Niu, a while Kuangwen. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      - Niu homeopathy fell on the bed&#21398; [Runescape GP](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      The next day at dusk. Meiyunganwan farm work at home, no-Niu and Wang carpenter, Quejian table with red Buguo the 5000 money. Meiyun mind is the span that matter. [Rs quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)      Six months later, Mei Yun from the hands of traffickers to buy a woman a wife. [rs money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      Has just completed marriage. Mei Mei Yun Niu suddenly received from Jiangsu to the distress of the letter: I was fooled by Wang carpenter, a carpenter at home with his wife Wang, the children, he will I money to sell 15,000 to a local 30-year-old Bozi Wife&#21398; Come help me. [runescape shop](http://www.runescape-shop.com)      Meiyun read the letter, a sigh out: "Oh, I Yousha to be? on when the pro-change! "

---

### Post by rvm4000 on 2008-09-18
New version available: [SVN r27636](https://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588&release_id=627164) (packages for i386 and amd64)

This time mplayer and mencoder are compiled with x264 support! (it wasn't easy...)

So in order to install the new mplayer packages you also need to install at least this package:
[libx264-64_0.svn20080917_i386.deb](http://downloads.sourceforge.net/smplayer/libx264-64_0.svn20080917_i386.deb)
[libx264-64_0.svn20080917_amd64.deb](http://downloads.sourceforge.net/smplayer/libx264-64_0.svn20080917_amd64.deb)

If you want to compile mplayer yourself, you'll need the development package too:
[libx264-dev_0.svn20080917_i386.deb](http://downloads.sourceforge.net/smplayer/libx264-dev_0.svn20080917_i386.deb)
[libx264-dev_0.svn20080917_amd64.deb](http://downloads.sourceforge.net/smplayer/libx264-dev_0.svn20080917_amd64.deb)

---

### Post by rvm4000 on 2008-10-13
New packages for [SVN r27751](https://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588&release_id=632913).

Compiled with dvdnav support!

Dependencies available [here](https://sourceforge.net/project/showfiles.php?group_id=185512&package_id=291876&release_id=627167).

In order to play protected dvds you need [libdvdcss2](http://packages.medibuntu.org/hardy/libdvdcss2.html).

**Update:** uploaded the packages for i386 (they are untested!)

---

### Post by mc4man on 2008-10-13
The r27751 works well without any issues yet, no problems with smplayer either. The dvdnav of mplayer is good though the results aren't always 100%. (can be worked around.

I think it's worth keeping another player available, what can co exist nicely is to build a 0.9x version of vlc using the 4.1.3-1 versions of libdvdread4, dvdnav4-dev's. (used 0.9.3, run from build dir.

---

### Post by rvm4000 on 2008-10-19
I managed to compile mplayer in the [lauchpad PPA](https://launchpad.net/~rvm/+archive), so now you can install mplayer (and dependencies) adding this line to your /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/rvm/ubuntu hardy main
```
This is experimental!

If you find any problems, please comment.

BTW, now the 64bit version of mplayer can use the w64codecs.

---

### Post by rvm4000 on 2008-10-29
Experimental and untested (I don't have intrepid installed).

Packages for MPlayer SVN r27751 compiled in intrepid:
[https://launchpad.net/~rvm4000/+archive](https://launchpad.net/~rvm4000/+archive)

Line for /etc/apt/sources.list:
> deb [http://ppa.launchpad.net/rvm4000/ubuntu](http://ppa.launchpad.net/rvm4000/ubuntu) intrepid main

(The repository also includes packages for smplayer 0.6.4)

---

### Post by andrew.46 on 2008-10-31
Hi RVM,

BTW congrats on the volume patch:

[http://svn.mplayerhq.hu/mplayer?view=rev&revision=27872](http://svn.mplayerhq.hu/mplayer?view=rev&revision=27872)

  Andrew

---

### Post by davidY on 2008-11-01
Hi rvm4000, thank you for your work! Without it I would be stranded on the land of no fast forward video watching - the pitch scaling patch is great. However, your experimental Ibex build installs to 2:1.0~rc2svn27751, but no pitch correction ~~ please help. 

Cheers!

EDIT::

Fixed! I'm so noob. "mplayer -af help" shows that i need gmplayer -af scaletempo in order for the plugin to work

I ended up editing /etc/mplayer/mplayer.conf to add a line 
af=scaletempo
To make scaletempo by default.

---

### Post by Jungleboss on 2008-11-08
I can't seem to install mplayer_1.0rc2svn27751_amd64.deb. I run Intrepid and the package liblame0 i needed and I don't have it and it can't be installed. liblame0 is obsolete in Intrepid and is replaced by libmp3lame0.

---

### Post by Jungleboss on 2008-11-08
I got it to work. I used rvm4000's repository. 

But dts-wav playback doesn't work with this new version like it says in the changelog. But that's another matter :)

---

### Post by CraymelCage on 2008-11-08
I'm using the repositories on the smplayer website but I can't install your version of mplayer it gives me this error

Depends: liblame0 (>=3.97) but it is not installable
 Depends: libopenal0a  but it is not installable

I tried to install liblame0 but it won't let me because of liblmp3lame0 I don't know what to do.

Wait never mind I fixed the problem. I put both repositories Intrepid and hardy's once I got rid of hardy's it worked

---

### Post by rvm4000 on 2008-11-08
Currently there are two repositories:

[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

In this one previously there were only packages for hardy, but now there are packages for intrepid too.

The lines for /etc/apt/sources.list:

**hardy**
deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) hardy main

**intrepid**
deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main

[https://launchpad.net/~rvm4000/+archive](https://launchpad.net/~rvm4000/+archive)

In this repository there were only packages for intrepid, although I'm uploading packages for hardy too.
The main difference is that I'm using this repository for experimental packages. For instance it's available there MPlayer SVN r27900 with some new patches. When people test these packages they'll be eventually moved to the other repository.

The lines for /etc/apt/sources.list:

**hardy**
deb [http://ppa.launchpad.net/rvm4000/ubuntu](http://ppa.launchpad.net/rvm4000/ubuntu) hardy main

**intrepid**
deb [http://ppa.launchpad.net/rvm4000/ubuntu](http://ppa.launchpad.net/rvm4000/ubuntu) intrepid main

Only one of the two repositories should be used, not both.

---

### Post by andrew.46 on 2008-11-23
Hi mc4man:

> **mc4man said:**
> Also on the mplayer side any rev. from april on I've tried the chapter end option seems non functional. (ex. option  '-chapter 5-5' will start on 5 and continue to end of title instead of ending at end of 5, any idea's.

This has been fixed:

[http://svn.mplayerhq.hu/mplayer?view=rev&revision=27987](http://svn.mplayerhq.hu/mplayer?view=rev&revision=27987)

  Andrew

---

### Post by ripps818 on 2008-12-07
How did you get this to build correctly in Launchpad?
I've been trying to build MPlayer in my PPA using the Directshow Server (Needed for CoreAVC) and Gnome-Screensaver patches, but I just end up dependency wait hell.

Actually, if you don't mind. Could you apply these patches to your build (it's svn, right?). Neither of these patches should interfere with mplayer's regular operations.

---

### Post by rvm4000 on 2008-12-10
I've just recompiled mplayer with your two patches:
[https://launchpad.net/~rvm4000/+archive](https://launchpad.net/~rvm4000/+archive)

The patches are in debian/patches/ and they are applied to the sources by dpatch just before compiling.

---

### Post by ripps818 on 2008-12-10
Thanks, this'll be alot easier for me to maintain an updated mplayer now. 
I did manage to get mplayer compiled in my ppa. I had to use your mplayer and libs to get it working, but I did it.

All I need to do is figure out how to package coreavc-for-linux as a debian package. That way other people won't have to compile their own directshow server like I did.

---

### Post by omne on 2009-01-01
Thank’s for this ppa.

I don’t use smplayer since mplayer I way enought for me. Anyway, this builts solve somme problems here with mp4. But why didn’t we have a recent mplayer package in intrepid ?

O.

---

### Post by no1wantdthisname on 2009-01-12
Did you remove the dshowserver patch?

---

### Post by rvm4000 on 2009-01-12
The latest build doesn't contain that patch.

You can still download the previous one (svn r28035):
[https://launchpad.net/~rvm4000/+archive?field.name_filter=mplayer&field.status_filter=superseded](https://launchpad.net/~rvm4000/+archive?field.name_filter=mplayer&field.status_filter=superseded)

I'll try to add the patch in future builds.

---

### Post by rvm4000 on 2009-01-26
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

New packages:

* MPlayer updated to SVN r28349 (2009-01-24).
* Two new patches added: 10-gnome-screensave.dpatch and 11-dshowserver.dpatch.
* Packages compressed with lzma, so now they are smaller.

---

### Post by rvm4000 on 2009-01-31
[https://launchpad.net/~rvm4000/+archive/ppa/](https://launchpad.net/~rvm4000/+archive/ppa/)

MPlayer updated to SVN r28403.

There's also a build for jaunty (i386 and amd64 only, the lpia build failed).

---

### Post by rvm4000 on 2009-04-08
New packages available for mplayer svn r29021.

This time the jaunty and intrepid builds are compiled with vdpau support (although they are untested).

[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

---

### Post by rvm4000 on 2009-05-04
Some news. Now the PPAs have changed:

For mplayer:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
or
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing) (experimental packages)

If you use the last one, you may need to add this repository too: [https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs) (includes some updated libraries required by mplayer)

There's also a PPA for the smplayer packages:
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

