---
title: "how to fix script from FFmpeg to Mencode ?"
date: 2010-07-04
forum: Multimedia Software
---

### Post by dark2x3d on 2010-07-04
I have this script to convert **any file to AVI using ffmpeg**

```


#!/bin/bash
# initialize file names
STRING_TEMP_FILENAME="/tmp/${RANDOM}.tmp"
STRING_INPUT_FILENAME=${1}
# >

# get source file length (we need it to calculate progress) 
INT_INPUT_FILELENGTH=`mplayer -identify -frames 0 -vc null -vo null -ao  null \
			"${STRING_INPUT_FILENAME}" 2>/dev/null | \
			grep ^ID_LENGTH | sed -e 's/^.*=//' -e 's/[.].*//'`

# if filelength is empty, we can't continue.
if [ -z ${INT_INPUT_FILELENGTH} ]; then
	kdialog --error "Selected file cannot be converted."
	exit
fi
# >

STRING_OUTPUT_FILENAME=`echo ${STRING_INPUT_FILENAME} | sed  s/${STRING_INPUT_FILENAME##*.}/avi/`
# get destination filename
STRING_OUTPUT_FILENAME=`kdialog --icon "reload" \
			--getsavefilename "${STRING_OUTPUT_FILENAME}" "*.avi|Supported video  files (*.avi)"`

# if user pressed cancel ...
if [ -z ${STRING_OUTPUT_FILENAME} ]; then
	exit
fi
# >
[B]
# ffmpeg file conversion
ffmpeg -i "${STRING_INPUT_FILENAME}" \
"${STRING_OUTPUT_FILENAME}" > /dev/null 2>  "${STRING_TEMP_FILENAME}" &
[/B]
# after execution, get ffmpeg's process id
INT_FFMPEGPID=${!}
# >

# create kdialog (ipod icon is optional)
STRING_KDIALOGID=`kdialog --progressbar "Converting file:

Source: ${STRING_INPUT_FILENAME}
Destination: ${STRING_OUTPUT_FILENAME}

" --title "Converting" --icon "reload"`
# >

# set kdialog's properties
dcop "${STRING_KDIALOGID}" setAutoClose true
dcop "${STRING_KDIALOGID}" showCancelButton true
# >
[B]
# main loop: here we read ffmpeg's progress
# and we use it in our kdialog window
while ps | grep "${INT_FFMPEGPID} " >/dev/null
do
	if [ `dcop "${STRING_KDIALOGID}" wasCancelled` == "true" ]; then
		kill ${INT_FFMPEGPID}
		break
	fi

	FFMPEG_SECONDS_COMPLETED=`tail -c 90 "${STRING_TEMP_FILENAME}" | \
					awk -F "time=" {'print $2'} | cut -d"." -f 1`
	[ -n "$FFMPEG_SECONDS_COMPLETED" ] || FFMPEG_SECONDS_COMPLETED=0
	 INT_PERCENTAGE=$((100*$FFMPEG_SECONDS_COMPLETED/${INT_INPUT_FILELENGTH}))

	dcop "${STRING_KDIALOGID}" setProgress ${INT_PERCENTAGE}
done
# >
[/B]
# make sure, our temporary file will be deleted, and
# kdialog will be destroyed
rm ${STRING_TEMP_FILENAME} > /dev/null 2>&1
dcop "${STRING_KDIALOGID}" setProgress 100
# >

```

I replace part 1 with mencoder script
```

# mencoder file conversion
mencoder "${STRING_INPUT_FILENAME}" -oac mp3lame -ovc lavc -lavcopts  vcodec=mpeg4 \
-o "${STRING_OUTPUT_FILENAME}" > /dev/null 2>  "${STRING_TEMP_FILENAME}" &

```
[B]
kdialog window will show and script will work fine _but without  showing how many percent %,_
but I don't know what should I change in part two.. 
any body can fix the script to make it work fine with mencoder , please?[/B]

---

