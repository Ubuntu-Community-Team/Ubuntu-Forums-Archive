---
title: "[SOLVED] Split Front/Backend and MythArchive"
date: 2008-09-04
forum: Mythbuntu
---

### Post by ian dobson on 2008-09-04
Hi All,

Is there anyway to get MythArchive working on a split Front/Backend? My backend doesn't have a monitor attached so I can't run a frontend on it and when I try running MythArchiveon the frontend I get to following in the frontend log file:-

```
2008-09-04 18:48:03.983 MythThemedMenuPrivate: Unknown tag image in background
chmod: cannot access `/mnt/video/tmp/work': Permission denied
chmod: cannot access `/mnt/video/tmp/logs': Permission denied
chmod: cannot access `/mnt/video/tmp/config': Permission denied
2008-09-04 18:48:07.810 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/mythburn-ui.xml
2008-09-04 18:48:09.063 MythArchive: Loading encoding profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_d$
2008-09-04 18:48:28.572 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/mytharchive-ui.xml
2008-09-04 18:48:28.888 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2008-09-04 18:48:28.888 Using protocol version 40
2008-09-04 18:48:28.890 lcddevice: received bad no. of arguments in CONNECTED response from LCDServer
2008-09-04 18:48:29.066 MythArchive cannot handle this file because it isn't available locally - myth://192.168.0.2:6543/32$
2008-09-04 18:48:29.074 MythArchive cannot handle this file because it isn't available locally - myth://192.168.0.2:6543/32$
2008-09-04 18:49:02.952 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/mytharchive-ui.xml
2008-09-04 18:49:15.168 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/mytharchive-ui.xml
MythburnWizard::createConfigFile: Failed to open file for writing - /mnt/video/tmp/config/mydata.xml
sh: cannot create /mnt/video/tmp/logs/mythburn.log: Permission denied

```

I can sortout the Permission denied errors but the "non-local file" errors are making me think that I can't use mytharchive.

Note my frontend is running from a 2Gb Flash SSD so I can't copy the file to a local drive.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-05
Wow,

The Silence is Almost Deafening.

OK I got round the "not local" problem by editing the settings table so that the recording dir from the frontend points to the recordings dir on the backend over a CIFS mount point.

I now am able to add a file to the archive list, but when I try to add a recording (With the info from the recordings DB) I get:-

cannot find file /mnt/video/mythtv/recordings/1015_20080902200900.mpg1015_20080902200900.mpg

Anyone got ay ideas?

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-06
Hi,

Here's the error I'm getting when I try to add a recording.

```
2008-09-06 08:24:28 mythburn.py (0.1.20080726-1-fixes) starting up...
2008-09-06 08:24:28 Found 2 CPUs
2008-09-06 08:24:28 Obtaining MythTV settings from MySQL database for hostname myth-frontend
2008-09-06 08:24:29 temppath: /mnt/video/tmp/work
2008-09-06 08:24:29 logpath:  /mnt/video/tmp/logs
2008-09-06 08:24:29 Setting process priority to 17
2008-09-06 08:24:29 Processing Mythburn job number 1.
2008-09-06 08:24:29 Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 1
2008-09-06 08:24:29           savefilename = ''
2008-09-06 08:24:29 Looking for: /usr/share/mythtv/mytharchive/themes/Compact/theme.xml
2008-09-06 08:24:29 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2008-09-06 08:24:29 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2008-09-06 08:24:29 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2008-09-06 08:24:29 wantIntro: 1, wantMainMenu: 1, wantChapterMenu:0, wantDetailsPage: 0
2008-09-06 08:24:29 Final DVD Video format will be pal
2008-09-06 08:24:29 There are 1 files to process
2008-09-06 08:24:29 Pre-processing recording 1: '/mnt/video/mythtv/recordings//32438_20080903222900.mpg/32438_20080903222900.mpg'
2008-09-06 08:24:29 ************************************************************
**2008-09-06 08:24:29 ERROR: Source file does not exist: /mnt/video/mythtv/recordings//32438_20080903222900.mpg/32438_20080903222900.mpg**
2008-09-06 08:24:29 ************************************************************
2008-09-06 08:24:29 
2008-09-06 08:24:29 Terminated
```

When I add the video as a file it works.

Regards
Ian Dobson

---

### Post by laga on 2008-09-06
MythTV uses storage groups these days. Try adding your recordings directory in the storage groups screen in mythtv-setup on your frontend.


I've actually got a patch which will download the recordings from MythBackend automagically, but it's not quite ready yet :(

---

### Post by ian dobson on 2008-09-07
Hi,

Removing the trailing / from the storage group dir fixed the // and double file name problem.

MythArchive isn't the most user friendly tool in the world but as I only burn DVD's once in a blue moon it's usable.

One thing I found is that I need to delete the .ICEAuthority in my home directory, otherwise mytharchive dies with an authority error.

Regards
Ian Dobson

---

