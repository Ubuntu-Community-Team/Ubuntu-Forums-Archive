---
title: "Record dvb-t at night"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by letex on 2007-03-26
Hello!!
I'm using a Ubuntu linux and running Mplayer with a dvb-T USB CARD
The USB CArd works correctly and I can use the tools scan, dvbstream, etc....

I want to record my favorite dvb-t channels and I found in docs the way to do it:

mplayer -dumpfile r1.ts -dumpstream dvb://CHANNEL

Or in avi file:

mencoder -o r1.avi -ovc xvid -xvidencopts bitrate=800 -oac mp3lame -lameopts cbr:br=128 -pp=ci dvb://CHANNEL

The second doesn't work, but it isn't the problem, the problem is that I want to do this record at night, programing it with cron or at

My question is that I can't found a way to do a  record with mplayer of a determined duration, as 50 minutes.

I've being searching and I found and way to do this for recording audio with mims, which supports this option:

and if this option isn't available; I've thougth doing a script and launch it with cron, but how can i stop it after a determined duration??

Thanks in advance.

NOTE: I'm not very experienced in Linux and, at least, sorry for not very correct english....I hope you understand it!!


Bye!!

---

### Post by simonn on 2007-03-26
You need to use the parameter -endpos. Check out the mplayer documentation. For example the following records for 1 hour (well, 3600 seconds to be precise):

```

mencoder -o r1.avi -endpos 3600 -ovc xvid -xvidencopts bitrate=800 -oac mp3lame -lameopts cbr:br=128 -pp=ci dvb://CHANNEL

```

I suspect the reason why the mencoder line does not work via cron or at (assuming it works if you use it striaght from the command line) is that you have not specified a destination directory e.g:

```

mencoder -o /path/to/dir/r1.avi -ovc xvid -xvidencopts bitrate=800 -oac mp3lame -lameopts cbr:br=128 -pp=ci dvb://CHANNEL

```

FWIW, a brain dump... I use the following script:

```

#!/bin/bash
mencoder dvb://"$1" -idx -oac copy -ovc copy -endpos "$2" -o "$3"/"$1-`date +'%F %T'`".avi > /tmp/"$1".log &2>1

```

Parameter 1 is the channel
Parameter 2 is the endpos
Parameter 3 is the directory to record into - the file name is the is CHANNEL-DATE.
It also creates a log file (/tmp/CHANNEL.log) for debugging purposes. 
No transcoding takes place (-oac and -ovc copy) so there is minimal CPU usage. If I want to keep the recording I transcode afterwards - if transcoding cannot keep up with the broadcast the recording may fail.

For one off recordings at a specific time, where script = whatever the script is called):

echo "script [channel] [endpos] [dir]"  | at [timespec]

Look at the at man pages for more details of the timespec param.

---

### Post by letex on 2007-03-27
Thank you very much.

I was not able to find out any option command in the mplayer docs.

I'll test it today!!!!

---

