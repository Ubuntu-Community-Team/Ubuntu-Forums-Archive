---
title: "VLC Crashing"
date: 2009-11-27
forum: Multimedia Software
---

### Post by ..::| Dave89 |::.. on 2009-11-27
I recently installed Ubuntu 9.04 on my PC, dual booting with Vista, and installed VLC Media Player, which is what I use in Vista, to watch DVD's, however, whenever I open a DVD within VLC, it crashes, I tried using Mplayer, but it wouldn't do anything, just sat there with a black window.  I'm using a PC with a 3GHz Intel Core 2 Duo CPU, 4 GB RAM, and 40 GB parttition on a 180 GB HDD.  DVD Writer is Ricoh MP5240A.

TIA

---

### Post by andrew.46 on 2009-11-27
Hi Dave,

> **..::| Dave89 |::.. said:**
> I recently installed Ubuntu 9.04 on my PC, dual booting with Vista, and installed VLC Media Player, which is what I use in Vista, to watch DVD's, however, whenever I open a DVD within VLC, it crashes

Can you run the dvd from the commandline as follows:

```
cvlc -v dvd://
```

and post the command + full terminal output here?

Andrew

---

### Post by alexfish on 2009-11-27
this may help
**VLC crashes.**

 Increase the verbosity level (either in the preferences or with a -vv command line option) and look at the debug messages (in the terminal or in the Messages window).
  If you are convinced that it is a bug in VLC, have a look at the [bug reporting page]("http://www.videolan.org/support/bug-reporting.html").

VLC has a strange behavior...

The first thing to do is to reset the VLC preferences in the preferences dialog of the application and restart VLC. If VLC doesn't even start anymore, delete VLC's configuration file (see the previous question to know about its location). Then restart VLC. If it does not get any better, read the following questions!

---

### Post by ..::| Dave89 |::.. on 2009-11-27
andrew.46: I copied and pasted the command you gave, this is what I got:

dave89@dave89-desktop:~$ cvlc -v dvd://
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc warning: could not open plugins cache file /home/dave89/.cache/vlc/plugins-04041e.dat for reading
[00000373] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: MY_NAME_IS_EARL_SEASON_4_D1
libdvdnav: DVD Serial Number: 3B076C54
libdvdnav: DVD Title (Alternative): MY_NAME_IS_EARL_SEASON_4_D1
libdvdnav: Unable to find map file '/home/dave89/.dvdnav/MY_NAME_IS_EARL_SEASON_4_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
*** Zero check failed in ifo_read.c:1786
    for pgcit->zero_1 = 0xf5b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1790 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1912 ***
*** for pgci_ut->nr_of_lus != 0 ***

libdvdnav: ifoRead_PGCI_UT failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

alexfish: I'm not sure what the verbosity level is, I looked at the preference pane, couldn't find it, I reset the prefs, still smae problem.

I forgot to mention what version of VLC I'm using: 0.99. Also the DVD is region 4.

---

### Post by alexfish on 2009-11-27
sorry not on ubuntu system at present
   list of advanced commands here
  [http://www.videolan.org/doc/play-howto/en/ch04.html](http://www.videolan.org/doc/play-howto/en/ch04.html)

---

### Post by Steeperton on 2009-11-27
I had the same problem... Assuming you've installed libdvdread4 from synaptic, Type this...

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by andrew.46 on 2009-11-27
Hi Dave,

> **..::| Dave89 |::.. said:**
> 
```
libdvdread: Encrypted DVD support unavailable.
```


Looks like you are missing libdvdcss2 which is required by vlc to read encrypted dvds. One way to install this is to use the Medibuntu repository:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

and then install libdvdcss2:

```
sudo apt-get install libdvdcss2
```

and then vlc should play dvds fine :).

Andrew

---

### Post by ..::| Dave89 |::.. on 2009-11-27
I got it playing, but the volume's a bit on the low side. Not too low, but somewhat lower than the Windows version of VLC is. I checked through all the volume settings, but, no success.

---

### Post by alexfish on 2009-11-27
if your using pulse check  to see if vlc pulse plugins are installed

---

### Post by ..::| Dave89 |::.. on 2009-11-27
What's pulse?

---

