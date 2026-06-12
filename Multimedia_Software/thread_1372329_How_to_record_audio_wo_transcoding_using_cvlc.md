---
title: "How to record audio w/o transcoding using cvlc?"
date: 2010-01-04
forum: Multimedia Software
---

### Post by MikeB23930 on 2010-01-04
The command

cvlc --run-time 180 "http://amber.streamguys.com:4500/wcvehd1.m3u" --sout file/ogg:/home/mikeb/Audio_Recordings/WCVE-test"$(date +%F-%T)".ogg

will successfully record a stream from my local NPR station.  If I understand the messages that are printed to stdout when I run it, this transcodes the mp3 stream to an ogg file.  Since I am using this to timeshift a program that I otherwise would not be able to listen to, I would prefer simply to dump the stream in mp3 format without transcoding.  I tried changing "ogg" to "dump" but that produces an error about the --sout option.  Can someone tell me how to modify this command so that it simply dumps the incoming stream to a file in mp3 format?

Thanks,

Mike

---

### Post by HappyFeet on 2010-01-04
Have you tried:

cvlc --run-time 180 "http://amber.streamguys.com:4500/wcvehd1.m3u" --sout file/mp3:/home/mikeb/Audio_Recordings/WCVE-test"$(date +%F-%T)".mp3

??? Just a thought.

I realize you do not want to transcode, but soundconverter will do the job very quickly.

---

### Post by ajgreeny on 2010-01-04
Not sure if this will be any use to you, but you can record using mplayer without transcoding, and an mp3 stream will be dumped as an mp3 file.
**/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3**

I use that and streamtuner as well to record streams but do it with cron and a shell script in order to time recordings in the future when I'm not around the computer.  In streamtuner you can set the length of recording with the -l option, but for mplayer I have only found that possible with the addition of **sleep 60m; killall mplayer**

Example shell script:-
```
#!/bin/bash
/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3 &
sleep 60m; killall mplayer
```

---

### Post by MikeB23930 on 2010-01-04
> **HappyFeet said:**
> Have you tried:

cvlc --run-time 180 "http://amber.streamguys.com:4500/wcvehd1.m3u" --sout file/mp3:/home/mikeb/Audio_Recordings/WCVE-test"$(date +%F-%T)".mp3

??? Just a thought.

I realize you do not want to transcode, but soundconverter will do the job very quickly.

Thanks, HappyFeet.  Will try your suggestion.

Mike

---

### Post by MikeB23930 on 2010-01-04
> **ajgreeny said:**
> Not sure if this will be any use to you, but you can record using mplayer without transcoding, and an mp3 stream will be dumped as an mp3 file.
**/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3**

I use that and streamtuner as well to record streams but do it with cron and a shell script in order to time recordings in the future when I'm not around the computer.  In streamtuner you can set the length of recording with the -l option, but for mplayer I have only found that possible with the addition of **sleep 60m; killall mplayer**

Example shell script:-
```
#!/bin/bash
/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3 &
sleep 60m; killall mplayer
```

Thanks, ajgreeny.  Will give it a try.  By the way, I actually use this as a cron job in a shell script almost exactly like yours.

Mike

---

### Post by MikeB23930 on 2010-01-04
> **HappyFeet said:**
> Have you tried:

cvlc --run-time 180 "http://amber.streamguys.com:4500/wcvehd1.m3u" --sout file/mp3:/home/mikeb/Audio_Recordings/WCVE-test"$(date +%F-%T)".mp3

??? Just a thought.

I realize you do not want to transcode, but soundconverter will do the job very quickly.

This fails with error:

main mux error: no sout mux module matched "mp3"

I think this means vlc doesn't understand the "mp3" in the --sout option.

Thanks,

Mike

---

### Post by MikeB23930 on 2010-01-04
> **ajgreeny said:**
> Not sure if this will be any use to you, but you can record using mplayer without transcoding, and an mp3 stream will be dumped as an mp3 file.
**/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3**

I use that and streamtuner as well to record streams but do it with cron and a shell script in order to time recordings in the future when I'm not around the computer.  In streamtuner you can set the length of recording with the -l option, but for mplayer I have only found that possible with the addition of **sleep 60m; killall mplayer**

Example shell script:-
```
#!/bin/bash
/usr/bin/mplayer <URL> -dumpstream -dumpfile file.mp3 &
sleep 60m; killall mplayer
```

This failed with the following

"MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://amber.streamguys.com:4500/wcvehd1.m3u](http://amber.streamguys.com:4500/wcvehd1.m3u).
Resolving amber.streamguys.com for AF_INET6...
Couldn't resolve name for AF_INET6: amber.streamguys.com
Resolving amber.streamguys.com for AF_INET...
Connecting to server amber.streamguys.com[205.234.238.42]: 4500...
Cache size set to 320 KBytes


Exiting... (End of file)"

Thanks,

Mike

---

### Post by mc4man on 2010-01-04
basically 
cvlc -vv [http://amber.streamguys.com:4500/wcvehd1](http://amber.streamguys.com:4500/wcvehd1) --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/doug/radio1.mp3}"

see [here ]("http://ubuntuforums.org/showthread.php?t=1359656")for sout for mp3. alt. method to record, ect.

---

### Post by ajgreeny on 2010-01-04
I see your mp3 stream is a playlist (m3u) so I think you will need to add -playlist to the front of the URL

```
#!/bin/bash
/usr/bin/mplayer -playlist [http://amber.streamguys.com:4500/wcvehd1.m3u](http://amber.streamguys.com:4500/wcvehd1.m3u) -dumpstream -dumpfile file.mp3 &
sleep 60m; killall mplayer
```I have to do the same when I record from the BBC radio realplayer streams, but not most of the mp3 streams that I go to.

Give that a try.

---

