---
title: "[SOLVED] Converting .flv files with ffmpeg no longer works?"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by whein on 2008-01-28
I used to be able to convert flv files into mp3/avi/mpeg files using ffmpeg and all was good.  Then a few weeks ago I noticed that the files coming out of ffmpeg were only a few kb in size and crashed every player I tried them in.  I even tried converting old flv files that had successfully been converted before and got the same symptoms.  Is there a bug in the repository packages for Gutsy?  I'm using the exact same script on the exact same files but the result is now different.  I'm using the AMD64 version of Gutsy on an Athlon 4400+ X2.  I'll post the script I'm using when I get home tonight.
-Will

---

### Post by dasunst3r on 2008-01-28
Can you type in the command you have been using to convert your files to .flv?  You may be typing the command incorrectly.  In any case, I have always been using the ffmpeg package in the Medibuntu repository.  This repository contains many, many restricted extras that official Ubuntu repositories may not have.  Check them out: [www.medibuntu.org](www.medibuntu.org)

If it works, kindly mark this thread solved.

---

### Post by whein on 2008-01-28
As I said, I don't think I typed it in wrong since I'm running it as a script, appended below.  I'll Try using the ffmpeg package from the Medibuntu repository, but shouldn't they all be the same?
-Will

```
#!/bin/bash

MY_HOME=`echo ~`
#FLV_DIR=$MY_HOME/Desktop/DropBox/youtube
DROPBOX_DIR="/media/sdb1/Media/Video/Music Videos/DropBox"
FLV_DIR="/media/sdb1/Media/Video/Music Videos/flash"
AVI_DIR="/media/sdb1/Media/Video/Music Videos/converted_avi"
MPG_DIR="/media/sdb1/Media/Video/Music Videos/converted_mpg"
MP3_DIR="/media/sdb1/Media/Music/converted_mp3"

[ ! -d "$AVI_DIR" ] && mkdir "$AVI_DIR"
[ ! -d "$MPG_DIR" ] && mkdir "$MPG_DIR"
[ ! -d "$MP3_DIR" ] && mkdir "$MP3_DIR"
[ ! -d "$FLV_DIR" ] && mkdir "$FLV_DIR"

cd "$DROPBOX_DIR"
for FILE in *.flv
do
FLV_NAME=`echo $FILE | awk -F. '{print $1}'`
OUTPUT_NAME="$MPG_DIR"/"$FLV_NAME".mpeg
[ ! -f "$OUTPUT_NAME" ] && echo ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
[ -f "$OUTPUT_NAME" ] && echo "$OUTPUT_NAME" already exists
[ ! -f "$OUTPUT_NAME" ] && ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
OUTPUT_NAME="$AVI_DIR"/"$FLV_NAME".avi
[ ! -f "$OUTPUT_NAME" ] && echo ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
[ -f "$OUTPUT_NAME" ] && echo "$OUTPUT_NAME" already exists
[ ! -f "$OUTPUT_NAME" ] && ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
OUTPUT_NAME="$MP3_DIR"/"$FLV_NAME".mp3
[ ! -f "$OUTPUT_NAME" ] && echo ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
[ -f "$OUTPUT_NAME" ] && echo "$OUTPUT_NAME" already exists
[ ! -f "$OUTPUT_NAME" ] && ffmpeg -i "$FILE" -ab 56 -ar 44100 -b 500 -s 640x480 "$OUTPUT_NAME"
done

mv *.flv "$FLV_DIR"

```

---

### Post by dasunst3r on 2008-01-29
According to the ffmpeg man page, which can be invoked using *man ffmpeg*, the -b parameter for video bitrate is in bits per second, not kilobits.

Also, why are you using the *echo* command before invoking ffmpeg?  Something tells me that might cause something to snag.  Can someone with better scripting knowledge help this person out, please?

---

### Post by philc on 2008-01-29
> **dasunst3r said:**
> According to the ffmpeg man page, which can be invoked using *man ffmpeg*, the -b parameter for video bitrate is in bits per second, not kilobits.


This is correct. Set -b to either 5000 or 500k for 500 kilobits per second.

I think FFmpeg changed this some time in the last 2 or 3 months.  However, unless FFmpeg has been upgraded on the machine in that time frame (Maybe this was done as part of an apt-get update), the script shouldn't have failed.

Still, try -b 500k and see what happens!

Edit: Same with audio. Set -ab to 56k or 560. At the moment the command posted above is only encoding audio at 56 bits per second.

---

### Post by whein on 2008-01-29
> **philc said:**
> This is correct. Set -b to either 5000 or 500k for 500 kilobits per second.

I think FFmpeg changed this some time in the last 2 or 3 months.  However, unless FFmpeg has been upgraded on the machine in that time frame (Maybe this was done as part of an apt-get update), the script shouldn't have failed.

Still, try -b 500k and see what happens!

Edit: Same with audio. Set -ab to 56k or 560. At the moment the command posted above is only encoding audio at 56 bits per second.

Ah ha!  That does sound very promising.  I'll try it out tonight and see if it fixes things.  Yes, I'm pretty sure ffmpeg did get updated around the time I noticed it stopped working.  I didn't keep track of when, but sometime not that long before I upgraded from Feisty to Gutsy, and possibly at least once after that upgraded ffmpeg using Synaptic to apply all updates that were available.

As far as the echo line in the script, that was just so that if I had any problems when I was initially writing the script I would know exactly what command had been issued and I could have an easier time finding my typo.  I am a complete novice to all the scripting stuff so I had to do a lot of trial and error to get everything formatted correctly when I transitioned from typing it in by hand to automating it to scan the whole directory.  I can probably remove it now, but I don't see why it should hurt anything.  As far as I understand it's just a println/printf command that shouldn't affect any of the other commands.  yes/no?
-Will

---

### Post by whein on 2008-01-31
Update:
I tried using just

ffmpeg -i inputfile.flv outputfile.mp3

and it worked, so I guess I need to do more reading on the actual options and maybe leave some of them out.  My hunch is that the old version either ignored the bad parameters or had different formatting (like the kb vs. b thing).  Thanks guys!
-Will

---

