---
title: "Mythtv idle shutdown"
date: 2008-02-14
forum: Mythbuntu
---

### Post by spylvas on 2008-02-14
Hi,

I moved this thread here because somebody was posting this a bit wrong forum :)
[http://ubuntuforums.org/showthread.php?t=695444](http://ubuntuforums.org/showthread.php?t=695444)

So I did proposed changes, but end result was that my backend never shutdown...

script I am using for checking if I am logged in is this:

#!/bin/sh

if [ "`users`" ]
then
  exit 1
else
   exit 0
fi

so for some reason it seems to think I am logged in even if I have I logged out there should be any users!

---

### Post by oscarsfriend on 2008-02-14
Hi,

Try running the following instead.  Log out, wait long enough for it to run, then if it doesn't shutdown, login and post the contents of /tmp/mythshutdowncheck.log (if it exists, if not let me know).

```

#!/bin/sh

echo -n "`date`: mythshutdowncheck: " >> /tmp/mythshutdowncheck.log

if [ "`users`" ]
then
   echo "`users` still logged on. Not shutting down." >> /tmp/mythshutdowncheck.log
   exit 1
else
   echo "shutting down now!" >> /tmp/mythshutdowncheck.log
   exit 0
fi

```

The script is the same as above, but just logs some information for debugging purposes.

---

### Post by spylvas on 2008-02-17
It\s looks like script is working alright. Problem seems to be that it isn't called time to time. Last time this morning.

Here is what I can see from backend logs:

2008-02-17 09:12:14.963 Using runtime prefix = /usr
2008-02-17 09:12:15.437 New DB connection, total: 1
2008-02-17 09:12:15.446 Connected to database 'mythconverg' at host: localhost
2008-02-17 09:12:15.545 Current Schema Version: 1160
Starting up as the master server.
2008-02-17 09:12:15.643 New DB connection, total: 2
2008-02-17 09:12:15.648 Connected to database 'mythconverg' at host: localhost
2008-02-17 09:12:15.673 EITHelper: localtime offset -8:00:00 
2008-02-17 09:12:15.782 New DB connection, total: 3
2008-02-17 09:12:15.784 Connected to database 'mythconverg' at host: localhost
2008-02-17 09:12:16.028 New DB scheduler connection
2008-02-17 09:12:16.031 Connected to database 'mythconverg' at host: localhost
2008-02-17 09:12:16.158 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-17 09:12:16.963 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-17 09:12:18.447 Reschedule requested for id -1.
2008-02-17 09:12:19.191 Main::Registering HttpStatus Extension
2008-02-17 09:12:19.219 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-17 09:12:20.162 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-17 09:12:22.979 Enabled verbose msgs:  important general
2008-02-17 09:12:23.773 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-17 09:12:24.018 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-17 09:12:33.813 Scheduled 129 items in 15.4 = 13.57 match + 1.79 place
2008-02-17 09:12:33.828 Seem to be woken up by USER

So last entry is more than two hours ago and it doesn't seem to go idle at all.

---

### Post by Kelly A on 2008-03-03
I've been having the same problem. I admit that I'm a beginner at this, and it took me a while to figure out that I needed to exit the front end to enable a shutdown. However, it still didn't do it even though I had an "exit 0" in the shutdown check.

I finally figured out that something was messed up with one of my tuner cards. I deleted all capture devices and video sources, and started over with the simplest configuration I could do. I reran the mythfilldatabase and the shutdown seemed to start working. Seems reliable now. Maybe the backend won't go idle when it's not satisfied with the capture card and/or database.

Just a thought.

---

### Post by Kelly A on 2008-03-03
Sorry, I seem to have spoken prematurely. After shutting itself down then waking to record several times, I turned in on manually and it no longer shuts down. I'll let you know if I find out anything more.

---

### Post by majoridiot on 2008-03-04
> **Kelly A said:**
> Sorry, I seem to have spoken prematurely. After shutting itself down then waking to record several times, I turned in on manually and it no longer shuts down. I'll let you know if I find out anything more.

in mythtv-setup, under General-->Shutdown and Wake-up Options, make sure that the box for
**block shutdown before client connected** is ***unticked***.

this will allow your backend to shutdown, regardless of whether or not a frontend has ever connected.

---

### Post by Kelly A on 2008-03-08
Thank you, I think that made the difference! I must have been through that screen a hundred times and never noticed that checkbox. 
Also, thanks  for writing the guide. I couldn't have done it without.

BTW, my MB is an Intel D845PESV and doesn't need the power off kernel.

On a side note, March 3rd probably isn't the day to figure out the order of month-day on the RTC.. doh!

---

### Post by majoridiot on 2008-03-08
> **Kelly A said:**
> Thank you, I think that made the difference! I must have been through that screen a hundred times and never noticed that checkbox. 

there's so much config info on so many different screens, it's easy to overlook things. ;)

> **Kelly A said:**
> Also, thanks  for writing the guide. I couldn't have done it without.

glad you found it useful and got your backend waking up properly!

> **Kelly A said:**
> BTW, my MB is an Intel D845PESV and doesn't need the power off kernel.

i added it to the list in the guide for you.

> **Kelly A said:**
> On a side note, March 3rd probably isn't the day to figure out the order of month-day on the RTC.. doh!

hehe... fortunately there are only 12 days a year like that.

---

