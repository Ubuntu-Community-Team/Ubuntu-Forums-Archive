---
title: "libdvdcss2, libdvdnav4, xine1-ffmpeg, still no DVD playback"
date: 2008-10-08
forum: Multimedia Software
---

### Post by 24601 on 2008-10-08
I know that a lot of people have posted about DVD playback problems in Ubuntu Hardy, and I have read a dozen help pages that recommend VLC, libdvdcss2, libdvdnav4, lib, totem-xine, libxine1-ffmpeg... I have tried every approach in these threads and I cannot play back any DVDs.  And YES, I have properly installed /usr/share/doc/libdvdread3/install-css.sh multiple times over.

VLC gives me a "cannot get next block" message, suggesting that this is still a DVD encryption problem

Totem-xine plays 3-12 seconds of intro and then dead-freezes X, and X can't even be reset or switched to command line (keyboard lockup).

I even tried adding a soft-link called plugins from the /usr/lib/xine/plugins to /home/xxxxx/.xine/, since this resolved one poster's problems in an earlier thread.  No dice.

Does anybody have ANY ideas on where to go from here?  I'm trying to get a very basic, very friendly Ubuntu system working for my mother-in-law.  If she can't even watch DVDs, though, it's not going to be very useful for her, and I'm going to end up fixing Vista every other week.

---

### Post by Steve1961 on 2008-10-08
Open a terminal and type the following (or copy and paste):

```
mv ~/.dvdcss ~/.dvdcss.ORIGINAL
```

Then try playing a DVD again and see if it makes a difference

---

### Post by 24601 on 2008-10-08
VLC now seems to play a second or so of *something* (timer bar appears and begins moving) but it doesn't even load any video output and dies immediately.  Still getting the same debug message:

dvdnav warning: cannot get next block (Error reading NAV packet.)

---

### Post by Steve1961 on 2008-10-08
> **24601 said:**
> VLC now seems to play a second or so of *something* (timer bar appears and begins moving) but it doesn't even load any video output and dies immediately.  Still getting the same debug message:

dvdnav warning: cannot get next block (Error reading NAV packet.)

Strange, are you sure the dvd player is working ok?  VLC will usually play just about anything, but if not xine usually does the job, although you will need the w32codecs package from the medibuntu repositories.  Worth a try if you haven't already tried that.

---

### Post by 24601 on 2008-10-08
> **Steve1961 said:**
> Strange, are you sure the dvd player is working ok?  VLC will usually play just about anything, but if not xine usually does the job, although you will need the w32codecs package from the medibuntu repositories.  Worth a try if you haven't already tried that.

I suppose I can't rule out a problem with the DVD player, but I can read the contents of the DVD just fine, and I haven't had any problems running CDs.  

I actually tried Medibuntu a few days ago, had no results, and removed it from my sources.  Maybe I'll give them another go.  Thanks for the help, though.

---

### Post by Steve1961 on 2008-10-08
You're welcome.  Medibuntu also provides a newer version of libdvdcss2 so upgrade to that as well.

---

### Post by 24601 on 2008-10-08
> **24601 said:**
> 
I actually tried Medibuntu a few days ago, had no results, and removed it from my sources.  Maybe I'll give them another go.  Thanks for the help, though.

Just added the Medibuntu repository again, reinstalled libdvdcss2 from their version, and attempted to add w32codecs (learned I already have them from a previous attempt).  No changes.

---

### Post by Steve1961 on 2008-10-08
In that case I'm out of ideas.  Perhaps someone else has other suggestions?  Anyway, good luck :confused:

---

### Post by mc4man on 2008-10-08
Have you checked to see if a region has been set on the drive?
If not install regionset and with a dvd in the drive run ```
regionset
``` from the terminal.

If it says 'set' around the 4th line the answer no and exit, if not then set a region

---

### Post by 24601 on 2008-10-08
> **mc4man said:**
> Have you checked to see if a region has been set on the drive?
If not install regionset and with a dvd in the drive run ```
regionset
``` from the terminal.

If it says 'set' around the 4th line the answer no and exit, if not then set a region

