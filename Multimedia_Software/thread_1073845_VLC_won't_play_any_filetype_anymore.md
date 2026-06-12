---
title: "VLC won't play any filetype anymore"
date: 2009-02-18
forum: Multimedia Software
---

### Post by odduck on 2009-02-18
Like the thread title says, VLC won't play any filetype (video, audio) anymore.  Any time I try to open a file with VLC (my default player for just about any media file) it will open but then nothing happens.  Trying to play a file that is in the playlist causes that file to just disappear from the playlist.

I've tried uninstalling/reinstalling as well as deleting the VLC config file but to no avail.  Any help is greatly appreciated.

---

### Post by odduck on 2009-02-18
i forgot to mention that this seemed to start after i followed the "Comprehensive Multimedia and Video Howto" on these boards.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Mercury_Alpha on 2009-02-18
Open VLC in a terminal and see if it spits out any errors.

---

### Post by odduck on 2009-02-18
> **Mercury_Alpha said:**
> Open VLC in a terminal and see if it spits out any errors.

so i tried this and there weren't any error messages that i could discern.  the interesting thing is when i try to play a file, i get the message: 

```
[00000370] main playlist: playlist is empty
```

very strange indeed...

... and after writing the above, i tried running vlc from the terminal with the -vvv verbose flag and came up with a bit more.  some of the interesting output lines:

```
[00000377] playlist demux warning: invalid <playlist> attribute:"xmlns:vlc"
[00000377] playlist demux debug: parsed 0 tracks successfully
...
[00000377] main demux debug: removing module "playlist"
[00000372] main access debug: removing module "access_mmap"
```

and much further down:
```

[00000404] qt4 interface debug: Error while initializing qt-specific localization
```


let me know if i should just post the entire output.  i just didn't want to dump the whole thing on here if it wasn't necessary.

---

### Post by whoop on 2009-02-18
When all else fails you could try fixing it the dirty way. Mark for complete removal in synaptic and reinstall.
Not really recommended as you don't "learn" anything, but still.

I read that you uninstalled but I'm not sure if you did a complete removal

---

### Post by odduck on 2009-02-18
> **whoop said:**
> When all else fails you could try fixing it the dirty way. Mark for complete removal in synaptic and reinstall.
Not really recommended as you don't "learn" anything, but still.

I read that you uninstalled but I'm not sure if you did a complete removal

it's true i didn't do a complete removal.  i might as well give it a whirl. sure it'd be nice to learn something out of this but at the same time, i'm not looking to become a VLC wizard or anything.  this is one of those occasions where i'd prefer that it would just work.

---

### Post by whoop on 2009-02-18
> **odduck said:**
> it's true i didn't do a complete removal.  i might as well give it a whirl. sure it'd be nice to learn something out of this but at the same time, i'm not looking to become a VLC wizard or anything.  this is one of those occasions where i'd prefer that it would just work.

Be sure to check if you /home/xxx/.config/vlc directory is gone when you reinstall. If not manually remove it before reinstalling (just the vlc dir in .config, not .config itself)

---

### Post by Reeman on 2009-02-18
> **odduck said:**
> Like the thread title says, VLC won't play any filetype (video, audio) anymore.  Any time I try to open a file with VLC (my default player for just about any media file) it will open but then nothing happens.  Trying to play a file that is in the playlist causes that file to just disappear from the playlist.

I've tried uninstalling/reinstalling as well as deleting the VLC config file but to no avail.  Any help is greatly appreciated.
I have VLC working just fine with Ubuntu. Play lists are most likely not the problem. The way I installed VLC was from source. Just make sure that you install build essential first and read the vlc release notes before you ./configure, make, sudo make install VLC. If you installed the debian community package it should have first loaded all the right dependencies, but it sounds like there is something missing. 

If you install the build essential it will put in the essential header files for audio and video servers that VLC needs to work with pulse and OSS. VLC will build and install all the codecs that it needs for mpeg2 and mpeg4 and not have to share them with the rest of the system cruft like Totem. The VLC packages for Debian should just work but I have had some trouble with them.

You might get configure errors but by installing the right libraries that don't show up (and their headers) when you try to configure VLC you will get a properly installed and better VLC!

My VLC install really smokes and I have dropped the pulse server all together. That way VLC just accesses the devices directly through alsa and works so much faster you will not believe it. It is actually faster and more stable than any Windows mpeg player I have seen.

---

### Post by odduck on 2009-02-19
so i've spent all day on this, including close to 4 hours compiling, configuring, and tracking down dependencies using synaptic to install the latest version of vlc from source myself, a la reeman's suggestion, and it still did the same exact thing as before.  so screw it.  i'll just grudgingly use mplayer or whatever.

---

