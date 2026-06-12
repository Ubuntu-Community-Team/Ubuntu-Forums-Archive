---
title: "Mythtv suddenly broken after daylight time savings"
date: 2008-10-26
forum: Mythbuntu
---

### Post by picbits on 2008-10-26
This might be a coincidence but my Mythtv has been working perfectly for the past couple of months.

This morning I checked my server time to see if putting the clocks back an hour had been done - it had resynced the time perfectly - no problems here.

Just been in via Mythweb to transcode some recorded programs and the majority of my icons on recorded programs have vanished. It seem to have forgotten that the programs have been recorded. If I click on an icon in recorded programs, I don't get the usual menu allowing me to transcode and most of the old recorded programs take me back to the listings screen with the dialogue "Warning: Unknown Programme"

I've rebooted the server and this has made no difference. I've also ran a mythfilldatabase with no change.

Programs are still there in the recorded directory but everything else is buggered up.

Any ideas ?

Ta
Dom

---

### Post by ian dobson on 2008-10-26
Hi,

I've written a small script that checks the Mythtv database/filesystem maybe it'll help you find your problem.

You can download the code here:- [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)

ps. Do you see anything in your backend log?

Regards
Ian Doson

---

### Post by picbits on 2008-10-26
You're talking to a bit of a Linux newby I'm afraid so you would have to tell me how to run/compile/execute that script.

I can't see anything obvious in either todays Mythbackend.log or yesterdays mythbackend.log.1

I've recorded a new program and it worked fine, thumbnail is there and it has the right menus etc when I click on the thumbnail.

It might just be coincidence that this has started happening after the time change but as said before its been working fine for months.

---

### Post by ian dobson on 2008-10-26
Hi,

To download my script just go to the terminal then type

wget [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)
mv CheckMythDB.txt CheckMythDB.pl
chmod +x CheckMythDB.pl
./CheckMythDB.pl -a

Thats it, it should then produce a printout like:-
```

[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--] Using HostName 'alpha2', DatabaseHost '192.168.0.2', SQLUserName 'mythtv', SQLPassword 'yYyYyYyY'
[--].Checking configuration for host 'alpha2'
[OK].Found 2 video sources
[OK].Videosource (1) 'analog' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource (2) 'digital' has a EPG source defined (eitonly)
[OK].Found 2 card inputs for Videoinput 1
[OK].Found 4 card inputs for Videoinput 2
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 5 visible and 2 invisible channels defined
[OK].Videosource 2 has 54 visible and 65 invisible channels defined
[OK].cardinput 1 type MPEG exists as device in /dev, file permissions are 0660 (rw- rw- ---)
[OK].cardinput 2 type MPEG exists as device in /dev, file permissions are 0660 (rw- rw- ---)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 5 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 6 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].4 dtv_multiplex entries do not have a valid channel
[!!].Channel BBC THREE has 139 programs in EPG.No EPG data or last program in the past
[!!].Channel BBC FOUR has 113 programs in EPG.No EPG data or last program in the past
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system at (/data/mythtv/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/data/mythtv/backup/)
[OK].Storage group 'LiveTV' exists in file system at (/data/mythtv/liveTV/)
[--].Checking files in storage group 'LiveTV'
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'DB Backups'
[OK].Checking 408 recordings in database (file system)
[OK].Checking 408 recordings found in database (seek,commflag etc)
[--].Recording 'n-tv History' 2008-10-26 16:05:00 appears to be a 'LiveTV' recording (no commflag)
[--].Recording 'EUReKA - Die geheime Stadt' 2008-10-26 16:05:00 Mythcommflag running
Took 1833 SQL queries

```

Regards
Ian Dobson

---

### Post by picbits on 2008-10-26
Ok - managed to do that - many thanks :-)