I set the region and VLC now plays the menu audio, very choppy.  No video at this point.  Is this a separate problem entirely, or have I just not figured out my DVD encryption problem yet?

---

### Post by mc4man on 2008-10-08
Try adjusting your your audio and video output modules.

Open vlc -> settings -> preferences. Enable the 'show advanced options' (ck.box lower right.) Then expand audio, highlight Output modules, and in the dropdown on right side change from 'default' to something specific. (try alsa
Do the same for the video, start by choosing the Xv ext...... Then click 'save' and try vlc again.
 
Before trying vlc again right click on Applications -> edit menus. Highlight sound and video and on the right side right click on vlc -> properties. Change the command to ```
vlc %f
```

If the Xv ext. isn't working go back into setting and this time try X11. Remember to click save. 

If your still having issues start vlc from the terminal, go file -> open disc, and post the terminal output.

---

### Post by 24601 on 2008-10-08
> **mc4man said:**
> Open vlc -> settings -> preferences. Enable the 'show advanced options' (ck.box lower right.) Then expand audio, highlight Output modules, and in the dropdown on right side change from 'default' to something specific. (try alsa
Do the same for the video, start by choosing the Xv ext...... Then click 'save' and try vlc again.
 
Before trying vlc again right click on Applications -> edit menus. Highlight sound and video and on the right side right click on vlc -> properties. Change the command to ```
vlc %f
```

If the Xv ext. isn't working go back into setting and this time try X11. Remember to click save. 


This did the trick.  Totem is still a disaster, but VLC now plays DVDs (set to ALSA, X11), and I think I can work out the bugs from here.  Thanks for all of the help!

---

### Post by mc4man on 2008-10-08
System wide settings are available in Systems -> preferences -> sound for audio and preferences -> multimedia systems selector for video. If multimedia systems selector isn't available then enable in edit menus ->preferences

---

### Post by jlh on 2008-10-10
VLC has always been fine for me on DVDs.  But since I installed 0.9.2 and subsequent upgrades, vlc won't play DVDs.  Audio, for files, CDs and shoutcast streams, is fine.  For DVDs, however, the most I get is a frame that freezes.

VLC 0.8.6f worked fine.  In fact, despite trying to remove it, that version is still installed, and still works fine - shows DVDs.  Indeed, vlc at the command line still launches that version.  To launch v.0.9.4, I have to call /usr/bin/vlc.

Other media players - totem, mplayer, gnome player - all play DVDs as well.  So it does not look like a codec issue.

Any ideas.

---

### Post by 24601 on 2008-10-10
Try messing with your output modules (see mc4man's posts above).  That made all the difference for me when VLC was freezing on DVD playback.

---

### Post by jlh on 2008-10-10
Yep.  Been there.  Done that. No help.

---

### Post by 24601 on 2008-10-10
I don't even know where to begin in that case.  Try posting your debug messages (VLC -> View -> Messages) or running from the command line and posting the output.  If I can't make any sense of it, maybe one of the more experienced posters will have an idea.

---

### Post by cor2y on 2008-10-10
it may just be a case of a non region 1 dvd.
I almost pulled my hair out a few months ago trying to figure out why Blade Trinity wouldn't play correctly in Linux for me, i'd be able to watch the beginning of the movie but half way through it would spit up an error about the disc being encrypted and on the extras dvd i could never get past the dvd menu.
I had reinstalled/compiled versions of libdvdcss libdvdnav, libdvdread not to mention custom compiles of mplayer, vlc and totem , turns out it was the dvd itself, defective by design, i got it at a flea market cheaply but its not a region 1 (dvd for the united states) dvd i didn't know this because my stand alone dvd players are all region free.
Anyhow the region the dvd is from (region 2 Europe) has terrible insane copy protection/disc check errors to ensure it won't be ripped/backuped this is not a problem for standalone or windows based dvd players/dvd backup programs like clonedvd etc since fixes have been issued for that but for libdvdcss libdvdnav libdvdread there are no fixes for this type of protection.

---

### Post by mc4man on 2008-10-10
The latest libdvdnav4 can help with playback of some structure protected titles (dvd-protect, x-protect)
There are definitely a couple that can't be played back using unlicensed players (two that I've seen from universal studios).

the intrepid version of libdvdnav4 is suitable for use on feisty thru hardy. (don't uninstall current libdvdnav4, just dl. and let GDebi handle
[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)

as is the latest libdvdcss2 (for i386, middle of the page, listed as below

"libdvdcss2_1.2.10-0.2medibuntu1_i386.deb	2008-Sep-10 21:30:10	35.9K"

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)


> VLC 0.8.6f worked fine. In fact, despite trying to remove it, that version is still installed, and still works fine - shows DVDs. Indeed, vlc at the command line still launches that version. To launch v.0.9.4, I have to call /usr/bin/vlc.
How you managed to have both versions i don't know, I'd purge vlc completely and install one or the other, for 8.10 I'd use 0.9.4

---

### Post by jlh on 2008-10-13
Here's my terminal output when I launch

vlc 0.8.6f, and after that
vlc 0.9.4

v.0.8.6f plays dvds fine.  v.0.9.4 not at all.

jay@jay-laptop:~$ vlc
VLC media player 0.8.6f Janus
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
[00000254] main playlist: nothing to play
[00000268] main interface error: option dvdnav-caching does not exist
[00000268] main interface error: option dvdnav-caching does not exist
[00000268] main interface error: option dvdnav-caching does not exist
[00000268] main interface error: option dvdnav-caching does not exist
[00000268] main interface error: option dvdnav-caching does not exist
[00000290] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000254] main playlist: stopping playback
jay@jay-laptop:~$ /usr/bin/vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--mandir=/share/man' '--infodir=/share/info' '--host=i486-linux-gnu' '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-real' '--enable-realrtsp' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-faad' '--with-faad-tree=extras/faad2' '--enable-x264' '--with-x264-tree=extras/x264' '--enable-glide' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'host_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'PKG_CONFIG_PATH=:extras/x264:extras/faad2'
[00000001] main libvlc debug: translation test: code is "C"
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HARVEST
libdvdnav: DVD Serial Number: 2AFE5618
libdvdnav: DVD Title (Alternative): HARVEST
libdvdnav: Unable to find map file '/home/jay/.dvdnav/HARVEST.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x001b496a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x001b54e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001f8e55
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00201b9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00211cd8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0025863d
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0

---

### Post by zcats on 2008-10-19
I have the same problem and this is also driving me nuts! Can play the encrypted video DVD in Windows using VLC but NOT in Ubuntu Hardy with libdvdcss2 and libdvdread3 libdvdnav4 (all from medibuntu).  Tried a bunch of the players available from the repos...(e.g.Xine, VLC, totem, ogle) and NONE work (garbled display).
*So strange why it works with VLC windows but not VLC linux??!?!?!?! :?  
(still dual booting this lappy..but not wanting to!)

I have searched ubuntu forums and googled away, but (unusually) no help to be found that solves this problem for me. Help!

Thought that maybe there needs to be "unhide" added to the CD/DVD device to see the encrypted files. ie
>sudo gedit /etc/fstab
/dev/scd0       /media/cdrom0   auto    unhide,user,exec,noauto 0	0
But still cannot see hidden files...? :cry:
Please someone help degub or interpret these errors with VLC/Ogle
>>Error with vlc:
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x002e0d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x002e0d77
libdvdread: Elapsed time 0
libdvdread: Found 17 VTS's
libdvdread: Elapsed time 0
[00000477] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
[00000494] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
Segmentation fault

>>Error with ogle:
 skipped blocks in I-picture
*** invalid macroblock type
*** skipped blocks in I-picture
*** invalid macroblock type
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
*** invalid macroblock type
*** invalid macroblock type
**** DP remove this when implemented
*** invalid frame motion type
Using Hardy LTS with all updates (main,universe, multiverse, backports,proposed plus medibuntu repo). 

Thanks
T42 Laptop 1.7 GHz, 2 GB RAM, Radeon Mobility 7500

---

