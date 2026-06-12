---
title: "ffmpeg bash script"
date: 2015-08-05
forum: Multimedia Software
---

### Post by NGnewb on 2015-08-05
I'm trying to make a bash script work for recursive 2-pass encoding. I have modified a script, which I have used successfully for ages, to do batches of single pass encoding, but when modified for 2-pass encoding it completes the first file it finds and then stops. I'm hoping someone can give it a look and point me in the right direction.


```
#!/bin/bash
# 2-pass-slow - convert .mkv to .mp4 recursively
#####################################


if [ -z $1 ];then echo Give target directory; exit 0;fi


find "$1" -depth -name '*' | while read file ; do
directory=$(dirname "$file")
oldfilename=$(basename "$file")
newfilename=$(basename "${file%.[Mm][Kk][Vv]}")


if [ "$oldfilename" != "$newfilename" ]; then
ffmpeg -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 1 -c:a aac -b:a 128k -strict -2 -c:s copy -f mp4 /dev/null && \ffmpeg -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 2 -c:a aac -b:a 128k -strict -2 -c:s copy "$directory/$newfilename.mp4" </dev/null
fi


done
```


EDIT:  Ok, so I finally tinkered around and found the solution: all I had to do was add a -nostdin flag after the ffmpeg in each line. All works correctly now. So the working code is as follows:

```
#!/bin/bash
# 2-pass-slow - convert .mkv to .mp4 recursively
#####################################


if [ -z $1 ];then echo Give target directory; exit 0;fi


find "$1" -depth -name '*' | while read file ; do
directory=$(dirname "$file")
oldfilename=$(basename "$file")
newfilename=$(basename "${file%.[Mm][Kk][Vv]}")


if [ "$oldfilename" != "$newfilename" ]; then
ffmpeg -nostdin -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 1 -c:a aac -b:a 128k -strict -2 -c:s copy -f mp4 /dev/null && ffmpeg -nostdin -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 2 -c:a aac -b:a 128k -strict -2 -c:s copy "$directory/$newfilename.mp4" </dev/null
fi


done
```

---

### Post by SeijiSensei on 2015-08-05
Why is the second ffmpeg command entered as \ffmpeg? If the slash is intended to tell bash that the command continues on the next line, you need to have whitespace on both sides of the slash.  Something like this, for instance,
```

ffmpeg -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 1 -c:a aac -b:a 128k -strict -2 -c:s copy -f mp4 /dev/null && \ 
ffmpeg -y -i "$directory/$oldfilename" -map 0:v -map 0:a -map 0:s -c:v libx264 -preset slow -b:v 600k -pass 2 -c:a aac -b:a 128k -strict -2 -c:s copy "$directory/$newfilename.mp4" </dev/null

```
Usually a slash followed by a non-blank character tells the shell to treat the following character as a literal, e.g., "\#".  That doesn't apply to your case since "\ffmpeg" and "ffmpeg" would be parsed identically.

---

### Post by NGnewb on 2015-08-05
Thank you for the quick response. Any help I can get is much appreciated. Honestly, I think it must have been a typo from wherever I had originally copied a command for 2-pass encoding, long ago (I have a few text files, compiled over the years, with commands for doing different things with ffmpeg). Curiously, it still ran the second pass successfully the way that I had it coded. After changing it to what you had recommended, it still completes conversion of the first file and then stops, leaving the rest of the files untouched, and with no errors reported from bash or ffmpeg. 

I remember having to add the "</dev/null/" to the single-pass encoding script for it to work properly, something about ffmpeg reading from stdin, but I can't, for the life of me, figure out why this script won't work for 2-pass encoding.

For single-pass encoding this is what I use, and it works flawlessly (of course, I'd rather use 2-pass encoding for smaller, better quality files):

```
#!/bin/bash
# convert .mkv to .mp4 recursively
#####################################


if [ -z $1 ];then echo Give target directory; exit 0;fi


find "$1" -depth -name '*' | while read file ; do
directory=$(dirname "$file")
oldfilename=$(basename "$file")
newfilename=$(basename "${file%.[Mm][Kk][Vv]}")


if [ "$oldfilename" != "$newfilename" ]; then
ffmpeg -i "$directory/$oldfilename" -acodec aac -vcodec libx264 -preset medium -crf 18 -strict -2 "$directory/$newfilename.mp4" </dev/null
fi


done 
```

---

### Post by FakeOutdoorsman on 2015-08-05
> **NGnewb said:**
> I'd rather use 2-pass encoding for smaller, better quality files
If you're trying to target a specific output file size, then go ahead and use 2-pass, but 2-pass won't provide any better quality than using a single pass with -crf.

You should probably just use the highest -crf value that gives you an acceptable quality, and the slowest -preset that you have patience for.

---

