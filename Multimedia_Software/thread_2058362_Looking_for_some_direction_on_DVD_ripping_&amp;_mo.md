---
title: "Looking for some direction on DVD ripping &amp; montage"
date: 2012-09-15
forum: Multimedia Software
---

### Post by afulldeck on 2012-09-15
Old unix guy, new to ubuntu looking for some suggestions on the following problem. 

I want to build a montages based on tagged ripped DVD sections. I a complete noob in this area and haven't done this before on any type of computer. I am starting from scratch, so I'm looking for the following input: 


[LIST=1]
[*]What format should I use for ripping? I would want the playback to be highest possible given my input.
[*]I would like to chop the DVD up into scenes easily? Is that even possible?
[*]What software would be the best to achieve those above?
[*]Does that software support tagging of scenes? I want to tag certain scenes with key words that I can search on later.
[/LIST]
Any help would be greatly appreciated.

---

### Post by afulldeck on 2012-09-15
bump. Anyone?

---

### Post by qyot27 on 2012-09-16
[LIST=1]
[*]What format should I use for ripping? I would want the playback to be highest possible given my input.
[*]    I would like to chop the DVD up into scenes easily? Is that even possible?
[*]    What software would be the best to achieve those above?
[*]    Does that software support tagging of scenes? I want to tag certain scenes with key words that I can search on later.
[/LIST]

