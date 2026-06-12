---
title: "Win32 library failed to load"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by BobLand on 2007-05-17
When I play .avi files with MPlayer, the screen get blocky with crazy colors.  It is almost impossible to recognize anything on the screen.

I'm trying to "fix" MPlayer so I can play avi files.  Using this command from the Linux Tutorial Blog: 
   mplayer -forceidx <filename.avi> 
I get this error:
   Playing <filename.avi>.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

One thing that puzzles me does Linux recognize and use dll's?

Searching for win32 in Synaptic gives up libs for a word processor, a dl open wrapper for GNU libtool and a bunch of stuff for PulseAudio.

I don't want to overload the system with un-needed libraries and packages.  Does anyone know how to fix this?  I tried reading the MPlayer documentation but it is way over my head.

Thanks,
bobland

---

### Post by saperduper on 2007-08-12
Take a look here [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
(You 'll probably need to install w32 codecs)

I am facing exactly the same problem not with .avi file, but with .ram.
I'm trying to listen to BBC radio with mplayer and i get the same error message about avisynth.dll.
Weird!

---

### Post by Hendrixski on 2007-10-03
yep, I'm looking at a few streams from beelinetv.com, many of which use .ram files, and I can't seem to play them in mplayer, the message I get is 

```
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll
```

I have w32codecs installed, and I've restarted gnome... anybody know how to fix this?

---

### Post by BobLand on 2007-10-04
The only player I use exclusively is VLC.  It plays just about ever thing.  I've found that .avi files just don't work too well in any player.  Mplayer, with a fresh install, will not play sound for anything.  I get a "sound something or other not found."

I'm tempted to try Windows Media player with wine.  Hopefully, gutsy will resolve some of these problems.

By the way, I ended up installing the Win32 codecs but they didn't make any difference.

bobland

---

### Post by teledyn on 2007-10-13
Curiously, there wasn't any avisynth.dll in the Windows Vista distribution either -- so are we just out of luck on this one?  These filed played fine on my old Mandriva 2007, so why not in Ubuntu?

---

### Post by teledyn on 2007-10-13
[http://www.fedoraforum.org/forum/printthread.php?t=168420](http://www.fedoraforum.org/forum/printthread.php?t=168420) contains some recipies that might help, basically involving pulling down the latest codecs directly from [ftp://ftp1.mplayerhq.hu/MPlayer/releases/codecs/](ftp://ftp1.mplayerhq.hu/MPlayer/releases/codecs/)

---

### Post by teledyn on 2007-10-13
alas no, and [http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-June/061232.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-June/061232.html) confirms it; this codec is apparently windows only :(

---

### Post by starglimmered on 2007-11-01
This generally happens when playing .PLS or .RAM files and is not actually a codec issue, but a playlist issue (RAM and PLS are simply playlists: try 'cat filename.ram' to see what I mean).

Try this:

mplayer -playlist youfile.ram

or

mplayer -playlist whatever.pls

It works a treat :)

---

### Post by wisam on 2007-11-01
> **starglimmered said:**
> This generally happens when playing .PLS or .RAM files and is not actually a codec issue, but a playlist issue (RAM and PLS are simply playlists: try 'cat filename.ram' to see what I mean).

Try this:

mplayer -playlist youfile.ram

or

mplayer -playlist whatever.pls

It works a treat :)

That's exactly the solution. 

If you feed mplayer a playlist without telling it so, it'll fail to open. Mplayer's way to say that it can't open a file is that stupid irrelevant error message
```
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
```

That doesn't mean that proper codecs is not installed. Trying opening an empty file with mplayer and you'll get the same error message.

Just type
```
mplayer -playlist http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram
``` 
and mplayer will work like a charm.

---

### Post by saperduper on 2007-11-07
> **starglimmered said:**
> This generally happens when playing .PLS or .RAM files and is not actually a codec issue, but a playlist issue (RAM and PLS are simply playlists: try 'cat filename.ram' to see what I mean).

Try this:

mplayer -playlist youfile.ram

or

mplayer -playlist whatever.pls

It works a treat :)

That solved the problem! thanks ;)

---

### Post by ezramorris on 2008-05-21
> **starglimmered said:**
> This generally happens when playing .PLS or .RAM files and is not actually a codec issue, but a playlist issue (RAM and PLS are simply playlists: try 'cat filename.ram' to see what I mean).

Try this:

mplayer -playlist youfile.ram

or

mplayer -playlist whatever.pls

It works a treat :)

I can't add a 'thanks' in the archives, so here is one:
:KS

---

