---
title: "Time Zone Problem"
date: 2012-12-01
forum: Mythbuntu
---

### Post by thegodfaza on 2012-12-01
I'm running Ubuntu Server 12.10 and mythtv v0.26-pre-1367-gf831b99. My problem is that mythtv is storing the starttine in the database in GMT, but when I use a userscript with the %STARTTIME% variable it is returned in my time zone which is -0600. Here is an example:
```
echo %DIR% %FILE% %CHANID% %STARTTIME% returns:
/var/lib/mythtv/recordings 1071_20121130020100.mpg 1071 20121129200100
```
while in the database the recording is stored as
```
1071	2012-11-30 02:01:00	2012-11-30 03:01:01	Person of Interest	Til Death	The team faces a challenge when the numbers of bot...	7_1	WSAW  	WSAW  
```

When I manually run mythcommflag using the database starttime it succeeds. When I use the starttime the userscript is given it fails.
```
 mythcommflag --chanid 1071 --starttime 20121129200100
2012-12-01 18:32:44.134847 C  mythcommflag version: master [v0.26-pre-1367-gf831b99] www.mythtv.org
2012-12-01 18:32:44.134863 C  Qt version: compile: 4.8.3, runtime: 4.8.3
2012-12-01 18:32:44.175474 E  Error Loading en_us translation for module mythfrontend
2012-12-01 18:32:44.176023 E  No program data exists for channel 1071 at 20121129200100
```
```
mythcommflag --chanid 1071 --starttime 20121130020100
MythTV Commercial Flagger, flagging commercials for:
    Person of Interest - Til Death
2012-12-01 18:28:07.686273 C  mythcommflag version: master [v0.26-pre-1367-gf831b99] www.mythtv.org
2012-12-01 18:28:07.686285 C  Qt version: compile: 4.8.3, runtime: 4.8.3
2012-12-01 18:28:07.703199 E  Error Loading en_us translation for module mythfrontend
2012-12-01 18:28:07.739016 E  Filter dir '/usr/lib/mythtv/filters' doesn't exist?
  1%/ 474fps
```

---

### Post by nickrout on 2012-12-01
> **thegodfaza said:**
> I'm running Ubuntu Server 12.10 and mythtv v0.26-pre-1367-gf831b99. My problem is that mythtv is storing the starttine in the database in GMT, but when I use a userscript with the %STARTTIME% variable it is returned in my time zone which is -0600. Here is an example:
```
echo %DIR% %FILE% %CHANID% %STARTTIME% returns:
/var/lib/mythtv/recordings 1071_20121130020100.mpg 1071 20121129200100
```
while in the database the recording is stored as
```
1071	2012-11-30 02:01:00	2012-11-30 03:01:01	Person of Interest	Til Death	The team faces a challenge when the numbers of bot...	7_1	WSAW  	WSAW  
```

When I manually run mythcommflag using the database starttime it succeeds. When I use the starttime the userscript is given it fails.
```
 mythcommflag --chanid 1071 --starttime 20121129200100
2012-12-01 18:32:44.134847 C  mythcommflag version: master [v0.26-pre-1367-gf831b99] www.mythtv.org
2012-12-01 18:32:44.134863 C  Qt version: compile: 4.8.3, runtime: 4.8.3
2012-12-01 18:32:44.175474 E  Error Loading en_us translation for module mythfrontend
2012-12-01 18:32:44.176023 E  No program data exists for channel 1071 at 20121129200100
```
```
mythcommflag --chanid 1071 --starttime 20121130020100
MythTV Commercial Flagger, flagging commercials for:
    Person of Interest - Til Death
2012-12-01 18:28:07.686273 C  mythcommflag version: master [v0.26-pre-1367-gf831b99] www.mythtv.org
2012-12-01 18:28:07.686285 C  Qt version: compile: 4.8.3, runtime: 4.8.3
2012-12-01 18:28:07.703199 E  Error Loading en_us translation for module mythfrontend
2012-12-01 18:28:07.739016 E  Filter dir '/usr/lib/mythtv/filters' doesn't exist?
  1%/ 474fps
```You need to amned your script. It is dealt with in the release notes:

> MythTV System Events and User Jobs should be checked for compatibility with UTC. Recording file names, for example, are now saved with the time component in UTC. %STARTTIME% is local time, use %STARTTIMEUTC% to access the file. Better option is to use the %FILE% tag to directly give the filename, rather than guessing from the channel ID and timestamp. [www.mythtv.org/wiki/Release_Notes_-_0.26](www.mythtv.org/wiki/Release_Notes_-_0.26)

---

### Post by thegodfaza on 2012-12-01
> **nickrout said:**
> You need to amned your script. It is dealt with in the release notes:

[www.mythtv.org/wiki/Release_Notes_-_0.26](www.mythtv.org/wiki/Release_Notes_-_0.26)

Thanks, that appears to be working. Missed automatic transcoding out commercials.

---