### Post by alexfish on 2009-11-27
> **..::| Dave89 |::.. said:**
> What's pulse?
  sorry its term is pulse audio
 pulse is a server for your sound system 
  
   in the    synaptic pkg manager you can type in the search area
     "pulse" from there you may see listings referenced to pulse audio / typing  "pulse" generally shows other software that may rely on pulse audio 

   check to see if pulse audio is installed
    also 
  
     vlc pulse audio plugins

   pulse audio helps to connect and configure your sounds
 
 Link here for reading
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by alexfish on 2009-11-27
> **..::| Dave89 |::.. said:**
> What's pulse?
  sorry its term is pulse audio
 pulse is a server for your sound system 
  
   in the    synaptic pkg manager you can type in the search area
     pulse from there you may see listings referenced to pulse audio / typing  "pulse" generally shows other software that may rely on pulse audio 

   check to see if pulse audio is installed
    also 
  
     vlc pulse audio plugins

   pulse audio helps to connect and configure your sound system
 
 Link here for reading
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by ..::| Dave89 |::.. on 2009-11-27
I installed PulseAudio plugin for VLC, still low volume.

---

### Post by alexfish on 2009-11-27
> **..::| Dave89 |::.. said:**
> What's pulse?

> **..::| Dave89 |::.. said:**
> I installed PulseAudio plugin for VLC, still low volume.

posted links which may help they are worth reading 

 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

also search the site with "vlc low volume"

 and start another thread  / other members may spot it

---

### Post by ..::| Dave89 |::.. on 2009-11-27
With certain discs, volume seems OK. With Others, it's low. I'll check those websites linked to previously when I get the time.

---

### Post by alexfish on 2009-11-28
not relative to above

libdvdcss2 i386/32bit:if you have problem with the Medibuntu or the keyring
  you can download via videolan
      

Code:
wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb[/url] -c


wget http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2-dev_1.2.8-1_i386.deb[/url] -c

sudo dpkg -i *.deb"

---

### Post by Onesimus on 2009-11-28
I also have VLC crashing, but none of the above suggestions have helped.

When I use the command

```
cvlc -v dvd://
```

everything seems to play fine.

Here is the output:

```
VLC media player 1.0.2 Goldeneye
[0x869b428] main demux warning: no access_demux module matching "file" could be loaded
[0x86aef40] main interface error: no interface module matched "globalhotkeys,none"
[0x86aef40] main interface error: no suitable interface module
[0x8602140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x86aeed8] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: ERAGON_SPECIAL_EDITION
libdvdnav: DVD Serial Number: 365a9d9b
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/wendy/.dvdnav/ERAGON_SPECIAL_EDITION.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00014c32
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001644e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002cc5ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002cc5f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002d0d47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d0d4d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002d3617
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d361d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002d36bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002d36c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00314619
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0031461f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00344ce5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00344ceb
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
[0xb7300aa8] main input error: ES_OUT_RESET_PCR called
[0xb7300aa8] main input error: ES_OUT_RESET_PCR called
[0x8728a00] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x86ff410] main decoder warning: dts != current_pts (-296710)
[0x87edc50] pulse audio output: No. of Audio Channels: 2
[0x8708058] scaletempo audio filter warning: bad input or output format
[0x8708058] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0xb7300aa8] main input error: ES_OUT_RESET_PCR called
[0x86ff410] main decoder warning: dts != current_pts (-247265)
[0x86ff410] main decoder warning: backward_pts != current_pts (-40000)
[0x87edc50] main audio output warning: the mixer got a packet in the past (88626)
[0x87edc50] main audio output warning: the mixer got a packet in the past (56626)
[0x87edc50] main audio output warning: the mixer got a packet in the past (24626)
[0x87edc50] main audio output warning: mixer start isn't output start (9456)
[0xb7300aa8] main input error: ES_OUT_RESET_PCR called
[0x86dd1e0] main decoder warning: dts != current_pts (-247265)
[0x8809c80] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x87edc50] pulse audio output: No. of Audio Channels: 6
[0x86dd1e0] main decoder warning: backward_pts != current_pts (-40000)
[0x8708d20] scaletempo audio filter warning: bad input or output format
[0x8708d20] main audio filter warning: no audio filter module matching "scaletempo" could be loaded

```

But when I use VLC I get this output:

```
[0x973cb08] main interface error: no interface module matched "globalhotkeys,none"
[0x973cb08] main interface error: no suitable interface module
[0x9690140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9690140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: ERAGON_SPECIAL_EDITION
libdvdnav: DVD Serial Number: 365a9d9b
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/wendy/.dvdnav/ERAGON_SPECIAL_EDITION.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00014c32
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001644e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002cc5ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002cc5f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002d0d47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d0d4d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002d3617
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d361d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002d36bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002d36c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00314619
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0031461f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00344ce5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00344ceb
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
[0xb7300a40] main input error: ES_OUT_RESET_PCR called
[0xb7300a40] main input error: ES_OUT_RESET_PCR called
[0x9ad0dc0] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x9ad2260] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103

```

