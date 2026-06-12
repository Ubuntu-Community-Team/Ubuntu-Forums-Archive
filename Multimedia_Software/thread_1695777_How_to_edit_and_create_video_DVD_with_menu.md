---
title: "How to edit and create video DVD with menu?"
date: 2011-02-26
forum: Multimedia Software
---

### Post by VanillaMozilla on 2011-02-26
Does anyone have a solution that actually works for creating video DVDs from beginning to end?  My requirements are pretty simple, I would think.  I need to take video from an NTSC DVD (which I made from 8mm analog tape), edit it, create a menu, and burn it.  It doesn't have to be fancy.  It just has to work.  The total project is a little over 1 hour of video.  I have reasonable computer power for this.

That doesn't seem like such a difficult task, but it actually requires using up to four different mutually incompatible programs, each of which has nearly infinite options, a huge number of intermediate file types, and infinite ways to fail.  If there are intermediate files to be written, I need to know EXACTLY what files and formats to use, and what packages must be installed to use those formats.  I don't care if the programs are KDE or Gnome (even a command line might work if the procedure is clear-cut).


The task consists of four parts:

* Rip or import an ordinary video from DVD.  (This was made by a hardware DVD recorder).

* Edit videos.  Create clips, cut, past, move, fade.

* "Author" video.  Divide it into chapters (or titles, or whatever you want to call them).  Provide a menu for direct access to each chapter.

* Burn NTSC DVD.  If I can get an .iso file from the previous step, this part is no problem.


Here's some of what I have tried:

* AcidRip succeeds in ripping one track at a time to .AVI file.  Other formats are problematic.  For example, Bombono crashes importing an .mpg file, Movie player won't play it at all, and VLC plays it with an audio delay.

* PiTiVi works very well for editing, but then what?  What output options for the next program?  The default .ogg .theora seems to work, up to a point, for importing by DeVeDe.  But, I cannot add chapters, as far as I know, and I can't export single clips from the video, as far as I know.  If I could export individual clips, each as a separate file, I could then import them into DeVeDe and easily create a menu item for each file.

* DeVeDe usually works, and imports files from PiTiVi.  It will create a menu item for each file imported, BUT it will not create menu items within the clips, as far as I know.  This is a problem if you want to divide a video into little pieces that you can find from a menu.

* Bombono looks beautiful, up to a point.  Theoretically, it imports directly from a DVD, creates menus, and exports to .ISO file or directly to DVD.  BUT (1) how to create a file that it can read?; it crashes at every opportunity.  Ubuntu has only version 0.6.0.  If I somehow can install the current version, 1.0.1, it might import and export all right, but it lacks editing capability?!

Any suggestions?

---

### Post by VanillaMozilla on 2011-02-28
First follow-up

I finally used a brute-force method, which almost worked, but the sound does not play.  According to the VLC player, there is a sound track, but it doesn't play on VLC or anything else.  So far I've wasted my evenings for about three days on this, plus a weekend.

EDIT: I succeeded in making a short test DVD, using .AVI files created by a digital camera.  According to the VLC player, the codecs are identical to the codecs in the disc that doesn't play sound.  Oh, and VLC has a huge memory leak under some conditions, but that's another story.

The brute-force method was to edit the video with PiTiVi, save the job as an XUL file, then delete all but one clip.  I rendered that clip, using the default ogg theora with CD sound.  Then I opened the .xul file again and deleted all but the second clip, etc.  This was needlessly tedious, but it worked.  Each of the files plays perfectly, with sound.

When I had all the clips rendered as separate files, I imported them into DeVeDe, which allowed me to create a menu item for each file.  I rendered it as .iso file and burned it with K3b.  This part worked perfectly, but alas, no sound.  I suspect the problem is the mencoder library, but I can barely begin to diagnose it.

