---
title: "Merge/Combine SWF and Convert to AVI/other"
date: 2011-02-22
forum: Multimedia Software
---

### Post by fl0at on 2011-02-22
Good afternoon,

Feel bad for this being my first post, but normally I just surf and beat on the keyboard until an answer presents itself; but I can't solve this problem alone, and so I need a guru to point me in the right direction.

Here is the background: my university has decided that classrooms should be used for collecting dust, and are beginning to migrate several lectures to an online "articulate" format.  It is basically a powerpoint slide with audio, and we can watch them at our leisure.  Which is great, but professors no longer feel the need to limit their lectures to 1 hour and they also seem to want to talk much more slowly.

So, I want to download the files and convert to MP4/AVI/anything, so I can speed up the playback to 2x.

The problem is that the videos are all converted to SWF, and each slide has its own file.  So, if the lecture is 30 slides, I get 30 SWF files varying in range from 30 seconds to 2 minutes. 

I tried swfcombine, but either the audio wouldn't merge, or the video wouldn't merge, and I ended up with images stacking over each other, or audio stacking over each other.  

So I ended up just unlocking the files with -d option, and then using some shady (probably infested) file off the net on a windows box to convert all the individual SWF files, one at a time, to MP4.  

I then booted back into Ubuntu and used avidemux to join all the individual MP4 files to one single file.  That was time consuming because avidemux makes you append one at a time.  (When I get a moment, I'll script in a way to just add all the append files and lengths to the "save project" output file, and just open that file instead of individually adding).  

The problem is that the program I downloaded in windows makes me convert each file 1 at a time, and watermarks the center of the slide.

So, basically, if I can:

1.  Combine all individual SWF files to one SWF file (would cat work?)
2.  Find a way to convert SWF to MPEG/other file format
3.  Find a way to automate avidemux (command line example?)

or

1.  Use OOo to extract images from the actual powerpoint file
2.  Use swfextract to remove the mp3 from each swf
3.  Find a way to automate audio + images in a slideshow to video (Imagination is about the closest thing I've found)
4.  Export without loss of timing and image quality (Not Imagination's strong suit)

Anyone got any ideas?  We are already up to 4 of these lectures and what used to take me 30 minutes to do (watching the podcasts at 2x speed) now takes me an hour. 

If I could find a good way to script the download, merge, extract, conversion at night, I could wake up to yesterday's lecture ready to go.

---

