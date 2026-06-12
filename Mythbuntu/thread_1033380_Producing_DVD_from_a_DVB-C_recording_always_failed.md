---
title: "Producing DVD from a DVB-C recording always failed; project- x failed to run"
date: 2009-01-07
forum: Mythbuntu
---

### Post by TVtalker on 2009-01-07
Hi everyone,

I tried to archive one of my dvb-c recordings. But everytime I'm doing this project-x failed or the whole computer crashes. Do you have any ideas what to do?

Here are the logs of my last try.

Thanks for helping!!

2009-01-07 15:59:02 mythburn.py (0.1.20080726-1-fixes) starting up...
2009-01-07 15:59:02 Found 2 CPUs
2009-01-07 15:59:02 Obtaining MythTV settings from MySQL database for hostname MythbuntuRecorder
2009-01-07 15:59:02 temppath: /home/detlef/Media/MythArchiv/work
2009-01-07 15:59:02 logpath:  /home/detlef/Media/MythArchiv/logs
2009-01-07 15:59:02 Setting process priority to 17
2009-01-07 15:59:02 Processing Mythburn job number 1.
2009-01-07 15:59:02 Options - mediatype = 3, doburn = 1, createiso = 0, erasedvdrw = 0
2009-01-07 15:59:02           savefilename = '/home/detlef/Media/MythArchiv/'
2009-01-07 15:59:02 Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
2009-01-07 15:59:02 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2009-01-07 15:59:02 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2009-01-07 15:59:02 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2009-01-07 15:59:02 wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
2009-01-07 15:59:02 Final DVD Video format will be pal
2009-01-07 15:59:02 There are 1 files to process
2009-01-07 15:59:03 Pre-processing recording 1: '/var/lib/mythtv/recordings/29224_20081015225500.mpg'
2009-01-07 15:59:03           Zapp
2009-01-07 15:59:03 Video resolution is 720 by 576
2009-01-07 15:59:03 *************************************************************
2009-01-07 15:59:03 Processing recording 1: '/var/lib/mythtv/recordings/29224_20081015225500.mpg'
2009-01-07 15:59:03 *************************************************************
2009-01-07 15:59:33 Preferred audio languages ger and eng
2009-01-07 15:59:33 Video id: 0xa29, Audio1: [1] 0xa2a (MP2, ger), Audio2: [2] - 0xa2b (MP2, 2ch)
2009-01-07 15:59:33 Using Project-X to demux file
2009-01-07 15:59:33 Preferred audio languages ger and eng
2009-01-07 15:59:33 Video id: 0xa29, Audio1: [1] 0xa2a (MP2, ger), Audio2: [2] - 0xa2b (MP2, 2ch)
2009-01-07 15:59:33 projectx -id 0xa29,0xa2a,0xa2b -out "/home/detlef/Media/MythArchiv/work/1" -name "29224_20081015225500" "/var/lib/mythtv/recordings/29224_20081015225500.mpg"
2009-01-07 15:59:33 Failed while running Project-X to cut commercials and/or demux an mpeg2 file.
Result: 127, Command was projectx -id 0xa29,0xa2a,0xa2b -out "/home/detlef/Media/MythArchiv/work/1" -name "29224_20081015225500" "/var/lib/mythtv/recordings/29224_20081015225500.mpg"
2009-01-07 15:59:33 ************************************************************
2009-01-07 15:59:33 ERROR: Failed to run Project-X to demux file
2009-01-07 15:59:33 ************************************************************
2009-01-07 15:59:33 
2009-01-07 15:59:33 Terminated

---

### Post by klc5555 on 2009-01-07
> **TVtalker said:**
> Hi everyone,

I tried to archive one of my dvb-c recordings. But everytime I'm doing this project-x failed or the whole computer crashes. Do you have any ideas what to do?

Here are the logs of my last try.

Thanks for helping!!

