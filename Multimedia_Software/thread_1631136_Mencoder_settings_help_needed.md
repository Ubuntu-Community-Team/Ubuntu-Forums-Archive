---
title: "Mencoder settings help needed"
date: 2010-11-26
forum: Multimedia Software
---

### Post by davbren on 2010-11-26
Hey all, I'm doin a little python app for encoding .avi from dvds. I know there are a few really good applications out there that do the same thing but I wanted something simple with less faff.

The application has 3 settings: Fast, Medium, and Slow. These are for the varying quality rips. 

For file format I was thinking either lavc or Xvid. So my first question is, which is better? I really don't know anything about it and I haven't found a decent site that compares them. 

And secondly what are the best settings for a DVD rip for a Fast Rip, a 'Best of Both' Rip, and a Best Quality Rip?

If I've missed any factors in this, please let me know, I'm new to the DVD ripping game.

*Disclaimer: I have no intentions of distributing the movies, they are for my own uses.*

---

### Post by Boondoklife on 2010-11-26
Here is a bash script I threw together a while ago to rip dvds, you can play with the commands if you like and use them.

```

#!/bin/bash
#
#
#    Requires: zenity, mencoder, dvdauthor, dvd+rw-tools
#
#
IFS=$'\n'
TEMP_DIR='converted'

if [ "$1" == "" ]; then
    zenity --error --text="No files were specified"
    exit
fi

while [ "$DRIVE_NUMBER" == "" ]
do
    DRIVE_NUMBER=$(zenity --entry --text="What dvd drive is the disc in" --entry-text="dvd://1")
done

FILE=$DRIVE_NUMBER
    FOLDER="${FILE%/*}"'/'
    FFILE="${FILE##*/}"

    mkdir "$FOLDER$TEMP_DIR"

    if [ $DEINTERLACE -eq 1 ]; then
        nice -n 19 mencoder "$FILE" -ss 32 -ovc x264 -x264encopts threads=auto:pass=1:turbo:bitrate=1000:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:\
        direct_pred=auto:keyint=300 -vf pp=md,scale=-10:-1,harddup -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000 -ofps 24000/1001 -o /dev/null 2>&1 | \
        awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Complete :\\t\\t"$3"%\\nProcessing Rate :\\t"$4"\\nTime Remaining :\\t"$6"\\nEstimated Size :\\t"$7; fflush();}' | \
        nice -n 19 zenity --progress --auto-kill --auto-close --title="Converting ${FILE##*/} (Pass 1 of 2)" --width=450

        nice -n 19 mencoder "$FILE" -ss 32 -ovc x264 -x264encopts threads=auto:pass=2:turbo:bitrate=1000:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:\
        direct_pred=auto:keyint=300 -vf pp=md,scale=-10:-1,harddup -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000 -ofps 24000/1001 -o "$foLDER$TEMP_DIR/${FFILE%.*}.avi" 2>&1 | \
        awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Complete :\\t\\t"$3"%\\nProcessing Rate :\\t"$4"\\nTime Remaining :\\t"$6"\\nEstimated Size :\\t"$7; fflush();}' | \
        nice -n 19 zenity --progress --auto-kill --auto-close --title="Converting ${FILE##*/} (Pass 1 of 2)" --width=450

    else

        nice -n 19 mencoder "$FILE" -ss 32 -ovc x264 -x264encopts threads=auto:pass=1:turbo:bitrate=1000:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:\
        direct_pred=auto:keyint=300 -vf scale=-10:-1,harddup -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000 -ofps 24000/1001 -o /dev/null 2>&1 | \
        awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Complete :\\t\\t"$3"%\\nProcessing Rate :\\t"$4"\\nTime Remaining :\\t"$6"\\nEstimated Size :\\t"$7; fflush();}' | \
        nice -n 19 zenity --progress --auto-kill --auto-close --title="Converting ${FILE##*/} (Pass 1 of 2)" --width=450

        nice -n 19 mencoder "$FILE" -ss 32 -ovc x264 -x264encopts threads=auto:pass=2:turbo:bitrate=1000:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:\
        direct_pred=auto:keyint=300 -vf scale=-10:-1,harddup -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000 -ofps 24000/1001 -o "$foLDER$TEMP_DIR/${FFILE%.*}.avi" 2>&1 | \
        awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Complete :\\t\\t"$3"%\\nProcessing Rate :\\t"$4"\\nTime Remaining :\\t"$6"\\nEstimated Size :\\t"$7; fflush();}' | \
        nice -n 19 zenity --progress --auto-kill --auto-close --title="Converting ${FILE##*/} (Pass 1 of 2)" --width=450
    fi

    rm divx2pass.log divx2pass.log.mbtree

```

---

### Post by SeijiSensei on 2010-11-27
You might consider using two-pass encoding for the "high quality" version.  The [mencoder guide]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html") is pretty helpful on all these topics.

---

