---
title: "Video Playback on Blackberry 8830"
date: 2008-06-05
forum: Multimedia Software
---

### Post by blazercist on 2008-06-05
Hey, I finally figured out how to do file transfers from my Ubuntu laptop to my Blackberry 8830 WorldPhone :) !!!

So here's the problem:  Video will not play back. 

I know that the Blackberry will only play .mp4 video, on windows I used the Blackberry manager app which in turn used Roxio to convert my avi files to mp4 on the fly while copying to the Blackberry.  I followed a guide on the ubuntu forums to convert .avi to .mp4 using mencoder, but the file won't play.  The Blackberry video player app just says "Loading..." and then after a minute it says "Error......."  

It sees the file and tries to load it so I think the problem is the encoding, does anyone know how to encode an avi to mp4 so that it will play on the Blackberry?

---

### Post by aeiah on 2008-06-05
maybe this will help:

[http://ubuntuforums.org/showthread.php?t=640227](http://ubuntuforums.org/showthread.php?t=640227)

---

### Post by blazercist on 2008-06-05
Thanks! I was looking for a cli solution (mainly because I can use SSH to do it from my Blackberry during work LOL), I'll give this a try after work.

---

### Post by blazercist on 2008-06-10
I tried this, the file converts well and everything seems fine until I copy it to my Blackberry...  It looks like it copies and then I unplug the Blackberry and the file is nowhere to be found, I plug it back in and Ubuntu says the file isnt there....


Its weird because if I copy a picture or mp3 file it works just fine...

any ideas?

---

### Post by tcpankon on 2008-08-13
I was having the same issue until i verified that I was safely removing the blackberry.  right click on the device and go to safely remove...use eject followed by device name from cli. 

On a side note, for a cli method, I have come up with the following for batch processing a directory with .avi's and creating mp4s.  I still need to add some error checking and perhaps user input for sub-directory naming; but for now, copy this script to a directory containing .avi's you wish to convert and simply run it.  It will grab all avi's and convert to .mp4 files capable of being viewed on a blackberry (tested on 8130 pearl).  A pearl folder will be created and all the mp4 files will be in this directory. Seems to take about 10 minutes for a 170 Mbit avi.  Once done, the file size should be a little less than half of what it was.


```
#!/bin/bash
VAR="files.txt"
ls *.avi | sort > $VAR
mkdir pearl
cat $VAR | while read line; do
  INPUT=$(echo ${line})
  OUTPUT="pearl/"
  OUTPUT+=${INPUT%.avi}
  OUTPUT+=".mp4"
  mencoder "$INPUT" -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=240:180,harddup -ofps 30000/1001 -o "$OUTPUT"
done
rm $VAR
```

Let me know how it works or if there are any glaring ways to further decrease file size yet maintaining quality.

You will need to install mencoder 'apt-get install mencoder'.  There may be other dependencies, but they should be available in the repos...simply adding mencoder got this to work on my system

---

### Post by sourlime on 2008-08-26
tcpankon, that's great; thank you.

I'm using a Curve, so my screen resolution is 320x240.  I replaced "scale=240:180" with "scale=320:-10,crop=320:240,expand=320:240" which, if I understand correctly, scales to a 320 width based on the original file resolution and a multiple of 16, and then crops and expands it for good measure.  I'm not sure if the crop and expand bits are strictly necessary, I just saw them mentioned in other places and they seemed to work for me.

Your script also seems to be missing a space in "acodec=libfaac-af", where it should say "acodec=libfaac -af".

But overall, this is much appreciated and saved me a lot of leg-work.

---