```
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--] Using HostName 'xxx.co.uk', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'xxxxx'
[--].Checking configuration for host 'xxx.co.uk'
[OK].Found 1 video sources
[OK].Videosource (1) 'EIT' has a EPG source defined (eitonly)
[OK].Found 4 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 82 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[!!].Channel 4TVinteractive has 0 programs in EPG.No EPG data
[!!].Channel 301 has 0 programs in EPG.No EPG data
[!!].Channel 302 has 0 programs in EPG.No EPG data
[!!].Channel 303 has 0 programs in EPG.No EPG data
[!!].Channel 305 has 0 programs in EPG.No EPG data
[!!].Channel BBC World Sv. has 0 programs in EPG.No EPG data
[!!].Channel GEMSTV1 has 0 programs in EPG.No EPG data
[!!].Channel Clyde 1 has 0 programs in EPG.No EPG data
[!!].Channel tvtv DIGITAL has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 1 storage groups for 'pbserver.picbits.co.uk'
[OK].Storage group 'Default' exists in file system at (/var/lib/mythtv/recordings/)
[--].Checking files in storage group 'Default'
[OK].Checking 34 recordings in database (file system)
[OK].Checking 34 recordings found in database (seek,commflag etc)
[--].Recording 'Radio 1 presents Metallica Night' 2008-09-15 19:04:00 Mythcommflag not run
[--].Recording 'Metallica Live' 2008-09-15 21:00:00 Mythcommflag not run
[--].Recording 'Radio 1's Metallica Story' 2008-09-15 23:00:00 Mythcommflag not run
Took 291 SQL queries

```

---

### Post by ardnut on 2008-10-26
I'm seeing exactly the same problem (also only seems to have happened since the clock changes) but can't find anything in the logs that points to the issue.  It's also only affecting mythweb, my frontend seems to have no issues at all.

Ash

---

### Post by ian dobson on 2008-10-26
Hi,

Can you try removing your png (preview files) from your recordings dir: Go to the terminal then

cd /your recordings dir
mv *.png *.sav

Then go to mythweb and see if it finds the preview/recordings.

Regards
Ian Dobson

---

### Post by picbits on 2008-10-26
Just done that. It rebuilt all of the thumbnails but the only one which is displaying is the program I test recorded earlier. The rest are all red crosses.

The thumbnails are in the right directory, I can view them over the network and they correspond to the program recorded but the same problem exists - I click on some of the older recordings and it comes up with "Warning: Unknown programme"

---

### Post by ardnut on 2008-10-26
I did try that as well, I removed all the preview files from both the mythweb cache dir and also the recordings dir. Then restarted the backend and refreshed the recordings page on mythweb.  It sat there for a while (as you would expect) generating thumbnails but although it's created a thumbnail file for each on the filesystem, most of those are empty, 0 bytes big.

Ash

---

### Post by picbits on 2008-10-26
Also noticed that the link for the thumbnail ends in .100x56.png on which doesn't exist in the recordings directory (the .png is there though). There were a load of .100x56.png before I moved them as above.

---

### Post by picbits on 2008-10-26
Current recordings directory listing: 