PiTiVi actually worked fairly well, although it bogged down seriously once the original file had been cut up into about 20 pieces.  It typically would fail to respond to the play button, although sometimes it would respond several minutes later, leading to great confusion and amusement.  If I deleted more than about three clips at once, the program would usually become totally unresponsive, so that I would have to terminate it.  The program terminated itself once.

Please, does anyone know of any video programs that actually work, and that work with each other?

---

### Post by emptythevoid on 2011-03-01
Was going to mention DeVeDe, but just re-read your post and saw you played with it and it didn't do what you wanted.  I've never had an issue with audio processed through DeVeDe didn't work, so I'm not sure what's going on there.

As for video editing with transitions, you could try OpenShot.  [http://www.openshot.org/download/](http://www.openshot.org/download/)

What hardware video recorder are you using?  You should be able to copy off the .VOB files from the DVD straight to your hard drive without having to rip it.  They're basically the same things as .MPG files.  If nothing else, you'll just have to rename them (I know Avidemux has no problem importing them in).

---

### Post by VanillaMozilla on 2011-03-01
> **emptythevoid said:**
> What hardware video recorder are you using?  You should be able to copy off the .VOB files from the DVD straight to your hard drive without having to rip it.  They're basically the same things as .MPG files.
Interesting!  It's a Philips recorder, which I use to digitize my 8-mm analog tapes.  I've never had any problem viewing the videos on any device, so I guess the output is all right.

I have a lot of things to try now, including Avidemux, and now Open Shot (it would be awfully nice if it would import my PiTiVi-rendered files -- any hints on exporting or importing them?).

Thinking about my predicament now, I'm several hours of editing into the project, and it would be nice to proceed from PiTiVi, since I have an edited PiTiVi project that I can read with the program, and I have 11 edited chapters outputted by that program that are now broken into separate files.

It would be awfully nice if I could lose as little work as possible.  There are two ways I can do that now:

(1) Import the edited chapters (in separate files) into an authoring program.  If DeVeDe was the problem (or was it mencoder?), this might be the way to go.  This would be the simplest solution if it works.  Any hints?

(2) Just set the appropriate options in PiTiVi and render the edited video into a file that could be read by an authoring program, which I could then use to insert chapter marks.  (There are MANY complicated options, and it's not so obvious which ones will give me a genuine, usable DVD-compatible file.)  One possible hint is that the default audio output sample rate for PiTiVi is CD, 44 kHz.  However, VLC says the output files are actually the correct 48 kHz.  Go figure.

Any further hints?

---

### Post by emptythevoid on 2011-03-01
If it were me, I'd try inputting the separate files into DeVeDe (maybe try two of them and generate an ISO and see what happens with the audio).  

I'm playing around with Pitivi right now and I'm having issue getting it to render a very simple project out to anything that's a DVD compliant mpeg.  I'm going to keep working on it (ogg works okay for me, just like it does with you.).

I'm going to try to get an ogg file the way you described and see how DeVeDe handles it on mine.  Hang tight.

---

### Post by emptythevoid on 2011-03-01
Alright, I *have* managed to take a video in Pitivi, export it using the plain default settings for OGG, and import that into DeVeDe.  I was then able to have DeVeDe make me an ISO of the DVD  (I set DeVeDe to do a two-pass render for better quality) and I was able to open the ISO with VLC and the audio was there.  Unfortunately, since DeVeDe has to take the OGG file and transcode it, there is some loss in this process, but it does work on mine.  Do you want me to list the exact procedure I used?

---

### Post by emptythevoid on 2011-03-01
First off, I'm using Ubuntu 10.04.  I'm not sure what version of Pitivi Ubuntu 10.10 uses.

I updated Pitivi using the PPA here:
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Had to update sources, update Pitivi (should be version 0.13.5), which updated some other gstreamer dependencies and things.

Once this was done, I was able to take a project and render it with this setting:

Container:  FFmpeg MPEG-2 PS format (DVD VOB) muxer [ffmux_dvd]
Audio Codec:  ATSC A/52A (AC-3) encoder [ffenc_ac3]
Video Codec:  mpeg2enc video encoder [mpeg2enc]

Pay attention to the settings for Video Codec.  There's an aspect ratio setting that can be set to "deduce from input" or can be manually set.  You might want to try a couple of tests with different aspect rations to make sure that your ratio is being preserved correctly.

I went ahead and rendered the file. Then I went to DeVeDe, new VideoDVD project, and added it as Title 1.  Except when I went to add it, I went to Advanced options, Misc tab, and checked "This file is already a DVD/xCD-suitable MPEG-PS file."  I then had DeVeDe make me an ISO (which it did quickly, since it didn't need to transcode anything) and I got a DVD ISO and it worked properly (with sound).

---

### Post by VanillaMozilla on 2011-03-01
Omigosh, I'm stunned by the effort you have put into this.  Thanks very much.  That gives me a lot to try, as my new plan B.

There are so many frikkin options.  I'm starting to understand some of them, but there is far more to this than I thought I should have to know.

One other hitch is that my DSL modem died yesterday, so there will be a gap before I can try this stuff and reply.

---

### Post by skullmunky on 2011-03-02
Reading this motivated me to finally sit down and try and do DVD creation, which I've wanted to do for years.  So far the winner for me is the Kdenlive video editor, which now includes a basic DVD creation wizard.

This is indeed a process fraught with peril :) so this may not work as well for you as it did for me, but here's what I did.  

0) set up kdenlive with settings for DV/DVD NTSC (or PAL if you're using that)
1) import clips.  I was able to import .VOB files straight into Kdenlive and they work fine.  If not, convert with avidemux, k9copy, or just ffmpeg.  

2) edit
3) render as MPEG-2.  I used MPEG-2 1000k for my test.  save it to "editedvideo.mpeg"

