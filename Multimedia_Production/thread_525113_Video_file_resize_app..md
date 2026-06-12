---
title: "Video file resize app."
date: 2007-08-13
forum: Multimedia Production
---

### Post by Netik09 on 2007-08-13
Common question I'm sure, but does anyone know what
program I can use to resize a video? I have a huge 2 gig
file that needs to be smaller. Would Mplayer do it?

---

### Post by Netik09 on 2007-08-14
Nothing?:confused:

---

### Post by aussiedini on 2007-08-14
Avidemux will do it for you

---

### Post by jacob01 on 2007-08-14
if it is video
try ffmpeg and change around with the video bit rate  and frame rate to make it smaller
try to chang the -b which is the bit rate the 768 is pretty low so try that and if the quality isnt what you want make the -f which is the frames per second higher

making a file smaller usually means you are loosing something which is usually the video quality

try 

ffmpeg -i filename with file extension -f avi -r 25 -b 768 filename.avi

and to convert videos for my psp i use this

ffmpeg -i file name -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

the -r and -b are so low because you are viewing the vid on a small screen so you don't need as good of quality

to use this cd to the video directory

to get it the quality and the size right you might have to play around with the -r and the -b settings

---

