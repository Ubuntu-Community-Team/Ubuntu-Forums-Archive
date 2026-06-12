---
title: "encoding video from the BDMV folder of a ripped bluray"
date: 2010-08-08
forum: Multimedia Software
---

### Post by second.exodous on 2010-08-08
I can't find any resources for this but I've used DVDFab to rip a bluray through wine and have the BDMV and CERTIFICATE folders on my HD and want to encode the video down to 720p MKV file.

Basically I'm looking for a Handbrake for Bluray.  This is what I do with DVDs, I rip them with DVDFab through wine and then encode them with Handbrake to the file I want.  Is there anything like this for Bluray?  I don't need to get it on my drive, it is already there, I just need a program that can put the files in order and ask me what chapters I want to include in my file.

Thanx

---

### Post by JohnAStebbins on 2010-08-09
Most bluray discs have the entire feature in a single m2ts file.  Usually it can be identified by looking for the largest file in BDMV/STREAM/*.M2TS.  If it is in a single file, then you can simply transcode this file with handbrake.  I highly recommend using a nightly build of handbrake since many bugs have been fixed since the 0.9.4 release.

---

### Post by second.exodous on 2010-08-09
Well, I'm backing up my Pixar collection to put on one of those media boxes and Toy Story 1 and 2 split everything up.  I've only ripped Pixar movies so far so maybe it is only those Blurays.  Do you know of a program that can put them all in order so it doesn't need to be done manually?

---

### Post by JohnAStebbins on 2010-08-10
There are a few options.  The easiest would probably be MakeMKV.
[http://forum.doom9.org/showthread.php?t=144611](http://forum.doom9.org/showthread.php?t=144611)

This is a ripper that can extract BD to mkv files.  It's not open source, but it's very handy. It does not compress, so if you need smaller files, you can transcode the files with handbrake.


Then there's some command line tools I wrote that are part of the libbluray project at videolan.
[http://www.videolan.org/developers/libbluray.html](http://www.videolan.org/developers/libbluray.html)

You would have to compile this yourself.  The tools get built in src/examples.  bdsplice can concatenate the proper files together if you give it the right title number.  list_titles can show you title numbers and their durations to help find the title.


Then there is tsMuxeR:
[http://www.smlabs.net/tsmuxer_en.html](http://www.smlabs.net/tsmuxer_en.html)

Also not open source.  I've not used it for this, but I hear you can point it at a playlist and remux to a single TS file.


Then there are several windows tools. BDInfo, eac3to, BDEdit
Never used them, but they get plenty of coverage at doom9 (a great resource for your video encoding needs).
[http://forum.doom9.org/](http://forum.doom9.org/)

There's also a long thread on transcoding BD's with handbrake on handbrake's forums.  It's mostly about windows and mac tools since that's 99% of handbrake's user base.  But it's useful information.
[http://forum.handbrake.fr/viewtopic.php?f=14&t=9258](http://forum.handbrake.fr/viewtopic.php?f=14&t=9258)

---

