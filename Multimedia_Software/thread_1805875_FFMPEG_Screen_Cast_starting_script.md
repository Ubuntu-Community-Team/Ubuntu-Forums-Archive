---
title: "FFMPEG Screen Cast starting script?"
date: 2011-07-16
forum: Multimedia Software
---

### Post by splosh5 on 2011-07-16
I apologise in advance if this post is in the wrong section.

I do quite allot of screen tutorials, and i am always useing this FMMPEG script.

 ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y video2.avi

I was just wondering if someone knows a script that i could put in a text file, make it executable and it would ask me what i wanted to save the file as, and it would put that text where "Video2.avi" goes, and then it would just run the normal FFMPEG script.

Again sorry if this is in the wrong section, but if anyone knows how to write on or knows one, please post below.

Thanks,
Josh.

---

### Post by FakeOutdoorsman on 2011-07-17
Here's a simple script. Copy it into a text file and name it *xgrab.sh*:
```
#!/bin/bash
# usage: ./xgrab.sh output.mkv

# if/then statement as an example. not really needed if you remove the "-y" from your encoding command
if [ -e "$1" ]; then
        echo "$1 already exists. Exiting."
        exit
fi

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y "$1"
```
Then give it executable permission:
```
chmod +x xgrab.sh
```
Now you can use it:
```
./xgrab.sh screencast.mkv
```
or
```
./xgrab.sh /path/to/file/screencast.mkv
```

---

### Post by splosh5 on 2011-07-17
Thank-you very much Fakeoutdoorsman, this is really appreciated & a very big help. :) Would there be away to make it so after running - 
./xgrab.sh screencast.mkv 
It would be able to put the video into a folder called "videos". That way it does not fill up my home folder with videos.

---

### Post by FakeOutdoorsman on 2011-07-17
Sure. Here is a new version. It checks to see if *~/videos* exists, and if it doesn't it creates that directory. I forgot to put your audio options in my previous example, but this one has them. I'll fix the previous example.
```
#!/bin/bash
# usage: ./xgrab.sh output.mkv

outputdir=~/videos

if [ ! -d "$outputdir" ]; then
   mkdir ~/videos
fi

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 "$outputdir"/"$1"
```

---

