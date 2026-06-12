---
title: "converting to awb for nokia audiobooks"
date: 2008-11-20
forum: Multimedia Software
---

### Post by klikklak on 2008-11-20
Hi all, 

I've been trying to get nokia audiobooks app for s60 to work.  It correctly finds the example books from nokia site, but not the files I converted with amrwb-encoder.  Has anyone managed to solve this?

EDIT: forgot to convert to wav first, duh!
the shell loops for doing this are: 
for i in *.mp3; do mpg321 -w /tmp/`basename $i .mp3`.wav $i; done
for i in /tmp/*wav; do amrwb-encoder 5 $i `basename $1`.awb; done

What I get now is slow garbled speech.  It looks like nokia audiobook manager works with wine, but it seems really slow.

---

### Post by fezouro on 2009-03-14
amrwbn-encoder doesn't work for me either... all I'm getting is noise in the .awb file...

I'm using 16 bit PCM (wav) as input, and have tried both big endian and little endian with no luck.

My platform is amd64.

Any help would be appreciated. I also use Nokia Audiobooks through VirtualBox, but it's a pain in the neck (too slow, and then the hassle of using Windoze).

---

### Post by fezouro on 2009-03-31
Well, I think that I found the problem. The input files to amrwb-encoder must be (for some obscure reason) sampled at 8kHz.

So you can use the "resample" command (available in Debian with apt-get) to obtain the correct input file. The whole process is:

mpg321 -w file.wav file.mp3 # output sampled at 22kHz
resample -to 8000 file.wav file2.wav
amrwb-encoder -dtx 7 file2.wav file.awb # dtx on, mode 7

This seems to work. But it is all the same misterious, since amr-wb should work for 16kHz speech...

Enjoy.> 

---

### Post by fezouro on 2009-04-01
Just in case somebody out there is interested, here is my complete hack to replace the Nokia Audiobooks application with a bash script, plus some Debian programs (Ubuntu must be the same). I hope that we can finally bin that awful Windoze program... enjoy.

BTW, forget my previous post, the input to amrwb-encoder must be sampled at 16kHz for the files to work in the phone (as it should). However the gstreamer plugin seems to want 8kHz...

```
#!/bin/bash

# Hack to avoid using the Nokia Audiobooks application 
# No hassle with Windoze plus conversion is faster too

# The script just takes one single compulsory parameter: book_title 
# Execute it in a directory contaning the mp3s plus a single cover jpg
# Any file names are fine
# Output files are in the folder ./book_title
# This folder can be moved as-is to the Audiobooks directory in the phone

# Change the parameters to amrwb-encoder if you want more compression, etc
# Change the chapter values by hand in the index file if you're a perfectionist

# Note: some sections are optional in theory (chapters, content_info),
# but removing some of them breaks the program

# Required packages (Debian): mpg321, resample, amrwb, mplayer

# Courtesy of Fezouro (Ubuntu forums)

index="/tmp/index.inx"
tmp="/tmp/tmp.wav" 
tmp2="/tmp/tmp2.wav"
rm -f  $tmp $tmp2 $index
mkdir "$1";
echo "#BOOK" > $index
echo "$1;" >> $index
echo "#PIC" >> $index
echo "$1.jpg;" >> $index
echo "#TRACKS" >> $index
find . -maxdepth 1 -iname "*mp3" | sort | while read i; do
    j=`basename "$i" .mp3`
    base=`basename "$j" .MP3`
    out="$base.awb"
    mpg321 -q -w $tmp "$i" 
    resample -to 16000 -terse $tmp $tmp2 # resample to awb rate
    lengthd=`mplayer -vo null -ao null -frames 0 -identify $tmp2 2>/dev/null | grep ID_LENGTH | awk -F= '{print $2}'`  # length in seconds
    length=`echo "scale=0;$lengthd/1" | bc`    # remove decimals
    amrwb-encoder -dtx 7 $tmp2 "$1/$out"  # convert to awb
    echo "$out:$length;" >> $index
    rm -f $tmp $tmp2 
done

echo "#CHAPTERS" >> $index
chapter=1;
find . -maxdepth 1 -iname "*mp3" | sort | while read i; do
    j=`basename "$i" .mp3`
    base=`basename "$j" .MP3`
    out="$base.awb"
    echo "$out:0s:$chapter:$base;" >> $index
    chapter=$(($chapter+1))
done
echo "#VERSION" >> $index
echo "0.7;" >> $index

echo "#CONTENT_INFO" >> $index
echo "NokiaAudiobookManagerVersion=Hack by Fezouro;" >> $index
echo "CodecMode=7;" >> $index
echo "CodecBitRate=23050;" >> $index
echo "DTX=1;" >> $index
echo "SBRA=0;" >> $index
echo "SBRA_Rate=900;" >> $index
echo "InputFormat=2;" >> $index

# index must be in little endian UTF-16 unicode format
iconv -t UTF-16 $index > "$1/$1.inx"

# copy book cover with right name
cover=`find . -maxdepth 1 -iname \*.jpg`
cp "$cover" "$1/$1.jpg"

rm -f $tmp $tmp2 $index
```

---

