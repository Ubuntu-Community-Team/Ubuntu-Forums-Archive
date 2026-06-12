---
title: "ffmpeg library problem"
date: 2011-04-17
forum: Multimedia Software
---

### Post by hufemj on 2011-04-17
It looks like the most recent (April 17th) update to 10.10 might have broken the libraries used by ffmpeg. I only suggest this because I had a script for creating desktop videos that was working just fine until this morning. Then all of a sudden (after an update) it couldn't find libfaac. I found posts on how to include libfaac, tried the various suggestions, but none of them worked. Given that I had been using this script for some time with no problems, it obviously was able to find the libraries before. In any case, The script is below. Note that the problem revolves around the '-acodec libfaac' parameter to the second ffmpeg call. If I remove it, the script completes and I get an mp4 file, but with really ugly audio.

#!/bin/bash
#
# The first line creates an ogv video. Make shure that the output file defaults to screencast.ogv. Delete older versions
#
# The second line does a first pass on screencast.ogv creating statistics and saving them in a log file. The input file is not modified and
# no output file is created.
#
# The third line uses the stats from the log file in a second pass on screencast.ogv and creates output.mp4. Remember to rename output.mp4 so that
# it doesn't get stepped on in subsequent renderings.
# 
echo $#
if [ $# -lt 1 ]; then
	echo no parameters
	read CONFIRM
else
	echo parameters
	CONFIRM=$1
fi
echo CONFIRM: $CONFIRM
filename=$(basename $CONFIRM)
fileroot=${filename%.*}
fileext=${filename##*.}
ogvfile=$fileroot.ogv
mp4file=$fileroot.mp4
if [ -f $ogvfile ]; then
	echo $ogvfile moved to ${ogvfile}.sav
	mv $ogvfile ${ogvfile}.sav
fi
if [ -f $mp4file ]; then
	echo $mp4file moved to ${mp4file}.sav
	mv $mp4file ${mp4file}.sav
fi

echo input file $ogvfile
echo Output file $mp4file

recordmydesktop -x 2000 -y 200 --width 800 --height 600 --freq 48000 --device hw:1,0 --v_bitrate 2000000 --s_quality 10  --buffer-size 65538 --fps 15 -o $ogvfile
ffmpeg -y -i $ogvfile -sameq -s 800x600 -aspect 16:9 -r 30000/1001 -b 2M -bt 4M -pass 1 -vcodec libx264 -vpre fastfirstpass -threads 0 -an -f mp4 -loglevel quiet /dev/null
ffmpeg -y -i $ogvfile -sameq -s 800x600 -aspect 16:9 -r 30000/1001 -b 2M -bt 4M -pass 2 -vcodec libx264 -vpre hq -threads 0 -async 1 -acodec libfaac  -ac 2 -ab 160k -ar 48000 -f mp4 -loglevel quiet $mp4file

echo Done
echo Press enter to exit
read PLEASE_WAIT

---

### Post by ron999 on 2011-04-17
Hi
There is a problem with some of the libraries.
Look at this thread :- [http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")
(Post #141 -> )

---

### Post by fixitdude on 2011-04-17
I compiled it with the static libraries and it works great!

I went and got a updated version rather than the ubuntu supplied one because it wasn't converting some .flv files.

See this thread:
[http://ubuntuforums.org/showthread.php?t=1727252](http://ubuntuforums.org/showthread.php?t=1727252)

It's pretty simple to do.

---

