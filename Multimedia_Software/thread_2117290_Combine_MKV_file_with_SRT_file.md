---
title: "Combine MKV file with SRT file?"
date: 2013-02-18
forum: Multimedia Software
---

### Post by Shadius on 2013-02-18
Hey all,

I have a video file in .mkv format and the subtitles file in .srt format. I want to combine the two instead of having two separate files like how it is now. Is there a way to do this? I want it so when I'm playing the video I can choose to enable subtitles or not. Thanks for the help.

---

### Post by evilsoup on 2013-02-18
From the command-line, you can do this with either FFmpeg or MKVmerge (part of mkvtoolsnix)

```

ffmpeg -i movie.mkv subtitle.srt -map 0 -map 1 -c copy output.mkv

##  or

mkvmerge -o output.mkv input.mkv subtitle.srt

```

---

### Post by Shadius on 2013-02-18
> **evilsoup said:**
> From the command-line, you can do this with either FFmpeg or MKVmerge (part of mkvtoolsnix)

```

ffmpeg -i movie.mkv subtitle.srt -map 0 -map 1 -c copy output.mkv

##  or

mkvmerge -o output.mkv input.mkv subtitle.srt

```

Thank you for replying. Is this a long process and just to be clear, where it says: "movie.mkv subtitle.srt", I'd use the name of the movie file and subtitle file, right?

---

### Post by evilsoup on 2013-02-18
Yes, replace movie.mkv and subtitle.srt with the names of your files (and output.mkv with whatever you want your output file to be called - note that you can't directly overwrite your input file with these commands, though when it's finished you can simply delete the input files). And this should take around the same amount of time as copying files from one location to another would.

---

### Post by Shadius on 2013-02-18
> **evilsoup said:**
> Yes, replace movie.mkv and subtitle.srt with the names of your files (and output.mkv with whatever you want your output file to be called - note that you can't directly overwrite your input file with these commands, though when it's finished you can simply delete the input files). And this should take around the same amount of time as copying files from one location to another would.

Thank you very much for clarifying. I'm going to go try it now. :)

---

### Post by Shadius on 2013-02-18
This is the output:

```
shadius@shadius-phantom:~$ ffmpeg -i Jab Tak Hai Jaan 2012.mkv Jab Tak Hai Jaan.srt -map 0 -map 1 -c copy output.mkv
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Jab: No such file or directory
shadius@shadius-phantom:~$ 

```

---

### Post by Grenage on 2013-02-18
Spaces in the file name "Jab Tak Hai Jaan 2012.mkv"

Try "Jab\ Tak\ Hai\ Jaan\ 2012.mkv" (or just use tab).

---

### Post by Shadius on 2013-02-18
> **Grenage said:**
> Spaces in the file name "Jab Tak Hai Jaan 2012.mkv"

Try "Jab\ Tak\ Hai\ Jaan\ 2012.mkv" (or just use tab).

The original file name is Jab Tak Hai Jaan (2012), but when I tried that it gave me and error with something about the parentheses. How do I write it properly?

---

### Post by Shadius on 2013-02-18
Got this:

```
shadius@shadius-phantom:~$ ffmpeg -i Jab\ Tak\ Hai\ Jaan.mkv Jab\ Tak\ Hai\ Jaan.srt -map 0 -map 1 -copy JTHJ.mkv
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Jab Tak Hai Jaan.mkv: No such file or directory
shadius@shadius-phantom:~$ 

```

I renamed the file name to Jab Tak Hai Jaan.mkv but it's still saying there's no such file or directory. What am I doing wrong?

---

### Post by Grenage on 2013-02-18
> **Shadius said:**
> Jab Tak Hai Jaan.mkv: No such file or directory

Are you absolutely sure that's the name?  For the record, this is why most files in certain scenes (especially Linux) will use periods instead of spaces; underscores are also common.

Just for fun, call it something short and sweet.  Failing that, show us the output of the *ls* command, when in the relevant directory.

---

### Post by Shadius on 2013-02-18
> **Grenage said:**
> Are you absolutely sure that's the name?  For the record, this is why most files in certain scenes (especially Linux) will use periods instead of spaces; underscores are also common.

Just for fun, call it something short and sweet.  Failing that, show us the output of the *ls* command, when in the relevant directory.

I'm absolutely sure of the name. I'm looking right at it on my desktop. I've changed the name again to JTHJ.mkv and JTHJ.srt and this is what I get:

```
shadius@shadius-phantom:~$ ffmpeg -i JTHJ.mkv JTHJ.srt -map 0 -map 1 -copy JTHJ.mkv
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
JTHJ.mkv: No such file or directory
shadius@shadius-phantom:~$ 

```

---

### Post by Grenage on 2013-02-18
Can you post the output of *ls*?