### Post by odduck on 2009-02-19
A little bit of an update here:  I did a bit of a search on the VLC forums to see if I could find a solution there and stumbled on a post from a guy experiencing the exact same issues ([link here]("http://forum.videolan.org/viewtopic.php?f=13&t=52379")).  It turns out that it was an issue with VLC not being able to differentiate between a simple file and a directory on an HFS+ formatted drive.  

Whether this is an issue with the VLC software or the HFS+ drivers on the Linux kernal depends on which side of it you're on and neither side seems too bothered to offer a fix.  So it looks like the only options right now (for using VLC to play media off of an HFS+ drive) are to either downgrade to version 0.8.6 of VLC or to use a different program.  I guess I didn't realize that the drive would be an issue since every other program I used to play this media worked fine.


I just want to thank all of you who took the time to try and help me with this.

---

### Post by detroit/zero on 2009-02-21
I have the same problem on my wife's Acer Travelmate laptop. The problem isn't limited to playing media from the external drive where we keep all our movies/music/etc, though -- her VLC refuses to play media of any type from any location.

The error message in the window is always the same: "Unable to open XXXXXXX.avi". The terminal output is similar to what you describe```
princess@princess-laptop:~$ cd Videos
princess@princess-laptop:~/Videos$ vlc -vvv nanking.avi
VLC media player 0.8.6e Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/princess/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: module bank initialized, found 17 modules
[00000001] main private debug: opening config file /home/princess/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 0 candidates
[00000001] main private error: no memcpy module matched "any"
[00000025] main playlist debug: waiting for thread completion
[00000025] main playlist debug: thread 3080981392 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000026] main private debug: waiting for thread completion
[00000026] main private debug: thread 3072588688 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000027] main interface debug: looking for interface module: 0 candidates
[00000027] main interface error: no interface module matched "hotkeys,none"
[00000027] main interface error: no suitable interface module
[00000001] main private error: interface "hotkeys,none" initialization failed
[00000028] main interface debug: looking for interface module: 0 candidates
[00000028] main interface error: no interface module matched "screensaver,none"
[00000028] main interface error: no suitable interface module
[00000001] main private error: interface "screensaver,none" initialization failed
[00000025] main playlist debug: adding playlist item `nanking.avi' ( nanking.avi )
[00000029] main interface debug: looking for interface module: 3 candidates
[00000029] main interface debug: using interface module "wxwidgets"
[00000029] main interface debug: thread 3046402960 (manager) created at priority 0 (interface/interface.c:216)
[00000029] wxwidgets interface debug: Using last windows config '(-1,0,0,1280,800)(0,427,379,425,72)(6,0,0,-1,150)'
[00000029] wxwidgets interface debug: id=0 p=(427,379) s=(425,72)
[00000029] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
[00000025] main playlist debug: nothing requested, starting
[00000025] main playlist debug: creating new input thread
[00000032] main input debug: waiting for thread completion
[00000032] main input debug: creating statistics handler
[00000032] main input debug: `nanking.avi' gives access `' demux `' path `nanking.avi'
[00000032] main input debug: creating demux: access='' demux='' path='nanking.avi'
[00000034] main demuxer debug: looking for access_demux module: 0 candidates
[00000034] main demuxer warning: no access_demux module matched "any"
[00000032] main input debug: creating access '' path='nanking.avi'
[00000035] main access debug: looking for access2 module: 0 candidates
[00000035] main access error: no access2 module matched "any"
[00000032] main input debug: creating access '' path='nanking.avi'
[00000036] main access debug: looking for access2 module: 0 candidates
[00000036] main access error: no access2 module matched "any"
[00000032] main input error: no suitable access module for `nanking.avi'
[00000032] main input debug: thread 3031448464 (input) created at priority 0 (input/input.c:265)
[00000032] main input debug: thread 3031448464 joined (input/input.c:412)
[00000025] main playlist: nothing to play
[00000001] main private debug: removing all interfaces
[00000029] main interface debug: thread 3046402960 joined (interface/interface.c:258)
[00000029] main interface debug: removing module "wxwidgets"
[00000001] main private debug: removing playlist handler
[00000026] main private debug: thread 3072588688 joined (playlist/playlist.c:247)
[00000025] main playlist debug: thread 3080981392 joined (playlist/playlist.c:248)
[00000025] main playlist: stopping playback
[00000025] main playlist debug: deleting playlist item `nanking.avi'
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: opening config file /home/princess/.vlc/vlcrc
[00000001] main private debug: saving plugins cache file /home/princess/.vlc/cache/plugins-04041e.dat
```
VLC version is listed as```
princess@princess-laptop:~$ vlc -v
VLC media player 0.8.6e Janus
```So I don't know if downgrading is the solution.

---

