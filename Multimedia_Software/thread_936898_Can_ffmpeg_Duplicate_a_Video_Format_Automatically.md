---
title: "Can ffmpeg Duplicate a Video Format Automatically?"
date: 2008-10-03
forum: Multimedia Software
---

### Post by JoeLinux117 on 2008-10-03
Hey All,

     I was wondering if ffmpeg is able to read information from a video, check its format (codecs, bitrate, dimensions, etc.), and convert another video to the same specifications using those newly discovered parameters?

     If it can't, maybe someone can respond to this thread and brainstorm for me so we can make this happen (imagine, it may be possible to get G1/iPod/iPhone/<insert your video player here> videos easily with a single command, and not have to worry about formats).  Maybe we can even share a sample video or two, and build a definition file so people won't even need a working video, they can just start from scratch!

     Am I being too hopeful on this?  This question came to mind because I'm trying to write a Ruby-GTK program using the RVideo library (which currently only supports ffmpeg) in order to encode some videos that currently necessitate a very long mencoder command.  I'd like to duplicate that in ffmpeg, but I don't want to have to figure out the command line options everytime I run into this scenario (or anyone else, I'm sure it's annoying).  This way my GUI is all that's needed.

     Any takers?

--JoeLinux

---

### Post by raymor on 2009-11-25
That seems perfectly reasonable - if ffmpeg (or mencoder) 
can PLAY the video, it knows which codecs, container formats, 
etc. were used.  Why couldn't it dump that information 
in a convenient format to be used for output, or even have 
a --copy-format-from switch.  

Did you ever find a solution?  Any software to detect all 
of the important parameters so I can convert a video to 
play on a certain device, based on a sample video from that device?

---

### Post by ilil on 2009-11-26
For GUI frontend you can use WinFF. It has various presets for many codecs and formats.

---

