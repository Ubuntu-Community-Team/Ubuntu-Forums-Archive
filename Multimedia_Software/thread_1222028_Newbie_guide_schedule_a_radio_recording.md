---
title: "Newbie guide: schedule a radio recording"
date: 2009-07-24
forum: Multimedia Software
---

### Post by KingNeil on 2009-07-24
Let's say you have a favorite radio show that you want to record, but it's on too late or while you're at work, or whatever. Well, here's what you do.

1. sudo apt-get install streamripper
2. sudo apt-get install gnome-schedule

3. start up Scheduled Tasks (under Applications > System Tools, or Terminal: gnone-schedule)
4. set up the time schedule you want to perform the job
5. for the "command" field, enter "streamripper URLofRADIOstreamHERE"

If you want it to stop recording after a certain number of seconds (maybe if you want to save hard drive space), enter "-l numberofsecondshere" after the previous command, e.g. "streamripper [http://radioshow.com/](http://radioshow.com/) -l 200" would record radioshow.com for 200 seconds.

Recordings are saved in your Home directory.

That's it!

---

### Post by andrew.46 on 2009-07-25
Hi KingNeil,

There is also a commandline method:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

Andrew

---

### Post by KingNeil on 2009-07-25
yeah, mine is command line. it just uses streamripper, as opposed to mplayer, which your version uses.

---

