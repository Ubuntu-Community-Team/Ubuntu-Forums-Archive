---
title: "Mplayer only dumping one chapter when ripping DVD"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by Azakus on 2007-04-08
I'm trying to write a batch script to create personal backups of DVD's, and when I use it, only the first chapter of the DVD is copied.
Has anyone had this happen before?
I'm using mplayer and mencoder.
Here's my full script.
```

#!/bin/bash
#Usage dvdrip <MoveName>.mkv <CROP>
CROP=$2
NAME=$1
mkdir ~/$NAME
cd ~/$NAME
dvdxchap -t 1 /media/cdrom0 >> $NAME.chaps.txt
CHAPNUM=$((`cat $NAME.chaps.txt | grep -c "CHAPTER"` / 2 ))
mplayer dvd://1 -chapter 1-$CHAPNUM -dumpstream -dumpfile $NAME.vob
mplayer $NAME.vob -ao pcm:file=$NAME.wav -vc dummy -aid 128 -vo null
oggenc -q5 $NAME.wav
mencoder $NAME.vob -vf crop=$CROP,scale=720:480,harddup -ovc xvid -nosound -xvidencopts pass=1:threads=2 -o /dev/null
mencoder $NAME.vob -vf crop=$CROP,scale=720:480,harddup -ovc xvid -nosound -xvidencopts pass=2:bitrate=800:threads=2 -o $NAME.avi
mkvmerge $NAME.avi $NAME.ogg --chapters $NAME.chaps.txt -o $NAME.mkv --title $NAME

```

---

### Post by crispy_420 on 2007-04-08
Looks like you want an avi file, right?

I've used acid rip in the past just fine, also thoggen should work too.

As far as your issue, a dvd is not just one file. A dvd is maybe up of a bunch of little files like bup, ifo, vob, etc. You script would need to read the ifo (like a table of contents for the dvd) to get all the chapters in order. Either that or read each vob, line up the chapters in order and encode as one.

---

### Post by Azakus on 2007-04-09
NVM. ivman was screwing up my dvd playback.

---

