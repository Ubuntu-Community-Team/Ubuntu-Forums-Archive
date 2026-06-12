---
title: "mythexport fails"
date: 2009-11-16
forum: Mythbuntu
---

### Post by odror on 2009-11-16
When I set mythexport to create an ipod mp4 file

Nothing is done and I get the following error in the log file.
 
> /usr/bin/mythexport-daemon[8509]: ERROR: AtomicParsley '/tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork HSTRYHD --TVShowName "Ancient Discoveries" --TVEpisode "EP005804270038" --TVEpisodeNum  --TVSeason  --description "Ancient prototypes of the modern gun; an ancient manuscript has a recipe for tracer fire; mega-mortar; the bizarre "wind of the cannonball" phenomena." --title "Guns 'N Ammo" 2>&1 FAILED at line 514 in /usr/bin/mythexport-daemon
rm: cannot remove `/tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4': No such file or directory
mv: cannot stat `/tmp/mp4/*temp*': No such file or directory
November 15 20:56:03 moriel-1 /usr/bin/mythexport-daemon[8509]: ERROR: /tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4 is not available at line 521 in /usr/bin/mythexport-daemon

WHen I try to see why AtomicParsley fails. I get this error
> $ AtomicParsley '/tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork HSTRYHD --TVShowName "Ancient Discoveries" --TVEpisode "EP005804270038" --TVEpisodeNum  --TVSeason  --description "Ancient prototypes of the modern gun; an ancient manuscript has a recipe for tracer fire; mega-mortar; the bizarre "wind of the cannonball" phenomena." --title "Guns 'N Ammo"
AP error trying to fopen: No such file or directory
AtomicParsley error: can't open /tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4 for reading: No such file or directory

The directory /tmp/mp4 is readable and writable by anyone. This error is unexplained.

Any ideas how to find the case of the failure.

Thanks

---

### Post by mlgim on 2009-11-24
Hi

I get the same error. Did you find a fix?

Cheers!

---

### Post by rhpot1991 on 2009-11-30
Any chance you guys are attempting to remove commercials?  I'd recommend disabling that until you have a working setup first.

---

### Post by odror on 2009-11-30
No Just basic conversion to ipod format. No commercial removal

The input format is either HD in mpeg2 or
HD from the hdPVR h.264 format.

---

### Post by woodleyc on 2009-12-07
I get exactly the same - seems the mpg file isn't copied over for processing

---

### Post by jimm on 2009-12-13
Hi,

I have the same problem. I have a pretty standard MythBuntu install and I have tried to get mythexport working "out of the box" and I get this error.

I have poked around a bit, but I can't see why it fails like this. Has anyone had any luck fixing it?

If I get it working I'll write up a working config on the wiki... but right now its very frustrating! This looks like such a cool and promising feature, but it just doesnt want to work!

Thanks,
James

---

### Post by crez79 on 2009-12-20
It doesn't look like ffmopeg is working it's magic so there is no file for atomicparsley to work with. By chance is there a space in your config name? Try [this.]("https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/393492")

---

### Post by odror on 2009-12-20
can you be more specific. Which config file and where is it located.

Thanks

---

### Post by rhpot1991 on 2009-12-21
> **odror said:**
> can you be more specific. Which config file and where is it located.

Thanks

The file is located at:
/etc/mythtv/mythexport/mythexport_settings.cfg

Or you could use the web interface to modify the config name.

---

### Post by odror on 2009-12-21
> **crez79 said:**
> It doesn't look like ffmopeg is working it's magic so there is no file for atomicparsley to work with. By chance is there a space in your config name? Try [this.]("https://bugs.launchpad.net/ubuntu/+source/mythexport/+bug/393492")

I tried it. The problem is not solved. There is a new updated to ffmpeg. Will this fix the problem.

---

### Post by rhpot1991 on 2009-12-21
> **odror said:**
> I tried it. The problem is not solved. There is a new updated to ffmpeg. Will this fix the problem.

Follow the wiki to enable debugging, run your ffmpeg lines by hand and verify they work.

[https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)

---

### Post by crez79 on 2009-12-21
Depending on the arguments you have set for ffmpeg, you will need to update the argument to their current form. From what I have learned, ffmpeg had a habit of changing the arguments. The things I needed to change are : -me to -me_method, remove loop and slice and add -flags +loop+slice, check that vcodec is libx264 (if that is what you want), and remove part4 and 8 things and make it -partitions +parti4x4+partp8x8. Also, if you have -rc_eq 'blurCplx^(1-qComp)' you need to add backslashes (\) before the ' like this: -rc_eq \'blurCplx^(1-qComp)\' or mythexport will remove the quotes. 

Basically, you need to copy the ffmpeg command mythexport is trying to run and check the errors and fix them one at a time. I didn't enjoy it very much but I have learned much about ffmpeg. I am still working on the audio going out of sync... any suggestions on that issue are welcome.

Good luck.

---

### Post by owenlinx on 2010-01-08
Good news ffmpeg now includes presets. So in your settings.conf file add 

-acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 18 -s 720x480 -aspect 16:9 -threads 0 -deinterlace

or something simular. [See here for more info.]("http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/")

But mythexport is failing for me also, but after ffmpeg runs. 

[http://paste.ubuntu.com/353586/]("http://paste.ubuntu.com/353586/")
[http://paste.ubuntu.com/353588/]("http://paste.ubuntu.com/353588/")
I have run table repair & optimizations in myth, but to no avail. Any ideas would be much appreciated.

Thanks Justin

---

### Post by rhpot1991 on 2010-01-08
> **owenlinx said:**
> Good news ffmpeg now includes presets. So in your settings.conf file add 

-acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 18 -s 720x480 -aspect 16:9 -threads 0 -deinterlace

or something simular. [See here for more info.]("http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/")

But mythexport is failing for me also, but after ffmpeg runs. 

[http://paste.ubuntu.com/353586/]("http://paste.ubuntu.com/353586/")
[http://paste.ubuntu.com/353588/]("http://paste.ubuntu.com/353588/")
I have run table repair & optimizations in myth, but to no avail. Any ideas would be much appreciated.

Thanks Justin

This is rather troubling:
DBD::mysql::st execute failed: MySQL server has gone away at /usr/share/perl5/MythTV/StorageGroup.pm line 89.

Is your backend working correctly?  I would run all the repair and optimization db tools in mythweb, then restart the backend or the whole system and then try again.

---

### Post by owenlinx on 2010-01-09
>  odror ERROR: AtomicParsley '/tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork HSTRYHD --TVShowName "Ancient Discoveries" --TVEpisode "EP005804270038" --TVEpisodeNum --TVSeason --description "Ancient prototypes of the modern gun; an ancient manuscript has a recipe for tracer fire; mega-mortar; the bizarre "wind of the cannonball" phenomena." --title "Guns 'N Ammo" 2>&1 FAILED at line 514 in /usr/bin/mythexport-daemon
rm: cannot remove `/tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4': No such file or directory
mv: cannot stat `/tmp/mp4/*temp*': No such file or directory
November 15 20:56:03 moriel-1 /usr/bin/mythexport-daemon[8509]: ERROR: /tmp/mp4/HSTRYHD-Ancient_Discoveries-Guns_N_Ammo-20091112230100.mp4 is not available at line 521 in /usr/bin/mythexport-daemon
> me ERROR: AtomicParsley '/home/justin/Videos/---20100102010000.mp4' --genre "TV Shows" --stik "TV Show" --TVNetwork  --TVShowName "" --TVEpisode "" --TVEpisodeNum  --TVSeason  --description "" --title "" 2>&1 FAILED at line 507 in /usr/bin/mythexport-daemon
rm: cannot remove `/home/justin/Videos/---20100102010000.mp4': No such file or directory
mv: cannot stat `/home/justin/Videos/*temp*': No such file or directory

I believe we had the same error. Is this resolved for the original poster? RHPOT running the optimizations & repair in mythweb fixed the problem  after reboot. 

Thanks for the help.

---

### Post by owenlinx on 2010-01-11
I spoke too soon. It worked for 2 shows then stopped again. I will post the error logs to pastebin soon, but I am sure it was similar to the above. Encode the movie with ffmpeg, then atomicparsley errors killing my db? The bad thing is that sometimes it erases the completed video after the error. The good thing is that sometimes it doesn't:D

---

### Post by rhpot1991 on 2010-01-11
> **owenlinx said:**
> I spoke too soon. It worked for 2 shows then stopped again. I will post the error logs to pastebin soon, but I am sure it was similar to the above. Encode the movie with ffmpeg, then atomicparsley errors killing my db? The bad thing is that sometimes it erases the completed video after the error. The good thing is that sometimes it doesn't:D

Normally if you see AtomicParsley errors that means your ffmpeg failed and there was no resulting file for AP to run against.  The other common issues are the space config bug and if you use a file type that AtomicParsley doesn't like (wmv, etc).

As for the DB errors it would seem you have a larger issue.  Neither AtomicParsley or ffmpeg are going to crash your MySQL server.  Your hard drives aren't filling up are they (df -h)?

You should look at the wiki ([http://www.mythbuntu.org/wiki/MythExport](http://www.mythbuntu.org/wiki/MythExport)) and enable debugging, grab the ffmpeg lines for a few shows and run them by hand.  This will normally point out what your issue is.

---

