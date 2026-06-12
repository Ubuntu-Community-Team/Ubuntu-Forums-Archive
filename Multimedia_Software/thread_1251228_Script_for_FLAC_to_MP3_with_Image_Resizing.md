---
title: "Script for FLAC to MP3 with Image Resizing"
date: 2009-08-27
forum: Multimedia Software
---

### Post by CNLiberal on 2009-08-27
I have an iPhone 3GS and would like to start putting music on it.  A lot of my music is in FLAC format, and the iPhone obviously will NEVER play that.  I'd like to write a script that will take my FLAC files (with embedded ID3 tags/images) and convert the FLAC to a 256kb VBR MP3, but keep all the embedded tags AND resize the image file to the iPhone's native CD cover size.  Has anyone seen anything like this before?  Thanks!

Jim

---

### Post by modorf on 2009-08-27
what about something like this?

```

#!/bin/bash
FLAC=$1
MP3="${FLAC%.flac}.mp3"
[ -r "$FLAC" ] || { echo can not read file \"$FLAC\" >&1 ; exit 1 ; } ;
metaflac --export-tags-to=- "$FLAC" | sed 's/=\(.*\)/="\1"/' >tmp.tmp
cat tmp.tmp
. ./tmp.tmp
rm tmp.tmp
flac -dc "$FLAC" | lame -b 192 -h --tt "$Title" \
--tn "$Tracknumber" \
--tg "$Genre" \
--ty "$Date" \
--ta "$Artist" \
--tl "$Album" \
--add-id3v2 \
- "$MP3"

```

From [http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3]("http://www.linuxtutorialblog.com/post/solution-converting-flac-to-mp3")

---

### Post by CNLiberal on 2009-08-27
Cool.  That solution is pretty good.  I just wish it took into account images.  This is my first "Video capable" iPod (iPhone) and it'd be cool to see the covers.  I just don't want to have the images be larger than the mp3 file.  I like high res images.  The reason being, I use MythTV and when I play the flac file on my 52" 1080p TV, it's nice to see a high res cd cover.  Maybe I can try my hand at scripting and come up with something.

Jim

[EDIT]

Looks like 160x160 is the sweet spot for cover flow.

[http://discussions.apple.com/thread.jspa?messageID=8783586](http://discussions.apple.com/thread.jspa?messageID=8783586)

This is a good solution for me as I don't use iTunes for my music listening, just syncing.  I really hope someone can break the iPhone DB encryption.  I really want to use Ubuntu!

---

### Post by Seq on 2009-08-27
Granted this does not do cover resizing, but [mp3fs]("http://mp3fs.sourceforge.net/") may be worth a look. It is a FUSE filesystem that will transcode FLAC files to MP3.

---

