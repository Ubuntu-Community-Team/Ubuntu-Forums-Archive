---
title: "Nice not nice enough"
date: 2010-06-01
forum: Multimedia Software
---

### Post by owenlinx on 2010-06-01
After several days of searching and honing my limited bash skills i have run into an issue I can't solve. So I am humbly asking for a bit of help. 

```

#!/bin/bash

CHAN=$(zenity --list --text "Choose Channel" --radiolist --column "Pick" --column "Channel" 3 'cox' 5 '5' 6 '6' 8 '8' 9 '9' 11 '11' 25 '25' 26 '26' 27 '27' 28 '28' 29 '29' 30 '30' 32 '32' 33 '33' 34 '34' 41 '41' 48 '48' 49 '49' 55 '55' 57 '57' 58 '58' 59 '59' 61 '61' 63 '63')

START=$(zenity --title "Start Time" --entry --text "Choose a recording time (HH:MM)")

END=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:02:00 '00:02:00' 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')

NAME=$(zenity --title "Name Selector" --entry --text "Select a file name (without extension or spaces)")

BIT=$(zenity --list --text "Choose a Bit Rate" --radiolist  --column "Pick" --column "Bit Rate" 500 '500' 1000 '1000' 1250 '1250' 1500 '1500' 2000 '2000' 2500 '2500')

DENOISE=$(zenity --list --text "Choose a Denoise Level" --radiolist  --column "Pick" --column "Denoise" off 'none' weak 'weak' medium 'medium' strong 'strong')

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
SVTIME=$( date +%d%H%M )

until test "$NOW" = "$START"
do
	sleep 10
	NOW=$(date +%H:%M)
done

mkdir -p "/home/justin/Videos/tv/${NAME}"

RECDIR=$"/home/justin/Videos/tv"
SAVDIR=$"/home/justin/Videos/tv/${NAME}"

#killall zenity
killall tvtime
killall transcode


amixer -q set "Line" 100% unmute
#amixer -q set "Analog Mix" 100% unmute
amixer -q set "Line" 0% mute

v4lctl setchannel ${CHAN}

#zenity --text "Recording ${NAME} on channel ${CHAN} started at ${NOW} and will last ${END} minutes" --notification

/usr/bin/nice -n -11 transcode -x v4l2,v4l2 \
	-M 2 \
	-i /dev/video0 \
	-p /dev/dsp1 \
	-y ffmpeg,tcaud \
	-F ffv1 --config_dir ~/.transcode \
	-c 00:00:00-${END} \
	-f 29.970,4 \
	-g 640x480 \
	-N 0x1 \
	-u 128,2 \
	-e 32000,16,2 \
	-J levels \
	-o ${RECDIR}/${NAME}${SVTIME}.mkv 

#killall zenity
killall transcode 
amixer -q set "Line" 0% mute  

/usr/bin/nice -19 HandBrakeCLI --input "${RECDIR}/${NAME}${SVTIME}.mkv" --output "$SAVDIR/${NAME}${SVTIME%.*}".mp4 -e x264 -b ${BIT} -w 720 -l 480 -a 1 -E faac -B 160 -R auto -6 dpl2 -f mp4 --detelecine --decomb --denoise=${DENOISE} --crop 0:0:0:0 -x level=41:me=umh &
PID=$! ;
cpulimit --pid "${PID}" --limit 50

rm "${RECDIR}/${NAME}${SVTIME}.mkv"

```

The issue is transcode is still losing frames. If handbrake is running transcode runs @ 22 fps. I have tried ulimit to stop mem &  
cpulimit to slow down well the cpu. Any help would be appreciated.

---

