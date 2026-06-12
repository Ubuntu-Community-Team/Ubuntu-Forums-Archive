---
title: "[SOLVED] streamripper cron bash script file"
date: 2008-10-19
forum: Multimedia Software
---

### Post by ajgreeny on 2008-10-19
I have tried to run a script file using cron which works fine if I run it manually, but with cron it will run only for a matter of seconds and then the rip stops.  I am trying to timer record ClassicFM radio shows in UK for my own use, but have to be here to do it as cron lets me down everytime; it starts and just stops after only seconds.  I have different versions of the script to run for different lengths, all of which are fine run manually

The script file is :-
```
#!/bin/bash
streamripper http://media-ice.musicradio.com:80/ClassicMP3 -t -d /home/andrew/Audio_recording/Radio -l 3600
```
Can anybody tell me why when using cron this will not record for an hour, as it does if I run it manually.

---

### Post by ajgreeny on 2008-10-28
Just a quick follow-up to this question.  My problem appeared to be related to using kcron to set the timing of this bash script.  I had not managed to get gnome-schedule to any commands at all in previous Ubuntu versions so tried kcron instead.  In the past I have never tried cron in the terminal, using ```
crontab -e
```but tried it after an answer in Linux Format magazine forums here in UK said it worked perfectly.  I must admit I found cron so easy to use I wonder why I didn't look at it before.  I also changed permissions of the script file to rw for user and none for all others as I read somewhere that this could possibly be a problem with user script files and cron.  Anyway all is well now, with everything working OK, and I can now record radio when not around.

I would still be very grateful for any ideas about the reasons for my problem previously - kcon in gnome?  permissions set wrongly for the script file?

---

