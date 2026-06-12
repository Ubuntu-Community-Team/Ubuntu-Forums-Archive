---
title: "problems playing wmv files in totem &amp; vlc"
date: 2008-05-19
forum: Multimedia Software
---

### Post by William.fries.is.here on 2008-05-19
when i play in totem it ask me for a codec then tells me there are none available (I have all repositories available through)
if i cancel and try to view in totem anyway.
it will play the first couple seconds with out sound get all jumpy and scrambled.

in vlc. 
i just get the jumpy and scrambled.

I have attempted to search for the codecs manually and have tried to download anything in synaptic that mentions wmv of windows media files.

if you can think of anything specific let me know.
ask me questions I'll do my best to answer.

And I'm willing to start from square one.:confused:

---

### Post by wolfen69 on 2008-05-19
just a shot in the dark, but totem has been known to have issues. go to synaptic and completely remove it. (you can always put it back) then search for mplayer and install that. see what happens.

---

### Post by michaelaly on 2008-05-19
Under Applications -> Add/Remove, run a search for 'Restricted Extras' or 'codec' and install what comes up. This should enable you to play wmv files and then some. 
Question : Have you tried playing various video files? They should be from different sources as if they're all from one place it's likely they're encoded in the same way, possibly with DRM.

---

### Post by William.fries.is.here on 2008-05-19
well here is what happened 
i did both.
installed mplayer along with the codec search and restricted extras.
in additional to searching for plugins as well and downloading every one of them i could.

and here we are

