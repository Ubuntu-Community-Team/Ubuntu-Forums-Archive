---
title: "Playing (newer?) DVDs"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by lode on 2008-02-04
Hi

I'm having trouble playing DVDs. Older DVDs tend to work, but nearly everything released since last year or so won't play. At the moment I'm trying to watch the last season of The Sopranos, without any avail, so far.

(This really pisses me off, those DVDs cost a bunch of money and I can't even play them the way I want to.) 

I have already installed libdvdread3, libxine1-ffmpeg, totem-xine, build-essential, debhelper, fakeroot and ran 'sudo /usr/share/doc/libdvdread3/install-css.sh' (as described [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")). 

Totem (xine) says:

```
Totem could not play 'dvd:/'.

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
```

VLC spins the disc but then nothing happens.

gxine says:

```
The xine engine failed to start.

No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.
```


Kaffeine says:

```
The source can't be read.

Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd)
```

and/or

```
No plugin found to handle this resource (dvd://)

Details:

02:35:33 PM: xine: cannot find input plugin for MRL [dvd://]
02:35:33 PM: xine: input plugin cannot open MRL [dvd://]
02:35:33 PM: xine: found input plugin : DVD Navigator
```

Does anyone have any idea?

Big thanks beforehand...

---

### Post by mc4man on 2008-02-04
sticking strictly with vlc there are only 3 libs needed for _dvd_ playback - libdvdcss2, libdvdnav4, and libdvdread3. Check your version of libdvdcss2 - get it up to 1.2.9. If still no playback then other non codec related factors are cause
run vlc thru terminal, open disc and post result

---

### Post by stooshbunutu on 2008-02-04
Have you tried installing the latest version of mplayer for DVDs, i have and its pretty good. Also it installs alot of other useful plugins

Hope this helps:)

---

### Post by lode on 2008-02-04
I (think I correctly) updated libdvdcss2 to version 1.2.9, but that doesn't seam to help much, I'm affraid.

This is wat VLC says when ran through the terminal:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: SOPRANOS_SEASON6_FINAL_DISC2
libdvdnav: DVD Serial Number: 372756C8
libdvdnav: DVD Title (Alternative): SOPRANOS_SEASON6_FINAL_DISC2
libdvdnav: Unable to find map file '/home/lode/.dvdnav/SOPRANOS_SEASON6_FINAL_DISC2.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000120)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000870)
[00000292] dvdread demuxer error: read failed for -1/4 blocks at 0xeda
[00000281] main playlist: nothing to play
```

---

### Post by lode on 2008-02-04
> **stooshbunutu said:**
> Have you tried installing the latest version of mplayer for DVDs, i have and its pretty good. Also it installs alot of other useful plugins

Hope this helps:)

Mplayer (MPlayer 2:1.0~rc1-0ubuntu13.1) does open the disc, but hangs terribly after a second or so.

This is what the terminal had to say about that (trying to play the DVD in mplayer):

```
Playing dvd://1.
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
There are 4 titles on this DVD.
There are 8 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000120)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000870)
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: da
subtitle ( sid ): 2 language: nl
subtitle ( sid ): 3 language: fi
subtitle ( sid ): 4 language: no
subtitle ( sid ): 5 language: pt
subtitle ( sid ): 6 language: sv
subtitle ( sid ): 7 language: en
number of subtitles on disk: 8
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
a52: CRC check failed!  
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  2.521 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
a52: error at resampling
a52: CRC check failed!  
a52: CRC check failed!  
a52: CRC check failed!  
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  0.825 ct:  0.004   2/  2 ??% ??% ??,?% 1 0              
a52: CRC check failed! 
```

Those a52 errors (whatever they may be) kept on appearing until I killed the dying mplayer process.

:(

---

### Post by mc4man on 2008-02-04
The error cracking keys is what's stopping playback, ck. and post dvd region of disc, region that player is set to, and model of dvd drive.  Adding more codecs, players, ect. will not help

---

### Post by lode on 2008-02-04
The DVD's region is 2. This is what I got on my drive:

```
id:      cdrom
description: 	DVD-RAM writer
product: 	DVD-RAM UJ-852
vendor: 	MATSHITA
physical id: 	
0.0.0
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/dvd
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	RB01
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	ready
id:	
disc
physical id: 	
0
logical name: 	
/dev/cdrom
```

I'm afraid I don't really know how to check the region the drive's set to.

---

### Post by ron999 on 2008-02-04
To find your drive's region setting install 'regionset' from the repo.
To run it, put a dvd in the drive and type regionset.
It will tell you which region that the drive's set to and how many more changes you are allowed to make.
It will also let you change the region, if you want to.

---

### Post by lode on 2008-02-04
This is wat regionset gave me:

```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:n
```

Is it normal there currently isn't anything displayed after 'Current Region Code settings:'?

I didn't type 'y' on that last question just yet, just to be sure (since it seams I only get five chances to get this right?).

---

### Post by mc4man on 2008-02-04
You should have drive set to region your in or to what region the majority of your disks are. (probably region2)
In most cases vlc can play disks from other regions though there are some exceptions and in most of those cases there is a workaround. 
 note: most mashitu drives will not allow playback from region mismatch

edit; in the rare case where you have lets say a region 1 that won't playback in vlc with a region 2 drive here's a workaround - requires 2nd drive or some help from "friend"
[http://ubuntuforums.org/showthread.php?t=657516&page=3](http://ubuntuforums.org/showthread.php?t=657516&page=3)  last post

---

### Post by ron999 on 2008-02-04
Hi lode
It works like this:-
When the drives are manufactured they are unset.
If you use Windows, the first time you play a DVD the drive gets set automatically to the region of that DVD.
But with Linux that doesn't happen. It's up to you to set the region yourself.
But it's only possible to change the region 4 more times once it's been set (You are right). After that you're supposed to return it to be set by the manufacturer, or else find a hack to do it yourself.
Usually VLC doesn't give a damn which region your drive's set to. And it doesn't care whether it's even unset.
So up to now you've been getting by with an unset drive. Mine's like that too.
But maybe the encryption on those new Soprano discs is more picky. Perhaps you'll have to set the drive to the correct region to get them to play.

edit mc4man beat me to it!

---

### Post by mc4man on 2008-02-04
@lode I missed your earlier post about drive model - if your mashitu drive behaves like most recent mashitu drives you will _not_ playback discs from other regions - period
The behavior of these drives is not to allow access to encrypted sectors when a region mismatch is found. There are a few mashitu drives where region free firmware is available, just desktop models though. Keep that in mind when purchasing titles

---

### Post by lode on 2008-02-04
Thanks guys, it (kinda) worked!

Now VLC opens and plays all DVDs...

except this one with the episodes on I was just trying to see (oh the bitter irony...).

All DVDs from the box set work perfectly, while this one DVD gives very sloppy image quality -- making it unwatchable (see added screenshot).

This is the DVD I've been testing with all the time. Could it be I broke it in the process? I don't see any scratches on it, though.

---

### Post by mc4man on 2008-02-04
try going into home directory - show hidden files and look for .dvdcss folder. Find the sopranos folder(s) and shift/delete it. Then try again

---

### Post by lode on 2008-02-04
Thanks!

Again I learned that the open source community is amazing --

and that I'm not purchasing any new DVDs anytime soon.

---

### Post by mc4man on 2008-02-04
> and that I'm not purchasing any new DVDs anytime soon
With that Mashitu drive keep to region 2 - i have one in a laptop and while the .dvdcss file swap will work with other drives nothing can force mashitu's to play from other regions

---

