---
title: "Setting Mythtv user job variables according to file extension and type"
date: 2014-03-29
forum: Mythbuntu
---

### Post by Iago6776 on 2014-03-29
I want to set the variable COMMAND to behave in one of two ways depending on the file extension and type. The reason behind this is some origin video files have been transcoded from *.mpg MPEG-4 video files to NuppelVideo *.nuv files, and some have not yet been. While I tweak the settings, I still want the script to call out a different command if necessary. Something like:
```
if[INDENT]{INDIR}/${CHANID}_${STARTTIME}.* == {INDIR}/${CHANID}_${STARTTIME}.mpg && {INDIR}/${CHANID}_${STARTTIME}.* is really an MPEG-4 file[/INDENT]
then[INDENT]COMMAND == MPGCOMMAND && PARAMS == MPGPARAMS[/INDENT]
or if[INDENT]{INDIR}/${CHANID}_${STARTTIME}.* == {INDIR}/${CHANID}_${STARTTIME}.nuv && {INDIR}/${CHANID}_${STARTTIME}.* is really an NuppelVideo file[/INDENT]
then[INDENT]COMMAND == NUVCOMMAND && PARAMS ++ NUVPARAMS[/INDENT]

but if[INDENT]{INDIR}/${CHANID}_${STARTTIME}.* == {INDIR}/${CHANID}_${STARTTIME}.neither mpg nor nuv && the file is something else[/INDENT]
then[INDENT]error out and send the error to the log file.[/INDENT]
fi

```

Here is my script:
```

[COLOR=#000000][FONT=Ubuntu Mono]#! /bin/bash
[/FONT][/COLOR]scriptstarttime=$(date +%F-%H%M%S)

CHANID=$1
STARTTIME=$2

INDIR="/var/lib/mythtv/recordings"
OUTDIR="/home/username/Dropbox"
PROG="/home/username/bin/ffmpeg"

NUVPARAMS="-y -stats -deinterlace -vcodec libx264 -vprofile baseline -level 13 -maxrate 76800 -bufsize 3000000 -acodec libfdk_aac -ac 2 -ab 128k -ar 44100 -sn"
MPGPARAMS="-y -stats -deinterlace -vcodec libx264 -vprofile baseline -level 30 -maxrate 100000-bufsize 10000000 -acodec libfdk_aac -ac 2 -ab 128k -ar 44100 -sn"
 
LOGFILE="/home/username/Dropbox/DropboxTranscode.log"
OUTFILE="${OUTDIR}/${CHANID}_${STARTTIME}"

touch $LOGFILE
echo "$scriptstarttime Dropbox Transcode" >> $LOGFILE 

#IF TEST

COMMAND="${PROG} -i ${INDIR}/${CHANID}_${STARTTIME}.* ${PARAMS} ${OUTFILE}.mp4"
[COLOR=#000000][FONT=Ubuntu Mono]
echo "${COMMAND}" >> $LOGFILE
[/FONT][/COLOR]
```
Thanks,
Iago6776

---

### Post by blm-ubunet on 2014-03-30
AFAIK nuv is deprecated and implies you have transcoded into MJPEG or MPEG-ASP?
Mythtv can not transcode mpeg4 layer 10 H264 except by piping into external prog (ffmpeg).

You are trying to use mythtv's job queue to launch scripts on files.
You can find the full filename path with mysql DB operations.

You could get mythtv to output the recording filename into your script %FILENAME%.

In your script can then work out extension from:
extension=${myfilename##*[/|.\\]}

---

