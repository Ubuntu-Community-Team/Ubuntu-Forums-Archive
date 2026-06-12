---
title: "Yet Another Autocrop Script..."
date: 2011-04-18
forum: Multimedia Software
---

### Post by Nutria on 2011-04-18
So far the input types I've tested it on are MPEG-2 and AVI.  It outputs h.264 in an MKV container.  Since video quality is more important to me than file size, I'm not overly aggressive at compression.

It only crops the top and bottom, since that's all I really want.

Dependencies are mktemp and handbrake-cli.

Yes, it only converts one file, but that's ok, since you can create a second script which call this script.  (Being an Old Programmer, I like that division of labor thing...)

Hope someone finds it useful!

Sample usage:

```
cd Videos/path/to/source
for f in *avi; do ~/convert_video.sh ${f}; done

```


```
#!/bin/bash

inp_name="$1"
audio_track=${2}

if [ -z $audio_track ]; then
    audio_track=1
fi

CONT=mkv
cont_name="${inp_name%.*}.$CONT"
ext=$(echo ${inp_name##*.} | tr [:upper:] [:lower:] )

tmpfile=$(mktemp)

HandBrakeCLI --scan -t1 -i ${inp_name}  2>&1 | egrep "bitrate:|Video:|Audio:|autocrop:" > $tmpfile

AENC=

case "$ext" in
    "mpeg|mpg") Q=18 ;;
    "avi")  Q=20
            AENC=$(grep 'Audio:' $tmpfile | awk '{print $3}')
            ABRATE=$(grep 'Audio:' $tmpfile | awk '{print $8}')
            ;;
esac

if [ -z $AENC ]; then
    AENC=ac3
fi

case "$AENC" in
    "aac") AUDIO="faac --arate 48 --ab 256" ;;
    "mp3") AUDIO="lame --arate 48 --ab 256" ;;
    "ac3") AUDIO="copy" ;;
esac


AC=$(grep autocrop: $tmpfile | awk '{print $3}')

AC_TOP=$(echo $AC | cut -d/ -f1)
AC_BOT=$(echo $AC | cut -d/ -f2)

echo "$(date +"%F %T, %a") Start ${inp_name}" >> timings.txt
HandBrakeCLI -e x264 -q $Q --encopts b-adapt=2:rc-lookahead=50:psy-rd=1\|0.2 \
             -a ${audio_track} -E $AUDIO -6 dpl2,auto -R Auto,Auto -D 0.0,0.0 --drc 2.0 \
             --detelecine --decomb -m \
             --loose-anamorphic --crop ${AC_TOP}:${AC_BOT}:0:0 \
             -i ${inp_name} \
             -t1 -o "$cont_name"
echo "$(date +"%F %T, %a") End ${inp_name}" >> timings.txt
echo "" >> timings.txt
```

---