---

### Post by Shadius on 2013-02-18
> **Grenage said:**
> Can you post the output of *ls*?

Oh, sorry. Here it is:

```
shadius@shadius-phantom:~$ ls
Desktop    Dune                   Jab Tak Hai Jaan  Public      Videos
Documents  examples.desktop       Music             Templates
Downloads  Firefox_wallpaper.png  Pictures          Ubuntu One
shadius@shadius-phantom:~$ 


```

---

### Post by Grenage on 2013-02-18
Go into the directory before you run ffmpeg, unless you want to use the full path in the command:

```
cd Jab\ Tak\ Hai\ Jaan
```

---

### Post by evilsoup on 2013-02-18
> I'm looking right at it on my desktop

Your terminal output is telling you that you are currently in your $HOME (/home/shadius in your case, I think). To get to your Desktop, you'd have to use `cd Desktop` (minus the quotes).

You might find [this website](http://linuxcommand.org/) useful, the 'learning the shell' section will teach you the basics of using the terminal pretty quickly.

---

### Post by Shadius on 2013-02-18
Thank you both for your patience and help with this. I'm a complete dummy with the Terminal and being away from Ubuntu Linux didn't help much either. I've moved the files into my Home directory and ran ffmpeg and got this:

```
shadius@shadius-phantom:~$ ffmpeg -i JTHJ.mkv JTHJ.srt -map 0 -map 1 -c copy JTHJ.mkv
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x20c79a0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'JTHJ.mkv':
  Duration: 02:56:01.50, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 1280x544 [PAR 40001:40000 DAR 2353:1000], PAR 1:1 DAR 40:17, 24 fps, 24 tbr, 1k tbn, 48 tbc (default)
    Stream #0.1(hin): Audio: ac3, 48000 Hz, 5.1, s16, 320 kb/s (default)
    Metadata:
      title           : rvarun7777
File 'JTHJ.srt' already exists. Overwrite ? [y/N] y
Unrecognized option 'c'
Failed to set value 'copy' for option 'c'
shadius@shadius-phantom:~$ 

```

---

### Post by Grenage on 2013-02-18
I don't have ffmpeg installed, but I'm going to go out on a limb here, and assume that the subtitle file name with require a qualifier, or some sort of preceding command.  As it stands, it regards it as the output name.

Be thankful it even warned you! ;)

---

### Post by Shadius on 2013-02-18
> **Grenage said:**
> I don't have ffmpeg installed, but I'm going to go out on a limb here, and assume that the subtitle file name with require a qualifier, or some sort of preceding command.  As it stands, it regards it as the output name.

Be thankful it even warned you! ;)

Maybe I should try the other method with mkvmerge?

---

### Post by evilsoup on 2013-02-18
Oh whoops, sorry I mis-typed when I put in the initial ffmpeg command; with ffmpeg, you need to put -i before every input file, so it would need to be 

```

ffmpeg -i movie.mkv -i subtitle.srt -map 0 -map 1 -c copy output.mkv

```...I'm afraid you may have just over-written your srt file with nonsense, so you might have to get a new one.

> ```
Unrecognized option 'c' 
Failed to set value 'copy' for option 'c'

```The version in the Ubuntu repositories is kind of old. I'm using an up-to-date version, so I sometimes forget which bits of syntax are different. You'd have to use:

```

ffmpeg -i movie.mkv -i subtitles.srt -map 0 -map 1 -acodec copy -vcodec copy -scodec copy output.mkv

```...or update to a more recent version (I recommend [this PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg")), or just use mkvmerge

---

### Post by Shadius on 2013-02-18
> **evilsoup said:**
> Oh whoops, sorry I mis-typed when I put in the initial ffmpeg command; with ffmpeg, you need to put -i before every input file, so it would need to be 

```

ffmpeg -i movie.mkv -i subtitle.srt -map 0 -map 1 -c copy output.mkv

```...I'm afraid you may have just over-written your srt file with nonsense, so you might have to get a new one.

The version in the Ubuntu repositories is kind of old. I'm using an up-to-date version, so I sometimes forget which bits of syntax are different. You'd have to use:

```

ffmpeg -i movie.mkv -i subtitles.srt -map 0 -map 1 -acodec copy -vcodec copy -scodec copy output.mkv

```...or update to a more recent version (I recommend [this PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg")), or just use mkvmerge


Oh nooooo, please don't tell me my subtitles file is gone now. :( Oh wait, no problem, I have the subtitles file stored on my WD My Book Live drive. So I'll try the new syntax after I've redownloaded the subtitles file.

---

### Post by Shadius on 2013-02-18
Results:

```
shadius@shadius-phantom:~$ ffmpeg -i JTHJ.mkv -i JTHJ.srt -map 0 -map 1 -acodec copy -vcodec copy -scodec copy JTHJ.mkv
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x64a9a0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'JTHJ.mkv':
  Duration: 02:56:01.50, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 1280x544 [PAR 40001:40000 DAR 2353:1000], PAR 1:1 DAR 40:17, 24 fps, 24 tbr, 1k tbn, 48 tbc (default)
    Stream #0.1(hin): Audio: ac3, 48000 Hz, 5.1, s16, 320 kb/s (default)
    Metadata:
      title           : rvarun7777
[mp3 @ 0x64f900] Format detected only with low score of 1, misdetection possible!
[mp3 @ 0x64f900] Estimating duration from bitrate, this may be inaccurate
Input #1, mp3, from 'JTHJ.srt':
  Duration: 00:00:23.12, start: 0.000000, bitrate: 95 kb/s
    Stream #1.0: Audio: mp1, 44100 Hz, stereo, s16, 96 kb/s
File 'JTHJ.mkv' already exists. Overwrite ? [y/N] y
[matroska @ 0x6507e0] No wav codec ID found.
Output #0, matroska, to 'JTHJ.mkv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 1280x544 [PAR 1:1 DAR 40:17], q=2-31, 1k tbn, 24 tbc (default)
    Stream #0.1: Audio: [0][0][0][0] / 0x0000, 44100 Hz, stereo, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)
shadius@shadius-phantom:~$ 

```

---

### Post by Shadius on 2013-02-18
Also, when it prompts me whether to overwrite anything, am I supposed to say yes?

---

### Post by Grenage on 2013-02-18
I'll leave the ffmpeg questions to evilsoup, as I have limited experience.  As for the overwriting, generally no, but especially not when you're unsure what's being over-written.

If you're simply replacing a failed encode with another attempt, it's fine - just keep an eye on what is being overwritten!

---

### Post by vanadium on 2013-02-18
mkvmerge GUI can be installed through software center and may provide an easier way to combine a subtitle file into an MKV video, of you only need to do that occasionally.

When combining a subtitle into the MKV, realize that many hardwareplayers will not support the embedded subtitle file. For this reason, it can be handy to keep the subtitles also around as a separate file. If you lost the external file, nothing is lost, though, as you can extract the embedded subtitle file at any time using mkvextract (there is no GUI for that command as fas as I am aware).

About ffmpeg is "depreciated". You should nowadays use avconv instead, which (as far as i know) currently still uses the same syntax. Indeed, this is an alternative possibility to embed the subtitles.

---

### Post by Shadius on 2013-02-18
Success! Many thanks to all of you! By using *mkvmerge* I was able to merge the subtitles file with the video file. 

Vanadium,

By hardware players, you mean DVD players? Say I was to now make this combined video file with the subtitles into an ISO I can use to burn onto a DVD, it won't play on a DVD player?

---

### Post by SeijiSensei on 2013-02-18
> **Shadius said:**
> By hardware players, you mean DVD players? Say I was to now make this combined video file with the subtitles into an ISO I can use to burn onto a DVD, it won't play on a DVD player?

No.  You need to use a DVD authoring program like [DeVeDe]("http://www.devede.org/").  DVDs have very specific formats and limitations on the types of codecs supported.  Your video is encoded with the H.264 codec, a much more recent invention than the MPEG4 encoding used on DVDs.  DeVeDe should handle all the transcoding for you.  You might want to start with the raw movie and SRT files, too, rather than trying to re-encode the file you just made.

Regular DVD players also cannot handle soft subtitles like a Matroska file can.  So the subtitles will need to be burned into the video image (so-called "hard" subtitles).  DeVeDe handles that, too, as I recall.

---

### Post by MrsUser on 2013-02-18
You can get the latest mkvtoolnix (mkvmerge + GUI) from here:
[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html)
(Section "Debian Packages").

---

### Post by vanadium on 2013-02-18
> **Shadius said:**
> 
By hardware players, you mean DVD players? Say I was to now make this combined video file with the subtitles into an ISO I can use to burn onto a DVD, it won't play on a DVD player?
I was referring to media players that support computer video files such as MKV files directly. Their MKV support tends to be basic: no support embedded subtitles, no chapter support, no support for the mkv audio delay tag.

---

### Post by Grenage on 2013-02-19
Most of the new stuff has pretty decent support, but it obviously doesn't come close to that of a decent software media centre.

---

### Post by sanderj on 2013-08-06
> **evilsoup said:**
> 
```


mkvmerge -o output.mkv input.mkv subtitle.srt

```

Wow ... it only took 39 seconds to merge in the subtitles:

```
The file 'output.mkv' has been opened for writing.
Progress: 100%
The cue entries (the index) are being written...
Muxing took 39 seconds.
```

Thank you very much!

---