```
root@pbserver:/media/store2/mythvideo# ls -l
total 71976720
-rw-r--r-- 1 mythtv mythtv 3255001092 2008-08-12 15:23 1001_20080802212000.mpg
-rw-rw-rw- 1 mythtv mythtv      87572 2008-10-26 16:24 1001_20080802212000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2047535260 2008-09-20 20:15 1001_20080920193000.mpg
-rw-rw-rw- 1 mythtv mythtv     105723 2008-10-26 16:24 1001_20080920193000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2047904304 2008-09-27 18:45 1001_20080927180000.mpg
-rw-rw-rw- 1 mythtv mythtv      85499 2008-10-26 16:24 1001_20080927180000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2048852764 2008-10-04 18:45 1001_20081004180000.mpg
-rw-rw-rw- 1 mythtv mythtv      61568 2008-10-26 16:24 1001_20081004180000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2048193824 2008-10-11 19:50 1001_20081011190500.mpg
-rw-rw-rw- 1 mythtv mythtv      51347 2008-10-26 16:24 1001_20081011190500.mpg.png
-rw-r--r-- 1 mythtv mythtv 2048357384 2008-10-18 18:40 1001_20081018175500.mpg
-rw-rw-rw- 1 mythtv mythtv      82428 2008-10-26 16:24 1001_20081018175500.mpg.png
-rw-r--r-- 1 mythtv mythtv 2733597080 2008-10-23 22:00 1001_20081023210000.mpg
-rw-rw-rw- 1 mythtv mythtv      63654 2008-10-26 16:24 1001_20081023210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2048480524 2008-10-25 18:35 1001_20081025175000.mpg
-rw-rw-rw- 1 mythtv mythtv      73702 2008-10-26 16:24 1001_20081025175000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1464020860 2008-10-01 19:45 1002_20081001190500.mpg
-rw-rw-rw- 1 mythtv mythtv      78455 2008-10-26 16:24 1002_20081001190500.mpg.png
-rw-r--r-- 1 mythtv mythtv 1347315160 2008-10-01 21:45 1002_20081001210000.mpg
-rw-rw-rw- 1 mythtv mythtv      69191 2008-10-26 16:24 1002_20081001210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2107516932 2008-08-12 15:30 1007_20080810193000.mpg
-rw-rw-rw- 1 mythtv mythtv      67988 2008-10-26 16:24 1007_20080810193000.mpg.png
-rw-r--r-- 1 mythtv mythtv 3654109188 2008-08-17 11:21 1007_20080812200000.mpg
-rw-rw-rw- 1 mythtv mythtv      56377 2008-10-26 16:24 1007_20080812200000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1529612368 2008-08-17 21:50 1007_20080817210000.mpg
-rw-rw-rw- 1 mythtv mythtv      67405 2008-10-26 16:24 1007_20080817210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2687131652 2008-08-22 15:20 1007_20080820210000.mpg
-rw-rw-rw- 1 mythtv mythtv      77945 2008-10-26 16:24 1007_20080820210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1628097296 2008-08-28 00:05 1007_20080827231500.mpg
-rw-rw-rw- 1 mythtv mythtv      97690 2008-10-26 16:24 1007_20080827231500.mpg.png
-rw-r--r-- 1 mythtv mythtv 1675075488 2008-08-31 21:50 1007_20080831210000.mpg
-rw-rw-rw- 1 mythtv mythtv     106104 2008-10-26 16:24 1007_20080831210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1673582016 2008-09-07 21:50 1007_20080907210000.mpg
-rw-rw-rw- 1 mythtv mythtv      35235 2008-10-26 16:24 1007_20080907210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1242516628 2008-10-01 22:40 1007_20081001220000.mpg
-rw-rw-rw- 1 mythtv mythtv      49838 2008-10-26 16:24 1007_20081001220000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1472332340 2008-10-08 22:45 1007_20081008220000.mpg
-rw-rw-rw- 1 mythtv mythtv      81996 2008-10-26 16:24 1007_20081008220000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1515491688 2008-10-15 22:45 1007_20081015220000.mpg
-rw-rw-rw- 1 mythtv mythtv     107096 2008-10-26 16:24 1007_20081015220000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1412201480 2008-10-22 22:45 1007_20081022220000.mpg
-rw-rw-rw- 1 mythtv mythtv      37414 2008-10-26 16:24 1007_20081022220000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2356744196 2008-08-10 19:29 1032_20080810130000.mpg
-rw-rw-rw- 1 mythtv mythtv      42841 2008-10-26 16:24 1032_20080810130000.mpg.png
-rw-r--r-- 1 mythtv mythtv 1388228660 2008-09-15 21:00 1700_20080915190400.mpg
-rw-rw-rw- 1 mythtv mythtv        779 2008-10-26 16:24 1700_20080915190400.mpg.png
-rw-r--r-- 1 mythtv mythtv 1440439644 2008-09-15 23:00 1700_20080915210000.mpg
-rw-rw-rw- 1 mythtv mythtv        779 2008-10-26 16:24 1700_20080915210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  719920996 2008-09-16 00:00 1700_20080915230000.mpg
-rw-rw-rw- 1 mythtv mythtv        779 2008-10-26 16:24 1700_20080915230000.mpg.png
-rw-r--r-- 1 mythtv mythtv  916481388 2008-10-26 13:00 23208_20081026123000.mpg
-rw-r--r-- 1 mythtv mythtv      10892 2008-10-26 16:26 23208_20081026123000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv      84247 2008-10-26 16:24 23208_20081026123000.mpg.png
-rw-r--r-- 1 mythtv mythtv 3165681668 2008-08-17 11:10 9258_20080816164500.mpg
-rw-rw-rw- 1 mythtv mythtv      43869 2008-10-26 16:24 9258_20080816164500.mpg.png
-rw-r--r-- 1 mythtv mythtv 1447589892 2008-08-17 11:13 9258_20080816213000.mpg
-rw-rw-rw- 1 mythtv mythtv      76934 2008-10-26 16:24 9258_20080816213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 2027212804 2008-08-17 11:16 9258_20080816224500.mpg
-rw-rw-rw- 1 mythtv mythtv      71593 2008-10-26 16:24 9258_20080816224500.mpg.png
-rw-r--r-- 1 mythtv mythtv 4920521932 2008-09-06 23:15 9258_20080906204600.mpg
-rw-rw-rw- 1 mythtv mythtv      72033 2008-10-26 16:24 9258_20080906204600.mpg.png
-rw-r--r-- 1 mythtv mythtv 3289129748 2008-08-27 01:20 9325_20080826231500.mpg
-rw-rw-rw- 1 mythtv mythtv      95637 2008-10-26 16:24 9325_20080826231500.mpg.png
-rw-r--r-- 1 mythtv mythtv 3931407872 2008-09-26 02:05 9325_20080925233000.mpg
-rw-rw-rw- 1 mythtv mythtv      78761 2008-10-26 16:24 9325_20080925233000.mpg.png
-rw-r--r-- 1 mythtv mythtv 4190455328 2008-09-28 00:25 9353_20080927214500.mpg
-rw-rw-rw- 1 mythtv mythtv      93086 2008-10-26 16:24 9353_20080927214500.mpg.png
-rw-r--r-- 1 mythtv mythtv 2148734980 2008-08-12 15:26 9448_20080809210000.mpg
-rw-rw-rw- 1 mythtv mythtv      59448 2008-10-26 16:24 9448_20080809210000.mpg.png
drwxr-xr-x 2 root   root         4096 2008-10-26 16:23 sav

```

