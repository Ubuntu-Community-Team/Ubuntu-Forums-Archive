---
title: "Lame question"
date: 2011-03-07
forum: Multimedia Software
---

### Post by Diametric on 2011-03-07
so, I'm learning to use lame and I'm trying to figure out how to get an entire directory converted from .wav to .mp3.  I've been successful in converting a single file using

```

```lame -V2 mymusic.wav mymusic.mp3```

```

But, let's say i want to operate a rip on a whole directory...how would I command that?  Would I need to cd to that directory, or could i do it from ~.  Also, I don't wish to change the song name, just the extension.

Also, I'm assuming that lame allows for .mp3 to .wav as well...correct?

thanks!

---

### Post by pastalavista on 2011-03-07
I don't know the commands to use lame but you can use the WinFF app in the software center to do the bulk conversion, both ways.

---

### Post by Diametric on 2011-03-07
> **pastalavista said:**
> I don't know the commands to use lame but you can use the WinFF app in the software center to do the bulk conversion, both ways.

Thanks for the reply, but I'm trying to do this from the command line...

---

### Post by gmargo on 2011-03-07
Here's the shell script that I use to convert all the *.wav files in the current directory.  Adapt as desired.  I call it "lame_all_192vbr".

```

#!/bin/bash
# Using bash to use arrays and arithmetic

# Uncomment to perform test
#TESTMODE=1

# Take the wav files from the current directory

# Choose first one for testing
if [ "$TESTMODE" == "1" ] ; then
    ECHO=/home/gmargo/bin/printargs
else
    ECHO=
fi

LAME=lame
LAMEARGS=""
LAMEARGS="$LAMEARGS -h"            # Use some quality improvements.
#LAMEARGS="$LAMEARGS --cbr -b 128"    # Constant bit rate, 128kbps
LAMEARGS="$LAMEARGS -v -b 192"        # Variable bit rate, 192kbps min
LAMEARGS="$LAMEARGS -V 0"        # Variable bit rate, highest quality


# Put basenames of files in $NAMES[] array
declare -a NAMES
declare -i indx=0

# Allows file/directory names to contain spaces:
OIFS=$IFS
IFS='\

'
# Take all available .wav files in alphabetical order
for FILE in `ls *.wav`
do
    BASE=`echo $FILE | sed 's/\\.wav$//'`
    #echo "indx=$indx BASE=$BASE"
    NAMES[indx++]=$BASE
done

#echo "length is ${#NAMES[@]}"
#exit 0

# Switch back to normal field separator
IFS=$OIFS

for (( indx=0 ; indx < ${#NAMES[@]} ; indx++ ))
do
    BASE=${NAMES[indx]}
   #echo       $LAME $LAMEARGS "$BASE.wav" "$BASE.mp3"
    $ECHO nice $LAME $LAMEARGS "$BASE.wav" "$BASE.mp3"
done

```

---

### Post by shantiq on 2011-03-08
ok Metric first of all "Lame question" has to be the best ever question asked on the forum :KS   most of my questions are lame.



if you want to do just one folder


cd to it then enter


```
for f in *.wav; do lame "$f" -b 320k  "${f%.wav}.mp3" ;done
```      that will do all the files

if you want to remove the originaL wav too add

```
for f in *.wav; do lame "$f" -b 320k  "${f%.wav}.mp3" **[COLOR="Red"]&& rm *.wav [/COLOR]**;done
```


**Now** and that was your question for a whole directory cd to where all your folders are then enter as is (or do as a .sh script) Personally i enter it as is


```
for i in */
do
  cd "$i"

for f in *.wav; do lame "$f" -b 320k  "${f%.wav}.mp3" ;done


  cd ..
done
```




again add the red bit above to remove all your wavs if you so wish


and **Change** 320k to whatever you want it to be

---

### Post by aeiah on 2011-03-08
> **Diametric said:**
> 
Also, I'm assuming that lame allows for .mp3 to .wav as well...correct?



probably not, no. lame is an mp3 encoder, not a general audio converter. there'd be little point in converting from mp3 to wav anyway, you'd just get an increase in file size. 

having said that, something more general such as ffmpeg or mencoder can convert from mp3 to wav (and convert to and from many other audio/video formats). things like mencoder and ffmpeg would probably call upon lame to convert to mp3 incidentally, since its the best tool for the job.

---

### Post by Diametric on 2011-03-08
Thanks for the replies.  I'll give it whirl this evening and see how it goes.  It's a shame lame doesn't convert back to .wav

My car has a cd player and only plays .wav or .cda files - so I find myself having to convert BACK to .wav just to listen to some tunes in my ride.  Oh well, I'll figure it out.

Cheers!

---

### Post by shantiq on 2011-03-08
diametric you can turn mp3 to wav very easily but it does not make any sense really since you are turning a lossy at best 320k file to a 1441k file with the same amount of data that you had in the 320, so you end up with a fat file with little info


**alternately**

maybe do a rip to wav for your car
then a rip to mp3 for your computer


but if you still want to turn mp3 to wav run this the way we did earlier


```
for f in *.mp3; do ffmpeg -i "$f" "${f%.mp3}.wav"; done

```

---

### Post by Diametric on 2011-03-08
> **shantiq said:**
> diametric you can turn mp3 to wav very easily but it does not make any sense really since you are turning a lossy at best 320k file to a 1441k file with the same amount of data that you had in the 320, so you end up with a fat file with little info


**alternately**

maybe do a rip to wav for your car
then a rip to mp3 for your computer


but if you still want to turn mp3 to wav run this the way we did earlier


```
for f in *.mp3; do ffmpeg -i "$f" "${f%.mp3}.wav"; done

```

Thanks for the info.  I get how a conversion from .mp3 back to .wav would be a "fat file with little info"...that makes sense.  But, how is a "rip to .wav" different?  I'd like to get the highest quality file when changed back to .wav for the car.  Any thoughts would be greatly appreciated.

Thanks again,
-Dylan

---

### Post by Yellow Pasque on 2011-03-08
> But, how is a "rip to .wav" different?
shantiq is suggesting that you rip your original CD to .wav (lossless) and use those files instead of converting to .mp3 (lossy) and back to .wav, so you don't lose audio quality. Of course, if you had a CD, you would probably just use that to begin with (assuming you had a lossless backup of some kind in case of damage to the original).

---

### Post by shantiq on 2011-03-09
ok well Diametric what Temujin says is that really


what i am really suggesting assuming you are starting with CDs is to rip **twice** once to mp3   for your computer and once to wav for your car  ([**rubyripper**]("http://ubuntuforums.org/showpost.php?p=4993055&postcount=1") does that at the same time)

click on codecs    and then   click wav and mp3
 (i suggest ```
-b 320k --id3v2-only
``` in the mp3 box )


================================================================


**But** there is really a much better way

again assuming you start from CD

**Rip** to flac  for your computer; then you have a lossless file; which contains **all** the data from the disc

**and then** when you want some of these files for your car return them to wav, which from flac or any other lossless format means you **really** have a wav at 1411k


So my suggestion is


CD to flac

then for car   decompress flac to wac    easiest trick in the world   ```
flac -d *
```



your call really but these are some of the options:KS

---

### Post by Diametric on 2011-03-09
Cool.  Thanks again for the info.  This gives me a lot to play with.
 
Cheers.

---

