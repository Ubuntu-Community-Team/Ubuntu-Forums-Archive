---
title: "Linux alternative for Replay A/V?"
date: 2010-05-06
forum: Multimedia Software
---

### Post by primetime34 on 2010-05-06
Is there some sort of Linux alternative for Replay A/V?  It's a program that will let me record a certain internet radio station on a schedule.  Let me know if there is something.  It works through Wine but I would prefer to do something natively.  Thanks.

---

### Post by primetime34 on 2010-05-07
Okay, let me be more specific.  I want to record the following online radio station [http://affiliates.foxnewsradio.com/Radio/player.html](http://affiliates.foxnewsradio.com/Radio/player.html) every weekday from 7-8pm.  I was using replay a/v on windows to do that.  Any way to do this through Ubuntu?  I see there are some command line methods and scripts, etc but I'm not even sure what the actual stream address is for the above player.  Thanks. :D

---

### Post by primetime34 on 2010-05-09
bump

---

### Post by primetime34 on 2010-05-12
Anybody??

---

### Post by mc4man on 2010-05-12
> but I'm not even sure what the actual stream address is for the above player.
The url. is 
```
mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137
```

Many ways to do - only have a few min. so here is a thread for one way that you could adapt for what you wish
[http://ubuntuforums.org/showthread.php?t=1359656](http://ubuntuforums.org/showthread.php?t=1359656)

If so (record with vlc, schedule with cron) first test vlc by in a terminal 
vlc [COLOR="Blue"]< space>[/COLOR] paste url above

If making the script this should do - replace blue with your username (you can save elsewhere by adding path  - Ex.
/home/doug/streams/

```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137 --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/[COLOR="Blue"]doug[/COLOR]/fox-$NOW.wma}" vlc://quit ;


```

your cron schedule would be something like this (if script is in your home dir. and named recordmyshow.sh 

```
00 19 * * * /home/[COLOR="Blue"]<username>[/COLOR]/recordmyshow.sh
```


=====================================================
> .---------------- minute (0 - 59) 
|  .------------- hour (0 - 23)
|  |  .---------- day of month (1 - 31)
|  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
|  |  |  |  .---- day of week (0 - 7) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu,fri,sat 
|  |  |  |  |
*  *  *  *  *  command to be executed


---

### Post by primetime34 on 2010-05-12
Fantastic!!  Two questions.  Is there a way to have it record to mp3 instead of wma?  Also, if I want to record from 7-8 every weekday, should the kron add look like this:

00 19 * * 1-5 /home/[COLOR=Blue]<username>[/COLOR]/recordmyshow.sh
Thank you so much!!

---

### Post by mc4man on 2010-05-13
> the kron add look like this:
yeah, that looks right - I misread your post as every day (7 days)

I don't use vlc to transcode streams very often, usually just to record.

Maybe give this a try for your sout 
(The orig. stream is wma2 64k 48 HZ - if you need 44.1 HZ I guess it could be worked in, otherwise I'd just record (copy) and convert later - many ways from gui's to batch same name convert commands - easy stuff there

```
--sout "#transcode{acodec=mp3}:duplicate{dst=std{access=file,mux=raw,dst=/home/[COLOR="Blue"]username[/COLOR]/fox-$NOW.mp3}"

```

---

### Post by primetime34 on 2010-05-13
Okay...so how would I do the transcoding automatically via batch?  Sorry for being so dense but I'm really new to all this.  Thanks.

---

### Post by mc4man on 2010-05-13
Not sure what you're asking here - have tested this and while I do a bit differently from the linked post works fine.

So atm, keeping to how the link suggests a script to mp3 keeping the orig. samplerate using default parameters

(one small change - made a folder in home to hold them named 'foxstreams', adjust blue as needed

```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137 --sout "#transcode{acodec=mp3}:duplicate{dst=std{access=file,mux=raw,dst=/home/[COLOR="Blue"]doug/foxstreams/[/COLOR]fox-$NOW.mp3}" vlc://quit ;

```

Or to change the samplerate - lame commands go inside the { }, added a few to show how
```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137 --sout "#transcode{acodec=mp3,channels=2,ab=128,samplerate=44100}:duplicate{dst=std{access=file,mux=raw,dst=/home/[COLOR="Blue"]doug/foxstreams/[/COLOR]fox-$NOW.mp3}" vlc://quit ;

```

(you can test your script at any time by opening a terminal and entering /path/to/scriptname, exit it with Ctrl+c

For cron use nano  - easier to figure out
======================================================================

If you still need a complete step-by I'll show you my method - later tonight - mention what your normal text editor is (gedit here), and what you want - orig. wma, mp3, or a resampled mp3
And are you on ubuntu or kubuntu

The 'batch convert' would only be used on streams already copied that you waqnted to convert to something else - not needed if you pick the script that suits your needs

---

### Post by primetime34 on 2010-05-13
Your last post made good sense.  I just used the mp3 script instead of the wma script.  Tested it and things work just fine.  Thank you so much for your help.  This community and os rock!!

---

### Post by primetime34 on 2010-05-14
Okay, thought I had this all figured out but when I just rip the stream to mp3 the resultant file is too big for what I need it to do.  Instead of being at 128 bitrate, I would like it to be 64 or even 32 (it is a talkshow so quality isn't a huge deal).  I tried the transcode script up above but I don't get anything on the output as far as listenable mp3.  I get an mp3, but there is no audio contained in the file.  Any help?  You've been very helpful so far and I really appreciate it. :D

---

### Post by mc4man on 2010-05-14
Maybe going back and forth from this thread to the other... though on one had you said it tested fine and now your mp3 has no sound..?
So here's what I'd do to use vlc for this.

(Maybe remove any previous scripts, folders, ect. and start fresh.

First I's use a ~/bin to hold the script(s) so,

```
mkdir bin
```
Then restart and it should have been added to tour path, to check rin this, look for blue (your user name
> doug@doug-desktop:~$ $PATH
bash: [COLOR="Blue"]/home/doug/bin[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory


If good then open a terminal and make sure vlc can play the stream without issue and or dropping - let it run a bit
```
vlc mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137

```

If ok make a folder to hold streams 
```
mkdir foxstreams
```

Then ( am using gedit, if on kubuntu - you didn't say, substitute your default text editor

```
touch ~/bin/recordfox1 && gedit ~/bin/recordfox1
```

copy and paste this in (after pasting in change blue to your username, red is ajustable
```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137 --sout "#transcode{acodec=mp3,channels=2,ab=[COLOR="Red"]64[/COLOR],samplerate=44100}:duplicate{dst=std{access=file,mux=raw,dst=/home/[COLOR="Blue"]doug[/COLOR]/foxstreams/fox-$NOW.mp3}" vlc://quit ;
```

Then 
```
chmod u+x ~/bin/recordfox1

```

To test open a terminal, enter this, wait a min or so Ctrl+c to exit and see if the .mp3 is playable and seekable (is here
```
recordfox1
```

=================================================
if you want to test recording as is then simply
```
touch ~/bin/recordfox2 && gedit ~/bin/recordfox2
```
C+P this
```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137 --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/[COLOR="Blue"]doug[/COLOR]/foxstreams/fox-$NOW.wma}" vlc://quit ;
```
save and exit text editor then
```
chmod u+x ~/bin/recordfox2
```

To test - in terminal
```
recordfox2
```

---

### Post by primetime34 on 2010-05-15
The transcode script works great.  I am so new to this so I really, really appreciate it!!

---