Old recordings thumbnails:

```
root@pbserver:/media/store2/mythvideo/sav# ls -l
total 2744
-rw-r--r-- 1 mythtv mythtv  11038 2008-08-02 22:04 1001_20080802212000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  87572 2008-08-12 15:32 1001_20080802212000.mpg.png
-rw-r--r-- 1 mythtv mythtv  12028 2008-09-20 22:15 1001_20080920193000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv 105723 2008-09-20 20:37 1001_20080920193000.mpg.png
-rw-r--r-- 1 mythtv mythtv  10011 2008-09-27 18:27 1001_20080927180000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  85499 2008-09-27 19:06 1001_20080927180000.mpg.png
-rw-r--r-- 1 mythtv mythtv   7074 2008-10-11 11:05 1001_20081004180000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  61568 2008-10-04 19:08 1001_20081004180000.mpg.png
-rw-r--r-- 1 mythtv mythtv   7228 2008-10-16 10:09 1001_20081011190500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  51347 2008-10-11 20:11 1001_20081011190500.mpg.png
-rw-r--r-- 1 mythtv mythtv  11589 2008-10-18 18:31 1001_20081018175500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  82428 2008-10-18 19:02 1001_20081018175500.mpg.png
-rw-r--r-- 1 mythtv mythtv   6774 2008-10-23 22:03 1001_20081023210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  63654 2008-10-24 00:39 1001_20081023210000.mpg.png
-rw-rw-rw- 1 mythtv mythtv  73702 2008-10-25 18:58 1001_20081025175000.mpg.png
-rw-r--r-- 1 mythtv mythtv  10869 2008-10-11 11:05 1002_20081001190500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  78455 2008-10-01 20:04 1002_20081001190500.mpg.png
-rw-r--r-- 1 mythtv mythtv   9913 2008-10-11 11:05 1002_20081001210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  69191 2008-10-01 22:05 1002_20081001210000.mpg.png
-rw-r--r-- 1 mythtv mythtv   8966 2008-08-10 19:43 1007_20080810193000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  67988 2008-08-12 15:32 1007_20080810193000.mpg.png
-rw-r--r-- 1 mythtv mythtv   6455 2008-08-14 11:52 1007_20080812200000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  56377 2008-08-18 14:59 1007_20080812200000.mpg.png
-rw-r--r-- 1 mythtv mythtv   9965 2008-08-18 14:59 1007_20080817210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  67405 2008-08-17 22:09 1007_20080817210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  12426 2008-08-22 15:17 1007_20080820210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  77945 2008-08-22 16:05 1007_20080820210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  10794 2008-08-28 08:45 1007_20080827231500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  97690 2008-08-28 00:24 1007_20080827231500.mpg.png
-rw-r--r-- 1 mythtv mythtv  11927 2008-08-31 21:11 1007_20080831210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv 106104 2008-08-31 22:10 1007_20080831210000.mpg.png
-rw-r--r-- 1 mythtv mythtv   5928 2008-09-09 18:44 1007_20080907210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  35235 2008-09-07 22:10 1007_20080907210000.mpg.png
-rw-r--r-- 1 mythtv mythtv   7404 2008-10-11 11:05 1007_20081001220000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  49838 2008-10-01 22:56 1007_20081001220000.mpg.png
-rw-r--r-- 1 mythtv mythtv   9728 2008-10-11 11:05 1007_20081008220000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  81996 2008-10-08 23:02 1007_20081008220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  13322 2008-10-16 10:09 1007_20081015220000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv 107096 2008-10-15 23:02 1007_20081015220000.mpg.png
-rw-r--r-- 1 mythtv mythtv   5958 2008-10-23 20:39 1007_20081022220000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  37414 2008-10-22 23:03 1007_20081022220000.mpg.png
-rw-r--r-- 1 mythtv mythtv   6995 2008-08-10 19:22 1032_20080810130000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  42841 2008-08-10 19:43 1032_20080810130000.mpg.png
-rw-r--r-- 1 mythtv mythtv    240 2008-09-15 19:05 1700_20080915190400.mpg.100x75.png
-rw-rw-rw- 1 mythtv mythtv    779 2008-09-15 21:00 1700_20080915190400.mpg.png
-rw-r--r-- 1 mythtv mythtv    240 2008-09-15 21:08 1700_20080915210000.mpg.100x75.png
-rw-rw-rw- 1 mythtv mythtv    779 2008-09-15 23:00 1700_20080915210000.mpg.png
-rw-r--r-- 1 mythtv mythtv    240 2008-09-16 08:12 1700_20080915230000.mpg.100x75.png
-rw-rw-rw- 1 mythtv mythtv    779 2008-09-16 00:00 1700_20080915230000.mpg.png
-rw-r--r-- 1 mythtv mythtv   8693 2008-10-26 12:33 23208_20081026123000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  84247 2008-10-26 13:11 23208_20081026123000.mpg.png
-rw-r--r-- 1 mythtv mythtv   5660 2008-08-16 22:49 9258_20080816164500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  43869 2008-08-18 14:59 9258_20080816164500.mpg.png
-rw-r--r-- 1 mythtv mythtv   9670 2008-08-16 22:49 9258_20080816213000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  76934 2008-08-18 14:59 9258_20080816213000.mpg.png
-rw-r--r-- 1 mythtv mythtv  12376 2008-08-16 22:49 9258_20080816224500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  71593 2008-08-18 14:59 9258_20080816224500.mpg.png
-rw-r--r-- 1 mythtv mythtv   8917 2008-09-06 20:46 9258_20080906204600.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  72033 2008-09-07 00:14 9258_20080906204600.mpg.png
-rw-r--r-- 1 mythtv mythtv  12301 2008-08-27 20:29 9325_20080826231500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  95637 2008-08-27 02:03 9325_20080826231500.mpg.png
-rw-r--r-- 1 mythtv mythtv   9896 2008-09-26 09:59 9325_20080925233000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  78761 2008-09-26 03:02 9325_20080925233000.mpg.png
-rw-r--r-- 1 mythtv mythtv  11825 2008-09-28 14:09 9353_20080927214500.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  93086 2008-09-28 01:24 9353_20080927214500.mpg.png
-rw-r--r-- 1 mythtv mythtv   8687 2008-08-10 10:20 9448_20080809210000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv  59448 2008-08-12 15:32 9448_20080809210000.mpg.png

```

