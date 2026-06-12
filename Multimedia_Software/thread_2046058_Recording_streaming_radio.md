---
title: "Recording streaming radio"
date: 2012-08-22
forum: Multimedia Software
---

### Post by wildtiger23 on 2012-08-22
I trying to record two internet radio with avconv at 5:30am for 4 hours every week day.

A wrote a script than add it to the /etc/crontab file

my crontab look like this :

30 5	* * 1-5	sandrine	/home/sandrine/Radio_internet/radiorecmatin.sh

and my command with avconv look like this :

avconv -loglevel quiet -i [http://stream.radiox.com/cklx.mp3](http://stream.radiox.com/cklx.mp3) -id3v2_version 3 -write_id3v1 1 -f mp3 -acodec libmp3lame -ab 32k -metadata title="$TITLE1" -metadata artist="$ARTIST1" -metadata album="$ALBUM1" -metadata year="$YEAR" -metadata date="$DATE" -ac 1 -t 4:00:00 $FILENAME1 &

the problem is : If a run it manually with a duration of 1 minute, the command stop perfectly, but in my script with 4 hours it doesn't stop. I add to kill the process.

---

### Post by ajgreeny on 2012-08-22
I do not know avconv at all at the moment, but I gather it needs some slightly different syntax to ffmpeg.

However, instead of using the syntax you have at the end>  -t 4:00:00 $FILENAME1 &have you tried using  -t 240m (240 minutes) if that is an acceptable way to define time duration as it is in, for example, streamripper, which I do use.  I may be talking out my backside and have no way to try this myself on 10.04.

Alternatively you could add a  ```
sleep 240m; killall avconv
```after the & at the end of your script, as I do when timer recording with mplayer using cron.

---

### Post by wildtiger23 on 2012-08-22
avconv accept duration in seconds or following this form hh:mm:ss[.xxx]

I thing I'll try with the sleep and killall command.

Thank you

---

### Post by wildtiger23 on 2012-08-23
Thank it work perfectly. Now I need to find a way to add a cover art to the mp3.

---

### Post by shantiq on 2012-08-24
use easytag or puddletag to add art to mp3   [both in repo]


with puddletag highlight dragged track into program then pick edit/extended tags   and +

---

### Post by mocha on 2012-08-25
Just wondering why are you using avconv to convert an mp3 stream to another transcoded mp3 file?  Why not just use a command like:

```
mplayer -cache 1024 -dumpstream http://stream.radiox.com/cklx.mp3 -dumpfile output.mp3
```

You can then integrate this into a script like this and call it from a cron job:

```
#!/bin/bash
DATE=$(date +"%b-%d-%y")
STREAM=http://stream.radiox.com/cklx.mp3
DURATION=2h
MUSIC_DIR=$HOME/Recordings

cd $MUSIC_DIR

mplayer -cache 1024 -dumpstream http://stream.radiox.com/cklx.mp3 -dumpfile $DATE.mp3 &

sleep $DURATION 
kill $!

```

---

