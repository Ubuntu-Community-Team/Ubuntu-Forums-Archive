---
title: "Importing AVCHD files"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Telos3K on 2010-11-25
When importing files from my digital camera, I find it less confusing to open a folder and then drag the files to where I want them on my hard drive rather than to have Shotwell do it automatically (as described by jennacav in this [post]("http://ubuntuforums.org/showthread.php?t=1596707&highlight=shotwell")).  That's straightforward for photo files, but what about for video files?  On my camera, they are stored in an AVCHD folder, which itself has several folders and subfolders.  Does this mean that I have to drag the files over as a group, or is there some way they can be handled individually as photos can be? (I'm new to both Ubuntu and digital photography.....)

Thanks!

---

### Post by ajgreeny on 2010-11-25
I don't think it matters what file type they are, but once you have found them on the camera memory card you can drag and drop just like any other file.  I do all this myself using a card reader and not the camera, as I find it easier and don't have to find the camera USB cable etc etc.

The video files on my camera are also in an AVCHD folder, but are separate MTS files in the folder /media/memcard/PRIVATE/AVCHD/BDMV/STREAM, and it took me a short search to find them as they are buried so deep in the card's folder hierarchy.  However once I had found them they could be handled like any other file without a problem.

Have a look yourself using a card reader if needed, though I assume connecting the camera will act just the same.

PS: My camera is a Panasonic DMC-FZ38, just for you to compare likely file positions on yours.

---

### Post by VideoRoy on 2010-11-25
I just picked up a Canon HD camcorder as well was playing around with the best way to get my .MTS files over and usable.  At least on my camera they are in the Stream folder under BDMV just like a Blu-Ray disc.  I just drag those .MTS files to the computer using a card reader picked up at Fry's for $9 USD (iogear)

Every time I hit pause on the camera it creates another .MTS file but at least they are sequentially numbered, perhaps yours are as well.

Here is another tip I picked up at this website for combining the .MTS files for use in Openshot or DeVeDe
[http://exposureroom.com/members/Georg/tutorials/post/77/](http://exposureroom.com/members/Georg/tutorials/post/77/)

Very nice script he wrote but I tweaked it a bit for my own use and maybe this will help you as well:
> 
#!/bin/bash
#allmts2avi.sh
# Create combine script for sorted .MTS files in current directory
# Assumes FFMPEG is installed and .MTS files are sequential
# Tested on Ubuntu 10.10 and FFmpeq version 0.6-4:0.6-2ubuntu6 
if [ $# -lt 1 ] ; then
  echo "Missing Output File Name"
  exit 1
fi

FILENAME="$1"

if [ -f $FILENAME ];
then
   echo "File $FILENAME already exists!"
   echo "You Must Rename, Move or Delete $FILENAME first!"
   exit 1
fi

# Create FIFO to allow input from multiple MTS files at once
TMPFILE=`mktemp /tmp/mts.XXXXXX` || exit 1
rm $TMPFILE
mkfifo $TMPFILE

# Create tmp file for cat command
CATTMP=`mktemp /tmp/cat.XXXXXX` || exit 1

# MTS files will be sorted in alpha order
# Note: This only works because Canon outputs numeric sequential files
ls *.MTS > sortedMTS.txt

# Build cat script as input to fifo
echo -n "cat " > $CATTMP
while read f; do echo "\"$f\" \\" >> $CATTMP; done < sortedMTS.txt
echo "> $TMPFILE &" >> $CATTMP
chmod +x $CATTMP
$CATTMP

nice -n 19 ffmpeg \
-i "$TMPFILE" \
-acodec copy \
-vcodec libx264 \
-crf 21 \
-r 30000/1001 \
-deinterlace \
-vpre lossless_medium \
-y \
-threads 0 \
"$FILENAME"

# delete temporary files/fifos
rm $TMPFILE
rm $CATTMP
My version takes just an ouput file as a parameter like this:

> ~/bin/allmts2avi.sh myvideo.aviThis script sorts all the *.MTS files alphabetically which for me at least is 0000.MTS, 0001.MTS and so on.  From there is does a quick pass combine in FFmpeg, you can play with those settings but the one that George put in is working for me.

You will be left with your original files, your .AVI and a sortedMTS.txt that contains a sorted list.

Any way this made working with OpenShot and DeVeDe directly much easier and I do not notice any loss for my output.

You can probably tweak the script to suit your needs or George's works good too.

Good Luck.

---

### Post by Telos3K on 2010-11-25
Many thanks to you both.  As it happens, I have a Panasonic DMC-ZS3, so my file structure is identical to ajgreeny's. So, just to confirm, I only need the MTS files-- the CPI files in /BDMV/CILPINF/ and the MPL files in /BDMV/PLAYLIST/, for example, I don't need, correct?

VideoRoy, your script for concatinating MTS files is a couple of steps ahead of where I am, but I look forward to trying it out. (My understanding is that you only need to do this where there are multiple MTS files covering one recording session. Could you tell me what the dunny variables in the code (e.g., XXXXXX) need to be replaced with?

Thanks again!

---

### Post by ajgreeny on 2010-11-28
As far as I can see the "other" files you mention are not needed for the playing of the MTS files at all, not in a linux box, at any rate.  All mine play reasonably well, though the system I have is not quite fast enough to do these HD files justice; they're much better on my wife's newer laptop.

I suspect all those other files are needed to use the many and varied applications that come on the CD with the camera, none of which I have even seen, not having a windows box to worry about.

---

### Post by VideoRoy on 2010-11-30
> **Telos3K said:**
> Many thanks to you both.  As it happens, I have a Panasonic DMC-ZS3, so my file structure is identical to ajgreeny's. So, just to confirm, I only need the MTS files-- the CPI files in /BDMV/CILPINF/ and the MPL files in /BDMV/PLAYLIST/, for example, I don't need, correct?

VideoRoy, your script for concatinating MTS files is a couple of steps ahead of where I am, but I look forward to trying it out. (My understanding is that you only need to do this where there are multiple MTS files covering one recording session. Could you tell me what the dunny variables in the code (e.g., XXXXXX) need to be replaced with?

Thanks again!
Sorry, I was out of town and could not reply.

Yes, I only use this when the .MTS files are broken up for the video (s) I want to edit.  Over the weekend I took some footage and every time I hit pause on record it creates another files.  I ended up with 85 .MTS files over 2 days that I want to be in one movie.  My Windows video software can deal with these no problem but all the apps I have tried in Ubuntu choke on them so this will combine them into one and do a little pre-production conversion.

Yes, .MTS are the only video files.  You do not need the other files unless you are trying to make a AVCHD compliant disc which I am playing with now but my Blu-ray player does not support.

Last you do not need to replace XXXXXX with anything.  That is just a prototype for the mktemp command and it will replace the XXXXXX with that many unique characters.

---

