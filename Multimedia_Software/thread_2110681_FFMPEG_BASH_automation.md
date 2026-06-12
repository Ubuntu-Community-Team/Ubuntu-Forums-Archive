---
title: "FFMPEG BASH automation"
date: 2013-01-30
forum: Multimedia Software
---

### Post by gachnar on 2013-01-30
I am trying to find a way to automate FFMPEG to extract the subtitles from some MKV's and transcode it to MP4. Pasted below is my script, but when it comes time to try and execute the script it errors out. Please help!!!

```

#!/bin/bash

IFS="|"

if test -z $1; then
WORKDIR="$PWD"
else
WORKDIR="$1"
fi

echo "Working from directory $WORKDIR"
echo $WORKDIR
pause

for MKVFILE in `find $WORKDIR -name '*.mkv' -printf "%p|"`; do
BASENAME=`basename $MKVFILE ".mkv"`
DIRNAME=`dirname $MKVFILE`
mkvextract tracks "$BASENAME.mkv" 3:"$BASENAME.***"
ffmpeg -i "$BASENAME.mkv" -c:v libx264 -c:a copy -vf "\"***=$BASENAME.***\"" "$BASENAME.mp4"
done


```I'm so definitely not a BASH coder, can anyone offer some ideas?

I cannibalized another script I found on the forums and tried to modify it... but yeah... didn't work.

*** = a-s-s (minus the -'s)

---

### Post by evilsoup on 2013-01-30
I had to solve this exact problem a while ago (well, I had srt subtitles, but close enough). I used ffmpeg both to extract the subtitles, and then to hardcode them using the subtitles filter.

```

#!/bin/bash

for f in *.mkv
do
    ffmpeg -i "$f" -map 0:s:0 "${f/%mkv/***}"
    ffmpeg -i "$f" -filter:v subtitles="${f/%mkv/***}" -c:v libx264 -crf 22 -preset veryfast -c:a copy "${f/%mkv/mp4}"
done

exit 0

```Make sure you put the script somewhere in your $PATH (~/bin is the customary directory to use, create it if you haven't already) and set it as executable. Then, just cd to the directory containing your MKVs and let her rip.

----

If you have a very beefy machine (4+ cores, loads of RAM), you may find that ffmpeg isn't utilising your system's full resources; if you would like it to do so, you can use the following script instead:

```

#!/bin/bash

for f in *.mkv
do
    ffmpeg -i "$f" -map 0:s:0 "${f/%mkv/***}"
done

parallel ffmpeg -i {} -filter:v subtitles={.}.*** -c:v libx264 -crf 22 -preset veryfast -c:a copy {.}.mp4 ::: *.mkv

exit 0

```Note that the above requires GNU parallel, NOT the parallel from moreutils in 12.04. I believe it has packages in 12.10+, but for 12.04 you'll have to [compile it yourself]("http://askubuntu.com/a/142757/112879") (not as hard as it sounds, just follow the instructions on that link).

---

### Post by gachnar on 2013-01-31
you'll have to forgive me if I can't quite make out the script... I did have a few quetions on how it worked and so forth.

1) what do both the sets of *** equal? I'm not quite sure what to place where.
2) I get an error that says "Encoder (codec none) not found for output stream #0:0 any ideas?

Hopefully you can help me get this working... If so it would be tremendous.

---

### Post by evilsoup on 2013-01-31
*** is this forum's swear filter being annoying; I means a-s-s, minus the '-'s.

See [here]("http://pastebin.com/H48Qpsi4") for an uncensored version of the script.

---

### Post by gachnar on 2013-01-31
I got it working, but for some strange reason it errored out on a few files, just completely skipped them and kept moving. got any ideas as to why? I mean it successfully got the subs file, but just didn't encode the media.

---

### Post by evilsoup on 2013-01-31
I also just noticed a serious error with my script as written - it would have created only a single output called 'output.mp4'... I have corrected it, including the version in that pastebin link.

> 
I got it working, but for some strange reason it errored out on a few  files, just completely skipped them and kept moving. got any ideas as to  why? I mean it successfully got the subs file, but just didn't encode  the media.


Ideally I'd need to see the ffmpeg output; without that, the only thing I can think of is that the audio is a codec that MP4 doesn't support (most likely ogg vorbis). If that is the problem, you can just replace "${f/%mkv/mp4}" with "${f/%.mkv/-out.mkv}", to make it output to mkv files.

---

### Post by gachnar on 2013-01-31
Yeah....  I had ran into an issue with the output.mp4 part as well... I made the following modification to get around that...

```

ffmpeg -i "$f" -filter:v subtitles="${f/%mkv/***}" -c:v libx264 -crf 22 -preset veryfast -c:a copy "`basename "$f" .mkv`.mp4"

```Below is the format of the MKV file that keeps giving me the error

```

File '07.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_AAC)
Track ID 3: subtitles (S_TEXT/***)

```It keeps giving me the following error

```

[AVFilterGraph @ 0x9e35300] Error initializing filter 'subtitles' with args '07.***'
Error opening filters!

```

It did work for all of my other files just fine, once I saw my error in the earlier converts.

The following command does work however to deal with this file

```
ffmpeg -i 07.mkv -c:v libx264 -crf 22 -preset veryfast -c:a copy -vf "***=07.***" 07.mp4
```

---

