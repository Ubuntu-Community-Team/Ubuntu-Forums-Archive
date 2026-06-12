---
title: "Converting AVI to FLV bash script"
date: 2013-01-30
forum: Multimedia Software
---

### Post by jar00n on 2013-01-30
[EDIT] Updated with evilsoup's suggestions. I got really awful quality when using h.264 option, went back to the default and got my q number to stay below 5... using '-c:v libx264' yielded q=20 and higher. As stated below you could pass in parameters so that $1 would be input and $2 would be output. For my uses, I will always use the same folders but this is handy to know.
```

./convert.sh /dir/input /dir/output

...

in_folder=$(readlink -f $1) #where $1 is /dir/input
out_folder=$(readlink -f $2) #where $2 is /dir/output

```evilsoup's changes:
```

#!/bin/bash
# convert.sh
# Converts AVI files to FLV files
# If audio bitrate is not detected file is moved to prevent being deleted
# If audio sample rate is 48kHz, sample rate is reduced to 44.1kHz
in_folder=$(readlink -f /home/media/Videos/Original/)
out_folder=$(readlink -f /home/media/Videos/Converted/)
find "$in_folder" -type f -iname "*.avi" -exec readlink -f '{}' \; | while read src
do
    # Determine bit rates and audio sample rate
    total=$(ffprobe $src 2>&1 | grep "Duration:" | egrep -o '\<[0-9]{3}\>')
    audio=$(ffprobe $src 2>&1 | grep "Audio:" | egrep -o '\<[0-9]{3}\>')
    hertz=$(ffprobe $src 2>&1 | grep "Audio:" | egrep -o '\<[0-9]{5}\>')
    let video="$total"-"$audio"
    outfile="$out_folder/$(basename $src .avi)"
    if [ "$audio" == "" ]
    then
        mv "$src" /home/media/Videos/Manual
    else
        # Conversion
        if [ "$hertz" == "48000" ]
        then
            ffmpeg -i "$src" -b:v "$video"k -c:a libfdk_aac -b:a "$audio"k -ar 44100 -f flv "$outfile".flv -y
        else
            ffmpeg -i "$src" -b:v "$video"k -c:a libfdk_aac -b:a "$audio"k -ar "$hertz" -f flv "$outfile".flv -y
        fi
        # Inject cuepoints and remove source file
        flvtool2 -U "$outfile".flv
        rm "$src"
    fi
done

```
I've been leeching from these forums for years and I feel that I finally have something worthwhile to contribute. I built myself a webserver that is hosting flv videos and I have been using crappy tools for the conversion and most of the time I have to do each one by hand because there is nothing standard with the files I'm using. I finally got fed up with the less than optimal output of these tools and decided to script a way to do the entire conversion with one script and improve overall quality.

```

#!/bin/bash
in_folder=/home/media/Videos/Original/
out_folder=/home/media/Videos/Converted/
files=`ls $in_folder`
k=k
flv=.flv
for src in $files
do
    total=`ffmpeg -i $in_folder$src 2>&1 | grep "Duration:" | egrep -o '\<[0-9]{3}\>'`
    audio=`ffmpeg -i $in_folder$src 2>&1 | grep "Audio:" | egrep -o '\<[0-9]{3}\>'`
    hertz=`ffmpeg -i $in_folder$src 2>&1 | grep "Audio:" | egrep -o '\<[0-9]{5}\>'`
    let video=$total-$audio
    base=${src%%.*}
    if [ $hertz == "48000" ]
    then
        ffmpeg -i $in_folder$src -b:v $video$k -acodec mp3 -b:a $audio$k -ar 44100 -f flv $out_folder$base$flv
    else
        ffmpeg -i $in_folder$src -b:v $video$k -acodec mp3 -b:a $audio$k -ar $hertz -f flv $out_folder$base$flv
    fi
    flvtool2 -U $out_folder$base$flv
    rm $in_folder$src
done

```This was done completely on Ubuntu 12.04 Desktop 32bit.

