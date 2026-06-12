---
title: "cvlc script not running properly as cron job"
date: 2010-01-02
forum: Multimedia Software
---

### Post by MikeB23930 on 2010-01-02
I've written the following little script to record a streaming program from my local NPR station:

#!/bin/sh
cvlc -vvv "http://amber.streamguys.com:4500/wcvehd1.m3u"\
 --sout file/ogg:/home/mikeb/Audio_Recordings/Time4Blues"$(date +%F-%T)".ogg  &
pid=$!
sleep 300
kill -9 $pid

When I run it manually from a terminal, it does exactly what it is supposed to do.  That is, it quietly records five minutes of the the audio stream to a file in the folder Audio_Recordings and then dies, but when I run it with a cron job, it plays the stream for the prescribed five minutes and then dies without recording.  In other words, running as a cron job it appears to completely ignore the --sout option.  Can anyone tell me how to write a script that will correct record the steam when run as a cron job?

Thanks,

Mike

Edit:  The problem apparently was with gnome-scheduler which I had been using to schedule the cron job.  Once I manually entered the cron job using "crontab -e" my script ran perfectly.

---

### Post by mc4man on 2010-01-02
Not exactly sure but why with the .m3u ext., try losing it.

cvlc -vvv "http://amber.streamguys.com:4500/wcvehd1" --sout ....ect

( you really don't need the -vvv either

---

### Post by MikeB23930 on 2010-01-02
> **mc4man said:**
> Not exactly sure but why with the .m3u ext., try losing it.

cvlc -vvv "http://amber.streamguys.com:4500/wcvehd1" --sout ....ect

( you really don't need the -vvv either

Thanks for the quick reply, mc4man, but the behavior is exactly the same with as without the .m3u extension and without the -vvv flag.

---

### Post by mc4man on 2010-01-02
Well, went ahead and did as a cron, set to run at 5:15, worked fine.

(though, at least here the .m3u can't be in command, otherwise it outputs an empty file - tested that from both cli and alt+f2 earlier

So don't get while it's a no go for you, can only show particulars here

script stored in ~/bin (cvlv comm. on 1 line
```
#!/bin/sh
cvlc "http://amber.streamguys.com:4500/wcvehd1" --sout file/ogg:/home/doug/Audio_Recordings/Time4Blues"$(date +%F-%T)".ogg & pid=$!
sleep 300
kill -9 $pid
```

permissions - screen 1
output - screen 2

---

