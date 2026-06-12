---
title: "Cannot seek in mkv video"
date: 2009-09-29
forum: Multimedia Software
---

### Post by fhucho on 2009-09-29
Hi,
I downloaded a .mkv movie, about 4.5GB large and mplayer can play it smoothly. But unfortunately I can't seek in the file (in other words when I want to move forward or backward in the movie, mplayer says "Cannot seek in this file..."). With ffplay, seeking works, but playback is not smooth. I have Ubuntu Jaunty, mplayer 1.0rc2-4.3.3.
Do you have an idea what can be causing this?

---

### Post by andrew.46 on 2009-09-30
Hi fhucho,

There are a few things to experiment with perhaps but I have no certain answer I am afraid :(. The easiest thing to do is to run mplayer with -forceidx:

```
mplayer -forceidx *[COLOR="Red"]myfile.mkv[/COLOR]*
```

Another option is to try a much more recent version of MPlayer, either compile your own from a guide on these forums or install from RVM's PPA, both options easy enough to find on these forums.

A final option would be to re-create the container with FFmpeg with something like:

```
ffmpeg -i myfile.mkv -acodec copy -vcodec copy my_newfile.mkv
```

Hopefully one of these options will help,

Andrew

---

### Post by x33a on 2010-01-27
> **andrew.46 said:**
> The easiest thing to do is to run mplayer with -forceidx:

```
mplayer -forceidx *[COLOR="Red"]myfile.mkv[/COLOR]*
```
Thanks, I was facing a similar seek problem with an h.264 encoded mkv. This option fixed it for me.

---

### Post by andrew.46 on 2010-01-27
Hi x33a,

> **x33a said:**
> Thanks, I was facing a similar seek problem with an h.264 encoded mkv. This option fixed it for me.

Great news :). The -forceidx option can be seen in the man pages:
```

-forceidx
   Force index rebuilding.  Useful for files with broken index (A/V
   desync, etc).  This will enable seeking in files  where  seeking
   was  not  possible.  You can fix the index permanently with MEn-
   coder (see the documentation)
```

but I have not experimented with the suggested MENcoder command to *permanently* rebuild the index:
```

mencoder input.avi -idx -ovc copy -oac copy -o output.avi
```

as I have moved completely to FFmpeg for transcoding video...

Andrew

---

### Post by x33a on 2010-01-27
I wasted hours trying to reencode the video using avidemux, but the resulting video was always out of sync, and even mplayer's audio delay option seemed to have no effect.

 Then i found this thread through google, and the option fixed it for me. though i too didn't try mencoder since it was just an anime episode and i deleted it after watching it.

---

### Post by keppel on 2012-01-17
> **andrew.46 said:**
> Hi fhucho,

The easiest thing to do is to run mplayer with -forceidx:

```
mplayer -forceidx *[COLOR=Red]myfile.mkv[/COLOR]*
```

Andrew

Thanks, that really works! It took me a whole night trying to mess with the configuration file...

---