---

### Post by SiHa on 2008-10-26
FWIW
I have the same problem. Interestingly, only two recordings which were watched today have missing thumbnails. All others are present, but I still get "Warning: Unknown Programme" for all recordings.

---

### Post by picbits on 2008-10-26
Has anyone tried putting their clock forward by an hour just to see if it cures the problem ?

I would but my machine is actually pretty critical for my business (MythTv is a bonus on it rather than a necessity).

---

### Post by funkydan2 on 2008-10-26
I've had the same problem as well (see [here]("http://ubuntuforums.org/showthread.php?t=954500") and [here]("http://ubuntuforums.org/showthread.php?t=951346")), but didn't think about it being related to daylight savings.

I think there's a bug/problem in the way that PHP5 in Gutsy handles daylight savings time, which has been fixed in the version of PHP5 in Intrepid.  I assume it's the same problem that causes the program guide in mythweb to be out by 1 hour.

An update to Intrepid fixed the problem for me, but that's not a great solution if you're planning on sticking with the 8.04**LTS**

---

### Post by ardnut on 2008-10-26
Editing my php.ini file (which on my system is located in /etc/php5/apache2) and replacing the line...

;date.timezone = 

...with...

date.timezone = Europe/London

...then restarting apache (sudo /etc/init.d/apache2 restart) fixed the issue for me.

