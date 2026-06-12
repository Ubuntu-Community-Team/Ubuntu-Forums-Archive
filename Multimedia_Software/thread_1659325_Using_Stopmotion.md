---
title: "Using Stopmotion"
date: 2011-01-03
forum: Multimedia Software
---

### Post by theepdinker on 2011-01-03
This post is not really a problem, as I have already found at least a partial solution to my difficulties, and I am now happily using Stopmotion.

My daughter has started making stop motion animation.  Unfortunately, a workshop that she went to got her started using tools on another operating system, and she quickly began bumping up against the limitations of that system.  So, I was heartened when she asked me what tools Ubuntu might have.

After a little research, I found Stopmotion in the Syanptic Package Manager and installed it.  Unfortunately, the none of default video export configurations worked to convert several .jpg stills in to a video (.avi or other format).  After some further research, I was able to add my own video export configuration that works:
[PHP]mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -o Test.avi
[/PHP]So, now I can start converting her to Ubuntu!:razz:

Has anyone else had difficulties getting Stopmotion working?  Am I missing something about the default export configurations that may be preventing them from working?

---

### Post by choben on 2011-01-11
> **theepdinker said:**
> This post is not really a problem, as I have already found at least a partial solution to my difficulties, and I am now happily using Stopmotion.

My daughter has started making stop motion animation.  Unfortunately, a workshop that she went to got her started using tools on another operating system, and she quickly began bumping up against the limitations of that system.  So, I was heartened when she asked me what tools Ubuntu might have.

After a little research, I found Stopmotion in the Syanptic Package Manager and installed it.  Unfortunately, the none of default video export configurations worked to convert several .jpg stills in to a video (.avi or other format).  After some further research, I was able to add my own video export configuration that works:
[PHP]mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -o Test.avi
[/PHP]So, now I can start converting her to Ubuntu!:razz:

Has anyone else had difficulties getting Stopmotion working?  Am I missing something about the default export configurations that may be preventing them from working?

This didn't work for me. Am I missing something? :confused:

---

### Post by ragtag on 2011-01-11
You might want to check out the [DJV view]("http://djv.sourceforge.net/") player. It's a RAM player for image sequences, that is great for previewing animation.

---

### Post by choben on 2011-01-11
I really wanted to export to a video format.

Here is the report I get from Stopmotion:

> MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/rachel/.stopmotion/packer/mosaic/images/*.jpg

Exiting...
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


---

### Post by OdnetninI on 2012-01-24
If you change jpg in the file name and jpg in the tipe of file on the command, it works

---

