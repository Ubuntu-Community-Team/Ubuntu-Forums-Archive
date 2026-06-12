---
title: "h264 video from 1080p MTS files"
date: 2012-02-04
forum: Multimedia Software
---

### Post by pixiq on 2012-02-04
Hi!

I have found some scripts using ffmpeg and been able tweak them to convert MTS files from my video camera to files that can be displayed

- [FONT=Courier New]  960x540-50p[/FONT] - in older computers
- [FONT=Courier New] 1280x720-50p[/FONT] - in ordinary computers
- [FONT=Courier New]1920x1080-30p[/FONT] - in powerful computers and modern TV sets
(our Samsung TV displays neither MTS files nor [FONT=Courier New]1920x1080-50p[/FONT] files) 

I use the script file ***mts2mp4***, that calls the script file*** ffx264*** to do it with ffmpeg using the codec libx264. But it is very slow, partly because it creates a big intermediate file encoded with a standard mpeg-4 codec.

* Can you help me to make these scripts better (faster and and at least the same quality versus size)?
--
If it makes it easier to help, I can upload an own [FONT=Courier New]1920x1080-50p [/FONT]MTS file. But I have prepared the script ***get-MTS*** to download a published [FONT=Courier New]1920x1080-60p[/FONT] MTS file, that we can start using to compare results.

I am running Ubuntu Studio 11.04 with standard ***ffmpeg*** from the repos.
--
pixiq

[I][B]get-MTS
[/B][/I]```
#! /bin/bash

wget http://s3.amazonaws.com/movies.dpreview.com/panasonic_dmcfz150/00000.MTS
mv 00000.MTS singer.MTS

# Check that you are is a suitable directory and run the script file
#
# mts2mp4
#
# to create 3 mp4 files with ffmpeg using the codec libx264
#
# l -h
# total 443M
# -rw------- 1 pixiq pixiq 2,0K 2012-01-12 10:26 ffx264
# -rw------- 2 pixiq pixiq  117 2012-02-04 20:37 get-MTS
# -rw------- 1 pixiq pixiq  519 2012-01-12 11:43 mts2mp4
# -rw------- 1 pixiq pixiq  38M 2012-02-04 18:57 singer_1080-30p.mp4
# -rw------- 1 pixiq pixiq  11M 2012-02-04 18:57 singer_540-50p.mp4
# -rw------- 1 pixiq pixiq  20M 2012-02-04 18:57 singer_720-50p.mp4
# -rw------- 1 pixiq pixiq 246M 2012-02-04 20:06 singer.mp4
# -rw------- 1 pixiq pixiq 130M 2012-02-04 18:57 singer.MTS
#
# Is it possible to create 3 mp4 files with similar properties
# without creating the intermediate big mp4 file (singer.mp4)
# encoded with the standard codec for mpeg-4 video?

```[I][B]mts2mp4
[/B][/I]```
#!/bin/bash

echo "----------------------------------------------------------------------"
echo "Usage: $0 "
echo " "
echo "to convert from high-quality MTS camera files to 3 quality video files"
echo " "
echo "---------- 960x540-50p ----- 1280x720-50p ----- 1920x1080-30p --------"
sleep 3

for i in *.MTS
do
 if test -f "${i/.MTS}.mp4"
 then
  echo $i and "${i/.MTS}.mp4" exist, already converted
 elif test -f "$i"
 then
  ffx264 "$i" 540
  ffx264 "$i" 720
  ffx264 "$i" 1080
 else
  echo "not a file $i "
 fi
done

```[I][B]
ffx264[/B][/I]
```
#! /bin/bash

if [ "$2" == "" ]
then
 echo "Usage: $0 <MTS file> <output video resolution>"
 echo "ex:    $0 00007.MTS 1080   or  $0 00007.MTS 1920x1080  or"
 echo "       $0 00007.MTS 720    or  $0 00007.MTS 1280x720   or"
 echo "       $0 00007.MTS 540    or  $0 00007.MTS 960x540"
 exit
fi

typeset infile="$1"

if test -f $infile
then
 if [ $infile == ${infile/\.MTS} ]
 then
  echo "$infile is not an MTS file"
 fi
else
 echo "$infile not found"
fi

if [ "$2" != "${2/1080}" ]
then
 typeset namex=1080-30p
 echo $namex
 typeset res=1920x1080
 typeset framerate=30
 typeset bitrate=8196k
elif [ "$2" != "${2/720}" ]
then
 typeset namex=720-50p
 echo $namex
 typeset res=1280x720
 typeset framerate=50
 typeset bitrate=4096k
elif [ "$2" != "${2/540}" ]
then
 typeset namex=540-50p
 echo $namex
 typeset res=960x540
 typeset framerate=50
 typeset bitrate=2048k
else
 echo "bad resolution specified (not 1080, 720 or 540)"
fi

typeset infile="${infile/\.MTS}.mp4"
typeset tmpfile="${infile/.mp4}_tmp.mp4"
typeset outfile="${infile/.mp4}_$namex.mp4"

echo typeset MTS-file=$1
echo typeset infile="$infile"
echo typeset tmpfile="$tmpfile"
echo typeset outfile="$outfile"

if test -f "$infile"
then
 echo "$infile exists, no need to make it again"
sleep 5
else
 ffmpeg  -i $1 -sameq "$infile"
sleep 5
fi

typeset options="-vcodec libx264 -s $res -r $framerate -b $bitrate -flags +loop+mv4 -cmp 256 \
       -partitions +parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 \
       -me_method hex -subq 7 -trellis 1 -refs 5 -bf 3 \
       -flags2 +bpyramid+wpred+mixed_refs+dct8x8 -coder 1 -me_range 16 \
           -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -qmin 2\
       -qmax 51 -qdiff 4"

ffmpeg -y -i "$infile" -an -pass 1 -threads 2 $options "$tmpfile"
ffmpeg -y -i "$infile" -acodec libfaac -ar 48000 -ab 384k -pass 2 -threads 2 $options "$tmpfile"

qt-faststart "$tmpfile" "$outfile"
touch -r "$1" "$outfile"
rm ffmpeg2pass-0.log x264_2pass.log x264_2pass.log.mbtree "$tmpfile"

```

