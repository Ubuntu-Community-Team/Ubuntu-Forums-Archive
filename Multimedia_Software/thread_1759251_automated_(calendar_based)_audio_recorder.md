---
title: "automated (calendar based) audio recorder"
date: 2011-05-15
forum: Multimedia Software
---

### Post by bkortleven on 2011-05-15
For our local Student Radio Broadcast station I'm looking for an automated/automatic audio recorder which can do the following:

- record 1 incoming audio signal from a sound card
- record in an open/convertible audio format with predefined format settings
- scheduled recording through some kind of calendar (ics, mysql or other basis)
- automatically rename the recordings to a preset name like the title of the schedule+the date of the recording

We'd like to use it as a standalone/headless/configurationless audio recording/archival solution for our programs, so we cannot forget recording it manually as it happens from time to time now...

I know Fluendo/Flumotion can do something like that, but I cannot seem to find how this can be achieved. Are there any people here knowing how to script/configure this, or have any other software package that can achieve (most of) the above?

Thanks!

---

### Post by ajgreeny on 2011-05-15
You should look at **arecord** to record as ogg from the sound card, **mplayer** to rip audio streams ( if that is what you want), and plain cron to schedule timings of recording.

This is not the place for a tutorial in how to do all that, and you probably need to look at each separately and understand them one at a time to do what you want., but here are some examples I use, first for steamed radio:-
 ```
mplayer <URL> -dumpstream -dumpfile stream.mp3
                    #saves mp3 stream as file stream.mp3
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
                    #saves real or other stream as file outfile.wav
```
and then as recording soundcard output:-
```
arecord -f cd -d 10 recording.wav
```

Could be piped through ffmpeg to produce an mp3 (or ogg with changes to command)
```
arecord -f cd $.wav | ffmpeg -i $.wav -acodec libmp3lame -aq 2 file.mp3
```
There is plenty of cron info around to allow you to find that, so I will not go further here.

---

### Post by cchhrriiss121212 on 2011-05-15
Someone asked this a while ago, the thread this post is from has some good tips too:
[http://ubuntuforums.org/showpost.php?p=10319249&postcount=13](http://ubuntuforums.org/showpost.php?p=10319249&postcount=13)

---