2009-01-07 15:59:02 mythburn.py (0.1.20080726-1-fixes) starting up...
2009-01-07 15:59:02 Found 2 CPUs
2009-01-07 15:59:02 Obtaining MythTV settings from MySQL database for hostname MythbuntuRecorder
2009-01-07 15:59:02 temppath: /home/detlef/Media/MythArchiv/work
2009-01-07 15:59:02 logpath:  /home/detlef/Media/MythArchiv/logs
2009-01-07 15:59:02 Setting process priority to 17
2009-01-07 15:59:02 Processing Mythburn job number 1.
2009-01-07 15:59:02 Options - mediatype = 3, doburn = 1, createiso = 0, erasedvdrw = 0
2009-01-07 15:59:02           savefilename = '/home/detlef/Media/MythArchiv/'
2009-01-07 15:59:02 Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
2009-01-07 15:59:02 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2009-01-07 15:59:02 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2009-01-07 15:59:02 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2009-01-07 15:59:02 wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
2009-01-07 15:59:02 Final DVD Video format will be pal
2009-01-07 15:59:02 There are 1 files to process
2009-01-07 15:59:03 Pre-processing recording 1: '/var/lib/mythtv/recordings/29224_20081015225500.mpg'
2009-01-07 15:59:03           Zapp
2009-01-07 15:59:03 Video resolution is 720 by 576
2009-01-07 15:59:03 *************************************************************
2009-01-07 15:59:03 Processing recording 1: '/var/lib/mythtv/recordings/29224_20081015225500.mpg'
2009-01-07 15:59:03 *************************************************************
2009-01-07 15:59:33 Preferred audio languages ger and eng
2009-01-07 15:59:33 Video id: 0xa29, Audio1: [1] 0xa2a (MP2, ger), Audio2: [2] - 0xa2b (MP2, 2ch)
2009-01-07 15:59:33 Using Project-X to demux file
2009-01-07 15:59:33 Preferred audio languages ger and eng
2009-01-07 15:59:33 Video id: 0xa29, Audio1: [1] 0xa2a (MP2, ger), Audio2: [2] - 0xa2b (MP2, 2ch)
2009-01-07 15:59:33 projectx -id 0xa29,0xa2a,0xa2b -out "/home/detlef/Media/MythArchiv/work/1" -name "29224_20081015225500" "/var/lib/mythtv/recordings/29224_20081015225500.mpg"
2009-01-07 15:59:33 Failed while running Project-X to cut commercials and/or demux an mpeg2 file.
Result: 127, Command was projectx -id 0xa29,0xa2a,0xa2b -out "/home/detlef/Media/MythArchiv/work/1" -name "29224_20081015225500" "/var/lib/mythtv/recordings/29224_20081015225500.mpg"
2009-01-07 15:59:33 ************************************************************
2009-01-07 15:59:33 ERROR: Failed to run Project-X to demux file
2009-01-07 15:59:33 ************************************************************
2009-01-07 15:59:33 
2009-01-07 15:59:33 Terminated

Debugging mytharchive is a thankless task under the best of circumstances. More so when projectx is involved <shudder!>. But you appear to have included your progress log file. The meat of the problem (whether easily fixable or not) is more likely to be found in the last lines of your mythburn log.

In the meantime, if this issue is related only to the one dvb recording, and if it has a cutlist for commercials to be removed, you might try generating a commercial-free file by hand by using:

mythtranscode --mpeg2  --honorcutlist  -c <myth's channel id> -s <myth's starttime for the recording>

This will read your recording, whose name ends in .mpg and create a new file, sans commercials, which ends in *.mpg.tmp

You could feed this .mpg.tmp file into a program like DeVeDe, which handles many dvb problem recordings that mytharchive seemingly can't.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

I tend to rely on DeVeDe as an easy solution to archive any dvb recording that runs longer than about 40 minutes (i.e., anything longer than an hour episode with commercials removed), because I find that beyond that point mytharchive's ability to audio sync dvb recordings just becomes unacceptable.

Cheers! :)

---

### Post by TVtalker on 2009-01-07
ok, I´did some tests and found out that project-x was not installed. In the log-file there was a message that project-x could not be found. I thought it ist installed with mythbuntu, too?

So I installed project-x seperatly.

