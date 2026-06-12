---
title: "ffmpeg audio/video/webcamstream out of sync (simple solution)"
date: 2013-08-26
forum: Multimedia Software
---

### Post by gargl on 2013-08-26
Hi there...
just for the record because mb anyone else got the same problem as I.
I've tried to record (grab) audio and video from my webcam using ffmpeg.
Unfortunately the resulting file was totally out of sync (audio<->video)!

After founding a bug report [http://trac.ffmpeg.org/ticket/692](http://trac.ffmpeg.org/ticket/692) which was
marked as solved but unfortunately did not help me i've was reading through
the ffmpeg documentation and found a very unusual and simple but still
working solution.

My first command was:
```

ffmpeg \
-f alsa -ac 1 -i plughw:1,0 \
-f v4l2 -s "320x240" -i /dev/video0 \
-vcodec libx264 -s "320x240" -preset "medium" \
-acodec libmp3lame -ar 44100 -q:a 3 -b:a 712000  -bufsize 512k \
-f flv out.flv \

```

However I get a warning when hitting enter:
```

[libmp3lame @ 0x27d5b80] Queue input is backward in time
Last message repeated 5 times
[flv @ 0x27d1380] Non-monotonous DTS in output stream 0:1; previous: 906, current: 902; changing to 906. This may result in incorrect timestamps in the output file.

```

resulting in an out of sync video file.


Reading the ffmpeg doc ([http://ffmpeg.org/ffmpeg-all.html](http://ffmpeg.org/ffmpeg-all.html)) I found option '-y' which means: "Overwrite output files without asking. "
So far I had to confirm every time at the beginning of the recording process to overwrite
the file 'out.flv' if it really existed before, I did not really think that this might cause the error or
could be a solution.

Although I do not think that this should be the proper solution to such a severe problem,
it just works. If you modifie the above command to:

```

ffmpeg **-y** \
-f alsa -ac 1 -i plughw:1,0 \
-f v4l2 -s "320x240" -i /dev/video0 \
-vcodec libx264 -s "320x240" -preset "medium" \
-acodec libmp3lame -ar 44100 -q:a 3 -b:a 712000  -bufsize 512k \
-f flv out.flv \

```

ffmpeg instantly starts the recording, without asking to overwrite out.flv but
just doing it. Still the warning is thrown several times but it will luckily not
result in an out of sync file.

Hope this might help others! Mb I should make a bug report to @ffmpeg.

Regards!


p.s. **Attention**; remember that any file with the same name of that
being specified in the ffmpeg command will be permanently deleted if you
execute the command using the '-y' argument. So be careful with possibly
earlier recorder files.

---

### Post by luctor on 2013-08-27
maybe you should post this in the wiki ?

---

### Post by garrett3 on 2013-09-16
> **gargl said:**
> 
Reading the ffmpeg doc ([http://ffmpeg.org/ffmpeg-all.html](http://ffmpeg.org/ffmpeg-all.html)) I found option '-y' which means: "Overwrite output files without asking. "
So far I had to confirm every time at the beginning of the recording process to overwrite
the file 'out.flv' if it really existed before, I did not really think that this might cause the error or
could be a solution.

Although I do not think that this should be the proper solution to such a severe problem,
it just works. 

Yes, I found the same error.  In fact, the first time I ran:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
```

which I found from [HOWTO: Proper Screencasting in Linux]("http://ubuntuforums.org/showthread.php?t=1392026"), it worked fine the first.  Audio and video were synched nicely.  

The second time I ran that command, it asks: 

```
File 'output.mkv' already exists. Overwrite ? [y/N]
```

but it starts recording the audio!  So you can say something, and THEN hit 'y' and 'enter', and that thing you said will appear in the final .mkv file.  Therefore, the audio and video will be out of synch by however long it took you to hit 'y' and 'enter'.


BTW, I compiled ffmpeg today follwing [this site]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide"), so I think it's up to date.

---

