---
title: "FFmpeg Live Stream Recording x264-aac-mkv on Bionic Beaver"
date: 2018-10-03
forum: Multimedia Software
---

### Post by xinuzi on 2018-10-03
Hello,

I've been digitizing live stream video succesfully with the Easycap007-usb-stick (SCART to Composite to usb to PC) and with this 
**ffmpeg-recordingscript** on (L)ubuntu 16.04 (and now also on (L)Ubuntu 18.01 Bionic Beaver) and this on different older and newer laptops (all with at least 4Gb ram - 2Gb ram+ should do fine):

```

#!/bin/bash

clear

echo "FFMPEG RECORD X264 AAC MKV"

# First of all set /dev/video* (video picture) and hw:*,* (video audio) to the correct number(s) for your input.

# -g = maximal 'gop'-distance between I-frames (keyframes). Standard = 250. 
# Lower values help to cut the video, with e.g. Avidemux, more easily afterwards. 
# Advised gop-settings: NTSC = 15, PAL = 12.

# For good video-audio synchronization, fps output preferably the same als fps-input. PAL = 25, NTSC = 30.

# All presets (default = medium): ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow, placebo.

# All -tune parameters (divide with comma): film (fine grain), animation (cartoons), grain (keep grain), 
# stillimage (for still images), fastdecode (fast input), zerolatency (fast encoding)

# All -profile:v settings (optional): baseline, main, high, high10, high422, high444. 

# '-pix_fmt yuv420p' strongly advised in output considering compatible replay of digital video on certain tv sets.
# '-vsync 1' = personal choice. Can be left out.

# Variables

OUTPUTFILE="Recording_$(date '+%Y%m%d_%H%M%S')_EDIT.mkv"  

echo

echo "This script launches FFmpeg Record x264-aac code and"
echo "displays the resulting file in GNOME Mplayer"

echo

ffmpeg -f v4l2 -standard PAL -thread_queue_size 4000 -i /dev/video0 -f alsa -thread_queue_size 4000 -i hw:0,0 -c:v libx264 -preset veryfast -tune film,fastdecode,zerolatency -crf 23 -s 640x360 -r 25 -aspect 16:9 -pix_fmt yuv420p -g 12 -vsync 1 -c:a aac -b:a 128k -ac 2 -ar 44100 $OUTPUTFILE &

sleep 1

gnome-mpv $OUTPUTFILE & 
# Opens gnome player to view recording stream
# If not working, try 'gnome-mplayer' or install it 

wait # let the original ffmpeg encoding continue

```

Save this recording script as e.g. "VID_SCRIPTS_Record_x264_aac_MKV.sh"

Give it rights Everyone and 'Execute in Terminal'.

Within the script you could replace the 'mkv' container with the 'mp4' one.

The script should work conveniently after 1 or two tries and on condition that the video and audio inputs are set correctly.

Also check if you have v4l2-ctl installed ('sudo apt-get install v4l-utils').

This **script to easily check input devices**:

```

#!/bin/bash

clear

echo "CHECK VIDEO AND AUDIO INPUT DEVICES"

# Checking the video requires the presence of v4l-utils

# Variables

VIDEODEV="v4l2-ctl --list-devices"
AUDIODEV="arecord -l"

echo

echo "VIDEO"

echo

$VIDEODEV

echo

echo "AUDIO"

echo

$AUDIODEV

echo

read # show terminal output

```

Name it e.g. 'VID_SCRIPTS_Check_Input_Devices.sh' and give it rights Everyone.
Click, Execute in Terminal or call it from cli with 'bash file_name.sh'.

Video image quality of recordings with e.g. the EasyCap007 usb video stick has improved tremendously since Bionic Beaver.
On any pc with this Ubuntu version.
Before, I had to tweak the image brightness all the time with v4l2-ctl.

Other settings: see FFmpeg and v4l2-ctl documentation.

P.S.: Note that recording script won't work for encrypted tv channels (CI+ and such). You'll become a black/blank video picture.


Happy recordings!

---

### Post by xinuzi on 2018-10-03
*[Obsolete, see first post]*

---

### Post by xinuzi on 2018-10-03
*[Obsolete, see first post]*

---

### Post by xinuzi on 2018-10-04
*[Obsolete, see first post]*

---

### Post by xinuzi on 2018-10-25
[I]Updated this thing for those interested.

See first post.[/I]

---

### Post by xinuzi on 2018-11-01
I am sorry. Sir Monologist again...

If you want to aftercut a recorded video (much faster in streamcopy mode) with **Avidemux** and the vid doesn't load, 
use this **script to recompile the video container**:

```

#!/bin/bash

clear

echo "FFMPEG CONVERT MKV TO MKV STREAMCOPY"

echo

for i in *.mkv; do ffmpeg -i "$i" -c copy "${i%.*}_converted.mkv"; done

exit

```

Name it e.g. 'VID_SCRIPTS_Convert_MKV_to_MKV.sh' and give it rights Everyone.

You can use it to reconvert the container of a bunch of mkv-files.
Or any other recorded video file (just change the file extensions of input and output).

After this, Avidemux should load your file fine.

---

