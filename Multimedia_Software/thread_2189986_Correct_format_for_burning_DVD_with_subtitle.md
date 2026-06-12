---
title: "Correct format for burning DVD with subtitle"
date: 2013-11-25
forum: Multimedia Software
---

### Post by ProgramErgoSum on 2013-11-25
I have a mp4 file and a collection of subtitles files in srt format. After burning, during play back, user should be able to choose the language of subtitle. There will be multiple such mp4 files and each one of them will have corresponding subtitle files. The idea Is to create one chapter from each mp4 file.

So, what should be the input and output format I should be look at?

---

### Post by philinux on 2013-11-25
I reckon you need to install devede from software center , synaptic or termial.

---

### Post by ProgramErgoSum on 2013-11-25
I want a command line option.

---

### Post by qyot27 on 2013-11-26
You can't do it all from the command-line, because there's too many things that can go wrong; only select parts of the DVD authoring process can be easily automated.  The conversion from [what I assume is H.264] mp4 to MPEG-2 can be done with the CLI through ffmpeg, which can also convert the audio to AC3.

DVD does not support text subtitles like SRT, only bitmapped ones (I'm not counting closed caption formats like EIA-608, since those are even more icky to try and work with).  And I'm not aware of any tool that is native to Linux that can export in the correct bitmapped format, although I've not looked.  You will need a visual editor so that you can be sure the subs won't look awful and - more importantly - can export to the SUP (or similar) format that you need.  On Windows, this would be Subtitle Creator.  Maybe it's possible to get it running under Wine, but I don't know.

Divvying up the files as chapters is also not very feasible, because chapters aren't separate on the disc, and the individual files will have their subtitles synced to the timecodes of the original files.  You'd need to completely re-do the timecodes in the subtitles to compensate for the fact that they're now inside of a single video.  Leaving them as separate titles will allow you to preserve the original timecodes in the subtitles.

To say nothing of making sure the DVD menu navigation works correctly or looks right.

I'm not sure if dvdauthor can take input of SUP subtitles (or similar format) by itself, which is a problem since virtually all the DVD authoring software I know of for Linux is built on dvdauthor.  While it's possible to use dvdauthor from the CLI, such an endeavor is pretty much experts-only: it's why GUIs on top of dvdauthor exist.  If dvdauthor can't take SUP input, this becomes pretty much impossible to do natively, since the only software I know of that can combine SUP with your video/audio input and output a correct DVD title is MuxMan, and that's Windows-only.  After that, you can probably give the .IFO/.VOB sets to dvdauthor and it might be able to pass the subtitles through untouched.  If not, you'll have to dive into the titleset structure with VobBlanker (again, Windows-only) to replace the non-subtitled output from dvdauthor with the subtitled single titles you get from MuxMan.


tl;dr: Softsubs on DVD are a lot harder than they should be, regardless of what OS you're using.

---

