---
title: "Simple Userjob"
date: 2008-05-03
forum: Mythbuntu
---

### Post by SniperKIng on 2008-05-03
Right i have been searching for hours now for a way to transcode myth recordings into a .3pg files using the userjob function.


using this wiki... 

[http://www.mythtv.org/wiki/index.php/Transcoding_into_a_3gp_Video](http://www.mythtv.org/wiki/index.php/Transcoding_into_a_3gp_Video)

I made this script and placed it in the correct location

#!/bin/sh
# MythTV user job to transcode a video to 3gp suitable for a phone
FILE=$1
TITLE=$2
OUTDIR="/tmp/"
/usr/bin/ffmpeg -i $FILE -ar 16000 -ac 1 -acodec libamr_wb -ab 23.85k -b 240 -s qcif -f 3gp "$OUTDIR$TITLE.3gp"


at the bottom of the wiki it mentions that the user, uses 

/home/mythtv/3gp.sh "%DIR%/%FILE%" "%TITLE% - %SUBTITLE%"

as his userjob. i have replicated this in my userjob setup and i just cant get it working.

Can anyone maybe correct the code or just do anything to help me out im guessing it shouldnt be too difficult . im a noob lol.

Thanks

---

### Post by SniperKIng on 2008-05-04
Well i managed to fix it on my own. 

Help would have been nice though

---

### Post by baudot on 2008-05-06
can you share the solution with us?

---

### Post by tgm4883 on 2008-05-06
> **SniperKIng said:**
> Well i managed to fix it on my own. 

Help would have been nice though

Help can only be provided by someone who knows the answer.

If you did fix the problem, in the future, people who have the same problem would greatly appreciate it if you posted what you did to fix it.

---

