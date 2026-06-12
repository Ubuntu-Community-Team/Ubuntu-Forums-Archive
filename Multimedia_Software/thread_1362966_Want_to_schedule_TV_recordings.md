---
title: "Want to schedule TV recordings"
date: 2009-12-23
forum: Multimedia Software
---

### Post by HappyFeet on 2009-12-23
I can watch TV just fine with vlc, and can record what I'm watching with a push of a button. However, I would like to schedule recordings via command line.

An example of how I can record (not scheduled) is:
First set channel:
```
ivtv-tune -c25
```
Then:
```
cat /dev/video0 > /home/user/tv_show.mpg
```
And the recording will show up in my home folder. I would like to be able to schedule recordings when I am not home though. Any idea where to start? And yes, I know I could use MythTV, but don't want to. I'd rather keep it CLI. Thanks ahead of time.

---

### Post by ttoilleb on 2009-12-23
Being new to Ubuntu I don't know all the tricks, but it seems to me some crontab entries would work.  1 set to start the recording and another to stop itl

---

### Post by HappyFeet on 2009-12-23
> **ttoilleb said:**
> Being new to Ubuntu I don't know all the tricks, but it seems to me some crontab entries would work.  1 set to start the recording and another to stop itl

It probably would work, but I've never done it before. I'll do some reading.

---

### Post by HappyFeet on 2009-12-23
OK. After a little reading, I came up with this:
```
crontab -e
```
```
35 23 23 12 05 cat /dev/video0 > /home/me/tv_show.mpg
```
which should record the show at 11:35 PM on Dec. 23
What about stopping the recording? What would the above look like?

---

### Post by HappyFeet on 2009-12-24
OK. I'm to the point where I can record tv with cron using:
```
34 00 24 12 05 cat /dev/video0 > /home/user/seinfeld.mpg
```
That's cool and it worked great, but I had to stop it manually. What do I add to it if I wanted it to stop at a certain time?

---

### Post by MeKino on 2009-12-24
I have a script which records using vlc so all I have to do is set the end time and use the killall command:

#TV
59 21 21 12 1 vlcrecord
01 23 21 12 1 killall vlc

---

### Post by rostube on 2009-12-24
> **HappyFeet said:**
> I can watch TV just fine with vlc, and can record what I'm watching with a push of a button. However, I would like to schedule recordings via command line.

An example of how I can record (not scheduled) is:
First set channel:
```
ivtv-tune -c25
```Then:
```
cat /dev/video0 > /home/user/tv_show.mpg
```And the recording will show up in my home folder. I would like to be able to schedule recordings when I am not home though. Any idea where to start? And yes, I know I could use MythTV, but don't want to. I'd rather keep it CLI. Thanks ahead of time.


please help me i am amateur how  to install this application?

---

### Post by MeKino on 2009-12-24
The folowing link shows how I set up vlc to record.


[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

but my new vlcrecord script is now attached and records approx 1.4GB per hour in good quality.

---

### Post by HappyFeet on 2009-12-24
> **rostube said:**
> please help me i am amateur how  to install this application?

It is not an application, just run those commands in the terminal.

---

### Post by HappyFeet on 2009-12-24
> **MeKino said:**
> I have a script which records using vlc so all I have to do is set the end time and use the killall command:

#TV
59 21 21 12 1 vlcrecord
01 23 21 12 1 killall vlc

How does it know what to record? Does vlc have to be on with tv running when this script is running?

Btw, thank you for your help. I don't want to run mythtv to be able to record.

---

### Post by MeKino on 2009-12-24
I don't use mythtv - I could never figure out how to get it working!

I have cable tv which plugs into a video capture card. When the script is called it records whatever channel is on at the time.

It would be possible to connect to an aerial instead. In which case you would need to determine the channel frequencies, etc. see the link in my previous post for details. You would then have to modify the script to include the channel frequency. In effect, having a seperate script for each channel.

All you would need to do then is to set the recording times with cron.

vlc only runs when the script is called and is closed afterwards.

---

### Post by HappyFeet on 2009-12-24
Well, I did it. Here's how in case someone may find it useful:

First change channel to what I want, let's say channel 25
```
ivtv-tune -c25
```
Then
```
crontab -e
```
Then, as an example of recording from 3:00 PM to 3:30 PM today
In crontab:
**00 15 24 12 05 cat /dev/video0 > /home/user/tv_show.mpg**
**30 15 24 12 05 killall cat**
Minimize terminal window so channel stays on 25.

I guess there's more than one way to skin a cat, eh?

Btw, I have never had a problem with MythTV, I just want to simplify things and go old school. It seems ridiculous to install all of that, when I just want to schedule recordings.

Also, CSMonkeyRemote is the name of the utility to change channels for PVR users. My signal is coming directly from the physical cable, and not the cable box, so I have to change channels on the computer.

I appreciate your help a lot, and have a happy holiday.

---

### Post by saedelaere on 2009-12-27
[TV-Viewer]("http://ubuntuforums.org/showthread.php?t=763698&page=14") also supports scheduled recordings for your device...

---

