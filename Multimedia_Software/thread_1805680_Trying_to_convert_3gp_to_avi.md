---
title: "Trying to convert 3gp to avi"
date: 2011-07-16
forum: Multimedia Software
---

### Post by ant2ne on 2011-07-16
I'm tyring to convert the 3gp format that my droid likes to avi format which is more recognizable (like on my xbmc black xbox) I'm doing this conversion using memcoder and this script I wrote.

```
#!/bin/bash
_Working()
{
 _INPUTFILE=$file
 _OUTPUTFILE=$(echo $file | sed 's/3gp/avi/')
 echo ____________________________________________________________________________
 echo ____________________________________________________________________________
 echo converting $_INPUTFILE to $_OUTPUTFILE
 echo ____________________________________________________________________________
 echo ____________________________________________________________________________
 
  #The following line didn't work. had lots of skipped frames
  #mencoder $_INPUTFILE -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o $_OUTPUTFILE  
  
  #tried this following line too and it doesn't work any better.
  mencoder -idx $_INPUTFILE -ovc lavc -oac mp3lame -o $_OUTPUTFILE

 cp $_INPUTFILE ./copyoforiginal3gp/$_INPUTFILE
 mv $_OUTPUTFILE ./convertedavi/$_OUTPUTFILE
}

mkdir ./copyoforiginal3gp 2> /dev/null
mkdir ./convertedavi 2> /dev/null

for file in ./*.3gp;do
  if [[ -f "$file" ]]; then
     #echo "Editing $file"
     _Working
  fi
 done
echo finished

```
I get a lot of duplicate frames like this
```
1 duplicate frame(s)!
Pos:  19.2s    876f (96%) 121.84fps Trem:   0min   3mb  A-V:-0.042 [1445:144]

1 duplicate frame(s)!
Pos:  19.4s    886f (97%) 121.79fps Trem:   0min   3mb  A-V:-0.042 [1445:144]

1 duplicate frame(s)!
Pos:  19.6s    896f (98%) 121.72fps Trem:   0min   3mb  A-V:-0.042 [1446:144]

1 duplicate frame(s)!
Pos:  19.8s    906f (99%) 121.55fps Trem:   0min   3mb  A-V:-0.042 [1448:144]
```And that makes for low quality and skipping up movies. basically I want to take the 3gp and convert to avi with leaving as much of the playback alone as possible. What is a better way to convert these files? How can I prevent these skipped frames? What would be the memcoder switches line to retain as much quality as possible while converting the files to avi?

---

### Post by andrew.46 on 2011-07-16
Have you thought of using FFmpeg instead of mencoder? Development of mencoder has essentially stopped quite some time ago while FFmpeg development is white hot :).

---

