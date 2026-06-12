---
title: "How to get mplayer source?"
date: 2008-09-21
forum: Multimedia Software
---

### Post by HyperHacker on 2008-09-21
I seem to have a copy-protected DVD that mplayer can't play. There's a patch to fix this, but I'm not sure what's the best way to get the mplayer source to apply the patch to. Is there a package I should install, or do I just download the source from the mplayer website and put it somewhere in /home? I know how to compile things, but I'm not sure if there's a specific place the source files have to be.

---

### Post by mc4man on 2008-09-21
see here
[http://ubuntuforums.org/showthread.php?t=558538&highlight=compile+mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=compile+mplayer)

Now if you just want a decent ver. of mplayer, optimized for your pc, with the dvdread patch applied, medibuntu diff applied and no other restrictions like the hardy repo source, there is a very easy way to build into nice .debs 
(you'll get mplayer ,mencoder, mplayer docs and nogui ver. .debs,  - you'll only really need to use the mplayer one

Just built and tested on a fresh xubuntu install with *nothing* but w32codecs installed (no other libs, codecs ,ect. (totally self contained
Mplayer plays all dvd's fine including x-protect

Based on using the repo source with the medibuntu diff applied and building solely off of the upstream debian .rules with one command from start to finish

Let me know and i'll post short list of *things to due prior* to build command
I'm using this (prefix is somewhat optional and or expandable 

```
DEB_BUILD_OPTIONS=" --disable-pulse --enable-gui" fakeroot debian/rules binary
```

---

### Post by HyperHacker on 2008-09-21
Yeah, that sounds like what I'd want to do. Although I'd be doing it twice, once on this machine and once on a 64-bit machine.

---

### Post by mc4man on 2008-09-22
Assuming you have *both* medibuntu and hardy source repo's enabled in sources

note: this is what works well for me on ubuntu hardy and tested on xubuntu hardy (_32 bit_). For certain reasons I don't want to use recent revisions of mplayer so this rev' is all I need (hardy  ver.) If you want a newer revision follow andrews's guide and adapt some of this as needed or possible
Any suggestions and or corrections most welcome

first open a terminal and run > mkdir mplayer; cd ~/mplayer
from that prompt run
```
apt-get source mplayer
``` when that's done 

```
cd ../.; sudo apt-get build-dep mplayer
```
After that go to the _link in 1st. post _and run the sudo apt-get for _hardy dev files_.
followed by 
```
sudo apt-get install fakeroot w32codecs
```

Then go here, right click -> select all -> copy. Leave firefox open and on your desktop create a new text document, paste the patch in and save. Rename it patch.patch ( you can then close firefox

[http://tobias.rautenkranz.ch/03-udf.patch](http://tobias.rautenkranz.ch/03-udf.patch)

Browse in your home folder to mplayer/mplayer-1.0~rc2 and open the dvdread folder and drop the patch file inside.

Open a terminal and run
```
cd ~/mplayer/mplayer-1.0~rc2/dvdread; patch -i patch.patch

```
you should see this
> doug@doug-desktop:~$ cd ~/mplayer/mplayer-1.0~rc2/dvdread; patch -i patch.patch
patching file dvd_reader.c
Hunk #1 succeeded at 1390 (offset -3 lines).
Hunk #2 succeeded at 1463 (offset -3 lines).
patching file dvd_reader.h
patching file ifo_read.c
Hunk #1 succeeded at 110 (offset 4 lines).
doug@doug-desktop:~/mplayer/mplayer-1.0~rc2/dvdread$


Now comes a choice (pick one or the other, run command from the terminal that's at the dvdread prompt. if you happen to close the terminal out then run just the command from a mplayer-1.0~rc2 prompt.
if your happy with the repo version as is and just wanted it patched then from the dvdread prompt run
```
cd ../.; fakeroot debian/rules binary
```
                or
If you want to enable more features then you can either edit the .rules file in the debian folder or do this

In your file browser go into the source folder like before and open the *debian upstream* folder. Right click on the .rules file in there -> copy.  Then go into the *debian folder*. Delete the .rules file in there and paste in the one you copied.
Then run this command (from your terminal at the dvdread prompt
```
cd ../.; DEB_BUILD_OPTIONS=" --disable-pulse --enable-gui" fakeroot debian/rules binary

```

Note i don't know if the --disable-pulse is needed. Several months ago without it the build failed, you could probably remove it.

i'm going to re post with the configure this produces - if there's something shown as 'no' that you want as 'yes' you'll want resolve it before you build. (Most of the no's aren't needed or not possible. note some things I didn't notate will be different due to differences in your system, the important stuff will be the same ( due to auto detect of your setup

If you close out a terminal inadvertently don't use any command that starts with cd ../. just manually cd to mplayer-1.0~rc2$ prompt and run the command itself. (the ../.; is just a time saver, not part of command, 


when it's done the .debs will be in your mplayer folder. You don't have to uninstall mplayer first, just d.click on it. (ignore the same version is already installed message
Though in your case (because of problems you may wish to 

```
sudo aptitude purge mplayer
```

If you do remove mplayer after installing the new one the only thing the .deb won't install is 'mplayer-fonts'. Do that from synaptic.

---

### Post by mc4man on 2008-09-22
red is pc specific, part of auto detect

```
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.2.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... no 
Checking for CPU vendor ... [COLOR="Red"]GenuineIntel (15:2:9) [/COLOR]
Checking for CPU type ...  [COLOR="Red"]Intel(R) Pentium(R) 4 CPU 3.00GHz [/COLOR]
Checking for kernel support of mmx ... yes 
Checking for kernel support of mmxext ... yes 
Checking for kernel support of sse ... yes 
Checking for kernel support of sse2 ... yes 
Checking for kernel support of cmov ... yes 
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... native 
Checking for assembler support of -pipe option ... yes 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... [COLOR="Red"]2.6.24-19-generic[/COLOR], ok 
Checking for -lposix ... no 
Checking for -lm ... yes 
Checking for langinfo ... yes 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... __restrict 
Checking for __builtin_expect ... yes 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... yes 
Checking for mkstemp ... yes 
Checking for nanosleep ... yes 
Checking for socklib ... yes 
Checking for inet_pton() ... yes (using )
Checking for network ... yes 
Checking for inttypes.h (required) ... yes 
Checking for int_fastXY_t in inttypes.h ... yes 
Checking for word size ... 32 
Checking for malloc.h ... yes 
Checking for memalign() ... yes 
Checking for alloca.h ... yes 
Checking for mman.h ... yes 
Checking for dynamic loader ... yes 
Checking for dynamic a/v plugins support ... no 
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no 
Checking for iconv ... yes 
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no 
Checking for sys/cdio.h ... no 
Checking for linux/cdrom.h ... yes 
Checking for dvd.h ... no 
Checking for termcap ... yes (using -lncurses)
Checking for termios ... yes (sys/termios.h)
Checking for shm ... yes 
Checking for strsep() ... yes 
Checking for vsscanf() ... yes 
Checking for swab() ... yes 
Checking for POSIX select() ... yes 
Checking for gettimeofday() ... yes 
Checking for glob() ... yes 
Checking for setenv() ... yes 
Checking for sys/sysinfo.h ... yes 
Checking for pkg-config ... yes 
Checking for Samba support (libsmbclient) ... yes 
Checking for tdfxfb ... no 
Checking for s3fb ... no 
Checking for tdfxvid ... no 
Checking for xvr100 ... no 
Checking for tga ... yes 
Checking for md5sum support ... yes 
Checking for bl ... no 
Checking for DirectFB ... yes (1.0.1)
Checking for X11 headers presence ... yes 
Checking for X11 ... yes 
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes 
Checking for XvMC ... no 
Checking for Xinerama ... yes 
Checking for Xxf86vm ... yes 
Checking for XF86keysym ... yes 
Checking for DGA ... yes (using DGA 2.0)
Checking for 3dfx ... no 
Checking for OpenGL ... yes 
Checking for VIDIX ... yes (internal)
Checking for /dev/mga_vid ... no 
Checking for xmga ... no 
Checking for GGI ... yes 
Checking for GGI extension: libggiwmh ... yes 
Checking for AA ... yes 
Checking for CACA ... yes 
Checking for SVGAlib ... yes 
Checking for FBDev ... yes 
Checking for DVB ... no 
Checking for DVB HEAD ... yes 
Checking for zr ... no 
Checking for PNG support ... yes 
Checking for JPEG support ... yes 
Checking for PNM support ... yes 
Checking for GIF support ... yes 
Checking for broken giflib workaround ... disabled 
Checking for VESA support ... no 
Checking for SDL ... yes (using sdl-config)
Checking for NAS ... yes 
Checking for DXR2 ... no 
Checking for DXR3/H+ ... yes 
Checking for IVTV TV-Out ... no 
Checking for V4L2 MPEG Decoder ... yes 
Checking for OSS Audio ... yes 
Checking for aRts ... yes 
Checking for EsounD ... yes 
Checking for esd_get_latency() ... yes 
Checking for pulse ... no 
Checking for JACK ... yes 
Checking for OpenAL ... yes 
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no 
Checking for VCD support ... yes 
Checking for dvdread ... yes (internal)
Checking for internal libdvdcss ... yes 
Checking for cdparanoia ... yes 
Checking for libcdio ... auto (using cdparanoia)
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
Checking for SSA/*** support ... yes 
Checking for fribidi with charsets ... yes 
Checking for ENCA ... yes 
Checking for zlib ... yes 
Checking for RTC ... yes 
Checking for liblzo2 support ... yes 
Checking for mad support ... yes 
Checking for Twolame ... yes 
Checking for Toolame ... no (disabled by twolame)
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... yes 
Checking for OggTheora support ... yes 
Checking for internal mp3lib support ... yes 
Checking for internal liba52 support ... yes 
Checking for libdca support ... yes 
Checking for internal libmpeg2 support ... yes 
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... yes 
Checking for FAAC (AAC encoder) support ... yes (in libavcodec: yes) 
Checking for FAAD2 (AAC) support ... yes (internal floating-point)
Checking for LADSPA plugin support ... yes 
Checking for Win32 codecs ... yes (using /usr/lib/codecs)
Checking for XAnim codecs ... yes (using /usr/lib/codecs)
Checking for RealPlayer codecs ... yes (using /usr/lib/codecs)
Checking for QuickTime codecs ... yes 
Checking for Nemesi Streaming Media libraries ... no 
Checking for LIVE555 Streaming Media libraries ... yes (using distribution version)   [COLOR="Red"]<- it you want latest upgrade firs[/COLOR]t
Checking for FFmpeg libavutil ... yes (static)
Checking for FFmpeg libavcodec ... yes (static)
Checking for FFmpeg libavformat ... yes (static)
Checking for FFmpeg libpostproc ... yes (static)
Checking for libamr narrowband ... yes 
Checking for libamr wideband ... yes 
Checking for libdv-0.9.5+ ... yes 
Checking for XviD ... yes 
Checking for XviD two pass plugin ... yes 
Checking for x264 ... yes (in libavcodec: yes) 
Checking for libnut ... no 
Checking for libmp3lame (for mencoder) ... yes 
Checking for mencoder ... yes 
Checking for fastmemcpy ... yes 
Checking for UniquE RAR File Library ... yes 
Checking for TV interface ... yes 
Checking for Video 4 Linux TV interface ... yes 
Checking for Video 4 Linux 2 TV interface ... yes 
Checking for TV teletext interface ... yes 
Checking for Radio interface ... no 
Checking for Capture for Radio interface ... no 
Checking for Video 4 Linux 2 Radio interface ... no 
Checking for Video 4 Linux Radio interface ... no 
Checking for Video 4 Linux 2 MPEG PVR interface ... yes 
Checking for audio select() ... yes 
Checking for ftp ... yes 
Checking for vstream client ... no 
Checking for byte order ... little-endian 
Checking for OSD menu ... no 
Checking for Subtitles sorting ... yes 
Checking for XMMS inputplugin support ... no 
Checking for inet6 ... yes 
Checking for gethostbyname2 ... yes 
Checking for D-BUS GLib interface ... yes 
Checking for GUI ... no
Checking for automatic gdb attach ... no 
Checking for compiler support for noexecstack ... yes 
Checking for joystick ... no 
Checking for lirc ... yes 
Checking for lircc ... no 
Checking for color console output ... no 
Checking for DVD support (libdvdnav) ... no    [COLOR="Red"]<- don't worry about this[/COLOR]
Creating config.mak
Creating config.h

Config files successfully generated by ./configure  !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: little-endian
  Optimizing for: native

  Languages:
    Messages/GUI: en
    Manual pages: en  

  Enabled optional drivers:
    Input: ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb network 
    Codecs: x264 xvid libdv libamr_wb libamr_nb libavcodec qtx real xanim win32 faad2 faac musepack libmpeg2 libdca liba52 mp3lib libtheora speex tremor(internal) twolame libmad liblzo gif 
    Audio output: alsa openal jack esd arts oss v4l2 nas sdl mpegpes(dvb) 
    Video output: v4l2 dxr3 sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi xvidix cvidix opengl dga xv x11 xover dfbmga directfb md5sum tga 
    Audio filters: ladspa 
  Disabled optional drivers:
    Input: dvdnav vstream radio nemesi 
    Codecs: toolame 
    Audio output: sun pulse ivtv dxr2 
    Video output: ivtv dxr2 vesa zr zr2 xmga mga winvidix 3dfx xvmc bl xvr100 tdfx_vid s3fb tdfxfb 
    
```

---

### Post by shirilover on 2008-09-22
The best way to get the source for mplayer is using svn. The source from the repos is most likely old.
```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

```
Also, libdvdnav-4.1.3 and libdvdread-4.1.3 have been released.
The only way you can use dvdnav in mplayer is to use the source provided by the mplayer dev team.

---

### Post by HyperHacker on 2008-09-22
OK, I got partway through mc4man's instructions and got an error:
> hyperhacker@mercury:~$ sudo apt-get install fakeroot w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate"apt-cache search w32codecs" lists nothing. Is that a problem?

---

### Post by mc4man on 2008-09-22
> Assuming you have both medibuntu and hardy [COLOR="Red"]source[/COLOR] repo's enabled in sources
you must have both repo's enabled for [I]source files
[/I]
If you didn't I'd delete the mplayer folder, enable it or them and start from the beginning (system -administration - software sources (see screen

> this is what works well for me on ubuntu hardy and tested on xubuntu hardy ([COLOR="Red"]32 bit[/COLOR])

if your on a 64 bit machine it's w64codecs ( and it's a pretty much worthless package anyway.

(did you get the pm regarding something else where i also mentioned these things?


> The only way you can use dvdnav in mplayer is to use the source provided by the mplayer dev team.  Have you been able to build a ver. where dvd navigation works? Tried a rev. a week ago or so and couldn't get it to work.

---

### Post by HyperHacker on 2008-09-23
I don't have Medibuntu in that list. How do I add it?

---

### Post by mc4man on 2008-09-23
> I don't have Medibuntu in that list. How do I add it

As far as the build method above you'll need to **start over completely** (delete *the mplayer folder in home*

go here and follow up to the add totem-xine lines (not sure if that works in xubuntu. 

Do the vlc line (if you want to, remove the 'ubuntu-restricted-extras' from the line, time consuming and not needed atm. Like this
```
sudo apt-get install vlc libdvdcss2
```


Set vlc as default as described for_ xubuntu_ - near bottom of post

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

After that try the disk in question in vlc (killing 2 birds with 1 stone)

After that if you want to, follow above 'exactly' from the *beginning* (do delete that mplayer folder first and check in software sources that the _medibuntu source code line is checked_ (as in screen

---

### Post by andrew.46 on 2008-11-22
Hi mc4man:

> **mc4man said:**
> Have you been able to build a ver. where dvd navigation works? Tried a rev. a week ago or so and couldn't get it to work.

I got the dvdnav running but it seemed such a hassle for a feature I would rarely use :-). Details are of course in the MPlayer svn source code in DOCS/tech/dvdnav-howto.txt. I decided to wait for the day when the libdvdread /dvdnav material is integrated into the MPlayer source itself. Not sure if that will ever happen though :(.

  Andrew

---

### Post by mc4man on 2008-11-22
@ andrew
I've been running it for several weeks, 2 different revisions. (latest MPlayer dev-SVN-r27806-4.2.3 (with -volume)

The major hangup seems to be the audio streams, or what i gather is the inability to resample  2 channel to 5.1 output. So if i don't specify -channels 6 in the command then it won't ever output 5.1
.
What is interrelated to that is even when specified most movie menus and or previews are 2 channel so when you do start the movie it only outputs 2 channel.

If there is more than 1 audio stream in the main movie then using shift+3 to cycle thru returns 5.1 output. 

If there are no additional streams to cycle thru then the only solution I see is to start mplayer on the main movie title itself, defeating the purpose of dvdnav to some degree.

So I guess it remains more of a curiosity than anything else, though i did set it up as an autorun choice using a generic launch command of 
 mplayer dvdnav:// -ao alsa -af-adv force=5 -channels 6 -fs

As long as there other audio streams it does work fairly well, pop the disk in and it starts up playing.

@ hyperhacker 
I found a really easy way that you can build any revision you wish into a proper .deb package with very little 'hassle' on your end, basically run a couple of commands, a quick patch of dvdread for x-protect titles, and some minor editing of a .rules file

---