1. The fastest, highest quality option (because yes, in this case it's actually both) is to simply decrypt the disc's contents, which will give you the MPEG-2 streams as they exist on the disc, just without the encryption cruft on them.  This eliminates the need to convert anything during the ripping process, or if you do decide to convert it to a smaller, more efficient format, you can do it later, with better tools and maintain higher quality and better accuracy.

2. This can be achieved either by the DVD ripping software used or by tools that can be used later to deal with the individual chapters on the disc.  Shorter scenes would need to be marked out manually, because DVDs only store the location of chapters.  For the more precise tools out there, you might run into an issue with where the group of pictures (GOP) is in the video stream itself - most trimming software that doesn't work on the frame level can only cut by GOP, which may include frames you don't want.  Ones that work on the frame level require conversion to greater or lesser degrees.

3. This is where it gets complicated, because there is no all-in-one tool to do this.  There's multiple methods of ripping the disc, some which might net you the chapters individually, or it could be whole-disc and you'd process the chapters afterward.  Tagging of the files themselves (as I assume that's what you want, and not an external index* to refer to) can only be done with certain container formats, notably Matroska (MKV) or MP4.  The ripping tools should not be the ones changing the container, so it'll be a separate step.

*Really, I'm just using fancier language to mention the option of having a plain text file with multiple columns: one with the file name(s) of the videos, one with the start/end timecodes of the scenes, and another with the relevant keywords.  This has the advantage of working regardless of container format, and it's much easier to grep.

4. The software responsible for changing the container usually can do tagging of some sort.

IMO, if you only want to demarcate the scenes by the chapters already signaled on the disc, then it's pretty easy to do with the chapter capabilities of MKV (MKV does have both chapters and tags, but I have no experience with the actual tagging functions; what you want may actually be closer in concept to chapters).  If you want more intensive per-scene stuff, you'd only need to create more chapters and give them names.  Software that can read MKV chapters and names can then give you the ability to search (or pipe through in a complex search).

The difficulty in *dealing* with chapters can be a barrier, though.  It may be easier to have the chapters or scenes stored as discrete files, and then you can access them without any of the weirdness of trying to handle or jump around inside of larger files (especially as you mentioned making a montage; it's easier to do this with discrete clips anyway).

---

### Post by afulldeck on 2012-09-16
> **qyot27 said:**
> 
[LIST=1]
[*]What format should I use for ripping? I would want the playback to be highest possible given my input.
[*]    I would like to chop the DVD up into scenes easily? Is that even possible?
[*]    What software would be the best to achieve those above?
[*]    Does that software support tagging of scenes? I want to tag certain scenes with key words that I can search on later.
[/LIST]

1. The fastest, highest quality option (because yes, in this case it's actually both) is to simply decrypt the disc's contents, which will give you the MPEG-2 streams as they exist on the disc, just without the encryption cruft on them.  This eliminates the need to convert anything during the ripping process, or if you do decide to convert it to a smaller, more efficient format, you can do it later, with better tools and maintain higher quality and better accuracy.

2. This can be achieved either by the DVD ripping software used or by tools that can be used later to deal with the individual chapters on the disc.  Shorter scenes would need to be marked out manually, because DVDs only store the location of chapters.  For the more precise tools out there, you might run into an issue with where the group of pictures (GOP) is in the video stream itself - most trimming software that doesn't work on the frame level can only cut by GOP, which may include frames you don't want.  Ones that work on the frame level require conversion to greater or lesser degrees.

3. This is where it gets complicated, because there is no all-in-one tool to do this.  There's multiple methods of ripping the disc, some which might net you the chapters individually, or it could be whole-disc and you'd process the chapters afterward.  Tagging of the files themselves (as I assume that's what you want, and not an external index* to refer to) can only be done with certain container formats, notably Matroska (MKV) or MP4.  The ripping tools should not be the ones changing the container, so it'll be a separate step.

*Really, I'm just using fancier language to mention the option of having a plain text file with multiple columns: one with the file name(s) of the videos, one with the start/end timecodes of the scenes, and another with the relevant keywords.  This has the advantage of working regardless of container format, and it's much easier to grep.

4. The software responsible for changing the container usually can do tagging of some sort.

IMO, if you only want to demarcate the scenes by the chapters already signaled on the disc, then it's pretty easy to do with the chapter capabilities of MKV (MKV does have both chapters and tags, but I have no experience with the actual tagging functions; what you want may actually be closer in concept to chapters).  If you want more intensive per-scene stuff, you'd only need to create more chapters and give them names.  Software that can read MKV chapters and names can then give you the ability to search (or pipe through in a complex search).

The difficulty in *dealing* with chapters can be a barrier, though.  It may be easier to have the chapters or scenes stored as discrete files, and then you can access them without any of the weirdness of trying to handle or jump around inside of larger files (especially as you mentioned making a montage; it's easier to do this with discrete clips anyway).

Well thank you very much, this was indeed very useful. I'm glad you pointed out that there was no all in one tool that will save me time looking for one. I take it that handbrake is what you use for ripping to mkv?

---

### Post by qyot27 on 2012-09-17
No, as far as I am aware, Handbrake converts while it rips.  So it'll both take longer and you'd have to be careful about the way it gets processed.

I'll be honest here: most of my multimedia work is done under Windows.  However, most of the tools are FOSS, can run under Wine with few issues, or are cross-platform and have native Linux versions.

A general workflow, though.  I'll try to stick to native apps where I can, otherwise I'll note where Wine is needed.

vobcopy -> decrypts the entire disc and saves the structure to the hard drive; doesn't do chapter parsing (that I know of)

mplayer -> if you can play the DVD in mplayer, you can do ripping by using the -dumpstream function.  As mplayer can also jump to specific chapters, it's possible that you could get it to output the chapters individually (or more problematically, it could merely jump to the chapter location and start dumping, but not stop when it reaches the next chapter).


In either of these cases, you're getting the original MPEG-2 streams, in the original container (which is a variant of MPEG-PS).  At this point, you can use the mkvtoolnix package to put it directly into MKV (the syntax for mkvmerge is a bit intense, but the GUI is fairly easy to use and can optionally show you what command it's running).  mkvmerge can do file splitting by timecode, you can create the chapter.xml file with the Chapter Editor in the GUI, and you can load the chapter.xml file before doing the final muxing so that the output file has chapters enabled.

In this particular case, since you kept the file in MPEG-2 and didn't do any converting, there is a risk that splitting by timecode will not quite get all of what you want (or it could get more than you want) because it can only cut on keyframes.  It's up to you whether this is acceptable.

If you need to read the chapter names from the MKV file(s), you can use mediainfo - a plain invocation will list any chapters+timecodes it finds at the end of the readout, or you could trim it down with sed:
```
mediainfo filename.mkv | sed '1,/Menu/d'
```







If you want the cutting to be exact, you need something that can operate on the frame level.  My preferred method of doing this is with AviSynth, a scripting language that operates on media files.  The original is Windows based, but it runs excellently under Wine.  There is a Linux port - AvxSynth - but as it's not in the repositories, you'll have to compile it yourself (there's also some limitations; AvxSynth is a port of AviSynth 2.5.8, whereas the trunk is on 2.6.0 and contains a lot of bugfixes and additional niceties...even though 2.6.0 is still technically 'alpha').

I'm not going to go all that in-depth on AviSynth usage here (there are other forums and tutorials that can do a much better job of it, [and this thread](http://ubuntuforums.org/showthread.php?t=1333264)), but using it you can do advanced processing on the source - you can remove interlacing or return the video to Film framerate, smooth, sharpen, transform in various ways, resize, trim scenes out with 1-frame precision, or so on.  All of this is performed in a single script.  Programs that can recognize AviSynth scripts then treat the script like a video file and can encode to a final video format.  It is possible to use FFmpeg or x264 (which both accept AviSynth scripts on Windows) under Wine, but you can also use the tool avs2yuv to pipe from the script (under Wine) to native Linux builds of FFmpeg or x264 instead.

In AvxSynth's case, Wine isn't involved.  One difference is that in normal AviSynth, you'd be likely to use the DGMPGDec package to handle MPEG-2 files using the MPEG2Source filter, but as far as I'm aware DGMPGDec hasn't been ported to Linux (whether it easily could be, I'm not sure).  So in AvxSynth, you'd actually be using FFMS2 (FFmpegSource2) to do this.  As far as I know, nothing can interface directly to AvxSynth yet, so you have to use the avxFrameServer application to pipe it to another program (by default it pipes to mplayer so the user can see what they've done, but you can use the -nomplayer option to stop it from doing that and facilitate piping to a different program).

---

### Post by afulldeck on 2012-09-18
Thank you qyot27. Your pointers have lead to reading volumes of stuff on editing. Yes I'm still reading probably now for weeks :-)

Learning about editing video and the complications that I never considered is quiet interesting, if not overwhelming. You noted above that you use mainly windows for editing. Is that because there are a better array of tool? (Just curious)  

Up til today, I've download a couple of FOSS tools to try out a few things. I kind of disappoint in the lack of cross functional playback problems. For example I ripped to MKV some material with subtitles that played back nicely on Windows, Linux, but not my Android Infinity tablet (where the subtitles where dropped). More work required on my part.

---

### Post by qyot27 on 2012-09-18
My preference for working under Windows is mainly because I prefer using a prosumer-level NLE (read: Adobe Premiere), although it's also that I learned on there, and it's often a lot easier to come by information that way.  If they aren't targeting the Mac, they probably are targeting Windows.  Also, my computer just turned 11 years old, and running any recent version of Ubuntu is burden enough from the environment alone (and I run LXDE), nevermind trying to run editing software on top of it - heck, it takes an hour and a half just to compile FFmpeg on this thing (vs. less than 5 minutes under the Ubuntu virtual machine running on the Core i5-equipped iMac I have access to).

Of course, I also haven't really edited anything on here in 3 years due to finally having had enough of putting up with my hardware.  I don't classify conversion software, AviSynth, or other types of things quite the same as using an NLE, though.

With the major tools, there has been a shift toward more and more of them being cross-platform, but the video editing world as it is in Linux is still very asymmetrical...even though it is a lot better than it was just a few years ago.  A much larger array of satellite utilities (pre-processing, post-processing, conversion and so forth), not so much on the core tools needed for a complete workflow.  The existing solutions are generally not replacements for Premiere, Vegas, Final Cut, or Avid, although they are admirable alternatives to things like iMovie or Windows Movie Maker.  The two most notable advanced solutions for Linux - Cinelerra and Blender's VSE mode - have terribly alien interfaces compared to those other NLEs, or aren't really intended for NLE work to start with.  I keep an eye peeled, but it seems to be incredibly slow going.


Regarding playback on devices, there being problems with support is practically a given due to them needing to be constrained by their hardware - subtitles are not very standardized*, unlike video or audio formats.  If you can manage to get mplayer or mplayer2 (making sure that lib[color="black"]a[/color]ss support is enabled) compiled for Android, then the subs shouldn't have a problem.  I have neither a tablet or smartphone, so I can't really say much beyond that.  Maybe there's a suitable software-based media player already available as an app, I don't know.

*by this I mean both that there's not a single subtitle format guaranteed for widespread support, or - like in the case of [color="black"]A[/color]SS - if there is support for it, it only supports the very bottom tier of what the format might be useful for (which is true of styled subtitles in general; all those fancy typesetting and karaoke effects that can be done with them are pretty much null and void on hardware-based solutions...they might show up so you can at least read them, but they'll have been stripped of all the customization that makes the format worth using).

---

### Post by afulldeck on 2012-09-18
> **qyot27 said:**
> 
*by this I mean both that there's not a single subtitle format guaranteed for widespread support, or - like in the case of [COLOR=black]A[/COLOR]SS - if there is support for it, it only supports the very bottom tier of what the format might be useful for (which is true of styled subtitles in general; all those fancy typesetting and karaoke effects that can be done with them are pretty much null and void on hardware-based solutions...they might show up so you can at least read them, but they'll have been stripped of all the customization that makes the format worth using).

This might be exactly why I was confused. I thought if I chose my container correctly (like .mkv) the play back with all information would be guaranteed. It certainly worked on Ubuntu (all audio, video, and text), but when I played in on the Android the text was dropped even though the player said it could play .mkv which I guess it did partially. Very confusing this video stuff....very confusing indeed.

---

