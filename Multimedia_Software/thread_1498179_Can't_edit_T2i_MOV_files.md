---
title: "Can't edit T2i MOV files"
date: 2010-05-31
forum: Multimedia Software
---

### Post by BobLand on 2010-05-31
Got my T2i a few days ago.  Shot a bunch of short MOV files.  Trying to do simple edits like trimming the beginning and ends.  Nothing else.

Cinelerra 4 - no sound
Kdenlive - aside from crashing all the time, renders with unacceptable artifacts.
Lives - spends a long time making proxies then crashes
Avidemux - crashes on save/render
Kino - plays back first frame then last frame.  Kinda funny but not.
Open Movie Editor - Does nothing at all
Open Shot - Can't find any libs
PiTiVi - Tools?  We don't need no stinkin' editing tools.

Will Lunmeria be released before I die?
Will Lightworks be released before I die?

Is it time to retrench back into Windows 7 where there are numerous editors that actually work?  Sure, costs money but the free stuff just dont work.

If you have any suggestions to prevent me from abandoning ship, please, please help.  

BTW, VLC plays the files back beautifully -- no skips, no jerks, sound completely in tact.

bobland, soon to be in exile

---

### Post by no2498 on 2010-05-31
PiTiVi you cut in the time line
you can put 2 or more together

it also uninstalls jack audio

that kills lives 

tragtor can put them back to mov file type to make em smaller

hope this helps

---

### Post by wildhostile on 2010-05-31
If Cinelerra can only read the video part, I would suggest you to export the audio part and load them separately into Cinelerra.
Can Cinelerra-CV read the file too?

---

### Post by BobLand on 2010-06-01
How would I separate the audio from the mov file?

---

### Post by wildhostile on 2010-06-01
you can do it using winff.
or with the command line using ffmpeg for example:

first: take informations of your video with ffmpeg -i yourvideo.mov OR with mplayer -identify OR using mediainfo

second: convert the sound part to wav file or mp3 if the audio is only 2 channels. If it has got more channels maybe you should use ac3.
ffmpeg -i yourvideo.mov -vn -ar 44100 -ac 2 -ab 192 -f mp3 yourvideosound.mp3 (I'm not an expert... taken from [http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs) )

---

### Post by FakeOutdoorsman on 2010-06-01
> **BobLand said:**
> Got my T2i a few days ago.  Shot a bunch of short MOV files.  Trying to do simple edits like trimming the beginning and ends.  Nothing else.

Cinelerra 4 - no sound
Kdenlive - aside from crashing all the time, renders with unacceptable artifacts.
Lives - spends a long time making proxies then crashes
Avidemux - crashes on save/render
Kino - plays back first frame then last frame.  Kinda funny but not.
Open Movie Editor - Does nothing at all
Open Shot - Can't find any libs
PiTiVi - Tools?  We don't need no stinkin' editing tools.

Will Lunmeria be released before I die?
Will Lightworks be released before I die?

Is it time to retrench back into Windows 7 where there are numerous editors that actually work?  Sure, costs money but the free stuff just dont work.

If you have any suggestions to prevent me from abandoning ship, please, please help.  

BTW, VLC plays the files back beautifully -- no skips, no jerks, sound completely in tact.

bobland, soon to be in exile

I use FFmpeg to trim files.  Example:
```
ffmpeg -ss 00:02:23 -i input.foo -t 25 -vcodec copy -acodec copy output.foo
```
[indent]**-ss**: Time offset from beginning.  The example will ignore the first 2 minutes and 23 seconds of the input file.  You could also just declare number of seconds as shown in *-t*.
**-t**: Duration. The output file will be 25 seconds long.[/indent]
This example simply copies the video and audio instead of re-encoding which preserves the quality and is much faster than re-encoding.

---

### Post by BobLand on 2010-06-10
After using Vegas for a few days, I can't look at any linux video editor.  Each has major show stopping "features."

I have found that Vegas works perfectly fine in VirtualBox so I can stay in Ubuntu, at least for the time being.

---

