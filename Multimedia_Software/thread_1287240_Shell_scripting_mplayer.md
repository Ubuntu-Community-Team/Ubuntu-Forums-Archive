---
title: "Shell scripting mplayer"
date: 2009-10-09
forum: Multimedia Software
---

### Post by ttabbal on 2009-10-09
I'm trying to set up an mplayer script so that I can have a little file in each subdirectory with a video file so I can specify particular options on the command line for some files. For example, when I rip DVDs that have subtitle tracks. I generally don't want subs, but it would be really nice to automatically select the proper sub track for some films. For example, ones that have foreign language parts and have subs in English for those bits. I can get the proper track number for them easy enough. But each file could end up with the sub track I want in a different place. What I have seems to work with "echo" statements, but mplayer complains that it doesn't understand "-sid 1" on the command line when I use the script to do it. If I cut and paste the resulting command line, it runs properly. It doesn't seem like I'm doing anything too odd here... 


```
#!/bin/bash
DIR=`dirname "$1"`

if [ -f "$DIR"/args ];
then
  . "$DIR"/args
fi

echo "$ARGS"
/usr/local/bin/mplayer -v -ao alsa:device=iec958 -afm hwac3 -alang eng -sws 0 -lircconf /home/mythtv/.mythtv/lircrc -fs -zoom -nocorrect-pts -autosync 30 "$ARGS" "$1"

```

The args file in the video directory...

```
ARGS="-sid 1"
```


I can see the ARGS var getting set with the echo command. If I add "echo" to the beginning of the mplayer command line, it echos out the right command. When I run it, I get:

```
Unknown option on the command line: -sid 1
Error parsing option on the command line: -sid 1

```

---

