---
title: "the default system player?"
date: 2011-01-31
forum: Multimedia Software
---

### Post by Alan87i on 2011-01-31
When I mouse over a wav file What plays it in 8.10 ?

I'm trying to write a small script that I can have another program run automatically. 

All I want the script to do is play a short .wav file on the system speaker just as it does when I mouse over it. 

I Used Mplayer on my old system but I reloaded with 8.10 and I don't want to upgrade because I'm running zoneminder and the version I like is not in the repos for the latest versions of Ubuntu. And The repo is dead for 8.10 so I cant easily install mplayer. 
Thanks for any help. 
Allan

---

### Post by mikewhatever on 2011-01-31
It's been a while since I used 8.10, but on Maverick, it's totem-audio-preview. Probably was the same back then.

---

### Post by Alan87i on 2011-01-31
That made it run and play manually 
Thanks 
Now I need to get the permissions right so www-data can execute the script. 
No luck so far.

---

### Post by Alan87i on 2011-01-31
I added some lines to my script to generate a log file each time it runs 
My script

#!/bin/bash
whoami >> /tmp/myscript.$$.log 2>&1
env >> /tmp/myscript.$$.log 2>&1
totem-audio-preview /ping.wav >> /tmp/myscript.$$.log 2>&1


The output of the log file. I'm lost at this point. 

www-data
APACHE_PID_FILE=/var/run/apache2.pid
APACHE_RUN_USER=www-data
PATH=/bin:/usr/bin
PWD=/var/cache/zoneminder/events
APACHE_RUN_GROUP=www-data
LANG=C
SHLVL=1
_=/usr/bin/env

(totem-audio-preview:13949): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstgnomevfs.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
couldn't parse command-line options: Error re-scanning registry , child terminated by signal

---