Ash

---

### Post by ian dobson on 2008-10-27
Hi,

Strange I don't have the "date.timezone = " set in my php.ini and am not seeing any problems with mythweb, maybe it's country specific.

Note: I haven't rebooted my backend for about a month now, if that makes any difference.
 
Regards
Ian Dobson

---

### Post by oobe-feisty on 2008-10-31
i experienced the same problem the problem isnt that mythtv or the sysyem doesnt know the correct time you will find that recordings start at the correct time its only mythweb you need to update the php time zones for mythweb to work i cant remember off hand the link i found that explains how to do this but will return with it once i do 
its on whirlpool.net.au forums

---

### Post by picbits on 2008-10-31
Excellent - will look forward to your answer :)

---

### Post by oobe-feisty on 2008-10-31
> **picbits said:**
> Excellent - will look forward to your answer :)

well i just went and search the above site and now have found the link
it wasnt very hard to find anyhow here is the link if you cant find it yourself. 

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1064041](http://forums.whirlpool.net.au/forum-replies.cfm?t=1064041)

---

### Post by picbits on 2009-10-25
> **ardnut said:**
> Editing my php.ini file (which on my system is located in /etc/php5/apache2) and replacing the line...

;date.timezone = 

...with...

date.timezone = Europe/London

...then restarting apache (sudo /etc/init.d/apache2 restart) fixed the issue for me.

Ash

I know its an old thread but its "this time of year" again and I had the same problem.

I must have missed the above last year as I've just added the timezone in my Php.ini file and its sorted out the problem (which was exactly the same as the one this time last year !!)

I'm bumping it as no doubt someone else will have exactly the same problem.

I found 2 instances of Php.ini when I used "Locate php.ini" so edited both just to be on the safe side. Once Apache was restarted everything worked perfectly again.

Dom

---