Now the process of demuxing in mythbuntu ist starting, but after some minutes the computer crashs without a warning. I tried it directly with the project-x frontend - same thing. It looks like it´s a problem with project-x.

The mythburn.log is scrambled after the crash. The first time it happens, it looks like 23% of the process was done.

any ideas?

---

### Post by TVtalker on 2009-01-07
Here my progress.log

It#s a file without a cutlist for commercials and running only for 30min.

2009-01-07 17:03:28 mythburn.py (0.1.20080726-1-fixes) starting up...
2009-01-07 17:03:28 Found 2 CPUs
2009-01-07 17:03:28 Obtaining MythTV settings from MySQL database for hostname MythbuntuRecorder
2009-01-07 17:03:28 temppath: /home/detlef/Media/MythArchiv/work
2009-01-07 17:03:28 logpath:  /home/detlef/Media/MythArchiv/logs
2009-01-07 17:03:28 Setting process priority to 17
2009-01-07 17:03:28 Processing Mythburn job number 1.
2009-01-07 17:03:28 Options - mediatype = 3, doburn = 1, createiso = 0, erasedvdrw = 0
2009-01-07 17:03:28           savefilename = '/home/detlef/Media/MythArchiv/'
2009-01-07 17:03:28 Looking for: /usr/share/mythtv/mytharchive/themes/Simple - Autoplay/theme.xml
2009-01-07 17:03:28 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2009-01-07 17:03:28 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2009-01-07 17:03:28 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2009-01-07 17:03:28 wantIntro: 0, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 0
2009-01-07 17:03:28 Final DVD Video format will be pal
2009-01-07 17:03:28 There are 1 files to process
2009-01-07 17:03:29 Pre-processing recording 1: '/var/lib/mythtv/recordings/29006_20080805011000.mpg'
2009-01-07 17:03:30           neues spezial
2009-01-07 17:03:30 Video resolution is 720 by 576
2009-01-07 17:03:30 *************************************************************
2009-01-07 17:03:30 Processing recording 1: '/var/lib/mythtv/recordings/29006_20080805011000.mpg'
2009-01-07 17:03:30 *************************************************************
2009-01-07 17:03:55 Preferred audio languages ger and eng
2009-01-07 17:03:55 Video id: 0x6e, Audio1: [3] 0x7d (AC3, dd), Audio2: [1] - 0x78 (MP2, dd)
2009-01-07 17:03:55 Using Project-X to demux file
2009-01-07 17:03:55 Preferred audio languages ger and eng
2009-01-07 17:03:55 Video id: 0x6e, Audio1: [3] 0x7d (AC3, dd), Audio2: [1] - 0x78 (MP2, dd)
2009-01-07 17:03:55 projectx -id 0x6e,0x7d,0x78 -out "/home/detlef/Media/MythArchiv/work/1" -name "29006_20080805011000" "/var/lib/mythtv/recordings/29006_20080805011000.mpg"

---

### Post by klc5555 on 2009-01-07
> **TVtalker said:**
> ok, I´did some tests and found out that project-x was not installed. In the log-file there was a message that project-x could not be found. I thought it ist installed with mythbuntu, too?

So I installed project-x seperatly.

Now the process of demuxing in mythbuntu ist starting, but after some minutes the computer crashs without a warning. I tried it directly with the project-x frontend - same thing. It looks like it´s a problem with project-x.

The mythburn.log is scrambled after the crash. The first time it happens, it looks like 23% of the process was done.

any ideas?

First try would be to switch over your preferred demuxer back to ffmpeg, which ought to have been set up as the default anyway during the original mytharchive installation, from projectx. If ffmpeg dies a horrible death during the demuxing phase, it's frequently connected to four (possibly) missing lines of code in the mythburn.py script relating to how liba52 is handled. But the mythburn log should reveal this as I've never heard of ffmpeg taking down a whole machine.

---

### Post by TVtalker on 2009-01-08
ok, I´m not an mythbuntu or linux professional :-). So I´m not sure what to do to switch back the demuxer to ffmpeg. Can you give me some help?

Thanks!!

---