4) transcode from MPEG-2 to .VOB.  using ffmpeg you can do this like so:
```

ffmpeg -i editedvideo.mpeg -target ntsc-dvd editedvideo.vob

```
or you can run that command from inside kdenlive:

File->Transcode Clips

there are a bunch of profiles you can choose from a popup menu. ignore that, and just go into the box that says "FFMPEG Parameters" and enter these settings:
```
 -target ntsc-dvd %1.vob
```

5) run the DVD wizard

File->DVD Wizard

6) click "Add Movie File" and add editedvideo.vob, then click "next"

7) Add chapters

move the playback head through the file, click the "Add Chapter" button for each chapter marker you want.  click "next" when done.

8) Create menu

check the "Create Basic Menu" box, use the "new" button on the left to make new buttons, and choose chapters for each from the "Target" popup menu.

9) Create DVD Image

choose a location, name, and click "Create ISO Image" to make a disc image.  

10) Click the "Preview" to preview it, and the "Burn" button to burn the ISO to DVD.  It'll open up K3B to do this.

---

### Post by emptythevoid on 2011-03-02
skullmunky, kudos for using kdenlive.  It's a powerful program, and I've used it a few times (not for a DVD, though).

I think I can save you some steps, though.  When you render your project, for "Destination" choose DVD (you won't be making a DVD in this process, but it's going to make you a DVD-ready .VOB file).  

When you set the destination to DVD, it gives you four options:  two 4:3 and two 16:9.  Choose whichever one you need, and if you have the time, go ahead and do two pass for better quality.  Once you render to file, you should have a nice DVD-friendly VOB file without having to go through a second transcode step.

I didn't know kdenlive's DVD wizard let you select chapter points that easily - I'll have to remember that one. :D

---

### Post by darronwolflx on 2011-03-02
I was thinking of experimenting with the DVD and menu and was on the search for more info, I'm glad I landed at the right place. The comments from the pro sounds brilliant! Thanks for all the help.

---

