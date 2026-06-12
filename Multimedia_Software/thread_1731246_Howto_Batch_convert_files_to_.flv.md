---
title: "Howto: Batch convert files to .flv?"
date: 2011-04-16
forum: Multimedia Software
---

### Post by steven.smith on 2011-04-16
So I have a php script that is setup to stream flash video (.flv) and I absolutely love having it. The problem is that any files I want to stream have to be in .flv format for it to work properly as .avi and others obviously don't stream well. Up until now, I've used FFMpeg to change the format from .avi to .flv, however the process takes a lot of time if you have a lot of videos, added to that you have to do one file at a time definitely makes it a pain.

     Does anyone know of a bash script that can take all the files (i.e. avi, .wmv, .mkv, .mpeg4) in one folder and automatically convert it to .flv? Then possibly delete the old files? Low resolution is fine, so long as it at least viewable. Does anyone have a script or know of a program that can do this (I run Ubuntu 10.04). I think FFMpeg has the best chance of doing this, but I don't know the syntax to actually do so.

     I've searched the internet, and while I have found a few scripts, they didn't work for me (still looking into two scripts I found....I am currently messing with them to see if I can get them to work).

     It would be immensely helpful if someone knew of a way to do this. Thanks for any and all help. :)


Edit: I also forget to mention that I have used Winff, but I was looking more for a bash script to do this so that I can set a cron job to convert them every hour or so.

---

### Post by FakeOutdoorsman on 2011-04-19
Here's an example you can start with (I didn't actually test it after I added the flvtool2 part). It doesn't delete your source and it puts the output in the same directory as the input so you'll want to change that. I'm not sure if the part with *flvtool2* will be required for you, but you can use it if your flash player does not show a duration for the video.

```
#!/bin/bash

inputdir=/home/biff/video

set -e

for input in ${inputdir}/*.*
do

# Check if output file already exists, and if yes, then exit.
if [[ -e "${input%.*}.flv" ]]; then
        echo "'${input%.*}.flv' exists. Exiting."
        exit
fi

# Encode with FFmpeg.
ffmpeg -i "${input}" -vcodec libx264 -vpre medium -crf 26 -threads 0 -acodec libmp3lame -ar 44100 -aq 4 -ac 2 "${input%.*}.flv"

# Updates FLV with an onMetaTag with flvtool++, flvmeta, or (if you can't avoid it) flvtool2.
flvtool2 -U "${input%.*}.flv"

done
```

You will need to enable the **libx264** and **libmp3lame** encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by GillbotRebirth on 2011-05-20
> **FakeOutdoorsman said:**
> Here's an example you can start with (I didn't actually test it after I added the flvtool2 part). It doesn't delete your source and it puts the output in the same directory as the input so you'll want to change that. I'm not sure if the part with *flvtool2* will be required for you, but you can use it if your flash player does not show a duration for the video.

```
#!/bin/bash

inputdir=/home/biff/video

set -e

for input in ${inputdir}/*.*
do

# Check if output file already exists, and if yes, then exit.
if [[ -e "${input%.*}.flv" ]]; then
        echo "'${input%.*}.flv' exists. Exiting."
        exit
fi

# Encode with FFmpeg.
ffmpeg -i "${input}" -vcodec libx264 -vpre medium -crf 26 -threads 0 -acodec libmp3lame -ar 44100 -aq 4 -ac 2 "${input%.*}.flv"

# Updates FLV with an onMetaTag with flvtool++, flvmeta, or (if you can't avoid it) flvtool2.
flvtool2 -U "${input%.*}.flv"

done
```You will need to enable the **libx264** and **libmp3lame** encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

Hi, i have copied that code that you gave us, but it says "Invalid data when processing the input" how do you fix that?

---

### Post by Mr.Dee on 2011-05-20
cd to the directory with the files...
 
for f in *.avi; do ffmpeg -i "$f"{$f%.avi}.flv" -sameq; done

---

### Post by GillbotRebirth on 2011-05-20
Okay well i got it to work, but now i am trying to play it back with a flash player on the web but it does not work, any suggestions?

EDIT: Never mind i know what i did wrong, ffmpeg can't convert wmv files the proper way -_-

---

