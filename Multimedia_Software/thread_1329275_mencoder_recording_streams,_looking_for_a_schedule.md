---
title: "mencoder recording streams, looking for a scheduler and more"
date: 2009-11-17
forum: Multimedia Software
---

### Post by sdowney717 on 2009-11-17
i have figured out some recording of both internet streams, devices like a capture card and endtimes so it will stop after a certain time and including transcoding to mp3 audio and divx video

for example this one reords for 1 minute off the device /dev/video0
> mencoder /dev/video0 -o /home/scott/Videos/test2.m4v  -endpos 00:01:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

> 

this works, gets the stream and transcodes it
[QUOTE]mencoder [http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v](http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v) -o /home/scott/Videos/test.m4v  -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame
 
his works, gets the stream and transcodes it and records only 1 minute of video
> mencoder [http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v](http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v) -o /home/scott/Videos/test.m4v  -endpos 00:01:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

What i would like to do is schedule the starting of the command line 
mencoder at various times and I would like to change the output file name to include perhaps the time and date of the recording, so output -o
would have to be a variable like date time, $

>  mencoder /dev/video0 -o /home/scott/Videos/date  -endpos 00:01:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

but it will just call it 'date'

so what is a system variable name for date?
any ideas about the scheduler and the name? it might be nice to also use part of the http stream name when recording http video

---

### Post by sdowney717 on 2009-11-17
i found a program called alarm-clock which lets me run a command line instruction at a certain time and has a bunch of option on how to start.

---

### Post by xzero1 on 2009-11-17
Everything you need to do can be done via a bash script. It takes a bit of effort to learn how to use bash effectively,  but it should be worth the effort. As an example, see my recording script here: [http://ubuntuforums.org/showthread.php?t=1169204]("http://ubuntuforums.org/showthread.php?t=1169204")

This is a general script and can probably be adapted for your use. To get the date/time simply redirect the command "date".

---

### Post by sdowney717 on 2009-11-17
interesting script, it saves to a transport stream?
however getting an error, i assume the -v 0 would be for my /dev/video0?

scott@scott-desktop:~$ ./tr.sh -t 0:04 -b 14 -v 0 test.ts
MAX BITRATE SET
./tr.sh: line 49: v4l2-ctl: command not found
./tr.sh: line 51: v4l2-ctl: command not found
4


Done    time left      avg bps           est size          cur size
^C
scott@scott-desktop:~$

---

### Post by xzero1 on 2009-11-17
> **sdowney717 said:**
> interesting script, it saves to a transport stream?
however getting an error, i assume the -v 0 would be for my /dev/video0?

scott@scott-desktop:~$ ./tr.sh -t 0:04 -b 14 -v 0 test.ts
MAX BITRATE SET
./tr.sh: line 49: v4l2-ctl: command not found
./tr.sh: line 51: v4l2-ctl: command not found
4


Done    time left      avg bps           est size          cur size
^C
scott@scott-desktop:~$

You cannot use this script as is. It is dependent on specific hardware. To use it, you must learn a bit about scripting, then edit out or modify the hardware references. The script merely sets up hardware and parameters for running the "executable" line and monitoring its results. Aside from the monitoring you can write a much simpler script to do what you need. My hardware creates a ".ts" file and -v 0 is expanded by the script to /dev/video0.

---

### Post by andrew.46 on 2009-11-17
Hi sdowney,

> **sdowney717 said:**
> I would like to change the output file name to include perhaps the time and date of the recording, so output -o
would have to be a variable like date time, $

Perhaps something simple like:

```
-o $(date +%d%m%Y).avi
```

might be enough?

Andrew

---

### Post by sdowney717 on 2009-11-17
that works, how can you add in the time?


if i create an mpeg recording using VLC, VLC will name the file like so (advanced controls click red record button)

vlc-record-2009-09-27-13h30m09s-v4l2:__-.mpg

interesting this works too
$(date +%d%m%Y+%I-%M-%S)

[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)
this looks better and puts time in 24 hour clock
-o $(date +%m%d%Y+%kH-%Mm-%Ss).avi

$(date +%A-%m-%d-%Y+%kH-%Mm-%Ss) prints this

Tuesday-11-17-2009+18H-16m-13s

this one puts it into your home/Videos folder
mencoder /dev/video0 -o $HOME/Videos/$(date +%A-%p-%m-%d-%Y+%T).avi -endpos 00:00:10 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

---

### Post by andrew.46 on 2009-11-17
Hi sdowney717,

Looks like you have already seen that there are many, many variations on the date syntax that will generate files that should suit you :). The man pages give the following possible formats:

```

 FORMAT controls the output.  Interpreted sequences are:

       %%     a literal %

       %a     locale's abbreviated weekday name (e.g., Sun)

       %A     locale's full weekday name (e.g., Sunday)

       %b     locale's abbreviated month name (e.g., Jan)

       %B     locale's full month name (e.g., January)

       %c     locale's date and time (e.g., Thu Mar  3 23:05:25 2005)

       %C     century; like %Y, except omit last two digits (e.g., 20)

       %d     day of month (e.g, 01)

       %D     date; same as %m/%d/%y

       %e     day of month, space padded; same as %_d

       %F     full date; same as %Y-%m-%d

       %g     last two digits of year of ISO week number (see %G)
       
       %G     year of ISO week number (see %V); normally useful only with %V

       %h     same as %b

       %H     hour (00..23)

       %I     hour (01..12)

       %j     day of year (001..366)

       %k     hour ( 0..23)

       %l     hour ( 1..12)

       %m     month (01..12)

       %M     minute (00..59)

       %n     a newline

       %N     nanoseconds (000000000..999999999)

       %p     locale's equivalent of either AM or PM; blank if not known

       %P     like %p, but lower case

       %r     locale's 12-hour clock time (e.g., 11:11:04 PM)

       %R     24-hour hour and minute; same as %H:%M

       %s     seconds since 1970-01-01 00:00:00 UTC

       %S     second (00..60)

       %t     a tab

       %T     time; same as %H:%M:%S

       %u     day of week (1..7); 1 is Monday

       %U     week number of year, with Sunday as first day of week (00..53)

       %V     ISO week number, with Monday as first day of week (01..53)

       %w     day of week (0..6); 0 is Sunday

       %W     week number of year, with Monday as first day of week (00..53)

       %x     locale's date representation (e.g., 12/31/99)

       %X     locale's time representation (e.g., 23:13:48)

       %y     last two digits of year (00..99)

       %Y     year

       %z     +hhmm numeric timezone (e.g., -0400)

       %:z    +hh:mm numeric timezone (e.g., -04:00)

       %::z   +hh:mm:ss numeric time zone (e.g., -04:00:00)

       %:::z  numeric  time  zone  with  :  to necessary precision (e.g., -04,
              +05:30)

       %Z     alphabetic time zone abbreviation (e.g., EDT)

```

So there is plenty of scope for experimentation :).

Andrew

---

