---
title: "Troubles with DVDs &amp; audio CDs"
date: 2008-06-11
forum: Multimedia Software
---

### Post by HyperHacker on 2008-06-11
Neither of these seem to be working properly after following all the instructions in the sticky threads.

DVDs: Working in Totem but no subtitles or menus. mplayer gives the same output for every DVD and video output driver:
> hyperhacker@Mercury:~$ mplayer -dvd-device /media/DOT_HACK dvd:///
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd:///.
There are 17 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  3000.0 kbps (375.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
V:   0.7  16/ 16 39%  4%  0.0% 0 0 

Exiting... (End of file)A video window appears and disappears, and that's it. For some reason the discs are mounted as /dev/dvd1 instead of /dev/dvd, but pointing it at that or /media/<name of disc> doesn't help.

Xine won't install: > Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidateI've used VLC before and ended up switching to mplayer because I was sick of it. >_>


CDs: Again, for some reason they mount as /dev/cdrom1 instead of /dev/cdrom. Amarok plays them but it takes several minutes to read the track list. mplayer won't play these either: > hyperhacker@Mercury:~$ mplayer cdda://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing cdda://.
Can't open CDDA device.
Failed to open cdda://.


Exiting... (End of file)


I'm wondering if it's safe to just symlink /dev/cdrom -> /dev/cdrom1 and /dev/dvd -> /dev/dvd1, that might fix some things, but by the looks of it mplayer has more problems than that, and I'd like to get it working as it's by far my favourite video player. (Worked great on Windows, works great for video files on Xubuntu, just can't get it to deal with discs...)

---

### Post by mc4man on 2008-06-12
Take a look here, sounds similar, any questions ask or post relevant info
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

---

### Post by HyperHacker on 2008-06-12
Thanks, almost everything is working after fixing the links and rebooting. DVDs don't seem to work well in mplayer though (and still no subtitles in Totem). If I use "dvd:///" it plays the first title (FBI blah blah), and I can skip through them, but when I get to the 5th (still not the actual movie <_<) it stops and returns to the first, sometimes with the error "No stream found to handle url dvd://0" (or another number).
If I use "dvdnav://" I see the menu but can't select anything, and it gives the error "INIT ERROR: couldn't get init pos New position not yet determined."
The only way to actually watch the movie is to manually specify each chapter on the command line one after another until I find it. :-/ I'd like to get mplayer working since it has some useful features other players don't seem to have (remote control from other programs, etc) and better subtitle support than I've seen from others.

Audio CDs seem to skip and stutter in mplayer, but they play fine in Amarok so it's not a big deal.

---

### Post by mc4man on 2008-06-12
For straight up playing dvd disks w/ mplayer why not use smplayer (latest ver.) for control, leave cli mplayer for specific tasks. (has access to logs for troubleshooting)
Totem-xine is better function wise and easier to config., for hardy just install it and see here - about 1/2 way down
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by HyperHacker on 2008-06-12
Hm, smplayer doesn't have the menus and doesn't play any sound. :-/

---

### Post by fred.warren on 2008-08-02
Hi I just solved this problem myself and will be filing a bug report.

Thunar has the association for audio cds cdda:/ instead of the proper cdda:// and for dvds as dvd:/ instead of dvd://

To correct this do the following
[LIST=1]
[*]Open Thunar (Can be found on the Menu under Accessories)
[*]From the menu at the top of Thunar select **_E_dit**
[*]From the **_E_dit** menu select **Pr_e_ferences**
[*]From the **File Manager Preferences** dialog, click on the tab labeled **Advanced**
[*]From the **Advanced** tab click on the blue linked word **Configure**
[*]From the **Removable Drives and Media** dialog, click on the tab labeled **Multimedia**
[*]From the **Multimedia** tab for the **Audio CDs _C_ommand** locate the entry **totem cdda:/**
[*]Change that to **totem cdda://**
[*]From the **Multimedia** tab for the **Video CDs/DVDs C_o_mmand** locate the entry **totem dvd:/**
[*]Change that to **totem dvd://**
[*]Close all dialogs and exit Thunar
[*]Insert your CD or DVD and enjoy
[/LIST]

---

### Post by darthchaosofrspw on 2009-07-27
Here's how to do it across the board on Hardy.

1. Hit Alt+F2 and enter the command **gksudo mousepad /etc/xdg/Thunar/volmanrc**. Enter your password if asked to do so.
2. Change **AutoplayAudioCdCommand=totem cdda:/** to **AutoplayAudioCdCommand=totem cdda://**
3. Change **AutoplayVideoCdCommand=totem dvd:/** to **AutoplayVideoCdCommand=totem dvd://**
4. Save and exit.
5. Pop in a CD or DVD to make sure Totem autoplays.

I have a customized system where I removed Totem and replaced it with Xine. I also installed Rhythmbox. My DVDs autoplay in Xine, and my CDs automatically bring up Rhythmbox so I can rip them or play them (they don't autoplay). So my volmanrc entries look like this:

[B]AutoplayAudioCdCommand=rhythmbox cdda:/
AutoplayVideoCdCommand=xine dvd:/[/B]

---

### Post by andrew.46 on 2009-07-28
Hi HyperHacker,

> **HyperHacker said:**
> Audio CDs seem to skip and stutter in mplayer

Don't give up on MPlayer yet for audio cds. Try adding cache:

```
mplayer -cache 2048 -cache-min 80 cdda://
```

and if your copy of MPlayer is set correctly you can also access a cddb:

```
mplayer -cache 2048 -cache-min 80 cddb://
```

All the best,

Andrew
[B]
Edit:[/B] Oops, did not realise I was necroposting :-).

---

