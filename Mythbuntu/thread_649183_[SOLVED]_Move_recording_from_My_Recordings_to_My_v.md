---
title: "[SOLVED] Move recording from My Recordings to My videos"
date: 2007-12-24
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-12-24
I'm sure this has been asked in the past if not on this forum but another.  But I haven't been able to find anything to explain how this is done.  We recorded Polar Express the other day and my wife wants me to see if I can save the recording and have it placed in our Videos folder.

I'm assuming this is done by using mythtranscode somehow.  However, any time I've tried using the Transcode feature it fails.

Is there another way to do this?

---

### Post by Meph1st0 on 2007-12-26
Does anyone know how to do this?

---

### Post by superm1 on 2007-12-26
You can copy the video over from what directory to another.  Probably the easiest way is to go to mythweb and click the recording.  It will offer to let you save it.  Just save it to your videos location.  That will "copy" it.  Just delete the original then.

---

### Post by ubnewbie2 on 2008-01-24
> **superm1 said:**
> You can copy the video over from what directory to another.  Probably the easiest way is to go to mythweb and click the recording.  It will offer to let you save it.  Just save it to your videos location.  That will "copy" it.  Just delete the original then.

I want to do this too.  It would be nice to keep the metadata when doing this.  

It would be on my wishlist.  Logically, it might fit under the myth archive section, but a hotkey to do the transfer, with metadata, from the "watch recordings" screen would be excellent.

---

### Post by se99paj on 2008-01-25
I was looking for the same solution.

I found this article: [http://ubuntuforums.org/showthread.php?t=346778&highlight=nuv&page=5](http://ubuntuforums.org/showthread.php?t=346778&highlight=nuv&page=5)

Its quite handy as you move recordings into videos, you can convert them into DivX at the same time.

I'm still trying to get it working perfectly at the moment.

---

### Post by stdPikachu on 2008-01-27
I didn't use nuvexport when I did the same thing as I wanted to edit them myself. I wrote this small (and probably dangerous) script which I added as a Myth user job:
```
#!/bin/bash
# Custom user job designed to convert the recorded MPEG2-TS files from the DVB recorders into MPEG2-PS files for editing in AviDemux or similar

# This script needs the following variables in this exact order to run:
#       %DIR%
#       %FILE%
#       %TITLE%
#       %SUBTITLE%
# TODO: error check args!

# So the prog will be called like: /path/to/script "%DIR%" "%FILE%" "%TITLE%" "%SUBTITLE%"

echo "Starting Replex job..."

# Locate the file speified
SRC_DIR="$1/"           #       %DIR% plus a trailing slash
SRC_FILENAME=$2 #       %FILE%

SRC_FILE="${SRC_DIR}${SRC_FILENAME}"

echo "Source file is $SRC_FILE"

# Specify output path
DEST_BASE_DIR=/home/mythtv/myth2avidemux/

# Save it to dir with name of show for easier handling of things
DEST_DIR="/home/mythtv/myth2avidemux/$3/"

# Check the destination directory exists
if [ ! -d "$3" ];
then
        mkdir -p "$DEST_DIR"
fi

# Form filename
DEST_FILENAME="$3 XX-XX $4.mpeg2"

DEST_FILE="${DEST_DIR}${DEST_FILENAME}"

# See if the destination filename exists
if [ -e "$DEST_FILE" ];
then
        # if it does already exist, prepend the date/time or something
        $FILE_PREFIX = `date +%y%m%d-%l%M`
        $DEST_FILE="${DEST_DIR}${FILE_PREFIX}${DEST_FILENAME}"
fi

echo "Destination file is $DEST_FILE"

# Run the file through replex
#REPLEX_CMD=`replex --type MPEG2 $SRC_FILE > $DEST_FILE`
#echo $REPLEX_CMD
#replex --type MPEG2 --of "$DEST_FILE" "$SRC_FILE"
#cp "$SRC_FILE" "$DEST_FILE"
mencoder "$SRC_FILE" -oac copy -noskip -ovc copy -of mpeg -o "$DEST_FILE"

echo "Finished Replexing $DEST_FILE"

# Exit nicely
exit 0
```

FWIW I never finished it but the basic syntax is there to retain the prog name/prog title metadata. It just copies the file out of the tvstore directory into another and then runs mencoder over it (I did this to turn it from an MPEG2-TS into and MPEG2-PS as Avidemux didn't play nicely with MPEG2-TS at the time). I wrote a similar script that did almost the same thing but transcoded and copied the video into a format that'd work on my iAudio X5 (if it was mounted, of course) for watching on my way into work.

---

### Post by ubnewbie2 on 2008-01-27
Excellent.  So are the variables %DIR%, %FILE% etc supplied by mythtv when the user job is run? i.e. if I point to program xyz, myth will populate the %FILE% variable with the coded filename of the xyz show?

---

### Post by stdPikachu on 2008-01-27
Aye, they're variables used internally by Myth and as such only work when defined in Myth jobs, think I found them somewhere in the MythTV docs. IIRC nuvexport gets around by querying the DB on its own. I'll have a gander when I'm back home to see what the exact line I supplied in mythtv-setup (which is where you set up user jobs, in case you were wondering).

---

### Post by ubnewbie2 on 2008-01-28
> **stdPikachu said:**
> Aye, they're variables used internally by Myth and as such only work when defined in Myth jobs, think I found them somewhere in the MythTV docs. IIRC nuvexport gets around by querying the DB on its own. I'll have a gander when I'm back home to see what the exact line I supplied in mythtv-setup (which is where you set up user jobs, in case you were wondering).

Yes, I'd appreciate that.

This will get me started on developing some of my own jobs for myth.  Something I haven't delved into yet, even though I've been writing programs and scripts in many different languages at work, bash shell scripts are something I've only dabbled with.  Nothing to frightening there from what I can see :)

---

### Post by stdPikachu on 2008-01-28
There we go, just hoiked this outta the DB:
```
/home/mythtv/.mythtv/mpeg-ts2mpeg-ps.job "%DIR%" "%FILE%" "%TITLE%" "%SUBTITLE%" >> /home/mythtv/job.log 2>&1
```
As you say, nothing too frightening :) Just write your script and define it in the same way I've done here; `/path/to/script "%ARG1%" "%ARG2%"` etc.

---

### Post by Weidbrewer on 2008-03-05
Is there a GUI application out there for this?   I'm yet to get any sort of scripting or command line trickery to work for this.   Something like Any Video Converter for Windows, but that can handle .nuv files.   I just need something I can plug the file in to, click a button, and out comes a Mpeg-2 or mpeg-4.    That would be awesome.

---

### Post by jakev383 on 2008-03-08
You can use the Optical Disks menu - select your video file and re-encode it like you were burning a DVD (follow the menus). You'll get it re-encoded to a smaller format (if you want - I use EP since I'm recording in standard definition anyway, makes the file smaller) and just make sure you have the box for "burn" unchecked in the make DVD menu. That will leave you with the ISO file for the DVD which you could burn, but I mount it:
```
sudo mount -o loop mythtv.iso /tmpiso
```
And then browse to that folder (/tmpiso or whatever you want to use) and then copy the MPEG file off of there into my video directory (mine is on a NFS share). You'll lose the metadata, b\ut you can get most of that back by entering the IMDB number and then you'll have it re-encoded in a smaller size (your card records something like 704x704 even though it's a standard definition signal) so it'll be re-encoded to a much smaller size 2.2G down to ~400M or so).
Kinda a round-about method and it could probably be scripted but it does work and it's all built in so there's no need to write/brew your own script if you don't want to.

---

