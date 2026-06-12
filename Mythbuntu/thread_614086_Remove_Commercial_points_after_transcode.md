---
title: "Remove Commercial points after transcode"
date: 2007-11-15
forum: Mythbuntu
---

### Post by ghuber on 2007-11-15
I'm having a problem.

I set my Mythbox up to transcode and remove commercials from my recorded programs based on the how to here:

[http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials](http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials)

I added the line to the script to remove the commercial points.  The script is working but it is not removing the commercial points.  Here is my script,  did I do something wrong?  I am using 7.10 Gutsy.

> #!/bin/sh
VIDEODIR=$1
FILENAME=$2
# Sanity checking, to make sure everything is in order.
if [ -z "$VIDEODIR" -o -z "$FILENAME" ]; then
        echo "Usage: $0 <VideoDirectory> <FileName>"
        exit 5
fi
if [ ! -f "$VIDEODIR/$FILENAME" ]; then
        echo "File does not exist: $VIDEODIR/$FILENAME"
        exit 6
fi
# The meat of the script. Flag commercials, copy the flagged commercials to
# the cutlist, and transcode the video to remove the commercials from the
# file.
mythcommflag -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -gt 126 ]; then
        echo "Commercial flagging failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
mythcommflag --gencutlist -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Copying cutlist failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
mythtranscode --honorcutlist --showprogress -i $VIDEODIR/$FILENAME -o $VIDEODIR/$FILENAME.tmp
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Transcoding failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
mv $VIDEODIR/$FILENAME $VIDEODIR/$FILENAME.old
mv $VIDEODIR/$FILENAME.tmp $VIDEODIR/$FILENAME
mythcommflag -f $VIDEODIR/${FILENAME} --rebuild
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "Rebuilding seek list failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
mythcommflag --clearcutlist -f $VIDEODIR/$FILENAME
ERROR=$?
if [ $ERROR -eq 0 ]; then
        # Fix the database entry for the file
        cat << EOF | mysql mythconverg
UPDATE
        recorded
SET
        cutlist = 0,
        filesize = $(ls -l $VIDEODIR/$FILENAME | awk '{print $5}')
WHERE
        basename = '$FILENAME';

DELETE FROM
       `recordedmarkup`
WHERE
       CONCAT( chanid, starttime ) IN (
               SELECT
                       CONCAT( chanid, starttime )
               FROM
                       recorded
               WHERE 
                       basename = '$FILENAME'
       );
EOF
        exit 0
else
        echo "Clearing cutlist failed for ${FILENAME} with error $ERROR"
        rm /usr/video/$FILENAME.tmp
        exit $ERROR
fi

---

### Post by superm1 on 2007-11-16
Personally I wouldn't recommend letting autocommercial removal and transcoding go on autopilot.

Let it flag things automatically, but for a few weeks at least make sure the flagging is dead on before you do any scripts like this.

To remove them permanently, just hit E during playback of the recording and z to load the commercial cut list.  You can adjust points in this editor too.  Then from the recordings menu go through and queue up a "Default" job.

---

### Post by hotstyle765 on 2007-11-16
ghuber I also went through that process from the wiki and had the same problem. It would run the transcode but not remove any commercials. I gave up on it because there was not a lot of information out there to get it going automatically.

superm1: I am guessing you would have to do that on every recoding? People usually want to cut out commercials automatically because they are not watching them through myth. At least that is what I was doing until I started messing around with the live CD client.

---

### Post by ghuber on 2007-11-16
Its been working very well for me and cutting the commercials out.  My only problem has been that after it removes the commercials, the cut list is still there.  So it will be playing along and all of a sudden jump ahead in the show.  I hit the back button and it jumps back to that point and continues like normal.  I just need to remove the cut list after it is done.  I've been happy with the accuracy so far.

---

