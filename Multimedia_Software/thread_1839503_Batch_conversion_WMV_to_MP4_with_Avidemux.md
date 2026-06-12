---
title: "Batch conversion WMV to MP4 with Avidemux"
date: 2011-09-05
forum: Multimedia Software
---

### Post by tonywhelan on 2011-09-05
I needed to convert a bunch of Windows movie files (.wmv) to MP4 format so my Motorola Xoom would play them reliably.

Installed Avidemux on my Ubuntu 11.04 (32 bit) PC. Its easy to use the GUI but I needed an unattended job to process multiple files, so I saved this script and set the executable bit, double-clicked and let it run through the night. 

Hope it is useful to someone else.


```
#!/bin/bash
# Usage: convert all WMV files to MP4
shopt -s nullglob
for f in *.wmv
do avidemux --force-alt-h264 --load "$f" --audio-bitrate 224 --audio-codec aac --video-codec x264 --save "${f%.wmv}.mp4" --output-format MP4 --quit
done 
```

---

### Post by andrew.46 on 2011-09-05
Nice, I did not know that avidemux could be used this way :).

---

### Post by apos on 2011-12-27
Just created the following script, which uses a avidemux-gui for creating a project file used for avidemux-cli batch conversion. I am currently under ubuntu 11.10.

[LIST=1]
[*]Open a file with avidemux-gui (!!!). 
[*]Configure like you want it to be. 
[*]Save the project.
[/LIST]

Needs avidemux2-cli package!!!

```

#!/bin/bash

FOLDER="Converted"   # Subfolder to put the converted files in
IN_TYPE="mp4"        # File ending of input files
OUT_TYPE="avi"       # Should match the type in avidemux
PROJECT="convert_to_mjpeg.proj"  # the avidemux project file

##########################################

mkdir -p $FOLDER

cat "${PROJECT}" | \
fgrep -v app.load  | \
fgrep -v app.clearSegments  | \
fgrep -v app.addSegment  | \
fgrep -v app.markerA  | \
fgrep -v app.markerB  \
> "${PROJECT}.cli"

BASE=""
for InputItem in *.${IN_TYPE}
do 
	BASE="$(basename $InputItem .${IN_TYPE})"
	avidemux2_cli \
            --load  "$InputItem" \
            --run "$PROJECT.cli" \
            --save "${FOLDER}/${BASE}.${OUT_TYPE}" 
done

```

Works like a charm. I am very happy.
Feel free to adjust.

Greets Axel

---

### Post by apos on 2011-12-27
And the version to put into /usr/local/bin:

```

#!/bin/bash

which avidemux2_cli > /dev/null || echo "Please install: sudo apt-get install avidemux-cli"
which avidemux2_cli > /dev/null || exit 1

[ "$4" ] || cat <<EOF

 USAGE: $(basename $0) 
		<OUTPUT_FOLDER_NAME> 
		<IN_TYPE OUT_TYPE> 
		<OUTPUT_FILETYPE> 
		<AVIDEMUX_PROJECT_FILE_NAME>

 e.g.

 $> $(basename $0) ConvertedFiles mp4 avi myavidemux.proj

EOF

[ "$1" ] || exit 1
[ "$2" ] || exit 1
[ "$3" ] || exit 1
[ "$4" ] || exit 1

FOLDER="$1"
IN_TYPE="$2"
OUT_TYPE="$3"
PROJECT="$4"
LOGFILE="conversion.log"

##########################################

mkdir -p $FOLDER

cat "${PROJECT}" | \
fgrep -v app.load  | \
fgrep -v app.clearSegments  | \
fgrep -v app.addSegment  | \
fgrep -v app.markerA  | \
fgrep -v app.markerB \
> "${PROJECT}.cli"

cat "${PROJECT}.cli"

BASE=""
ERROR="0"
for InputItem in *.${IN_TYPE}
do 
BASE="$(basename $InputItem .$IN_TYPE)"

cat <<EOF
#######################################################################
#######################################################################
## avidemux2_cli 
## --load  "$InputItem"
## --run "$PROJECT.cli" 
## --save "${FOLDER}/${BASE}.${OUT_TYPE}
##
EOF

avidemux2_cli --load  "$InputItem" --run "$PROJECT.cli" --save "${FOLDER}/${BASE}.${OUT_TYPE}" || ERROR="1"

cat <<EOF
#######################################################################

EOF

done

[ "$ERROR" = "1" ] && zenity --info --title "Conversion ended" --text "There have been ERRORS" 
[ "$ERROR" = "0" ] && zenity --info --title "Conversion ended" --text "OK"


```

---

