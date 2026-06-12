---
title: "How do you archive audio recordings in Mythtv?"
date: 2008-07-16
forum: Multimedia Software
---

### Post by Declan Moriarty on 2008-07-16
I have the 0.21 version of Mythtv installed.  Upgrading was dreadful.  I had to drop the database since I think I must have missed a few versions.  It complained about storage_group table not existing.  I created this and inserted the relevant data and ran the upgrade again.  This failed.  At this point I dropped the database and upgraded again.  I had to reconfigure everything and test everything again.

The new version is better.  Radio programs work now!  Before it wouldn't lock on to the radio stations (BBC Radio 4 etc.)  Now this works successfully.  I recorded some radio programs and wanted to archive them using myth archive.  This didn't work.  I tried to output to a file this time but I always get the same result it always produces an error saying there are no video streams present.  The mythburn.log file is as follows:-
```

Using simple_fix_rtl
mythburn.py (0.1.20080325-1-fixes) starting up...
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /var/lib/mytharchive/temp/config/mydata.xml
passed progress log file: /var/lib/mytharchive/temp/logs/progress.log
mythburn.py (0.1.20080325-1-fixes) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname desktop
temppath: /var/lib/mytharchive/temp/work
logpath:  /var/lib/mytharchive/temp/logs
Setting process priority to 17
Processing Mythburn job number 1.
Options - mediatype = 2, doburn = 1, createiso = 0, erasedvdrw = 1
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
Final DVD Video format will be pal
There are 1 files to process
Pre-processing file '/home/mythtv/1710_20080712013000.mpg' of type 'recording'
2008-07-16 21:19:50.049 Opening /home/mythtv/1710_20080712013000.mpg
Input #0, mpegts, from '/home/mythtv/1710_20080712013000.mpg':
  Duration: 00:29:59.8, start: 28757.997311, bitrate: 129 kb/s
    Stream #0.0[0x641](eng): Audio: mp2, 48000 Hz, mono, 64 kb/s
    Stream #0.1[0x642]: Data: 0x0000
    Stream #0.2[0xfa0]: Data: 0x0000
streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file filename="/home/mythtv/1710_20080712013000.mpg" type="mpegts">    
        <streams count="3">        
                <audio bitrate="64000" channels="1" codec="mp2" ffmpegindex="0" id="1601" language="eng" samplerate="48000" start_time="2588.219758" streamindex="0"/>        
                <data codec="Data: 0x0000" streamindex="1"/>        
                <data codec="Data: 0x0000" streamindex="2"/>        
        </streams>    
</file>
          Science in Action
************************************************************
ERROR: Didn't find any video elements in stream info file. (/var/lib/mytharchive/temp/work/1/streaminfo.xml)
************************************************************

Terminated

```

Is there a way to use transcoding in Mythtv to generate mp3 files from recordings of radio programs.  I have set up audio profiles for the various recording groups but the transcode menu for the program I am trying to transcode doesn't have any of the audio profiles in it.  The transcodeing jobs I run on it fail.

Is this a case of using the scripts to get the name of the files in Mythtv recordings and locating the file and writing scripts to do the transcode manually? Or is there a way to do this in Mythtv?

All this is a bit of a pity because Mythtv works much better at watching tv than my Windows WinFast PVR program that of late has begun to stutter.  If I stop it and restart it it is fine!

Thank you for your attention.

---

