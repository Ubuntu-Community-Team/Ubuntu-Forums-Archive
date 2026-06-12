---
title: "Record video stream with script"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by josno on 2007-02-28
I'm trying to capture a video stream using a script. This is what I have so far:
```
#!/bin/bash

DONE="false"

echo `date +%F` `date +%R`": Started" >> /home/rayj/m6/log.txt
if [ ! -d /home/rayj/m6/`date +%Y` ]
then
	mkdir /home/rayj/m6/`date +%Y`
	chmod 777 /home/rayj/m6/`date +%Y`
fi

if [ ! -d /home/rayj/m6/`date +%Y`/`date +%B` ]
then
	mkdir /home/rayj/m6/`date +%Y`/`date +%B`
fi

if [ ! -f /home/rayj/m6/`date +%Y`/`date +%B`/`date +%d_%A`.asf ]
then
	echo `date +%F` `date +%R`": Trying to create "`date +%d_%A`".asf" >> /home/rayj/m6/log.txt
	mplayer32 -playlist http://www.m6.fr/content/video/info/asx/National12_00_`date +%d%m%y`.asx -dumpstream -dumpfile /home/rayj/m6/`date +%Y`//`date +%B`//`date +%d_%A`.asf
	DONE="true"

fi

FILESIZE=$(stat -c%s "/home/rayj/m6/"`date +%Y`"/"`date +%B`"/"`date +%d_%A`".asf")
if [ ! -f /home/rayj/m6/`date +%Y`/`date +%B`/`date +%d_%A`.asf ]
then
	echo `date +%F` `date +%R`": Could not create "`date +%d_%A`".asf" >> /home/rayj/m6/log.txt
elif [ $FILESIZE -lt 45000000 ]
then
	echo `date +%F` `date +%R`": File looks incomplete - re-doing." >> /home/rayj/m6/log.txt
	rm /home/rayj/m6/`date +%Y`/`date +%B`/`date +%d_%A`.asf
	mplayer32 -playlist http://www.m6.fr/content/video/info/asx/National12_00_`date +%d%m%y`.asx -dumpstream -dumpfile /home/rayj/m6/`date +%Y`//`date +%B`//`date +%d_%A`.asf
elif [ $DONE != "true" ]
then
	echo `date +%F` `date +%R`": "`date +%d_%A`".asf already exists" >> /home/rayj/m6/log.txt
fi

echo `date +%F` `date +%R`": Completed" >> /home/rayj/m6/log.txt
echo "" >> /home/rayj/m6/log.txt
```
This is run by cron every hour of every weekday, the crontab entry looking like this:
```
0 * * * 1,2,3,4,5 /home/rayj/m6/m6.sh
```
My problem is this: if I run the script in a terminal as me (i.e. not sudo) it works absolutely fine. However, when cron runs it, or if I run it from nautilus (not in a terminal window) it won't actually write the file. I'll get this in the log:
```
2007-02-28 22:00: Started
2007-02-28 22:00: Trying to create 28_Wednesday.asf
2007-02-28 22:16: Could not create 28_Wednesday.asf
2007-02-28 22:16: Completed
```
Sometimes it will have taken time between start and end, sometimes not, and both times no file will have been created. Does anyone have any ideas what's going wrong?

EDIT: Forgot to add, the folder it's writing to and the script both have 777 permissions

---