Ideas anyone ???  (I reset all preferences)

---

### Post by andrew.46 on 2009-11-28
Hi Onesimus,

> ```
[????????] x11 video output error: X11 request 132.19 failed with error code 8:

```

Try a different video out setting, this can be found:

Tools --> Preferences --> Video --> Output

All the best,

Andrew

---

### Post by Onesimus on 2009-11-29
> **andrew.46 said:**
> Hi Onesimus,



Try a different video out setting, this can be found:

Tools --> Preferences --> Video --> Output

All the best,

Andrew

Thanks for this.  It worked !

---

### Post by andrew.46 on 2009-11-30
Hi Onesimus,

> **Onesimus said:**
> Thanks for this.  It worked !

Excellent news :).

Andrew

---

### Post by Z06Gal on 2009-11-30
I have great audio and zero video.  I have reinstalled and still nothing.  I'd love some help if anyone has any ideas.  I have ubuntu 9.10 and it worked after I did the fresh install when karmic was released but something has occurred.  Thanks. 


Robin

---

### Post by andrew.46 on 2009-11-30
Hi Robin,

> **Z06Gal said:**
> I have great audio and zero video.

Perhaps this post might help:

[http://ubuntuforums.org/showpost.php?p=8402772&postcount=18](http://ubuntuforums.org/showpost.php?p=8402772&postcount=18)

All the best,

Andrew

---

### Post by alexfish on 2009-11-30
Re: VLC Crashing
I also have VLC crashing, but none of the above suggestions have helped.

  in synaptic can you check if these are installed

vlc

gstreamer010-pulse audio

libsdl1.2.debian-all

vlc-plugin-pulse

libdvdcss2 

on my system had play around with the audio settings in the vlc tools preferences / to match the setting in pulse

ie my pulse settings are dolby 5.1

and force detection of dolby suround sound in vlc

added: link for enabling speaker channels

[http://www.unix-tutorials.com/go.php?id=4126](http://www.unix-tutorials.com/go.php?id=4126)
[http://mybroadband.co.za/vb/blog.php?b=303](http://mybroadband.co.za/vb/blog.php?b=303)
added

[0x86aef40] main interface error: no interface module matched "globalhotkeys,none"


to start vlc with Global Hotkeys enabled call 'vlc --extraintf=globalhotkeys' (with this way it's possible to control which vlc-instance has them enabled).
the automatic startup is enabled by adding globalhotkeys to "Preferences/Interface/Main Interfaces/Extra interface modules" (in this case only the first instance has them working).

link here
[http://forum.videolan.org/viewtopic.php?f=7&t=18350&start=60](http://forum.videolan.org/viewtopic.php?f=7&t=18350&start=60)

---

### Post by Z06Gal on 2009-11-30
> **andrew.46 said:**
> Hi Robin,



Perhaps this post might help:

[http://ubuntuforums.org/showpost.php?p=8402772&postcount=18](http://ubuntuforums.org/showpost.php?p=8402772&postcount=18)

All the best,

Andrew


Thanks Andrew.  Unfortunately it didn't work.  I am wondering if my settings in compiz is the problem.  I have played with those alot and maybe there is a conflict.  I'll give that a look.

---

### Post by Z06Gal on 2009-11-30
Well it's not compiz.  What is strange is that the player comes up but the screen looks like its transparent.  The borders are there but the screen is invisible or something.  Lol.

---

### Post by alexfish on 2009-12-02
> **Z06Gal said:**
> Well it's not compiz.  What is strange is that the player comes up but the screen looks like its transparent.  The borders are there but the screen is invisible or something.  Lol.

hi 
sorry not on ubuntu / no access to vlc again/ going to down load soon




this link will hopfully get you a start

it is a link for the command line help




[http://wiki.videolan.org/VLC_command-line_help](http://wiki.videolan.org/VLC_command-line_help)

---

### Post by alexfish on 2009-12-03
> **Z06Gal said:**
> Well it's not compiz.  What is strange is that the player comes up but the screen looks like its transparent.  The borders are there but the screen is invisible or something.  Lol.
   

try this code

first

vlc --reset-config --reset-plugins-cache


then look here

[http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html)

---

### Post by alexfish on 2009-12-07
hi
  Tip

if you are using pulse audio

 after you have installed vlc and libdvdcss2

insert a dvd  

then select  play with Movie Player

   It may look for other plugins  

not always but some times

---

