---
title: "Batch extraction of subtitles from mkv files"
date: 2011-07-16
forum: Multimedia Software
---

### Post by ukyo_rulz on 2011-07-16
Hello there. I have recently been tasked to extract the subtitles from a lot of mkv files. Hundreds of them, maybe even more than a thousand. To do this, I modified a script I found online:

------------------------------------------------
#!/bin/bash

IFS="|"

if test -z $1; then
     WORKDIR="$PWD"
else
     WORKDIR="$1"
fi

echo "Working from directory $WORKDIR"

for MKVFILE in `find $WORKDIR -name '*.mkv' -printf "%p|"`; do
     BASENAME=`basename $MKVFILE ".mkv"`
     DIRNAME=`dirname $MKVFILE`
     NEWBASEFILE=`echo "$BASENAME" | sed "s/ /_/g"`
     NEWNAME="$NEWBASEFILE.***"
     mkvextract tracks "$BASENAME.mkv" 3:"$NEWNAME"
done
------------------------------------------------

The script above works... as long as the subtitle is in track number 3. Not all the files follow that convention. If I was doing this manually I need to run mkvinfo to get the information and be sure. Something like this:

|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 650449040
|  + Track type: subtitles
|  + Lacing flag: 0
|  + Codec ID: S_TEXT/***
|  + CodecPrivate, length 4605
|  + Name: ***

So in the above example the subtitle is actually in track number one and my script would be borked for that particular file. Is there a way to integrate mkvinfo into the script and parse it to see what track should be extracted? Like, read it line-by-line and change the value of some #TRACKNO variable everytime a string like "|  + Track number:" appears, and stop when a string like "|  + Track type: subtitles" appears? Maybe even skip doing anything if there aren't any subtitles.

PS: I actually prefer SRT subtitles to ***. If there was some command line tool I could use to convert the resulting *** file to SRT I would be much obliged.

---

### Post by SeijiSensei on 2011-07-16
How about this alternative using mplayer?

```
mplayer -vo null -ao null -frames 0 /path/to/file.mkv 2>&1 | grep mkv.*subtitles
```

That produces the following output from a sample file I have:
```
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
```

If you want just the track number you can run:

```
TRACKNO=$(mplayer -vo null -ao null -frames 0 /path/to/file.mkv 2>&1 | grep mkv.*subtitles | awk '{print $4}' | sed 's/://g')
```

That would store "3" in environment variable $TRACKNO using the example above.  Then you could use

```
mkvextract tracks "$BASENAME.mkv" "$TRACKNO:$NEWNAME"
```

in your script above.

---

### Post by ukyo_rulz on 2011-07-17
Thanks for the reply, SeijiSensei. I'll be sure to try that example later, just to learn it. In the meantime I've finally gotten my script to work using this horrible, hacked up code to find the track number:

```
     # Use mkvinfo to get information on which track the subtitles reside
     MKVINFO=`mkvinfo "$MKVFILE"`
     NOTFOUND=true
     while read -r line
     do
          if $NOTFOUND ; then
               if echo "$line" | grep -q "Track type: subtitles" ; then
                    NOTFOUND=false
               fi

               if echo "$line" | grep -q "Track number:" ; then
                    IFS=":"
                    for x in $line
                    do
                         TRACKNO=`echo $x`
                    done
               fi
          fi
     done <<< $MKVINFO
```

---

