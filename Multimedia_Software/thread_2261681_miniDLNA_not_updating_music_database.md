---
title: "miniDLNA not updating music database"
date: 2015-01-20
forum: Multimedia Software
---

### Post by percy4209 on 2015-01-20
[COLOR=#000000][FONT=verdana]I am having trouble with miniDLNA not updating my music database. My video folders update no problem. My initial music that I had on my Ubuntu 14.04 box before installing miniDLNA shows up fine, but the music that I recently transferred from my Windows 7 machine to my music folder which is supposedly scanned by miniDLNA does not show up when I connect to the server on my Android phone with an app called BubbleUPnP, nor does it show up when I connect with Kodi 14 on the Windows 7 machine. For some reason the initial music I had will show up without problem. The music I added is all in MP3 format. I have tried to manually update the DB by using the command: 'sudo service minidlna force-reload' in the terminal to no avail. I have restarted the service multiple times and even restarted the PC. There are no errors pertaining to this in the log file, but I can link that if it will help. Any help would be just fantastic. [/FONT][/COLOR]

---

### Post by percy4209 on 2015-01-20
Here is a link to my minidlna.log in case it is of any help. [https://www.dropbox.com/s/s9kabqbus5ak196/minidlna.log?dl=0](https://www.dropbox.com/s/s9kabqbus5ak196/minidlna.log?dl=0)

---

### Post by Nutria on 2015-01-24
> **percy4209 said:**
> [COLOR=#000000][FONT=verdana]I am having trouble with miniDLNA not updating my music database. My video folders update no problem. My initial music that I had on my Ubuntu 14.04 box before installing miniDLNA shows up fine

I've had similar problems with video files.

> I have tried to manually update the DB by using the command: 'sudo service minidlna force-reload' in the terminal to no avail. I have restarted the service multiple times and even restarted the PC. There are no errors pertaining to this in the log file, but I can link that if it will help. Any help would be just fantastic.

That does not recreate the db.

First thing is to edit /etc/init.d/minidlna and add "[FONT=Courier New] -v[/FONT]" to the ARGS variable.  (Line 24 in my version of the file.)
```
ARGS="-f $CONF** -v**"
```

Then:
```
sudo service minidlna stop
sudo minidlna -Rv

```

Depending on how many files you have, and the speed of your machine, that might take a couple of hours.  **Note** that "sudo minidlna -Rv" **instantly** returns to the $ prompt.  (That scared the poop out of me the first time that happened, and caused no amount of wasted time searching for non-existent problems.  Tail the minidlna log file (on my system, it is /var/log/minidlna.log) to see that it is actually doing something.)

I don't remember if you have to do "sudo service minidlna start" after the db is rebuilt.

---

