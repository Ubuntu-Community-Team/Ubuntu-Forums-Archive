---
title: "FFMPEG batch video convert?"
date: 2009-08-11
forum: Multimedia Software
---

### Post by babujbf on 2009-08-11
Hi guys I got a folder full of different avi files and I want to convert them to mpegs or if possible flv. I want to convert them exactly as they are I dont want to alter the video quality or anything, I saw the commands to do conversions one by one but I want to convert like 50. How can I do this?

Thanks

I also have Mplayer I read you can do conversions with mplayer too?

---

### Post by bumanie on 2009-08-11
You could try [winff]("http://winff.org/html_new/") - not sure whether it will convert more than one file at a time. It is basically a gui for ffmpeg.

---

### Post by FakeOutdoorsman on 2009-08-11
> **babujbf said:**
> Hi guys I got a folder full of different avi files and I want to convert them to mpegs or if possible flv. I want to convert them exactly as they are I dont want to alter the video quality or anything, I saw the commands to do conversions one by one but I want to convert like 50. How can I do this?

Thanks

I also have Mplayer I read you can do conversions with mplayer too?

The *find* command is the perfect tool for this:
[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937) [ubuntuforums.org]

Example to convert all *.avi to *.mp4 in the ~/encode folder:
```
find ~/encode -name '*.avi' -type f -exec ffmpeg -i '{}' -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 '{}'.mp4 \;
```

---

### Post by cotcot on 2009-08-11
This was useful for me. Thanks. The output gives files names with double extention .MTS.mpg (I am batch converting MTS to mpg with mencoder). 
Any suggestion how to keep .MTS (in your example .avi) out of the output file name ?

---

### Post by babujbf on 2009-08-11
That command didn't work for me... where do I have to run it? DO I have to cd to the file containing the avis? Cause it says file not found.

By the way how would I convert avis without decreasing quality of video or audio and convert them to mpeg?

Thanks for the replies.

---

### Post by andrew.46 on 2009-08-11
Hi cotcot,

> **cotcot said:**
> Any suggestion how to keep .MTS (in your example .avi) out of the output file name ?

I wrestled with the find syntax + sed for some time and failed fairly miserably :(. However if it is a *single folder* with avi files that you are dealing with the following variation of Fakeoutdoorsman's syntax using a for loop will work:

```

for i in *.avi
do 
	ffmpeg -i $i \
	-acodec libfaac -ac 2 -ab 128k \
	-vcodec libx264 -vpre hq -crf 24 -threads 0 \
	$(echo $i | sed 's/\.avi$//').mp4 
done

```

This effectively creates a file called *outfile.mp4* rather than *outfile.avi.mp4* and can be used in a script or as a simple copy and paste job. Somebody more skilled that me should be able to weave this into a proper find search :-).

Andrew

**Edit**: I guess I should mention that this fails if there are spaces in the filenames...

---

### Post by FakeOutdoorsman on 2009-08-11
> **babujbf said:**
> That command didn't work for me... where do I have to run it? DO I have to cd to the file containing the avis? Cause it says file not found.
My *find* example looked for files in the *encode* directory which is in my home directory (the *~/* is the same as typing */home/fakeoutdoorsman/*).  Alternatively you could navigate to your target directory and then run:
```
find . -name '*.avi' -type f -exec ffmpeg -i '{}' -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 '{}'.mp4 \;
```
> By the way how would I convert avis without decreasing quality of video or audio and convert them to mpeg?
You can't convert to a lossy format such as mpeg without loss of quality.  If you explain what you are trying perhaps a better format can be used.

---

### Post by mc4man on 2009-08-11
Solely in terms of the 'double' ext. (with or without spaces in name), and using a 'for' then something like this gives same filename w/ 1 ext. 

((with the for and wildcard *, you **must** be at the dir. prompt where files are.
Alternate save paths, if desired, go directly in front of "${f%.avi}.mp4"

```
for f in *.avi; do ffmpeg -i "$f" -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 "${f%.avi}.mp4"; done

```

---

### Post by andrew.46 on 2009-08-11
Hi mc4man,

> **mc4man said:**
> Solely in terms of the 'double' ext. (with or without spaces in name), and using a 'for' then something like this gives same filename w/ 1 ext.[...]

```
for f in *.avi; do ffmpeg -i "$f" -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 "${f%.avi}.mp4"; done

```

Very nice! I officially withdraw my gratuitous use of sed :-).

Andrew

---

### Post by cotcot on 2009-08-12
Any idea why this command is a no go ? (I am in the folder with these two .MTS files).
```
for f in *.MTS; do mencoder “$f” -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o "${f%.MTS}.mpg"; done
MEncoder SVN-r29123-4.3.3 (C) 2000-2009 MPlayer Team
File not found: '“00119.MTS”'
Failed to open “00119.MTS”.
Cannot open file/device.

Exiting...
MEncoder SVN-r29123-4.3.3 (C) 2000-2009 MPlayer Team
File not found: '“00126.MTS”'
Failed to open “00126.MTS”.
Cannot open file/device.

```

The  following command works fine however with the double extension :
```
find ~/encode -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

---

### Post by babujbf on 2009-08-12
> **FakeOutdoorsman said:**
> My *find* example looked for files in the *encode* directory which is in my home directory (the *~/* is the same as typing */home/fakeoutdoorsman/*).  Alternatively you could navigate to your target directory and then run:
```
find . -name '*.avi' -type f -exec ffmpeg -i '{}' -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 '{}'.mp4 \;
```

You can't convert to a lossy format such as mpeg without loss of quality.  If you explain what you are trying perhaps a better format can be used.

What other formats can I convert a video without loosing quality then?

Thanks

---

### Post by FakeOutdoorsman on 2009-08-12
> **babujbf said:**
> What other formats can I convert a video without loosing quality then?

Thanks

It depends on why you want to convert a video and what the final usage is.  If you don't want to loose quality, your choices are:

[list][*] Copy the video and audio streams and put them into another [container format](http://en.wikipedia.org/wiki/Container_format_%28digital%29) without re-encoding.  Useful for trimming videos or moving from one container to another compatible container.


[*] Convert using a lossless encoder such as: libx264, ljpeg, ffv1, huffyuv, ffvhuff.  These files will be large.[/list]

---

### Post by babujbf on 2009-08-13
Yeap thats why I want to convert, so I can trim and stuff. So what container format would it be? How would the command be?

Thanks man

---

### Post by FakeOutdoorsman on 2009-08-13
> **babujbf said:**
> Yeap thats why I want to convert, so I can trim and stuff. So what container format would it be? How would the command be?

Thanks man

You can use the same container format as your original if you're just trimming a file.  For example, avi to avi.  Example with option descriptions:

[http://ubuntuforums.org/showpost.php...78&postcount=4](http://ubuntuforums.org/showpost.php...78&postcount=4)

---

### Post by GrouchyGaijin on 2013-01-04
Man, you guys are a wealth of information!

I've learned some really cool and useful things in this forum.

---

