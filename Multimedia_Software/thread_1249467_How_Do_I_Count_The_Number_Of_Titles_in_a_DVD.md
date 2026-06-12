---
title: "How Do I Count The Number Of Titles in a DVD?"
date: 2009-08-25
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2009-08-25
For current and future ripping of DVDs to HDD, I am writing a bash script using mencoder. Have several DVDs that have many titles, up to 25 on one of them, so am looking for a way to "count" the number of titles on a DVD and to then run mencoder to rip each title separately to an avi.

I can see that **lsdvd** will list the titles, and that **ffmpeg** and **mplayer** list the number of titles in their "preliminaries".

How can I "grab" the number to put into a variable for my script?

Thanks

---

### Post by andrew.46 on 2009-08-25
Hi Jose,

> **Jose Catre-Vandis said:**
> I can see that **lsdvd** will list the titles, and that **ffmpeg** and **mplayer** list the number of titles in their "preliminaries".

How can I "grab" the number to put into a variable for my script?

I am sure this is not the complete answer but something like:

```

TITLE_NUMBER=$(lsdvd | grep ^'Title: ' | wc -l)

```

might do what you are after, although the syntax is a little clumsy :-).

Andrew

---

### Post by Jose Catre-Vandis on 2009-08-26
Hi Andrew

Brilliant. This is just what I needed. Looks like I will need to read up on all the various options available from **grep** for the future!

FWIW, here is the code in place and the for sequence used:
```
#!/bin/bash

#convert all titles in dvd to avi
#requires lsdvd installed


#path to dvd or dvdiso e.g. /media/dvd.iso or /media/cdrom0
#NOT required if always ripping from CD/DVD Drive
DVDPATH=

#output name
AVINAME=

#counts number of titles in dvd
#again remove $DVDPATH if only ever ripping from CD/DVD Drive
TITLES=$(lsdvd $DVDPATH | grep ^'Title: ' | wc -l)

for T in `seq $TITLES`

do
echo "Encoding Title Number $T"
#you can chose your own encoding options :)
mencoder dvd://"$T" -dvd-device $DVDPATH -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate="1200" -vf scale -zoom -xy 640 -oac mp3lame -lameopts br=128 -o "$AVINAME""$T".avi

done
```

---

### Post by lucio_araujo on 2010-03-25
Other similar script, just to copy all the titles to computer

```
#!/bin/bash
#copy all dvd titles to computer 
#requires lsdvd and transcode installed

#path to dvd or dvdiso e.g. /media/dvd.iso or /media/cdrom0
#NOT required if always ripping from CD/DVD Drive
DVDPATH=/dev/dvd

#output name
echo "video name: " ; read VIDEONAME

#counts number of titles in dvd
#again remove $DVDPATH if only ever ripping from CD/DVD Drive
TITLES=$(lsdvd $DVDPATH | grep ^'Title: ' | wc -l)

for i in `seq $TITLES`

do 
tccat -i $DVDPATH -T $i,-1 -P > "$VIDEONAME"_$i.mpg
done

```

---

