---
title: "&quot;Avidemux with proper fast wind controls&quot; video editor wanted"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by Pigeon. on 2008-01-17
I am looking for a very simple video editor to do some very simple stuff... basically to run through a 4-hour video file and chop out all the bits I'm not interested in.

Avidemux would be great but it has one BIG problem - the fast wind controls **suck.** All you can do is move by single frames, jump to the next/previous keyframe or jump forwards/backwards by 1% of the entire file. (Sliding the slider with the mouse is only useful for files which are MUCH shorter than 4 hours.) This makes accurately finding the start and end of the bits I want to cut out a real PITA.

I want something like avidemux but with fast wind controls like a VCR, so I can play forwards and backwards at variable speed and stop it when it gets to the good bit, then jog back and forth to find where to cut.

Kino seems to be able to do this but the source files that I want to edit are not in the format that it wants and while it is capable of importing them, it is horribly slow at doing it. I've got a 2.4GHz processor and it is much slower than real time. 

Even worse, the imported file is TEN TIMES the size of the original, and I simply do not have enough disk space to use it. I've just imported a 70-second, 25-megabyte file; the imported version is 244 megabytes for the same data, which is frankly ridiculous. This machine just doesn't have a big enough HD to cope with importing the full 4-hour files I need to work with.

Everything else I've looked at seems so grossly overcomplex for my needs as to be essentially useless. Some of them are not even capable of opening a video file without going through some "create project" procedure, it seems. I don't need any of that. I don't "create a project" or a "storyboard" or anything like that when I'm editing an ASCII text file to cut out paragraphs I don't need, I just scroll up and down the file, mark the bits to delete, and delete them. For video all I need is the equivalent function, which as I say, equates to avidemux but with proper VCR-like fast wind controls.

Any suggestions would be much appreciated.

---

### Post by cor2y on 2008-01-17
have you tried kdenlive or the new release of avidemux?
The new release you'll have to compile yourself or get the deb file from the official site but be warned the deb version might be missing some media addons if you plan to convert to another media format.

---

### Post by disturbed1 on 2008-01-17
2 questions first ;) What version of Avidemux are you using? What format are your files in?

With Avidemux 2.4preview3 (r3688 ) the jog dial works as expected with divx/xvid files. When ever I'm looking to cut footage with Avidemux I use the keyboard shortcuts
[SIZE=4]
////8\\\\
4////\\\6
////2\\\\[/SIZE]


8=keyframe forward, 2=keyframe back, 4 and 6 are frame by frame. I tend to scan the video by keyframe forward, then dial in frame by frame using the number pad. Works rather quickly. I find it easier than the jog dial.

---

### Post by Pigeon. on 2008-01-18
@cor2y:
I tried kdenlive but for me it falls into the "ghastlily overcomplicated UI/operating paradigm" category; when I can't even open a straight video file without first creating a project... I tend to look for something else :) in my usual frame of reference, it's like building a whole .deb package to implement a one-line shellscript instead of going "cat> foo" ... (type stuff) ..."chmod a+x foo"... done :) Will try the new release of avidemux...

@disturbed1:
avidemux 2.3.0; files are eg. "1.avi: RIFF (little-endian) data, AVI, 352 x 198, 25.00 fps, video: FFMpeg MPEG-4, audio: MPEG-1 Layer 1 or 2 (stereo, 48000 Hz)" but they are transcoded down from much larger format kaffeine recordings using mencoder so really they can be whatever format is convenient.

My avidemux has a volume control slider where your screenshot shows a jog dial :confused: I'll try 2.4preview3 and see how I get on, thanks.

The method of using avidemux that you describe sounds just like what I'm doing at the moment; it's OK but not as convenient as I would like, there seems to be some kind of caching/latency issue in that if I haven't already played through recently in normal playback mode the section of video I'm trying to work on, it doesn't scan smoothly, it proceeds in a series of jerks - scans a bit then stops for a second or two before it moves again, and in that second or two the keyboard buffer fills up, so when I get to the point where I want to stop and release the keys, it carries on moving until the keyboard buffer empties, and overshoots... Keyframes tend to be once every several hundred frames, which doesn't help.

As I say, I'lll try the version you mention and see how I get on with its jog dial.

---

### Post by Pigeon. on 2008-01-22
Avidemux 2.4 with the jog dial is exactly what I needed, does just what I wanted, many thanks.

---

