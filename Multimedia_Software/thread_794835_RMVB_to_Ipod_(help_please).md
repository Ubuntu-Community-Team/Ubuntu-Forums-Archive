---
title: "RMVB to Ipod (help please)"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Sephyryx on 2008-05-15
I can't seem to convert RMVB to Ipod
FFMPEG won't take RM files

Does anyone know of a good linux rmvb to ipod converter?

---

### Post by Creative2 on 2008-05-15
on fuoco tools i have writtten a commad line but there is a problem with it you could try with this for now : 

mencoder INPUT -ofps 25 -oac mp3lame -lameopts preset=64 -ovc xvid -xvidencopts bitrate=600 -o OUTPUT.avi

then with this 

ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 600k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 64k -s 320x240 -aspect 4:3 OUTPUT

i am sure you could do with mencoder with one single command line but unluckly i have not time , and above all , i have not ipod

---

### Post by Sephyryx on 2008-05-15
Thanks for the command line, unfortunately, converting twice is even less desirable than using windows.  Please PM me or post here once the Fuoco tools is working, Thanks   : )

---

### Post by Creative2 on 2008-05-19
well i will but unluckly i have nto rmvb so i can't test...

try this 

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=750:acodec=libfaac:abitrate=128  -af lavcresample=44100 -vf scale=320:240  -ofps 30 -o OUTPUT

---

### Post by jaxomnia on 2010-11-29
A faster method is convert RMVB straight into MP4:

ffmpeg -i [input_filename (.rmvb)] -acodec aac -strict experimental [input_filename (.mp4)]

---

