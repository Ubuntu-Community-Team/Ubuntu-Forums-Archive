---
title: "mplayer went missing"
date: 2010-05-01
forum: Multimedia Software
---

### Post by greebothecat on 2010-05-01
Hi,
I have upgraded (so it's not a clean new installation) from Karmic to Lucid yesterday and all is smooth with the exception of mplayer. It's shortcut disappeared from the Main Menu, it also cannot be found in the Open With tab, Preferences menu of files.
I removed it and downloaded it again (sudo apt-get install mplayer), but it's still the same. I tried using SMplayer then but it shows me an error (MPlayer has finished unexpectedly. Exit code: 1), no matter what type of file I choose (or what type of output driver). In the meantime, VLC works with pretty much everything.
Lastly: I tried running mplayer from the terminal and it worked (no gui though, gmplayer gives me an error that there's no skin file in specified directory, but I don't think it's my main concern right now).
I also downloaded mplayer source from their website and compiled & installed it. It came up in the Main Menu and Open With but wasn't even working and I'm not quite sure where it did actually go and what happens with it now (My Ubuntu's system partition is kind of a dark well to me - I drop things inside and sometimes don't even hear the splash).

If it's not the lucid or mplayers fault then it must be, because I'm not really grasping the whole picture here. I'm a beginner, as you can tell :)

Any help will be appreciated, any smiting will be humbly born.

---

### Post by jimmers on 2010-05-01
You could try this :-
  	 	 	 	 	 	   

 **Install Mplayer in Ubuntu 10.04 (Lucid)**
 You have to make sure you have enabled universe,multiverse repositories
 Now you need to run the following command to update the source list
 [INDENT]sudo apt-get update[/INDENT] Install mplayer using the following command
 [INDENT]sudo apt-get install mplayer[/INDENT] or
 Click on the following link
 [INDENT][apt://mplayer](apt://mplayer)[/INDENT] If you want to open mplayer go to Applications—>Sound&Video—> Mplayer Movie Player
 **Install w32 video codecs and libdvdcss2 in Ubuntu 10.04 (Lucid)**
 


 The following command adds Medibuntu’s repository to Ubuntu. It also adds Medibuntu’s GPG key to your keyring, which is needed to authenticate the Medibuntu packages.
 [INDENT]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list[/INDENT] [INDENT]sudo apt-get -q update[/INDENT] [INDENT]sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring[/INDENT] [INDENT]sudo apt-get -q update[/INDENT] For** i386 Users** install Codecs using the following command
 [INDENT]sudo apt-get install w32codecs libdvdcss2[/INDENT] For **amd64 Users** install Codecs using the following command
 [INDENT]sudo apt-get install w64codecs libdvdcss2[/INDENT] Using above download locations you can install most of the mutimedia codecs for ubuntu.
 **Mplayer Plugin for Firefox**
  If you want to install Mplayer with plug-in for [[COLOR=#006400]_Mozilla_[/COLOR]]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html#") Firefox run the following command
 [INDENT]sudo apt-get install mozilla-mplayer[/INDENT] or click on the following link
 [INDENT][apt://mozilla-mplayer](apt://mozilla-mplayer)
 This is in Open Office Format.

  	 	 	 	 	 	   [B]This is MS Office format
[/B]
[B]
[/B]
******Install Mplayer in Ubuntu 10.04 (Lucid)**
 You have to make sure you have enabled universe,multiverse repositories
 Now you need to run the following command to update the source list
 [INDENT]sudo apt-get update[/INDENT] Install mplayer using the following command
 [INDENT]sudo apt-get install mplayer[/INDENT] or
 Click on the following link
 [INDENT][apt://mplayer](apt://mplayer)[/INDENT] If you want to open mplayer go to Applications—>Sound&Video—> Mplayer Movie Player
 **Install w32 video codecs and libdvdcss2 in Ubuntu 10.04 (Lucid)**
 


 The following command adds Medibuntu’s repository to Ubuntu. It also adds Medibuntu’s GPG key to your keyring, which is needed to authenticate the Medibuntu packages.
 [INDENT]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list[/INDENT] [INDENT]sudo apt-get -q update[/INDENT] [INDENT]sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring[/INDENT] [INDENT]sudo apt-get -q update[/INDENT] For** i386 Users** install Codecs using the following command
 [INDENT]sudo apt-get install w32codecs libdvdcss2[/INDENT] For **amd64 Users** install Codecs using the following command
 [INDENT]sudo apt-get install w64codecs libdvdcss2[/INDENT] Using above download locations you can install most of the mutimedia codecs for ubuntu.
 **Mplayer Plugin for Firefox**
  If you want to install Mplayer with plug-in for [[COLOR=#006400]_Mozilla_[/COLOR]]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html#") Firefox run the following command
 [INDENT]sudo apt-get install mozilla-mplayer[/INDENT] or click on the following link
 [INDENT][apt://mozilla-mplayer](apt://mozilla-mplayer)

Good Luck
[/INDENT] 

 
[/INDENT]

---

### Post by greebothecat on 2010-05-02
Yeah, I can google this Ubuntugeek Tutorial too. I've tried that already.
(libdvdcss2 is not available at the moment from Medibuntu's repository..)

I have wiped my system partition clean and did a fresh new Lucid installation (kept the old /home partition, though) and the problem is still there: after installing mplayer, it's not shown in the Apps menu, nor does it work with SMplayer..

Is the lucid mplayer release broken or is it just me?

---

### Post by oussama on 2010-05-03
Hello here is the reason :D

From synaptic package "**[COLOR="Red"]gecko-mediaplayer[/COLOR]**"
> 
Multimedia plug-in for Gecko browsers

Gecko Media Player is a browser plug-in that uses GNOME MPlayer
and Mplayer to play media in a browser.
It uses the NS4 API and is therefore compatible with all NS4 derived browsers:
Iceweasel, Firefox, Iceape, Epiphany, Galeon, Midbrowser, Xulrunner, etc.

It is [COLOR="Red"]**the modern replacement for mplayerplug-in (from the same author)**[/COLOR].


So install gecko-mediaplayer insted of mozilla-mplayer, it is exact as mozilla-mplayer but a bit better and nicer look, 

You will also get a try-icon near the clock where you can control the player without changing tab in Firefox, I like it :D

---

### Post by greebothecat on 2010-05-03
Thanks, but I don't even use Firefox (Chrome user here), so I don't have a problem with the browser plug-in.

My problem is with mplayer not working other than from terminal and not being compatible with SMplayer (and not showing in the Main Menu or Open With menu).

---

### Post by mc4man on 2010-05-03
> My problem is with mplayer not working other than from terminal 
The lucid repo mplayer and your svn build are command line only, for a gui you need to install one. the most common being smplayer or gnome-mplayer
> 
not showing in the Main Menu
being only cli you shouldn't expect it to.
> 
not being compatible with SMplayerThat's what you should look at - there is a log viewer in smplayer's options - the mplayer log, the smplayer log

You mentioned building mplayer and installing the repo version - you shouldn't have both installed at the same time.

How did you install your svn build - sudo make install or checkinstall?

---

### Post by greebothecat on 2010-05-04
I used sudo apt-get install to get mplayer

Thanks, I found the log and I'll try to figure out now what it says.

Here it is, if you could cast an eye on it, I'd be grateful!

```

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xvidix -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 79692294 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/greebo/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -cache 2000 -ss 17 -osdlevel  -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/greebo/Videos/anime/Afro Samurai/Afro Samurai episode 1.avi

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/greebo/Videos/anime/Afro Samurai/Afro Samurai episode 1.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  592x320  12bpp  23.976 fps  1085.1 kbps (132.5 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=VirtualDubMod 1.5.10.2 (build 2540/release)
ID_CLIP_INFO_N=1
ID_FILENAME=/home/greebo/Videos/anime/Afro Samurai/Afro Samurai episode 1.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1085112
ID_VIDEO_WIDTH=592
ID_VIDEO_HEIGHT=320
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=127008
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=1575.62
ID_SEEKABLE=1
ID_CHAPTERS=0
No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
Error opening/initializing the selected video_out (-vo) device.
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=mp3
Video: no video
Starting playback...


MPlayer interrupted by signal 11 in module: seek
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```

---

### Post by mc4man on 2010-05-04
> [COLOR="Red"]/usr/bin/mplayer[/COLOR] -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave [COLOR="Red"]-vo xvidix[/COLOR]

I gotta go to work so only a quick mention of a few of your options here (which are numerous as far as mplayer, smplayer, using a built version, the repo version or from any number of ppa's

smplayer is using the mplayer in /usr/bin, did you configure your build to install there or do you also have the repo mplayer installed?

The video output of xvidix is not going to work - no such thing

Assuming your build of mplayer is good and it works from the cli I'd try this
open synaptic, search mplayer and remove if installed (inc. mplayer-nogui
also search smplayer and remove

Then open a terminal and 
```
sudo apt-get install checkinstall
```

When done then cd to your mplayer build source folder and run 
```
sudo make uninstall
```
when done use this to install as a package
```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"

```

Then open home folder, ( view -> show hidden files) and open .config and delete the smplayer folder
Then re-install smplayer

If your not sure about your mplayer build then you could check out this how to or just remove your checkinstall mplayer build in synaptic and try the repo one or a ppa ,ect.
[http://ubuntuforums.org/showthread.php?t=1305181&highlight=svn+mplayer](http://ubuntuforums.org/showthread.php?t=1305181&highlight=svn+mplayer)

an updated build dep list for lucid is in post 241 (last page

because you keep your /home I'd delete the smplayer folder as described - you'll may also have a .mplayer folder with a config file inside - don't delete, just look and see if anything is improper

You could also install gnome-mplayer to d. check your mplayer build

---

### Post by couder on 2010-05-19
> **oussama said:**
> Hello here is the reason :D

From synaptic package "**[COLOR="Red"]gecko-mediaplayer[/COLOR]**"


So install gecko-mediaplayer insted of mozilla-mplayer, it is exact as mozilla-mplayer but a bit better and nicer look, 

You will also get a try-icon near the clock where you can control the player without changing tab in Firefox, I like it :D

Thanks a lot Oussama
Didn't know that, you saved a lot of my time.:guitar:

---

