---
title: "Nuvexport Error"
date: 2008-06-14
forum: Multimedia Software
---

### Post by ed3120 on 2008-06-14
I'm running myth2ipod to transcode my MythTV recordings to Ipod compatible recordings.

When I run ```

/usr/local/bin/myth2ipod <DIR> <FILE>  
```

directly, it works and outputs a file.  But when MythTV executes it as a user job, I get nothing.  My backend log says:```
2008-06-14 10:09:13.657 JobQueue: Started "Convert to Ipod" for "67 (VH1)" recorded from channel 2067 at Sat Jun 14 10:08:00 2008
Starting nuvexport...
/usr/bin/nuvexport --chanid=2067 --start=20080614100800 --mode=iPod --nice=19 --cutlist --nodenoise --nodeinterlace --nomultipass --filename=2067_20080614100800.temp --path=/myth/ipodfeed/
No config found; attempting to find mythbackend via UPnP.
No backends found.  Please copy /home/mythtv/.mythtv/config.xml from a working MythTV installation instead.
Compilation failed in require at /usr/bin/nuvexport line 36.
BEGIN failed--compilation aborted at /usr/bin/nuvexport line 36.
Nuvexport encoding seems to have failed
/usr/bin/MP4Box -add /myth/ipodfeed/2067_20080614100800.temp.mp4 /myth/ipodfeed/2067_20080614100800.ipod.mp4
Unknown input file type
Error importing /myth/ipodfeed/2067_20080614100800.temp.mp4: Requested URL is not valid or cannot be found
MP4Box cleanup seems to have failed
Nuvexport completed, starting xml generation...
"67__VH1_-Sat_Jun_14_10_07_00_2008-20080614" has been added to the feed.
XML file created for "67__VH1_-Sat_Jun_14_10_07_00_2008-20080614" : Yipeee
Cleaning up temporary files
rm -f /myth/ipodfeed/2067_20080614100800.temp.mp4
67 (VH1) is ready for your ipod
2008-06-14 10:09:18.379 JobQueue: Finished "Convert to Ipod" for "67 (VH1)" recorded from channel 2067 at Sat Jun 14 10:08:00 2008.
2008-06-14 10:09:18.852 MainServer::HandleAnnounce Monitor
2008-06-14 10:09:18.857 adding: mythtv as a client (events: 0)
QDateTime::fromString: Parameter out of range
```


Line 35 in Nuvexport is "use MythTV;"```
# Load the MythTV object
    use MythTV;
    our $Myth = new MythTV();
```

---

### Post by dtcwee on 2008-11-08
You must run mythfrontend at least once to generate the config.xml file.

---

### Post by dtcwee on 2008-11-08
You must run mythfrontend at least once to generate the config.xml file.

---

### Post by freddyg on 2009-03-17
are you running myth as the mythtv user or as another login?
my system is setup to run as me and i was having the same problem because  mythtfrontend had never been run as the mythtv user, so i just had to copy /home/me/.mythtv/config.xml to /home/mythtv/.mythtv/ 
and that got me running, i could always remote in as myself and run nuvexport manually, but couldnt get it to run as a job from the frontend. i just fixed it and its plugging away.

as for the other errors you were getting, they are out of my experience.

btw, i've been trying off and on for about 5 months to fix this :(

---

