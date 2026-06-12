---
title: "MythArchive won't do anything"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by lionsnob on 2007-04-29
Help!

When I try to make a backup of a show I taped on my MythTV frontend, MythArchive gives this error:

```

mythburn.py (0.1.20061201-1) starting up...
Process priority 8
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /tmp/config/mydata.xml
passed progress log file: /tmp/logs/progress.log
mythburn.py (0.1.20061201-1) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname alien
Processing Mythburn job number 1.
Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 13
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing file '1621_20070428200000.mpg' of type 'recording'
chmod: changing permissions of `/tmp/': Operation not permitted
chmod: changing permissions of `/tmp/.ICE-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X0-lock': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix/X0': Operation not permitted
------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3600, in <module>
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3378, in processJob
    preProcessFile(node,folder)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 1076, in preProcessFile
    mediafile = os.path.join(recordingpath, file.attributes["filename"].value)
  File "posixpath.py", line 62, in join
    elif path == '' or path.endswith('/'):
AttributeError: 'NoneType' object has no attribute 'endswith'
------------------------------------------------------------

```

Any ideas?  I'd really like to get this working.  The recording I'm trying to burn is an hour long 1080i broadcast from a pcHDTV-5500.

Thanks!

---

### Post by lionsnob on 2007-04-30
Bump.  Anyone see this problem before?

---

### Post by moaxey on 2008-02-01
Had the same and it took me months to work out that this means that I was running out of space in /tmp. 

dont want to re-partition... but i do want to re-encode/archive some 12 gig files and have only 4 gigs free on /

thought i was being smart having a small system partition and huge mythtv media space!

---

