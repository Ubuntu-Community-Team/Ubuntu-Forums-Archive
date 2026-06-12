---
title: "PulseAudio is dead, DBus is dead, KDE is dead. Sorry. Please refer to Ubuntu support."
date: 2010-05-31
forum: Multimedia Software
---

### Post by Istrebitel on 2010-05-31
Recently i had installed a kubuntu (i'm new to linux), recently being 3 days, 1 day of actual use. When i tried to watch dvd's i installed vlc and it didnt work at all.

I made this post:
[http://ubuntuforums.org/showthread.php?t=1496410](http://ubuntuforums.org/showthread.php?t=1496410)

then i found a thread with comprehesive guide, 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
that installed about 250mb of stuff into my system and now i can watch everything pretty well (video_ts.ifo wont open still but xine now plays videos from dvds correctly and i can switch audio streams and subtitles).

Then i made a post at vlc forums and asked what can be wrong with vlc as it is closing after anything. They asked for some debug log, i provided it
```
istrebitel@dom-tux:~$ gdb --args vlc -vv
GNU gdb (GDB) 7.1-ubuntu
Copyright  (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL  version 3 or later <http://gnu.org/licenses/gpl.html>
This is  free software: you are free to change and redistribute it.
There is  NO WARRANTY, to the extent permitted by law.  Type "show copying"
and  "show warranty" for details.
This GDB was configured as  "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading  symbols from /usr/bin/vlc...(no debugging symbols found)...done.
(gdb)  run
Starting program: /usr/bin/vlc -vv
[Thread debugging using  libthread_db enabled]
VLC media player 1.0.6 Goldeneye
[0x8052148]  main libvlc debug: VLC media player - version 1.0.6 Goldeneye - (c)  1996-2010 the VideoLAN team
[0x8052148] main libvlc debug: libvlc was  configured with ./configure  '--build=i486-linux-gnu' '--config-cache'  '--disable-maintainer-mode' '--disable-update-check'  '--enable-fast-install' '--enable-release' '--prefix=/usr'  '--with-binary-version=1ubuntu1.1' '--disable-atmo'  '--disable-fluidsynth' '--disable-gnomevfs' '--disable-kate'  '--disable-mtp' '--enable-x264' '--disable-zvbi' '--enable-a52'  '--enable-aa' '--enable-bonjour' '--enable-caca' '--enable-dca'  '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad'  '--enable-flac' '--enable-freetype' '--enable-fribidi' '--enable-ggi'  '--enable-gnutls' '--enable-jack' '--enable-libass' '--enable-libmpeg2'  '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv'  '--enable-mod' '--enable-mozilla' '--enable-mpc' '--enable-ncurses'  '--enable-notify' '--enable-ogg' '--enable-pulse' '--enable-qt4'  '--enable-realrtsp' '--enable-sdl' '--enable-shout' '--enable-skins2'  '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib'  '--enable-telx' '--enable-theora' '--enable-twolame' '--enable-vcd'  '--enable-vcdx' '--enable-vorbis' '--with-mozilla-pkg=libxul'  '--enable-alsa' '--enable-dv' '--enable-pvr' '--enable-v4l'  '--enable-v4l2' '--enable-svgalib' 'build_alias=i486-linux-gnu'  'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x8052148]  main libvlc debug: translation test: code is "C"
[0x8052148] main  libvlc debug: checking plugin modules
[0x8052148] main libvlc debug:  loading plugins cache file  /home/istrebitel/.cache/vlc/plugins-04041e.dat
[0x8052148] main  libvlc debug: recursively browsing `/usr/lib/vlc'
[0x8052148] main  libvlc debug: module bank initialized (380 modules)
[0x8052148] main  libvlc debug: opening config file (/home/istrebitel/.config/vlc/vlcrc)
[0x8052148]  main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x8052148]  main libvlc debug: looking for memcpy module: 3 candidates
[0x8052148]  main libvlc debug: using memcpy module "memcpymmxext"
[0x80e8bd0]  main input debug: Creating an input for 'Media Library'
[0x80e8bd0]  main input debug: Input is a meta file: disabling unneeded options
[0x80e8bd0]  main input debug: using timeshift granularity of 50 MBytes
[0x80e8bd0]  main input debug: using timeshift path '/tmp'
[0x80e8bd0] main input  debug: `file/xspf-open:///home/istrebitel/.local/share/vlc/ml.xspf'  gives access `file' demux `xspf-open' path  `/home/istrebitel/.local/share/vlc/ml.xspf'
[0x80e8bd0] main input  debug: creating demux: access='file' demux='xspf-open'  path='/home/istrebitel/.local/share/vlc/ml.xspf'
[0x80ec318] main  demux debug: looking for access_demux module: 1 candidate
[0x80ec318]  main demux warning: no access_demux module matching "file" could be  loaded
[0x80ec318] main demux debug: TIMER module_need() : 4.122 ms -  Total 4.122 ms / 1 intvls (Avg 4.122 ms)
[0x80e8bd0] main input  debug: creating access 'file'  path='/home/istrebitel/.local/share/vlc/ml.xspf'
[0x80f6458] main  access debug: looking for access module: 3 candidates
[0x80f6458]  access_file access debug: opening file  `/home/istrebitel/.local/share/vlc/ml.xspf'
[0x80f6458] main access  debug: using access module "access_file"
[0x80f6458] main access  debug: TIMER module_need() : 7.177 ms - Total 7.177 ms / 1 intvls (Avg  7.177 ms)
[0x80f6540] main stream debug: Using AStream*Stream
[0x80f6540]  main stream debug: pre buffering
[0x80f6540] main stream debug:  received first data after 0 ms
[0x80f6540] main stream debug:  pre-buffering done 296 bytes in 0s - 19270 kbytes/s
[0x80f6ce0] main  stream debug: looking for stream_filter module: 5 candidates
[0x80f6ce0]  main stream debug: TIMER module_need() : 8.556 ms - Total 8.556 ms / 1  intvls (Avg 8.556 ms)
[0x80f8d78] main stream debug: looking for  stream_filter module: 1 candidate
[0x80f8d78] main stream debug:  using stream_filter module "stream_filter_record"
[0x80f8d78] main  stream debug: TIMER module_need() : 2.703 ms - Total 2.703 ms / 1 intvls  (Avg 2.703 ms)
[0x80e8bd0] main input debug: creating demux:  access='file' demux='xspf-open'  path='/home/istrebitel/.local/share/vlc/ml.xspf'
[0x80f9410] main  demux debug: looking for demux module: 1 candidate
[0x80f9410]  playlist demux debug: using XSPF playlist reader
[0x80f9410] main  demux debug: using demux module "playlist"
[0x80f9410] main demux  debug: TIMER module_need() : 2.262 ms - Total 2.262 ms / 1 intvls (Avg  2.262 ms)
[0x80e8bd0] main input debug:  `file/xspf-open:///home/istrebitel/.local/share/vlc/ml.xspf'  successfully opened
[0x80f91d8] main xml debug: looking for xml  module: 2 candidates
[0x80f91d8] main xml debug: using xml module  "xml"
[0x80f91d8] main xml debug: TIMER module_need() : 4.588 ms -  Total 4.588 ms / 1 intvls (Avg 4.588 ms)
[0x80f9410] playlist demux  debug: parsed 0 tracks successfully
[0x80f91d8] main xml debug:  removing module "xml"
[0x80e8bd0] main input debug: EOF reached
[0x80f9410]  main demux debug: removing module "playlist"
[0x80f8d78] main stream  debug: removing module "stream_filter_record"
[0x80f6458] main  access debug: removing module "access_file"
[0x80e8bd0] main input  debug: TIMER input launching for 'Media Library' : 28.205 ms - Total  28.205 ms / 1 intvls (Avg 28.205 ms)
[New Thread 0xb7a4ab70 (LWP  7529)]
[New Thread 0xb79c9b70 (LWP 7530)]
[New Thread 0xb7948b70  (LWP 7531)]
[0x80e7bf0] main playlist debug: Activated
[0x80e7bf0]  main playlist debug: rebuilding array of current - root Playlist
[0x80e7bf0]  main playlist debug: rebuild done - 0 items, index -1
[0x80e8bd0]  main interface debug: looking for interface module: 1 candidate
[0x80e8bd0]  main interface debug: using interface module "hotkeys"
[0x80e8bd0]  main interface debug: TIMER module_need() : 3.153 ms - Total 3.153 ms / 1  intvls (Avg 3.153 ms)
[New Thread 0xb78bfb70 (LWP 7532)]
[0x80e8bd0]  main interface debug: thread (interface) created at priority 0  (interface/interface.c:151)
[0x80e8bd0] main interface debug: thread  started
[0xb7700570] main interface debug: looking for interface  module: 1 candidate
[0xb7700570] main interface debug: using  interface module "inhibit"
[0xb7700570] main interface debug: TIMER  module_need() : 3.726 ms - Total 3.726 ms / 1 intvls (Avg 3.726 ms)
[New  Thread 0xb76ffb70 (LWP 7533)]
[0xb7700570] main interface debug:  thread (interface) created at priority 0 (interface/interface.c:151)
[0x80ec7c0]  main interface debug: looking for interface module: 1 candidate
[0xb7700570]  main interface debug: thread started
[0x80ec7c0] main interface  debug: using interface module "screensaver"
[0x80ec7c0] main  interface debug: TIMER module_need() : 2.464 ms - Total 2.464 ms / 1  intvls (Avg 2.464 ms)
[New Thread 0xb767eb70 (LWP 7534)]
[0x80ec7c0]  main interface debug: thread (interface) created at priority 0  (interface/interface.c:151)
[0x80ec7c0] main interface debug: thread  started
[0x80fbe80] main interface debug: looking for interface  module: 1 candidate
[New Thread 0xb75fdb70 (LWP 7535)]
[0x80fbe80]  main interface debug: using interface module "signals"
[0x80fbe80]  main interface debug: TIMER module_need() : 3.769 ms - Total 3.769 ms / 1  intvls (Avg 3.769 ms)
[New Thread 0xb757cb70 (LWP 7536)]
[0x80fbe80]  main interface debug: thread started
[0x80fbe80] main interface  debug: thread (interface) created at priority 0  (interface/interface.c:151)
[0x80fbe80] main interface debug: thread  ended
[0xb7700e80] main interface debug: looking for interface  module: 1 candidate
[Thread 0xb757cb70 (LWP 7536) exited]
[New  Thread 0xb74e1b70 (LWP 7537)]
[0xb7700e80] main interface debug:  using interface module "globalhotkeys"
[0xb7700e80] main interface  debug: TIMER module_need() : 11.251 ms - Total 11.251 ms / 1 intvls (Avg  11.251 ms)
[New Thread 0xb7460b70 (LWP 7538)]
[0xb7700e80] main  interface debug: thread (interface) created at priority 0  (interface/interface.c:151)
[0xb7700e80] main interface debug: thread  started
[0xb7700e80] main interface debug: thread ended
[0x8052148]  main libvlc: Running vlc with the default interface. Use 'cvlc' to use  vlc without interface.
[Thread 0xb7460b70 (LWP 7538) exited]
[0x80eb5e0]  main interface debug: looking for interface module: 4 candidates
[New  Thread 0xb5e7db70 (LWP 7539)]
[0x80eb5e0] main interface debug:  using interface module "qt4"
[0x80eb5e0] main interface debug: TIMER  module_need() : 502.772 ms - Total 502.772 ms / 1 intvls (Avg 502.772  ms)
[New Thread 0xb3939b70 (LWP 7540)]
[0x80eb5e0] main interface  debug: thread (interface) created at priority 0  (interface/interface.c:151)
[0x80eb5e0] main interface debug: thread  started
[0x80eb5e0] main interface debug: thread ended
[Thread  0xb3939b70 (LWP 7540) exited]
[0x80eb5e0] qt4 interface debug: Error  while initializing qt-specific localization
(7526)  KSycocaPrivate::openDatabase: Trying to open ksycoca from   "/var/tmp/kdecache-istrebitel/ksycoca4"
QInotifyFileSystemWatcherEngine::addPaths:  inotify_add_watch failed: No such file or directory
[New Thread  0xb23b3b70 (LWP 7546)]
QFileSystemWatcher: failed to add paths:  /home/istrebitel/.config/ibus/bus
Bus::open: Can not get  ibus-daemon's address. 
IBusInputContext::createInputContext: no  connection to ibus-daemon 
[0x80e7bf0] main playlist debug: adding  item `Yami no Matsuei - Love Me.mp3' ( /media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei - Love Me.mp3 )
[0x80e7bf0]  main playlist debug: rebuilding array of current - root Playlist
[0x80e7bf0]  main playlist debug: rebuild done - 1 items, index -1
[0x80e7bf0]  main playlist debug: processing request item Yami no Matsuei - Love  Me.mp3 node null skip 0
[0x80e7bf0] main playlist debug: resyncing on  Yami no Matsuei - Love Me.mp3
[0x80e7bf0] main playlist debug: Yami  no Matsuei - Love Me.mp3 is at 0
[0x80e7bf0] main playlist debug:  starting new item
[0x80e7bf0] main playlist debug: creating new input  thread
[0x8484000] main input debug: Creating an input for 'Yami no  Matsuei - Love Me.mp3'
[0x80eb5e0] qt4 interface debug: Adding a new  MRL to recent ones: /media/&#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no  Matsuei - Love Me.mp3
[New Thread 0xb1bb2b70 (LWP 7547)]
[0x8484000]  main input debug: thread (input) created at priority 10  (input/input.c:230)
[0x8484000] main input debug: thread started
[0x80eb5e0]  qt4 interface debug: IM: Setting an input
[0x8484000] main input  debug: using timeshift granularity of 50 MBytes
[0x8484000] main  input debug: using timeshift path '/tmp'
[0x8484000] main input  debug: `/media/&#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei -  Love Me.mp3' gives access `' demux `' path `/media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei - Love Me.mp3'
[0x8484000]  main input debug: creating demux: access='' demux='' path='/media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei - Love Me.mp3'
[0xb77036d8]  main demux debug: looking for access_demux module: 7 candidates
[0x80eb5e0]  qt4 interface debug: Updating the geometry
[0x80eb5e0] qt4 interface  debug: Updating the geometry
[0xb77036d8] main demux debug: TIMER  module_need() : 66.445 ms - Total 66.445 ms / 1 intvls (Avg 66.445 ms)
[0x8484000]  main input debug: creating access '' path='/media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei - Love Me.mp3'
[0x83b8ea0]  main access debug: looking for access module: 7 candidates
[0x83b8ea0]  vcd access debug: trying .cue file: /media/&#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime  Music=-/Yami no Matsuei - Love Me.cue
[0x83b8ea0] vcd access debug:  could not find .cue file
[0x83b8ea0] access_file access debug:  opening file `/media/&#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no  Matsuei - Love Me.mp3'
[0x83b8ea0] main access debug: using access  module "access_file"
[0x83b8ea0] main access debug: TIMER  module_need() : 28.070 ms - Total 28.070 ms / 1 intvls (Avg 28.070 ms)
[0x83c1cc8]  main stream debug: Using AStream*Stream
[0x83c1cc8] main stream  debug: pre buffering
[0x83c1cc8] main stream debug: received first  data after 5 ms
[0x83c1cc8] main stream debug: pre-buffering done  1024 bytes in 0s - 194 kbytes/s
[0x84af250] main stream debug:  looking for stream_filter module: 5 candidates
[0x84af250] main  stream debug: TIMER module_need() : 0.090 ms - Total 0.090 ms / 1 intvls  (Avg 0.090 ms)
[0x84a3738] main stream debug: looking for  stream_filter module: 1 candidate
[0x84a3738] main stream debug:  using stream_filter module "stream_filter_record"
[0x84a3738] main  stream debug: TIMER module_need() : 0.082 ms - Total 0.082 ms / 1 intvls  (Avg 0.082 ms)
[0x8484000] main input debug: creating demux:  access='' demux='' path='/media/&#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime  Music=-/Yami no Matsuei - Love Me.mp3'
[0x83e7bf8] main demux debug:  looking for demux module: 51 candidates
[0x83e7bf8] es demux debug:  detected format mpga
[0x837f5b0] main packetizer debug: looking for  packetizer module: 21 candidates
[0x837f5b0] main packetizer debug:  using packetizer module "mpeg_audio"
[0x837f5b0] main packetizer  debug: TIMER module_need() : 264.048 ms - Total 264.048 ms / 1 intvls  (Avg 264.048 ms)
[0x83e7bf8] main demux debug: using demux module  "es"
[0x83e7bf8] main demux debug: TIMER module_need() : 298.087 ms -  Total 298.087 ms / 1 intvls (Avg 298.087 ms)
[0x8484000] main input  debug: looking for a subtitle file in /media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/
[0x83e7bf8] main demux debug:  looking for meta reader module: 1 candidate
[0x83e7bf8] main demux  debug: TIMER module_need() : 23.475 ms - Total 23.475 ms / 1 intvls (Avg  23.475 ms)
[0x8484000] main input debug: `/media/&#1061;&#1091;&#1081;  &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;/Audio/-=Anime Music=-/Yami no Matsuei - Love Me.mp3'  successfully opened
[0x837f5b0] mpeg_audio packetizer debug: MPGA  channels:2 samplerate:44100 bitrate:128
[0x8484000] main input debug:  selecting program id=0
[0x83c3608] main decoder debug: looking for  decoder module: 31 candidates
[0x80eb5e0] qt4 interface debug:  Updating the geometry
[0x80eb5e0] qt4 interface debug: Updating the  geometry
[0x80eb5e0] qt4 interface debug: Updating the geometry
[0x80eb5e0]  qt4 interface debug: Updating the geometry
[0x80eb5e0] qt4 interface  debug: Updating the geometry
[0x83c3608] main decoder debug: using  decoder module "mpeg_audio"
[0x83c3608] main decoder debug: TIMER  module_need() : 93.700 ms - Total 93.700 ms / 1 intvls (Avg 93.700 ms)
[New  Thread 0xb0949b70 (LWP 7548)]
[0x83c3608] main decoder debug: thread  (decoder) created at priority 5 (input/decoder.c:315)
[0x83c3608]  main decoder debug: thread started
[0x8484000] main input debug:  Buffering 0%
[0x8484000] main input debug: Buffering 8%
[0x8484000]  main input debug: Buffering 17%
[0x8484000] main input debug:  Buffering 26%
[0x83c3608] mpeg_audio decoder debug: MPGA channels:2  samplerate:44100 bitrate:128
[0x8484000] main input debug: Buffering  34%
[0x8484000] main input debug: Buffering 43%
[0x8484000] main  input debug: Buffering 52%
[0x8484000] main input debug: Buffering  60%
[0x8484000] main input debug: Buffering 69%
[0x8484000] main  input debug: Buffering 78%
[0x8484000] main input debug: Buffering  87%
[0x8484000] main input debug: Buffering 95%
[0x8484000] main  input debug: Stream buffering done (313 ms in 0 ms)
[0x80eb5e0] qt4  interface debug: Updating the geometry
[0x80eb5e0] qt4 interface  debug: Updating the geometry
[0x8484000] main input debug: creating  aout
[0xb0700618] main audio output debug: looking for audio output  module: 4 candidates
[0xb0700618] pulse audio output: No. of Audio  Channels: 2
[New Thread 0xac696b70 (LWP 7549)]
[0xb0700618] pulse  audio output debug: Pulse mainloop started
[0xb0700618] pulse audio  output debug: Failed to connect to server: Connection refused
[0xb0700618]  pulse audio output debug: Pulse initialization unlock and fail
[0xb0700618]  pulse audio output debug: Pulse initialization failed
[Thread  0xac696b70 (LWP 7549) exited]
[0xb0700618] alsa audio output debug:  opening ALSA device `default'
vlc: pcm_plug.c:388:  snd_pcm_plug_change_channels: Assertion  `snd_pcm_format_linear(slv->format)' failed.

Program received  signal SIGABRT, Aborted.
[Switching to Thread 0xb0949b70 (LWP 7548)]
0xb7fe2430  in __kernel_vsyscall ()
(gdb) ^CQuit
(gdb)
```
then they told me the subj:

Your system is so broken that it's not funny. PulseAudio is dead, DBus  is dead, KDE is dead. Sorry. Please refer to Ubuntu support.
[http://forum.videolan.org/viewtopic.php?f=13&t=77028&p=253324#p253324](http://forum.videolan.org/viewtopic.php?f=13&t=77028&p=253324#p253324)

Now could someone please tell me what exactly should i fix in my system? And what do they mean by it being broken and dead? I can pretty well listen to audio and watch video and kde is working fine with all that nice eyecandy...

---

### Post by lidex on 2010-06-01
Why are you using pulseaudio on kubuntu? Have you tried using vlc with the audio out set to alsa?

---

### Post by Istrebitel on 2010-06-01
Tried alsa output, it also crashes

tried "UNIX OSS" and it worked - i could listen to mp3 or view video

FFS EVEN VIDEO_TS NOW WORKS!

Phew! Finally!

Okay then, whats wrong with my alsa output or pulseaudio? What should i do to fix this Bus and KDE?

PS: The only thing i did to my system aside from installing packages was
- install nvidia drivers
- change config files for grub to see my windows dualboot
- change config files for disk manager to let me mount wihtout password requirement
- try to install alsa-driver-1.0.23 (make, make install) that failed to install and crashed my audio card, but after restart it looked like all was right

---

### Post by lidex on 2010-06-01
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Istrebitel on 2010-06-02
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Jun  2 17:14:51 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      P5E


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_ctxfi


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K2 SB0880


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 02)
    Subsystem: 1043:8277
--
04:00.0 0403: 1102:000b (rev 03)
    Subsystem: 1102:0041


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_ctxfi
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    multiple : 2
    reference_rate : 48000
    use_system_timer : N


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Jun  2 11:09 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Jun  2 11:09 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  8 Jun  2 21:13 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  7 Jun  2 11:09 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 Jun  2 11:09 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  5 Jun  2 11:09 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  4 Jun  2 11:09 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  3 Jun  2 11:09 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Jun  2 11:09 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun  2 11:09 .
drwxr-xr-x 3 root root 240 Jun  2 11:09 ..
lrwxrwxrwx 1 root root  12 Jun  2 11:09 pci-0000:04:00.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [XFi]

Card hw:0 'XFi'/'Creative X-Fi 20K2 SB0880'
  Mixer name    : '20K2'
  Components    : ''
  Controls      : 29
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 205 [80%] [-12.75dB] Capture 205 [80%] [-12.75dB]
  Front Right: Playback 205 [80%] [-12.75dB] Capture 205 [80%] [-12.75dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 205 [80%] [-12.75dB] Capture 205 [80%] [-12.75dB] [on]
  Front Right: Playback 205 [80%] [-12.75dB] Capture 205 [80%] [-12.75dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 205 [80%] [-12.75dB] [on]
  Front Right: Playback 205 [80%] [-12.75dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Line-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'S/PDIF-in',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [off] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'S/PDIF-out',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.XFi {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 205
        value.1 205
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 205
        value.1 205
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Line-in Playback Volume'
        value.0 256
        value.1 256
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'S/PDIF-in Playback Volume'
        value.0 256
        value.1 256
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'S/PDIF-out Playback Volume'
        value.0 256
        value.1 256
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 205
        value.1 205
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Surround Playback Volume'
        value.0 256
        value.1 256
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Center/LFE Playback Volume'
        value.0 256
        value.1 256
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Side Playback Volume'
        value.0 256
        value.1 256
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Capture Volume'
        value.0 205
        value.1 205
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'PCM Capture Volume'
        value.0 205
        value.1 205
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Line-in Capture Volume'
        value.0 256
        value.1 256
    }
    control.14 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Mic Capture Volume'
        value.0 0
        value.1 0
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 256'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'S/PDIF-in Capture Volume'
        value.0 256
        value.1 256
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Capture Switch'
        value true
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line-in Capture Switch'
        value true
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Capture Switch'
        value false
    }
    control.19 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'S/PDIF-in Capture Switch'
        value true
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line-in Playback Switch'
        value false
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'S/PDIF-out Playback Switch'
        value false
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'S/PDIF-in Playback Switch'
        value false
    }
    control.23 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Front Playback Switch'
        value true
    }
    control.24 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Surround Playback Switch'
        value false
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Center/LFE Playback Switch'
        value false
    }
    control.26 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Side Playback Switch'
        value false
    }
    control.27 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        device 4
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.28 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 4
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.29 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        device 4
        name 'IEC958 Playback PCM Stream'
        value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
ppdev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_ctxfi
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
fbcon
snd_rawmidi
snd_seq_midi_event
tileblit
snd_seq
snd_timer
snd_seq_device
font
snd
bitblit
x38_edac
sbp2
soundcore
softcursor
edac_core
nvidia
agpgart
vga16fb
vgastate
usbhid
serio_raw
snd_page_alloc
hid
asus_atk0110
lp
parport
ohci1394
floppy
usb_storage
ieee1394
sky2
pata_jmicron


!!ALSA/HDA dmesg
!!------------------

[    7.117060] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[    7.830702] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.830726] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.861012] hda-intel: no codecs found!
[    7.861247] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   10.102066] sky2 eth0: enabling interface



```

---