### Post by VanillaMozilla on 2011-03-02
> **emptythevoid said:**
> 
Container:  FFmpeg MPEG-2 PS format (DVD VOB) muxer [ffmux_dvd]
Audio Codec:  ATSC A/52A (AC-3) encoder [ffenc_ac3]
Video Codec:  mpeg2enc video encoder [mpeg2enc]

I seem to be limited to the FFmpeg MPEG-2 video encoder [ffenc_mpeg2video], and the image is way too compressed.  I can hardly recognize people.  Any hints to avoid that?  Here are some of the (default) settings (too many to list all):

Bit rate 300000
GOP Size 15
ME Method EPZS (Best quality, Fast)
Buffer Size 0
RTP Payload Size 0
Encoding pass/type Constant Bitrate Encoding
Constant Quantizer 0.01000
...
DCT and IDCT Algorithms:  Automatically select a good one
Quantizer Type H263 quantization
Minimu Quantizer 2
Maximum Quantizer 31

---

### Post by VanillaMozilla on 2011-03-02
At a glance, Kdenlive looks like it might be good, if I can figure out how to use it.  Thanks.  Gotta go now.

---

### Post by emptythevoid on 2011-03-02
If you're using kdenlive, I suggest saving often.  I have occasionally experienced crashes with it (although it's gotten MUCH better as it's been developed), but your mileage may vary, of course. :)

---

### Post by VanillaMozilla on 2011-03-03
Thinking about it, the current rescue project can be simplified to this.  I have 11 Ogg-Theora video files with I don't know what audio format.

Does anyone know a simple way to convert those to DVD-compliant files?  There are lots of converters TO Ogg-Theora, but not so many FROM.  I plan to try ffmpeg and Avidemux.

---

### Post by VanillaMozilla on 2011-03-03
Arrgh, all converters have failed for one reason or another.  Good suggestions, though, skullmunky.  They should have worked.  Giving up and starting from scratch.

---

### Post by VanillaMozilla on 2011-03-06
Success, of sorts.  I gave up and settled for poor quality, highly compressed video.  The DVD is good enough, but just barely.  Your suggestions have all been helpful, though.  They helped me to learn more about it.

I'll post some notes on what I've learned and what worked, if I get that far.

---

### Post by VanillaMozilla on 2011-03-08
Solved, for now.

If you look above, you'll see that the default bit rate for exporting DVD with PiTiVi is set ridiculously low.  That program is promising, but it's quite new, with some rough edges and no documentation for the back end.

Thanks to all who contributed suggestions.  It looks like there are some good programs out there.  I'm planning to come back after I've tried them some more and (finally) know what I'm doing.

---

### Post by VanillaMozilla on 2011-03-12
Has anyone tried Bombono?  Ubuntu only has an early, rudimentary version.  I didn't try the current version, but it supposedly has the useful ability to place chapter marks within files, so you don't have to import each menu item as a separate file.

---

### Post by jtroxel on 2012-05-04
I have spent some time with kdenlive, even followed the process above, but I fall prey to the (apparently infamous) SCR error when I try to create the DVD

ERR: SCR moves backwards, remultiplex input: 63 < 8589934509

[http://www.kdenlive.org/forum/rendering-slideshow-dvd](http://www.kdenlive.org/forum/rendering-slideshow-dvd)

guess I will try Devede.

---

### Post by VanillaMozilla on 2012-05-05
Since there's some interest again, I'll give a brief reply.  The ONLY thing I have found that works consistently is Avidemux.  If you start and end with a .VOB, you can do it without transcoding, and it works almost instantaneously.  Other programs are not working for me at the moment in either Natty or Precise.  I think the libraries are screwed up.

For authoring, DeVeDe works pretty well, but it has a couple of limitations.  If you can get Bombono working (library problem with Precise?), it's excellent and extremely fast.  The directions don't tell you, but the "edit" button is the one with the check mark, and you have to press that after selecting an item.  For text fields, you have to press the "arrow" button to move it or set attributes.

---

