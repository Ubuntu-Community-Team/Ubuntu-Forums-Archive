---
title: "Moving a recording to video section - 1st try -  user job using mythtranscode"
date: 2008-01-30
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-30
I have written the following user job, based on the script posted by stdPikachu (thanks heaps)

Mine is simplified, and uses mythtranscode.   It seems to work, except that mythtranscode gets the aspect ratio wrong - I have to look into that.

Here's the code...

```
#!/bin/bash
# Custom user job designed to save recordings to the videos directory for myth video

# This script needs the following variables in this exact order to run:
#       %DIR%
#       %FILE%
#       %TITLE%
#       %SUBTITLE%
#	%CHANID%
#	%STARTTIME%
# TODO: error check args!

# So the prog will be called like: /path/to/script "%DIR%" "%FILE%" "%TITLE%" "%SUBTITLE%" "%CHANID%" "%STARTTIME%"

echo "Starting save_to_videos job..."

# Locate the file specified (not really used - from old script)
SRC_DIR="$1/"           #       %DIR% plus a trailing slash
SRC_FILENAME=$2 #       %FILE%
SRC_FILE="${SRC_DIR}${SRC_FILENAME}"

echo "Source file is $SRC_FILE"

# find channel and start time
CHANID="$5"
STARTTIME="$6"

echo "Channel ID and start time are $CHANID , $STARTTIME"

# Specify output path to myth video directory
DEST_DIR=/var/lib/mythtv/videos/

# Form unique filename
DEST_FILENAME="$3 XX-XX $4.mpeg2"
FILE_PREFIX="$5$6"
DEST_FILE="${DEST_DIR}${FILE_PREFIX}_${DEST_FILENAME}"

echo "Destination file is $DEST_FILE"

mythtranscode --mpeg2 --chanid "$CHANID" --starttime "$STARTTIME" --outfile "$DEST_FILE" --profile autodetect

echo "Finished  $DEST_FILE"

# Exit nicely
exit 0
```

---

### Post by ubnewbie2 on 2008-01-30
Actually, mythtranscode isn't getting the aspect ratio wrong.  It was mplayer. I have had to force the aspect ratio for mplayer when playing videos because the default command line, using -zoom, was getting it wrong.

It's all working great now.

btw:  the main reason I chose to use mythtranscode here is that I wanted it to honour my cut-points, so, at the very least, I can trim the start of the recording, so that when I save it as a video for keeping, it will not have rubbish at the start. If I get very keen, I can also load up the commercial flagging as cut points too I suppose.

---