---

### Post by BicyclerBoy on 2012-02-04
AFAIK
you are transcoding twice..because -sameq is a transcode & that makes it slower.
The ffmpeg option -sameq commonly results in files twice as big.
m2ts files contain either mpeg4/10 (h264), VC1 or mpeg2 video.
All these are supported in mpeg4 mpeg2-ts container.
ffmpeg chokes on interlaced VC1.

Your first transcode could just be a remux into mpeg4 container by using -vcodec copy.

The temp file makes the process faster if the m2ts file must be transcoded into mpeg4 container.
Because in the past ffmpeg was not able to remux h264 into new container, it had to transcode..this situation may have changed.

There are some ffmpeg ppa with later & more complete versions..

---

### Post by pixiq on 2012-02-05
Thanks for your reply, BicyclerBoy,

I try, but I cannot quite understand. Do you mean that I should use [FONT=Courier New][SIZE=3]-vcodec copy[/SIZE][/FONT] instead of [FONT=Courier New][SIZE=3]-sameq[/SIZE] [/FONT]in the first step to make the intermediate big mp4 file (singer.mp4)? 

Or could I skip that step completely, if I install the newest version of ffmpeg from its own internet page? I guess that is described by FakeOutdoorsman in 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by ron999 on 2012-02-05
> **pixiq said:**
> 
Or could I skip that step completely, if I install the newest version of ffmpeg from its own internet page? I guess that is described by FakeOutdoorsman in 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
Yes.
With latest version of FFmpeg compiled you should be able to convert straight from MTS to mp4.
Like this:-
```
ffmpeg -i input.MTS -c:v libx264 [options] -c:a libfaac [options] output.mp4
```

Attached is a small 15 second sample using this command:-
```
ffmpeg -i 00000.MTS -t 15 -vf "scale=128:trunc(ow/a/2)*2" -c:v libx264 -c:a libfaac output.mp4
```

---

### Post by pixiq on 2012-02-05
Thanks ron999,

I'll try your example with your input file as well as with one of mine. And please explain the option -vf "scale=128:trunc(ow/a/2)*2"

*Edit: I understand it is the scaling (to a small size, that can be attached) but still ... And I'll need some time to get the new version running ...*

---

### Post by ron999 on 2012-02-05
> **pixiq said:**
> And please explain the option -vf "scale=128:trunc(ow/a/2)*2"
This vf filter sets width and height. Instead of using -s option.
In my sample, width is set to 128 pixels. (scale=128 )
Height is calculated to keep same aspect ratio. (trunc(ow/a/2)*2")

---

### Post by pixiq on 2012-02-05
Thanks, now I understand, this formula can be used instead of specifying both (wxh)

---

