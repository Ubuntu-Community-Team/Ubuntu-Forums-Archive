---
title: "Transcoding user job and mythlink.pl"
date: 2014-03-24
forum: Mythbuntu
---

### Post by Iago6776 on 2014-03-24
I want to know how to make my user job transcode script more flexible. To start, I've been using and tweaking Myth 0.25 on LTS 12.04 since upgrading to it from 11.10. I've added hard disks, installed webmin and used tight vnc to control it from anywhere, got mythlink.pl to work as a cron job or as a direct command (more about that later), installed a custom ffmpeg instance to transcode 2.5 GB files to h264 200 MB files, installed Dropbox to auto-upload those files once I manually changed the name of the file, and added a HDHomerun Prime to supplement the original HDHomerun single video source.

With the failure of the installation hard drive, I have recovered the database and the recordings, installed a new CentOS operating system on a mirrored RAID 1 system of 2 2TB hard drives, added memory to bring the system up 4Gb to 12Gb, added a volume group to the system of one 3TB drive and one 4TB drive, added a wireless NIC to move the rig downstairs, and virtualized the back end 12.04/0.25 so I can back up the back end and rebuild it quickly. I use the 7TB volume to store all the recordings and have access to it through the virtualized backend.

My problem is now I've been running a replacement computer which will become the dedicated frontend. It hasn't been running my scripts for autotranscoding correctly, so some of my files are .nuv now but those I haven't transcoded are still .mpg.  My transcoding script I used to shrink and export my recordings to Dropbox doesn't work the same anymore because they're not transcoded. Rather than figure out how to merge the two databases and folders of recordings and etc., (something I haven't heard of anyone doing,) I want to back up some of the files by script transcoding and shrinking them, and uploading the smaller files. 

Eventually I want to run the script in two versions. The first to send some TV shows I want accessible in HTML5 to one folder for viewing through mythweb (for me), and the second to send others to Dropbox (for my kid).

Since I know I can tweak the settings of ffmpeg to get it to work, eventually to the right size and quality, my question is this:

How can my script automatically choose between .nuv transcoded files and original .mpg files, and how can my script use the mythlink-generated name of the file I'm transcoding with the custom instance of ffmpeg to name the script's output file?

My mythlink cron job command and the transcode script follows. Thanks go out to the mythlink.pl creators and updaters, mythbrake.pl creators and updaters, the mythpodcaster creators, the cats and code page, and myriad other users and tweakers I've pieced this together from. I have edited it so that it could be used with the default recordings file location set up when the 12.04/0.25 installs (/var/lib/myth/recordings) and the default location that Dropbox installs itself to (/home/username/Dropbox) and the popular "pretty" folder that many still use from before mythlink was mythlink.

```
 mythlink.pl --link /var/lib/mythtv/pretty --format '%T %-%S%-%c_%Y%m%d%H%i%s
```

```

#! /bin/bash

scriptstarttime=$(date +%F-%H%M%S)

CHANID=$1
STARTTIME=$2

INDIR="/var/lib/mythtv/recordings"
OUTDIR="/home/username/Dropbox"
PROG="/home/username/bin/ffmpeg"
PARAMS="-y -stats -deinterlace -vcodec libx264 -vprofile baseline -level 13 -maxrate 76800 -bufsize 3000000 -acodec libfdk_aac -ac 2 -ab 128k -ar 44100 -sn"

LOGFILE="/home/username/Dropbox/DropboxTranscode.log"
OUTFILE="${OUTDIR}/${CHANID}_${STARTTIME}"

COMMAND="${PROG} -i ${INDIR}/${CHANID}_${STARTTIME}.* ${PARAMS} ${OUTFILE}.mp4"

touch $LOGFILE
echo "$scriptstarttime Dropbox Transcode" >> $LOGFILE
echo "${COMMAND}" >> $LOGFILE
$COMMAND >> $LOGFILE 2>&1

```

Thanks, 
Iago6776

---

### Post by Iago6776 on 2014-03-30
I'm trying to get this answered now in two parts, [here ]("http://ubuntuforums.org/showthread.php?t=2214016")and [here]("http://ubuntuforums.org/showthread.php?t=2214013").

---

