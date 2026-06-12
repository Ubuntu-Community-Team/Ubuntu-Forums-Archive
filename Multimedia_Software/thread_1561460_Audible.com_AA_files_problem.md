---
title: "Audible.com AA files problem"
date: 2010-08-26
forum: Multimedia Software
---

### Post by keevill on 2010-08-26
I have downloaded some audiobooks from Audible.com
They are 'aa' files and I want to play them on my ipod.
How can I do this using Ubuntu 10.04?
Do I have to use Wine with some application or something like that ?

-keevill-

---

### Post by tommyscott45 on 2011-06-07
Wine with the Audible Manager software only works with a patching wine. 

The easiest solution is to use virtualbox with windows and run either itunes or audible manager in it. Then you will be able to play the files on your ipod. 

I am dying for a better solution as well. I now have audible on my android phone but would love to play the files from my Ubuntu box.

---

### Post by frytek on 2011-07-18
Can sox play these aa files? If so, you could use this script on them (after modifications because it is meant for mp3). ```
#!/bin/bash
# mp3tom4b.sh
# mp3 to m4b converter to generate bookmarkable aac files for ipod

mp3files="*.mp3"
aacend=m4b
GENRE=Audiobook
tmpdir=~/tmp/ #change this depending on what you want to do with the old files

for file in $mp3files
do

basenam=${file%.*3} # Get the first part of the filename, without the mp3 part
id3v2 -C $file
TITLE="`id3v2 -l $file | grep TIT2 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
ARTIST="`id3v2 -l $file | grep TPE1 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
ALBUM="`id3v2 -l $file | grep TALB | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
TRACK="`id3v2 -l $file | grep TRCK | awk '{ORS=" "} {for (i = 6; i <= NF; i++) print $i}'`"
YEAR="`id3v2 -l $file | grep TYER | awk '{ORS=" "} {for (i = 3; i <= NF; i++) print $i}'`"
sox $basenam.mp3 -t wav - | faac -b 96 -c 44100 --title "$TITLE" --artist "$ARTIST" --album "$ALBUM" --genre "$GENRE" -w -o $basenam.$aacend -
done
```

If sox can't do it try mplayer to produce wav ```
 mplayer file -ao pcm:file="dump.wav" 
``` and then run faac on it as above.

---

