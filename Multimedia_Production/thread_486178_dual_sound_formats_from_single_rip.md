---
title: "dual sound formats from single rip"
date: 2007-06-27
forum: Multimedia Production
---

### Post by Ergo on 2007-06-27
I am trying to determine the best way to rip an audio CD into 2 different sound formats in 2 different directories while maintaining the format (artist - title) on the song and placing them in directories in the format (/artist/album/).  Sound Juicer does this but works you to death while doing it plus it gets confusing and I have a lot of CD to do.  Soundconverter will convert the sound files, but will not set the directories up like I want it, so I just end up doing it all by hand which also gets confusing.  Can I simply rip in Sound Juicer to wav then use a script to do the conversion?  Or does this not add the ID3 tag information?  I'm not new to linux, but have only begun computer programming over the last semester (want to give something back eventually).

---

### Post by duffrecords on 2007-08-21
As for ID3 info, the WAV format doesn't include any artist/album information besides the filename.  You could write a script that encodes the files with LAME, but to retrieve the correct ID3 information you'd need to query a music database and include some form of error handling (zero or multiple matches requires user intervention).  It would probably make more sense to use a GUI that does all the querying, ripping, and encoding.  Ideally, such a program would have an option to not delete the original WAV file after encoding.

As for setting up the directory structure, a simple script could do the job.  I thought Sound Juicer lets you specify the directory and filename format, but maybe I'm thinking of a different program.

---

