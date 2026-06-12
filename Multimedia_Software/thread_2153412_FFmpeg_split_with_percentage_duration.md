---
title: "FFmpeg split with percentage duration"
date: 2013-06-11
forum: Multimedia Software
---

### Post by SilverbugNZ on 2013-06-11
I have a bunch of video (ok actually over 1500) ranging from 2 mins to about 20 mins long. I want to be able to create a preview or demo video for each one which is 10% of the duration of the original video. Ideally I want to be able to script this to run on my Ubuntu server.

I can see you can specify the length of time you want the video to split, but cant see that you can specify a %.

Also if possible I would like to display an image at the end of the video for about 4 seconds, to say something along the lines of "to watch the rest of this video please register"

Any help would be greatly appreciated.

---

### Post by evilsoup on 2013-06-11
You can't get a % within ffmpeg, becauseit works more-or-less linearly. However, you can scan the video with ffprobe first and extract the duration there, and then divide that by ten and feed it to ffmpeg. Here's a quick and dirty script that will do it -- it will take the first argument as the input, and output to the second argument, so run it like './percentconvert input.mp4 output.mp4' and be careful, as it will overwrite any already-existing files without asking you:

```

#! /usr/bin/env bash
duration=$(ffprobe -i "$1" -show_format | sed -En '/duration/s|.*=(.*$)|scale=2; \1/10|p' | bc)
ffmpeg -y -i "$1" -t "$duration" -c copy "$2"
exit 0

```

'ffprobe -i "$1" -show_format' will give you a bunch of information about the video. 

sed's '-E' option enables extended regex (you can ignore this if you want, but then you have to use \(\) instead of () ), and '-n' tells it not to print anything to STDOUT. '/duration/' has sed find the line containing the string 'duration'. The sed command strips away the 'duration=' from the beginning of the line, and outputs the line 'scale=2; xxx.xx/10', where xxx.xx is the duration given by ffprobe; the 'p' at the very end of the line overrides the '-n' setting for this line only.

bc is a command-line calculator program. 'scale=2' tells it to be accurate to two decimal places (probably more accurate than you need, actually). 'xxx.xx/10' obviously tells bc to divide the duration by ten.

For the other thing, the easiest way would be to create an image in GIMP or something, and then run ffmpeg over it to make a video:

```

ffmpeg -loop 1 -i image.png -t 4 -c:v libx264 ending.mp4

```

...then [have a lookt at the concatenation guide](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files) on the ffmpeg wiki.

---

### Post by SilverbugNZ on 2013-06-11
This is exactly what i was after, thanks evilsoup :)

---

