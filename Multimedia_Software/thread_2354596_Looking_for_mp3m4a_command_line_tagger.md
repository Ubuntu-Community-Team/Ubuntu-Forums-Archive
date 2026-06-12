---
title: "Looking for mp3/m4a command line tagger"
date: 2017-03-04
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-03-04
I have a large number of audio files of various types and from a variety of sources.
Some of these have been extracted from a larger file (usually an internet download) and so (presumably) have no met data.
Have looked at lltag, eyed3, easytag, id3v2, mid3v2, AtomicParsley.

id3v2 and mid3v2 don't seem to work properly with m4a files.  Before setting a tag ,Kid3 shows Tag2: mp4 info such as title. genre etc.  After setting a new tag using id3v2 or mid3v2 Kid3 has no mp4 data.

Any ideas would be appreciated

Kubuntu 14.04

---

### Post by TheFu on 2017-03-04
How do you propose to get metadata for unknown files?

---

### Post by bill-lancaster on 2017-03-05
No, I propose to **create** meta data for the files.
These audio files are items of classical music or jazz and need to use my own system of genre.
Thanks

---

### Post by TheFu on 2017-03-05
I use **Easytag** - select all files you desire recursively and set the different metadata fields as you like. For example, I created a "Lounge" genre for famous lounge singers regardless of what others might call the genre.  Can set the data 1 file at a time or across 10,000 files, if you like.

If you have a directory system for the files like I do - genre/artist/album/tracks .... then that data can be used to fill in the metadata too.  Doing the reverse is possible as well - moving the files based on their metadata into a matching directory structure.

---

### Post by bill-lancaster on 2017-03-05
Thanks for the ideas.
I don't see a way of using easytag from the command line.

---

### Post by TheFu on 2017-03-05
> **bill-lancaster said:**
> Thanks for the ideas.
I don't see a way of using easytag from the command line.

Ah - I missed that in the title. Sorry.  My media is stored on a headless server, so I use sshfs to mount it to a netbook running Ubuntu and use easytag to deal with ID3 tags/metadata.

I wrote a perl script (think it was perl) around 1996 when I converted all my audio CDs into MP3s which generated and stored the metadata as ID3 tags inside the files.  Worked for over 1,000 CDs.  Let me look for it.  ... found something from 2002.  It is bourne shell and I break all sorts of scripting rules.

It requires a genre/artist/album/ directory layout to work. This is just the tagging part of my script. Above this code was code that converted WAV files into mp3 files. Anyway, it appears to be self-contained.  Oh ... and file/directory names **cannot have** funny characters or **spaces**.

[B][I][U]Before doing anything, have a complete, total, backup.  That should go without saying.  I take no responsibility if you run that script and it completely wipes your entire OS.
[/U][/I][/B]
```
#!/bin/sh
##################################
# MP3 ID3 Tagging
MP3S=`ls *.mp3`
for MP3 in $MP3S ; do

  ##################################
  # Add id3 tags to the new mp3 file
   PWD1=`pwd`
   # Get the Album
   ALBUM=`basename $PWD1 | sed -e "s/_/ /g"`
   # Get the Artist
   # ARTIST="Rick Springfield"
   cd ..
   PWD2=`pwd`
   ARTIST=`basename $PWD2 | sed -e "s/_/ /g"`
   cd $PWD1
   # Get the Track #
   TRACK=`echo $MP3 | sed -e "s/-.*$//g"`;
   # Get the Song Title
   SONG=`echo $MP3 | sed -e "s/.*-//g" | sed -e "s/.mp3//g" | sed -e "s/_/ /g"`;
   # Set all this into the ID3 Tag 
   nice id3ren -tag -tagonly -genre=79 -comment="$COMMENT" \
          -song="$SONG" -artist="$ARTIST" -album="$ALBUM" -year="$YEAR"\
          -track="$TRACK" -template='%n-%s' -space=_ "$MP3"

done

```
I didn't test it recently.
Can't help with m4a - I don't touch that format. Been switching to vorbis audio recently since all my players support it well.

---

### Post by bill-lancaster on 2017-03-05
Thanks a lot!
You've given me plenty to work on.  I may have to process m4a files separately possibly using AtomicParsley works from the command line but creates a new file.  Well that's not a big problem.
I'll update this post when I get a result.
:)

---

### Post by TheFu on 2017-03-05
Well - before doing anything, have a complete, total, backup.  That should go without saying.  I take no responsibility if you run that script and it completely wipes your entire OS.

---

### Post by andrew.46 on 2017-03-11
> **bill-lancaster said:**
> I may have to process m4a files separately possibly using AtomicParsley works from the command line but creates a new file. 

You can get around this issue by using AtomicParsley with the '--overWrite' option....

---