There are a few assumptions made with this script, namely you are going from avi to flv, I'm pretty sure that mkv or mp4 would likely work I just don't have any on my computer at this time. The next assumption is that ffmpeg is compiled by source. I used this website as a guide, I did not install the optional opus library: [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). I also sanitized all my file names prior to the conversion, I'm pretty sure my script will fail as it generates its files array from the output of ls /path/name/ which does not include the escape characters. There is probably an easy way to handle that, I just didn't look into it.

A key thing to take note when you are watching the output of the conversion that the "q=x.x" value should never approach 31, the range is 2 to 31 with 2 being best and 31 being worst. On my VM I gave it 4gb of ram (even though I'm on 32bit OS...) and a single core on my processor and I was able to keep the q value pretty low, somewhere between 2 and 6 with the occasional spike to 16 or so.

The conditional that is questioning the hertz value of the source avi is important because flv files cannot exceed 44100 hertz on their audio track, and from my tests dropping it down from 48k to 44.1k didn't hurt the audio in a noticeable way.

You will also need flvtool2 installed as well, as this will allow you to inject keyframe or cuepoints, not sure which is the correct term, into the flv file to allow you jump to a given point in the stream. **This part is extremely CPU intensive and takes along time to complete, open up a new terminal and watch it with top.**

You may want to comment out the last line where it is removing the source file from the computer, as you will likely want to have that on hand again if something goes wrong with the script.

Please give me some comments if something could be changed to improve quality or anything like that. I am not a pro at this stuff so I likely won't be able to answer any questions regarding obscure errors but ask away.

---

### Post by evilsoup on 2013-01-30
You should use 'ffprobe file 2>&1' instead of 'ffmpeg -i file 2>&1', and $(...) instead of `...` - that's relatively minor stuff, though.

You could use something like

```

in_folder=$(readlink -f "$1")
out_folder=$(readlink -f "$2")

```Then people could use the script like 'scriptname infolder outfolder' (with either a relative or /absolute/path/to/dir).

```

k=k
flv=.flv

```You don't need these. I suspect that you're trying to isolate $video from the letter k later in the script, and $base from .flv. A better way would be to simply quote your variables - which you should nearly always do anyway. Instead of

```

flvtool2 -U $out_folder$base$flv
##  use
flvtool2 -U "$out_folder"/"$base".flv

```

...but I'll show you an entirely different, better way to do that in a minute.

Now, on to a more serious issue...

```

files=`ls $in_folder`
...
for src in $files

```

[Don't try to parse the output of ls](http://mywiki.wooledge.org/ParsingLs). I know what you're trying to do, because I did exactly the same thing until I was corrected. A better way to do this is to use find with a while read loop:

```

find "$in_folder" -type f -iname "*.avi" -exec readlink -f '{}' \; | while read src
*ffmpeg stuff*
...
done

```

I've included '-exec readlink -f '{}' \;', which will have the advantage of feeding the absolute path of each *.avi into $src, so you won't need to use that '$in_folder$src'  construction - you can use "$src" instead. Likewise, if you define a variable:

```

outfile="$out_folder/$(basename $src .avi)"

```

...then you can simply use "$outfile".flv instead of '$out_folder$base$flv'.

Adding all of this together, the script can be tidied a bit (and made more reliable to boot).

As for the actual ffmpeg stuff... wouldn't you be better served by using [libx264](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for the video and [libfdk_aac](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide) for the audio? If you compiled ffmpeg yourself, you should have both of those; h.264 & AAC are the current gold standard of delivery formats, and the flv container supports them both.

---

### Post by jar00n on 2013-01-30
Thanks for the feedback, I really didn't have an understanding of how bash concatenated strings so I just did added those two variables to solve what I couldn't figure out. I'll try to rewrite given what you supplied, but I'll need to read up on the av codecs

---