i can get the application to play slowly but with not audio 
(error reads "cannot find audio codec for format 0x162)

right now im downlaoding some updates for the application and gonna do a restart and some prayer.   any further ideas or applications or a place to find such codecs?

---

### Post by mc4man on 2008-05-19
make sure you have w32codecs installed, if not install (medibuntu repo) and restart before trying playback

---

### Post by William.fries.is.here on 2008-05-19
how would one install such a repository?

---

### Post by cor2y on 2008-05-19
Yes you need the w32codecs add the medibuntu repos ([www.medibuntu.org](www.medibuntu.org)) then either via the terminal or synaptic install it, although the stand alone plugins for gstreamer should allow wmv playback.
```
sudo apt-get install w32codecs
```
for gstreamer make sure all the plugins are installed.

---

### Post by mc4man on 2008-05-19
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
follow instr. for ver. of ubuntu your using

---

### Post by mc4man on 2008-05-19
@cor2y
can you ck. this thread and advise for mp3 it always worked for me never paid att. to what enabled
[http://ubuntuforums.org/showthread.php?t=794229](http://ubuntuforums.org/showthread.php?t=794229)

---

### Post by William.fries.is.here on 2008-05-19
ok did all that 
here is the update.

still same situation as far as totem
gnome player
vlc 
mplayer still displays same error

 dragon player will play audio correctly but video still comes out slowed down.

---

### Post by William.fries.is.here on 2008-05-19
sorry
actually
mplayer runs fine
just no audio and i keep getting that no codedc 0x162 error

---

### Post by William.fries.is.here on 2008-05-19
make that gnome m player plays find just with no audio

---

### Post by cor2y on 2008-05-19
can you post the error message mplayer prints out if you run it from the terminal?

---

### Post by William.fries.is.here on 2008-05-20
i'd be more then happy to if i knew how to do such.

how does one play it from the terminal?

---

### Post by jdoggy on 2008-05-20
> **wolfen69 said:**
> just a shot in the dark, but totem has been known to have issues.


here, using 8.04 on a P3@500 with P2B-S Asus mobbo & Diamond S3 Savage2000 agp, that video tool installed by default, Totem, crashed the system by trying to play .mov files of my Panasonic camera.
The only workaround was to shut down the machine using the power button : the screen was full of shaggy colours and no answer of basic commands anymore, even not trying to change of screen to log into another session and "kill" that first one.

I don't understand why Totem is installed as default viewer if it is known to have issues. In 7.10 on another machine, Totem caused also problems for wmv & mov & avi's, and indeed I replaced it by mplayer, with good results.
it's not nice that Totem remains installed by default.

jm

---

### Post by William.fries.is.here on 2008-05-20
so how would i run mplayer or what not from the terminal?

---

### Post by cor2y on 2008-05-20
open the terminal and use gmplayer to play the file in question
```
 gmplayer
``` this will launch the gui version of mplayer and right click to get to the menu to open a file.

---

### Post by William.fries.is.here on 2008-05-20
gmplayer
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Model: 7, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/will/Desktop/untitled folder/game 12/drg12r1l.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  1000.0 kbps (122.1 kbyte/s)
Clip info:
 name: DareRing - Game 12 - Round 1 - 640x480
 author: [www.darering.com](www.darering.com)
 copyright: 2007
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Trying to force video codec driver family vfw...
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0x893a790]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Forced audio codec: mad
Trying to force audio codec driver family acm...
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wma9dmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
GNOME screensaver enabled  0.0% 0 0

---

### Post by mc4man on 2008-05-20
Have you rebooted since installing w32codecs?

if so and still doesn't work try removing and reinstalling mplayer

---

### Post by cor2y on 2008-05-20
Did you compile mplayer yourself?
its looking for w32codecs in /usr/local/lib
Check if its installed there the error is that.
So you have a choice of creating a symlink to the w32codec directory in /usr/local/lib or edit the mplayer.conf file so it points to where w32codecs are installed, if its from synaptic its installed in /usr/lib

---

### Post by William.fries.is.here on 2008-05-21
and how do you creaye a system link?

---

### Post by cor2y on 2008-05-21
Ok first off lets do a little experiment.
Lets locate wmv9dmod.dll to see if its on your system and if it is where exactly it is so you can create the symlink or move the files to the correct directory etc.
So via the terminal 
```
locate wmv9dmod.dll
``` Look at where wmv9dmod.dll is located on your hard drive if nothing shows up then the w32codecs are not installed, then you will have to install the w32codecs.
If it is installed and i bet it is in /usr/lib/codecs you can create a symlink or move the files to the old directory of /usr/lib/w32 
```
sudo cp /usr/lib/codecs /usr/lib/win32
```That directory /usr/lib/win32 was the old place where mplayer put the w32codecs now its /usr/lib/codecs which makes me think your version of mplayer is an old one.

---

### Post by William.fries.is.here on 2008-05-21
will@will-desktop:~$ locate wmv9dmod.dll
/usr/lib/codecs/wmv9dmod.dll
will@will-desktop:~$ sudo cp /usr/lib/codecs /usr/lib/win32
cp: omitting directory `/usr/lib/codecs'
will@will-desktop:~$ 


just did tht i'll reboto now to see if there is any effect.

---

### Post by William.fries.is.here on 2008-05-21
no effect seems to have happened
\

---

### Post by mc4man on 2008-05-21
If your using the repo versions of both mplayer and w32codecs (from medibuntu ) then mplayer will  first look in /usr/lib for win32. The repo ver. of w32codecs will install to /usr/lib/codecs and _create a folder link in /usr/lib named win32_ that targets codecs. (in hardy the target is simply codecs, in gutsy it's /usr/lib/codecs, same difference)
see screen shot for clarity. Maybe try a complete uninstall of mplayer and w32codecs, then install w32codecs followed by mplayer. Plus before installing look in /usr/lib and delete win32 (folder and or link)
Edit: 
Would be interesting to to know what ver. of ubuntu your using
> CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner that's some very dated hardware

---

### Post by cor2y on 2008-05-21
well its back to square one then.
```
sudo apt-get purge vlc totem totem-xine totem-gstreamer w32codecs mplayer
```
That should install all the media players, you will lose the mplayer-mozilla plugin and mplayer fonts as well when removing mplayer if those are installed but don't worry you can re-install that as well.
Remove the .mplayer file in your home directory either enable view hidden folders in nautilus (ctrl+h) or
```
rm ~/.mplayer
``` **NOTE rm is a very powerful command it COMPLETELY deletes something there is no getting it back when you use this command, using it here completely removes your local mplayer settings when you reinstall mplayer the folder will return with the mplayer default settings.**
Next lets add some repos if they have not been added first off the universe, restricted, multiverse repos of ubuntu if they have not been added. You can find these in System->Administration->Software Sources, make sure they are checked off as enabled if not do so now, next update the source file the dialogue to update appears when you hit the Close button, update it.
Next add the medibuntu repos [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu), make sure you pick the right repo for your version of ubuntu, follow the instructions there.
Now lets put back the removed media players all their plugins etc
```
 sudo apt-get install totem totem-xine libxine1-ffmpeg libxine1-plugins libxine1-misc-plugins libxine1-gnome totem-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mpegdemux gstreamer0.10-fluendo-mpegmux  vlc w32codecs mplayer mozilla-mplayer mplayer-fonts
```
Then try media playback again using all four players totem-gstreamer, totem-xine , vlc and mplayer
if it works in all four now you have a choice to make about which media player you will keep , all work great but totem-gstreamer while it can play dvds it cannot navigate dvd menus something you have to keep in mind if you want to navigate a dvd,vlc, mplayer and totem-xine can all navigate dvds.

---

### Post by William.fries.is.here on 2008-05-22
thanks for all your help by the way guys
 its nice to have a community that looks out for each other.
and help us ms defectors become a bit (no pun intended) more comfortable with linux
that said no progress yet.(pending a reboot)

two questions (thanks for your patience)

1) how do i modify/create  the folder to be a system link its telling me that i can't change any properties because the owner is "root"

2i ran  in to trouble at the removing mplayer directory

> will@will-desktop:~$ sudo apt-get purge vlc totem totem-xine totem-gstreamer w32codecs mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl libqt4-assistant libgtk-vnc-1.0-0
  obex-data-server librdf0 kdebase-runtime-data-common libqt4-test libqt4-dbus
  libqt4-qt3support librasqal0 libxosd2 libgmp3c2 kdelibs5-data libqtcore4
  libqt4-sql libqt4-svg libstreamanalyzer0 libqt4-xml vdr libqt4-network
  libqt4-designer libqtgui4 libpq5 libstreams0 vlc-plugin-pulse libraptor1
  libtar libqt4-script linux-headers-2.6.24-16-generic libavahi-ui0
  linux-headers-2.6.24-16 libopenobex1 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-mplayer* mplayer* mplayer-fonts* totem* totem-gstreamer*
  totem-plugins* totem-xine* vlc* w32codecs*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
After this operation, 61.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140396 files and directories currently installed.)
Removing mozilla-mplayer ...
Purging configuration files for mozilla-mplayer ...
Removing mplayer-fonts ...
Purging configuration files for mplayer-fonts ...
Removing mplayer ...
Purging configuration files for mplayer ...
Removing totem ...
Removing totem-plugins ...
Removing totem-gstreamer ...
Purging configuration files for totem-gstreamer ...
Removing totem-xine ...
Purging configuration files for totem-xine ...
Removing vlc ...
Purging configuration files for vlc ...
Removing w32codecs ...
will@will-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
will@will-desktop:~$ rm ~/.mplayer
rm: cannot remove `/home/will/.mplayer': Is a directory
will@will-desktop:~$  sudo apt-get install totem totem-xine libxine1-ffmpeg libxine1-plugins libxine1-misc-plugins libxine1-gnome totem-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mpegdemux gstreamer0.10-fluendo-mpegmux  vlc w32codecs mplayer mozilla-mplayer mplayer-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
libxine1-plugins is already the newest version.
libxine1-misc-plugins is already the newest version.
libxine1-gnome is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-fluendo-mp3 is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-base-apps is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-fluendo-mpegdemux is already the newest version.
gstreamer0.10-fluendo-mpegmux is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl libqt4-assistant libgtk-vnc-1.0-0
  obex-data-server librdf0 kdebase-runtime-data-common libqt4-test libqt4-dbus
  libqt4-qt3support librasqal0 libgmp3c2 kdelibs5-data libqtcore4 libqt4-sql
  libqt4-svg libstreamanalyzer0 libqt4-xml vdr libqt4-network libqt4-designer
  libqtgui4 libpq5 libstreams0 libraptor1 libqt4-script
  linux-headers-2.6.24-16-generic libavahi-ui0 linux-headers-2.6.24-16
  libopenobex1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  totem-plugins
Suggested packages:
  ladspa-sdk libdvdcss mozilla-plugin-vlc
Recommended packages:
  totem-plugins-extra totem-mozilla videolan-doc
The following NEW packages will be installed:
  mozilla-mplayer mplayer mplayer-fonts totem totem-gstreamer totem-plugins
  totem-xine vlc w32codecs
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.1MB of archives.
After this operation, 61.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mplayer.
(Reading database ... 139824 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_2%3a1.0~rc2-0ubuntu13+medibuntu1_i386.deb) ...
Selecting previously deselected package mozilla-mplayer.
Unpacking mozilla-mplayer (from .../mozilla-mplayer_3.50-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package mplayer-fonts.
Unpacking mplayer-fonts (from .../mplayer-fonts_3.5-2_all.deb) ...
Selecting previously deselected package totem-gstreamer.
Unpacking totem-gstreamer (from .../totem-gstreamer_2.22.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package totem-xine.
Unpacking totem-xine (from .../totem-xine_2.22.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package totem-plugins.
Unpacking totem-plugins (from .../totem-plugins_2.22.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package totem.
Unpacking totem (from .../totem_2.22.1-0ubuntu2_all.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package w32codecs.
Unpacking w32codecs (from .../w32codecs_20071007-0medibuntu2_i386.deb) ...
Setting up mplayer (2:1.0~rc2-0ubuntu13+medibuntu1) ...

Setting up mozilla-mplayer (3.50-1ubuntu2.1) ...
Setting up mplayer-fonts (3.5-2) ...

Setting up totem-gstreamer (2.22.1-0ubuntu2) ...

Setting up totem-xine (2.22.1-0ubuntu2) ...

Setting up totem-plugins (2.22.1-0ubuntu2) ...
Setting up totem (2.22.1-0ubuntu2) ...
Setting up vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) ...

Setting up w32codecs (20071007-0medibuntu2) ...
will@will-desktop:~$ 


---

### Post by cor2y on 2008-05-22
This isn't windows where you need to reboot for everything :)
Sorry about the .mplayer bit its
```
rm -r ~/.mplayer
```
As for creating a symlink ALT+F2 then type ```
gksu nautilus
```
Now you will have a root version of nautilus and you can create symlinks in the root section by simply right clicking on the item/folder you wish to create a symlink for.

---

### Post by Corvair on 2008-06-01
Hello every one,

I have the same problem. I can't play wmv files.I have gone through this thread and can't install the 32 codecs

claude@claude-desktop:~$ claude@claude-desktop:~$ sudo apt-get install w32codecs
bash: claude@claude-desktop:~$: command not found
claude@claude-desktop:~$ Reading package lists... Done
bash: Reading: command not found
claude@claude-desktop:~$ Building dependency tree       
bash: Building: command not found
claude@claude-desktop:~$ Reading state information... Done
bash: Reading: command not found
claude@claude-desktop:~$ Package w32codecs is not available, but is referred to by another package.
bash: Package: command not found
claude@claude-desktop:~$ This may mean that the package is missing, has been obsoleted, or
bash: This: command not found
claude@claude-desktop:~$ is only available from another source
bash: is: command not found
claude@claude-desktop:~$ E: Package w32codecs has no installation candidate
bash: E:: command not found
claude@claude-desktop:~$ claude@claude-desktop:~$ 
bash: claude@claude-desktop:~$: command not found
claude@claude-desktop:~$ 
claude@claude-desktop:~$ 


I have both hardy medibuntu repos checked.

I have removed and reinstalled mplayer and VLC player.
Totem movie player tells me: This file is encrypted and cannot be played
VLC player gives a weird scrambled window and no sound.)

Any suggestions?


:P

---

### Post by Pjotr123 on 2008-06-02
> **Corvair said:**
> Hello every one,

I have the same problem. I can't play wmv files.I have gone through this thread and can't install the 32 codecs

claude@claude-desktop:~$ claude@claude-desktop:~$ sudo apt-get install w32codecs
bash: claude@claude-desktop:~$: command not found
claude@claude-desktop:~$ Reading package lists... Done
bash: Reading: command not found
claude@claude-desktop:~$ Building dependency tree       
bash: Building: command not found
claude@claude-desktop:~$ Reading state information... Done
bash: Reading: command not found
claude@claude-desktop:~$ Package w32codecs is not available, but is referred to by another package.
bash: Package: command not found
claude@claude-desktop:~$ This may mean that the package is missing, has been obsoleted, or
bash: This: command not found
claude@claude-desktop:~$ is only available from another source
bash: is: command not found
claude@claude-desktop:~$ E: Package w32codecs has no installation candidate
bash: E:: command not found
claude@claude-desktop:~$ claude@claude-desktop:~$ 
bash: claude@claude-desktop:~$: command not found
claude@claude-desktop:~$ 
claude@claude-desktop:~$ 


I have both hardy medibuntu repos checked.

I have removed and reinstalled mplayer and VLC player.
Totem movie player tells me: This file is encrypted and cannot be played
VLC player gives a weird scrambled window and no sound.)

Any suggestions?


:P

Apply this simple how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Greetz, Pjotr.

---

### Post by Corvair on 2008-06-02
Hi,

Thanks for the tip.
I tried everything in this ubuntutip.
I can't find the libdvdcss2.

---

### Post by Pjotr123 on 2008-06-03
> **Corvair said:**
> Hi,

Thanks for the tip.
I tried everything in this ubuntutip.
I can't find the libdvdcss2.

Then you haven't applied the how-to to the letter. Repeat the how-to and use copy/paste for all code lines, in order to avoid mistakes.

---

### Post by Corvair on 2008-06-03
OK, thanks for the reply.

I tried twice, I will try again to see what I missed

---

### Post by Corvair on 2008-06-03
Here is my sources list.
The Medibuntu non free is there.
Does anything look suspicious in here?


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy main restricted
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-updates main restricted
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security main restricted
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security universe
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-updates main multiverse universe
deb-src [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-updates main multiverse universe #Added by software-properties
deb [http://ftp.ucr.ac.cr/ubuntu/](http://ftp.ucr.ac.cr/ubuntu/) hardy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by Pjotr123 on 2008-06-03
Not good, Corvair: you have Medibuntu twice. Also for Feisty (a few lines above the good line). Wipe the Feisty line and you should be fine.  :-)

---

### Post by Corvair on 2008-06-03
deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Which one of these two do I have to remove, or do I have to remove both?


I have removed the extra medibuntu line

---

### Post by Pjotr123 on 2008-06-03
> **Corvair said:**
> deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Which one of these two do I have to remove, or do I have to remove both?


I have removed the extra medibuntu line

There should be no Feisty lines at all in your sources list..... How did they get there?

---

### Post by Corvair on 2008-06-03
I don't know how feisty got there.

Now I get this response


claude@claude-desktop:~$ deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
bash: deb: command not found
claude@claude-desktop:~$

---

### Post by Pjotr123 on 2008-06-03
> **Corvair said:**
> I don't know how feisty got there.

Now I get this response


claude@claude-desktop:~$ deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
bash: deb: command not found
claude@claude-desktop:~$

Corvair, please.... just apply the how-to. This line is not a terminal line, it's supposed to be in the sources list. As stated in the how-to.

---

### Post by Corvair on 2008-06-03
Thanks for your patience and your help.

I finely have loaded the libdvdcss2 file
and completed the ubuntutip.

I tried viewing a wnv file and I am still told that the file is encoded and cannot view.

Maybe the file is corrupted.

---

### Post by amir1 on 2008-06-16
I have the exact same problem. went through many forums and tips and applied them all nothing works. 
I have installed w32codec and a lot more
totem refuses to play 

i am beginning to hate hardy. everything was fine before my upgrade. :confused:

---

### Post by CoYoT_ on 2008-06-18
Hi,

had the same problem after upgrading from Feisty to 8.10. All answers on forums didn't help so i tried to figure it out myself and it turned out the permissions on the codecs directory were fcked up. A quick
```
chmod -R 777 /usr/lib/codecs
```
and creating a symlink /usr/lib/win32 to /usr/lib/codecs (i was missing it too) solved the problem.
Dist-upgr sucks sometimes :/

Cheers,

Wojtek

---

