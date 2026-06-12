---
title: "Burning subtitles to video with mencoder"
date: 2009-05-11
forum: Multimedia Software
---

### Post by uhappo on 2009-05-11
Just to remind myself, this was the first time I tried it

```

mencoder movie.avi -sub movie.srt -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1200

```

Mencoder is fast, took about 10 minutes to burn hardcode the subs to a 1:30 hour movie. Excellent!

---

### Post by mlahey on 2009-08-16
I think that the default font size (%5) is way too big, so I add this to the mencoder command to make it %3.3
```
-subfont-text-scale 3.3
```

I also like to move the subtitles up a smidgeon so that they don't get cut-off when I play on my TV.
```
-subpos 96
```


-mlahey

---

### Post by mlahey on 2009-08-16
If you want to burn a subtitle track that is part of a matroska file (i.e .mkv file)

replace
```
-sub subfile.srt
```
with
```
-slang eng
```

of course replace "eng" with the language of your choice.  inspect the output of mencoder to find out what subtitle languages are available.

If you want to adjust the size or other properties of the subtitles it becomes complicated.  Matroska files can include at least three different kinds of subtitle tracks: SSA/*** , SRT or Vobsub. each uses a different set of mencoder commands. get the "mkvtoolnix" package to figure out which type of subs you have. also read the mencoder man page

if you have vobsubs that are printed too high, you can try this to move the subtitles to the bottom of the screen
```
-spualign 2 -subpos 96
```

-mlahey

ha - the forums won't let me put in the file format for Advanced Sub Station files.  apparently it thinks subtitles are obscene.  it replaces the A S S with ***

---

### Post by mlahey on 2009-08-16
Also keep if you are encoding to DivX (which we are) you really should do two-pass encoding to get the best quality video.

see any mencoder gude or check out the mencoder docs [here]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-mpeg4.html")

for example

pass 1
```
mencoder movie.avi -sub movie.srt -subfont-text-scale 3.3 -subpos 96 -o /dev/null -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1
```
pass 2
```
mencoder movie.avi -sub movie.srt -subfont-text-scale 3.3 -subpos 96 -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2
```

sorry about the serial posts

-mlahey

---

### Post by joshkhanii on 2009-08-17
Thanks a bunch guys, I'm really new to Ubuntu and was having trouble figuring out what to do with an avi/srt combo that I had downloaded. This worked like a charm

---

### Post by mlahey on 2009-08-18
Here is a sample script to hardsub your avi or matroska files.  should work with mpegs too


it takes a single movie file as the argument. if you add "fast" after the movie file it will do a one-pass encode instead of a two-pass

for example
```
sh ./hardsub.sh movie.avi
sh ./hardsub.sh movie.avi fast
```

it assumes that your .srt has the same name as the avi
if you are hardsubbing a matroska file and don't have an .srt it tries to use an english subtitle track embedded in the matroska

here's the script


hardsub.sh:
```

#!/bin/bash

# hardsub.sh
# a basic script to hardcode subtitles into movie files using mencoder
#
# uses a two pass - high quality encode by default
# fast option invokes a quick one pass encode 
#
# it assumes that you are using an .srt subtitle file with the same
#+ name as the movie file
#
# if you are using a matroska movie (.mkv) and it can't find the .srt
#+ file it uses the embedded english subtitle track
#
#
# NB: this is a preliminary script and doesn't do much error checking
#
# Version 0.11
#
# Mike Lahey 2009
#####################

# language used for subtitle track embedded in a matroska file
# for alternative subtitle (& audio) tracks try "mplayer -v movie.mkv"
LANG=eng

# these mencoder options scale down the subtitles and move them 
#+ up just a bit 
SUBOPTS="-subfont-text-scale 3.3 -subpos 96"

if [ -z "$1" ]; then
	echo usage: $0 movie.avi [fast]
	echo 
	echo fast -  do a fast one pass encode
	exit 1
fi
MOVIE=$1
EXT=${MOVIE##*.}
OUTPUT=${MOVIE/%.$EXT/.hardsub.avi}

# first make sure that our movie file is there
if [ ! -f "$MOVIE" ]; then
	echo input file \"$MOVIE\" does not exit
	exit 1
fi

# next check if we have the SRT file and create subtitle command for 
# mencoder 
SRT=${MOVIE/%$EXT/srt}

if [ -f "$SRT" ]; then
	
	# good we have an SRT file, so create our subtitle command
	SUBCMD="-sub \"$SRT\""
else	
	#no SRT file? well check if we are dealing with a matroska file
	if [ "$EXT" == "mkv" ]; then
		echo "################################################"
		echo couldnt find \"$SRT\" 
		echo so trying embedded subtitle track \"$LANG\"
		echo "################################################"
		SUBCMD="-slang $LANG -spualign 2"
                # "-spualign 2" ensures proper placement of vobsub tracks
	else
		echo could not find subtitle file \"$SRT\"
		echo
		echo maybe its called something else? try renameing it.
		exit 1
	fi
fi

# if the input movie is not an avi then transcode the audio to mp3 
# this may result in an unnecessary transcode but it will make 
#+ incompatable audio streams (such as ogg/vorbis) work with an avi

if [ "$EXT" == "avi" ]; then
	ACODEC=copy
else
	ACODEC=mp3lame
fi

# most formats other than avi allow non-square pixels.  
# by invoking the scale filter we ensure that the video is 
# displayed with the proper aspect ratio in our avi
# since were scaling anyway - scale to a multiple of 16 to make the encoding more effiecient
if [ "$EXT" != "avi" ]; then
	SUBOPTS="$SUBOPTS -vf-pre scale=-8:-8"
fi

#### if fast option was invoked, do a fast one pass encode
if [ "$2" == "fast" ]; then

	CMD="mencoder \"$MOVIE\" $SUBCMD $SUBOPTS -o \"$OUTPUT\" \
	-oac $ACODEC -ovc lavc"
	echo $CMD
	eval $CMD

	if [ $? != 0 ]; then
	   echo "################# mencoder failed ################"
	   exit 1
	fi
	exit
fi




#### normal two pass encode

CMD="mencoder \"$MOVIE\" $SUBCMD $SUBOPTS -o /dev/null -oac $ACODEC \
-ovc lavc -lavcopts vcodec=mpeg4:vhq:turbo:vpass=1"
echo $CMD
eval $CMD

if [ $? != 0 ]; then
	echo "################# mencoder failed ################"
	rm divx2pass.log
	exit 1
fi

CMD="mencoder \"$MOVIE\" $SUBCMD $SUBOPTS -o \"$OUTPUT\" -oac $ACODEC \
-ovc lavc -lavcopts vcodec=mpeg4:vhq:vpass=2"
echo $CMD
eval $CMD

if [ $? != 0 ]; then
	echo "################# mencoder failed ################"
	rm divx2pass.log
	exit 1
fi

rm divx2pass.log

```

remember to set the executable bit of the script
```
chmod +x hardsub.sh
```


-mlahey

---

### Post by GuiGuy on 2009-08-28
Thanks for that, but I get "./hardsub.sh: 17: Bad substitution" when I run the script. 

Any ideas?

Thanks

---

### Post by asphixmx on 2009-09-18
I made a very simple script (subtitles.sh) for making an .avi file with the .srt subtitles already embedded. Save my script to your scripts folder in Nautilus: 
~/.gnome2/nautilus-scripts/
Make it executable:
sudo chown +x subtitles.sh
To use it:
You should have 2 files, same name, different extension. For example:
MyMovie.avi  (The video without subtitles)
MyMovie.srt  (The subtitles file)
Then, using Nautilus, point to the MyMovie.avi file, right click, Scripts, subtitles.sh. A message "working..." appears. When it finishes, it says "Finished". Now you will have a third file, MyMovie_subt.avi with the subtitles embedded.
Hope you find my script useful.
Here is the script subtitles.sh:

#!/bin/bash
for file
do
base=${file%.*}
ext=${file##*.}
newname=${base}"_subt".${ext}
mencoder "$file" -sub ${base}.srt -oac copy -ovc lavc -o "$newname" -subcp latin1 -font /usr/share/fonts/msttcorefonts/arial.ttf -subfont-text-scale 3.8 | zenity --progress --text="Working: $file" --pulsate --auto-close
done
zenity --info \
          --text="Finished"

---

### Post by srix on 2009-10-11
Using mencoder 2:1.0~rc2-0ubuntu19+medibuntu1, there seems to be a problem when applying a filter and embedding subtitles into the video. I use a command like (removed all unnecessary options in this example):

```
mencoder -sub test.srt  -vf pp=lb -ovc lavc -oac lavc INPUT.MPG -o out.avi
```

The de-interlace filter is applied, but the subtitles don't show up. If I remove the "-vf pp=lb", the subtitles show up fine. Is this combination of options not allowed, or is my usage incorrect?

Thanks...

---

### Post by m_rahman on 2010-02-07
hi
does anybody know how to    	 	 	 	 	 	     	 	 	 	 	add visual effects to the subtitle text being played, such as text flys in from the left or right, comes in sideways or becomes 3d ect.. any effect of these does the job for me.

---

### Post by asphixmx on 2010-02-08
Subtitle animation with mencoder? I doubt it. But you can do what you want, with kdenlive

---

### Post by Ian Clark on 2010-02-27
I'd love to find a way to burn subs through mencoder to an .ogv file.

---

### Post by Ian Clark on 2010-02-27
```
mencoder movie.ogv -sub movie.srt -o movie.hardsubs.avi -oac pcm -ovc lavc -lavcopts vbitrate=1200
```

This added the subs, but changed the .ogv file into an .avi, messed up the sub timing, the audio sync, and the aspect ratio. The subs looked pretty though!

---

### Post by linuxguru1 on 2010-08-18
> **asphixmx said:**
> I made a very simple script (subtitles.sh) for making an .avi file with the .srt subtitles already embedded. Save my script to your scripts folder in Nautilus: 
~/.gnome2/nautilus-scripts/
Make it executable:
sudo chown +x subtitles.sh
To use it:
You should have 2 files, same name, different extension. For example:
MyMovie.avi  (The video without subtitles)
MyMovie.srt  (The subtitles file)
Then, using Nautilus, point to the MyMovie.avi file, right click, Scripts, subtitles.sh. A message "working..." appears. When it finishes, it says "Finished". Now you will have a third file, MyMovie_subt.avi with the subtitles embedded.
Hope you find my script useful.
Here is the script subtitles.sh:

#!/bin/bash
for file
do
base=${file%.*}
ext=${file##*.}
newname=${base}"_subt".${ext}
mencoder "$file" -sub ${base}.srt -oac copy -ovc lavc -o "$newname" -subcp latin1 -font /usr/share/fonts/msttcorefonts/arial.ttf -subfont-text-scale 3.8 | zenity --progress --text="Working: $file" --pulsate --auto-close
done
zenity --info \
          --text="Finished"


Thanks man! That script works like a charm!

---

### Post by HangukMiguk on 2010-10-24
Sorry to necromance, but does anyone know what I'm doing wrong in trying to hardcode subs with mencoder in Korean?

Here is the options I'm passing currently:

```
mencoder &#49464;&#47116;&#46356;&#54588;&#54000;.Serendipity.2001.XviD.AC3-WAF.avi -oac copy -ovc xvid -xvidencopts bitrate=800 -sub &#49464;&#47116;&#46356;&#54588;&#54000;.Serendipity.2001.XviD.AC3-WAF.smi -slang kor -subfont ~/.fonts/&#44396;&#47492;&#52404;-dru50sawayolshk955.ttf -o Serendipity.avi
```

However, any time I try to hardcode, everything is gibberish.

Really needing to get this working, and know what options to pass this week.  Have about 5 movies to encode so I can get these working on my Xbox 360 for a visitor from Korea.

fixed my own problem, for anyone having similar issues:

use the following command for mencoder

```
mencoder filename.avi -ovc xvid -oac copy -xvidencopts bitrate=800 -sub filename.smi -subcp cp949 -font UnJamoBatang -subfont-text-scale 3.3 -o filename.avi
```

You can change the bitrate to whatever size you want.  You may also have to change the font to a different one depending on what you have on your system, you can check OpenOffice like I did to see the listing.  I also use 3.3% as the font size as 5% tends to cut off on several movies.

---

### Post by thanasis57 on 2010-10-28
> **mlahey said:**
> Here is a sample script to hardsub your avi or matroska files.  should work with mpegs too
...
remember to set the executable bit of the script

Mike's script worked just fine for me.

To correctly burn greek subtitles (a utf-8 encoded srt file) I needed to add a
```
-subcp utf-8
```argument in the first SUBOPTS line, i.e.
```
SUBOPTS="-subfont-text-scale 3.3 -subpos 96 -subcp utf-8"
```Otherwise, it worked painlessly, without however, retaining the special formatting (e.g. the <i> italics tags didn't work).

---

### Post by adremasu on 2010-11-01
i have some problem encoding charcters like "È". I'm Italian...

---

### Post by ricky15100 on 2011-12-03
> **asphixmx said:**
> I made a very simple script (subtitles.sh) for making an .avi file with the .srt subtitles already embedded. Save my script to your scripts folder in Nautilus: 
~/.gnome2/nautilus-scripts/
Make it executable:
sudo chown +x subtitles.sh
To use it:
You should have 2 files, same name, different extension. For example:
MyMovie.avi  (The video without subtitles)
MyMovie.srt  (The subtitles file)
Then, using Nautilus, point to the MyMovie.avi file, right click, Scripts, subtitles.sh. A message "working..." appears. When it finishes, it says "Finished". Now you will have a third file, MyMovie_subt.avi with the subtitles embedded.
Hope you find my script useful.
Here is the script subtitles.sh:

#!/bin/bash
for file
do
base=${file%.*}
ext=${file##*.}
newname=${base}"_subt".${ext}
mencoder "$file" -sub ${base}.srt -oac copy -ovc lavc -o "$newname" -subcp latin1 -font /usr/share/fonts/msttcorefonts/arial.ttf -subfont-text-scale 3.8 | zenity --progress --text="Working: $file" --pulsate --auto-close
done
zenity --info \
          --text="Finished"

Starman thankyou works brilliantly

---

### Post by josvanr on 2012-03-20
dont know if anyone is still reading this...but if I try that thing with the scaling of the font, two subtitles are encoded superimposed on one another: One large font and one small font...?


josvanr


> **uhappo said:**
> Just to remind myself, this was the first time I tried it

```

mencoder movie.avi -sub movie.srt -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1200

```

Mencoder is fast, took about 10 minutes to burn hardcode the subs to a 1:30 hour movie. Excellent!

---

### Post by Exeleration-G on 2012-04-22
Mlahey's script in post #6 worked great for me. However, it only works with one .AVI and .SRT file at a time, while I often want to encode whole directories at a time. So, imagine you've got this:

```
$ ls moviedirectory

Movie1.avi
Movie1.srt
Movie2.avi
Movie2.srt

```etcetera etcetera,

you probably want to convert them all at once. I've made a script for this. It works along with Mlahey's script, so be sure to have that script, as posted in post #6, saved in your ~ directory, as hardsub.sh.

Run the script (that you can find as an attachment on this post) from a terminal: ```
bash dirsrt.bash
```Unpack dirsrt.bash.gz to get the dirsrt.bash file.

---

### Post by r3bol on 2012-10-26
(I am the thread resurrecter and the life). 
Hi, I wanted to add some subs to a language podcast. Does anyone know how to do this without a video file, ie, create a video file on the fly maybe using a image file for the background while burning the subs onto it?

Thanks

---

### Post by oldos2er on 2012-10-26
Please start a new thread.

---

