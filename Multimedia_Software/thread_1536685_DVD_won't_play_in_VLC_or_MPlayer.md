---
title: "DVD won't play in VLC or MPlayer"
date: 2010-07-22
forum: Multimedia Software
---

### Post by JRod37 on 2010-07-22
Sorry if this is a repost, but I can't seem to find the magic Google search syntax that will give me the answer to my question from anywhere.

I'm using 10.04, trying to play a DVD on my drive. I downloaded both VLC and MPlayer including all of the restricted codecs available in synaptic. Also tried installing ffplayer, but that was just a cluster.

When I press play the DVD plays for about 1 second on a black screen and then stops in VLC. MPlayer at least tries to scroll through all the files, but the same thing happens on each "chapter" of the disc.

Since I can't seem to find anything anywhere on any forums about this, someone please, please, please, please help me out. I'm not much of a multimedia guru, but I know enough to know that I need a codec to play filetypes. I also know how to install them.

---

### Post by ajgreeny on 2010-07-22
libdvdcss2 installed?

If not enable medibuntu and follow the instructions on [http://www.medibuntu.org/](http://www.medibuntu.org/)

EDIT:
wojox's answer below is another way of getting to the same place without medibuntu.

---

### Post by wojox on 2010-07-22
```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Rebooting may be necessary.

---

### Post by techunit on 2010-07-22
You may need to install Ubuntu restricted extras

something like

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by andrew.46 on 2010-07-22
Hi JRod,

> **JRod37 said:**
> When I press play the DVD plays for about 1 second on a black screen and then stops in VLC. MPlayer at least tries to scroll through all the files, but the same thing happens on each "chapter" of the disc.

Could you try playing the dvd from the commandline in the following manner:

```
mplayer -v dvd://1
```

and then post the full terminal output here? The error messages should give a good indication of what is going wrong...

Andrew

---

### Post by JRod37 on 2010-07-22
Thanks gang. Can't get to it at the moment. Stay tuned.

---

### Post by JRod37 on 2010-07-27
Ok, folks. I'm back. 

I did this: mplayer -v dvd://1 and got the following message:

Playing dvd://1.
get_path('sub/') -> '/home/leder/.mplayer/sub/'
URL: dvd://1
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
Reading disc structure, please wait...
There are 12 titles on this DVD.
There are 1 angles in this DVD title.
DVD successfully opened.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
number of subtitles on disk: 3
DVD start cell: 0  pack: 0x0-0x102A8  
DVD start=0 end=3850416  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x102A8  
stream_seek: WARNING! Can't seek to 0x0 !
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x102A8  
stream_seek: WARNING! Can't seek to 0x0 !
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x102A8  
stream_seek: WARNING! Can't seek to 0x0 !

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)


So I did what wojox suggested and ran sudo /usr/share/doc/libdvdread4/install-css.sh without the reboot.

After that MPlayer, GNOME MPlayer and the default movie player all did something similar. They would play everything until the main menu. I reran mplayer -v dvd://1 with this output:

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
extended cpuid-level: 8
extended cache-info: 16810304
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 0 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/leder/.mplayer/codecs.conf'
Reading /home/leder/.mplayer/codecs.conf: Can't open '/home/leder/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'dvd://1'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/leder/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/leder/.mplayer/input.conf'
Can't open input config file /home/leder/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/leder/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/leder/.mplayer/sub/'
URL: dvd://1
libdvdread: Using libdvdcss version 1.2.10 for DVD access
Reading disc structure, please wait...
There are 12 titles on this DVD.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_03_0.IFO).
Cannot open the IFO file for DVD title 3.
No stream found to handle url dvd://1

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)

Any ideas? After I post this I will reboot and post an update ONLY if this fixes the problem. If no further post assume the problem still exists.

---

### Post by Vaphell on 2010-07-27
from [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by JRod37 on 2010-07-27
I was able to get the DVD to play in Movie Player. I'm going to uninstall MPlayer and reinstall to see if that fixes MPlayer. I am also going to now install VLC and see if the issue still exists there.

Looks like it was the css issue.

Thanks, everyone. I'll post a followup for VLC and MPlayer.

---

### Post by JRod37 on 2010-07-27
It did not fix the issue for MPlayer, but VLC is working great! That's my player of choice anyway. I'm going to let the MPlayer issue lie.

Thanks everyone for all of your help. I'll try to change the heading of this post to SOLVED, but since this is my first resolved issue it may take me a little to figure it out.

---

### Post by JRod37 on 2010-07-28
If someone could be so kind as to explain why this worked I'd appreciate it. Nice to know that it works, but I'm the type of person that would like to know WHY it worked. What is the CSS in relation to video players? How does it work? Why does a video player need a CSS built?

---

### Post by mc4man on 2010-07-28
With the exception of a title here and there most all commercial dvd movies are css encrypted.
Licensed players like powerdvd, windvd, ect. and hardware standalone dvd players have the means to decrypt the content.

Unlicensed and open source players cannot  - so they need the assistance of a lib that can - that's what libdvdcss2 does.

---

### Post by MysticEdge on 2010-12-27
> **wojox said:**
> ```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Rebooting may be necessary.

Hey, Just wanted to say I had the same problem and I tried these two commands for both my desktop and laptop and now they both work perfectly for DVDs. Thank you very much wojox.

---

### Post by Randall on 2011-01-22
> **JRod37 said:**
> It did not fix the issue for MPlayer, but VLC is working great! That's my player of choice anyway. I'm going to let the MPlayer issue lie.


Hi JRod37,
Just curious- did you ever sort out what was wrong with mplayer? I'm having similar issues with 10.04 where DVDs play just fine with vlc and totem, but do not work with mplayer.
Thanks,
Randall.

---

### Post by mc4man on 2011-01-22
> I'm having similar issues with 10.04 where DVDs play just fine with vlc and totem, but do not work with mplayer.

The command posted here for mplayer is assuming the main movie (or any 'playable' title) is title 1 (the -v is for verbose terminal output. 
While quite common it's not assured title 1 is anything that can be played (up to 99 titles are allowed on a dvd movie disk
so
mplayer dvd://1
will only try to play title 1

You could try using a frontend to mplayer like smplayer or gnome-mplayer, both will usually find the main movie title for you.

Or find out the movie or playable extra title # and replace the 1 in the command (if it isn't 1

Or if your mplayer has dvdnav support then this - you control thru the keyboard - look in man mplayer for general keyboard and dvdnav specific controls (near the beginning of the man file

mplayer dvdnav://


.

---

### Post by Sky Aisling on 2011-04-01
Hi Folks,

I've had same issue with 10.04 using VLC and MPlayer.
Wojax's solution works perfect.  Thank you.

    > Code:
     sudo apt-get install libdvdread4 
     Code:
     sudo /usr/share/doc/libdvdread4/install-css.sh 
Rebooting may be necessary.[I]For beginners reading this: You must use the terminal  APPLICATIONS/ACCESSORIES/TERMINAL
Be patient and wait for all the processing to complete.  Reboot when done.[/I]

---

### Post by HC48 on 2011-05-18
hello,
Sorry if this is a bit late but I can't get my home video (copied from my camcorder to a DVD disk on my DVD recorder) to work on the computer. I have Lucid Lynx and libdvdread4 + ubuntu restricted areas packages. I have VLC and can read other DVDs ok. Would this be a codec problem? My recorder says that the result should read like any DVD.

I'll continue to search but have been looking at the documentation etc so far...

Thank s for any help.

LATER:

This worked:

mplayer -v dvd://1this worked mplayer opened the video,thanks Andrew 46!

PS I found out I needed GNOME Mplayer! I was using the other mplayer. I can open the DVD with GNOME mplayer without the terminal command . (useful for beginners to know...)

---

### Post by christon74 on 2012-08-25
> **techunit said:**
> You may need to install Ubuntu restricted extras

something like

```
sudo apt-get install ubuntu-restricted-extras
```

Same problem here
and here is what I get 

 apt-get install ubuntu-restricted-extras
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

uh?

---

### Post by Perfect Storm on 2012-08-25
> **apt-get install ubuntu-restricted-extras**
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Make sure to use 'sudo' in this case.

```
sudo apt-get install ubuntu-restricted-extras
```

Or just find the package in the software center.


EDIT: This is an old thread. I'm closing it, if you need futher help start a new one or try search for the solution.

---

