---
title: "Running script as a user job"
date: 2009-11-11
forum: Mythbuntu
---

### Post by bkristan on 2009-11-11
I'm trying to figure out how to convert recorded shows to a format that will play on my Sandisk Sansa Fuze. I have two working mencoder lines I found in the video2fuze program for 2-pass encoding. Since it's not working for me, I'm just trying to get the first pass to work, and produce a temporary file. I put the command for the first pass into a shell script, which I'm trying to run as user job 1. I have the job enabled in mythtv-setup, Job Queue (backend specific), and the command for user job 1 is set to:

/home/mythtv/export_to_fuze.sh %DIR% %FILE%

I've kept everything _very_ simple, because my level of understanding of all this is pretty simplistic, so all I'm trying to do is pass the filename information to the script. The script is simple too:

#!/bin/sh
VIDEODIR=$1
FILENAME=$2
FILE=$VIDEODIR/$FILENAME
echo $VIDEODIR > /home/mythtv/videodir.txt
echo $FILENAME > /home/mythtv/filename.txt
echo $FILE > /home/mythtv/file.txt
mencoder $FILE \
-ffourcc DX50 \
-ofps 20 \
-vf pp=li,expand=:::::224/176,scale=224:176,harddup \
-ovc lavc \
-lavcopts vcodec=mpeg4:vbitrate=683:vmax_b_frames=0:keyint=15:turbo:vpass=1 \
-srate 44100 \
-af resample=44100:0:1,format=s16le \
-oac mp3lame \
-lameopts cbr:br=128 \
-o /media/nfs_share/vids_pass1/1


I put in the echo statements so I could check that everything was being passed correctly from mythtv to the script. When I run the user job on a file, the txt files get created with the correct filename and directory info, but mencoder doesn't get further than creating the output file (at /media/nfs_share/vids_pass1/1) with 0 bytes. The crazy thing is that when I run the script and pass the directory name and filename from the txt files manually, everything runs fine.

So, I'm stumped. If I pass the wrong directory information the output file doesn't get created, so that's not the problem. Given what does work, it seems like it has to be a problem with running mencoder as a job within mythtv, but I don't see what I'm doing wrong. Can anybody see what my mistake is?

Thanks in advance, this is driving me nuts.

---

### Post by ian dobson on 2009-11-11
Hi,

What do you see from mencoder? You could add > /home/mythtv/memcoder.txt to the end of the memcoder line.

Regards
Ian Dobson

---

### Post by laffinet on 2009-11-12
Have you considered using one of the scripts that is already out there to convert ?

I'm using mythnuv2mkv, which can be configured to use mencoder, different codecs, containers, sizes etc.

Works great for me.

Sorry if this is not what you're after, thought I'll throw another option in the mix

---

### Post by bkristan on 2009-11-13
Hi - I'd definitely consider using other approaches (mythexport, nuvexport), but the problem is that my player is apparently picky about formats. I was hoping it would be easier to use the working mencoder commands from the video4fuze package in my own script, rather than figure out how to set up one of these other packages to produce a working avi file.

I'll check the mencoder output this evening, thanks for the suggestion - it's probably something really obvious.

---

