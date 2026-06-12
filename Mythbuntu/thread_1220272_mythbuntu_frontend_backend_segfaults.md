---
title: "mythbuntu frontend backend segfaults"
date: 2009-07-22
forum: Mythbuntu
---

### Post by malnon on 2009-07-22
Hi, new to these forums but have been using mythbuntu for a while, took the plunge and running the trunk builds from ppa as described on the mythbuntu home page. I have a strange problem that is persistent on local backend/frontend box and also a remote frontend only box. some recordings do not have a thumbnail, whenever i watch these from the frontend it crashes as soon as the intro screen finishes.  this is strange as recording that used to play properly now do not, so it is a mix of new and old recordings affected. I have tried to recreate all the thumbnails by clearing the png files from the recordings directory and also from the mythweb cache, then going into mythweb and looking at recorded programs, some pngs do get recreated but others do not, on checking the kern.log file I have found that the backend segfaults for each recording that does not get a thumbnail rebuilt. I am running on an E6320, with 2gb ram, nvidia 9500-gt card and mythbuntu 9.04, utilising vdpau and drivers 185.14. has anyone seen this problem before? here is a short snippet from the kern.log , which is consistent with either accessing the recording from mythweb or from the frontend, local or remote.

Jul 22 21:04:42 mal-tv kernel: [32001.530084] mythbackend[23044]: segfault at b740d350 ip b4fbd896 sp bfc39288 error 7 in libc-2.9.so[b4f44000+15c000]
Jul 22 21:04:42 mal-tv kernel: [32001.762568] mythbackend[23047]: segfault at b7416350 ip b4fc6896 sp bf941f88 error 7 in libc-2.9.so[b4f4d000+15c000]
Jul 22 21:04:43 mal-tv kernel: [32001.988842] mythbackend[23050]: segfault at b742d350 ip b4fdd896 sp bfd593a8 error 7 in libc-2.9.so[b4f64000+15c000]
Jul 22 21:04:43 mal-tv kernel: [32002.202273] mythbackend[23053]: segfault at b7409350 ip b4fb9896 sp bfd37378 error 7 in libc-2.9.so[b4f40000+15c000]
Jul 22 21:04:46 mal-tv kernel: [32005.027404] __ratelimit: 9 callbacks suppressed
Jul 22 21:04:46 mal-tv kernel: [32005.027409] mythbackend[23083]: segfault at b74c5350 ip b5075896 sp bf7f0e38 error 7 in libc-2.9.so[b4ffc000+15c000]
Jul 22 21:04:46 mal-tv kernel: [32005.264622] mythbackend[23086]: segfault at b7554350 ip b5104896 sp bff81dc8 error 7 in libc-2.9.so[b508b000+15c000]
Jul 22 21:04:46 mal-tv kernel: [32005.497698] mythbackend[23089]: segfault at b745d350 ip b500d896 sp bfa8b0d8 error 7 in libc-2.9.so[b4f94000+15c000]
Jul 22 21:04:46 mal-tv kernel: [32005.729392] mythbackend[23092]: segfault at b7469350 ip b5019896 sp bfa948d8 error 7 in libc-2.9.so[b4fa0000+15c000]

---

### Post by newlinux on 2009-07-22
any useful info in your backend logs? Maybe try turning up the verbosity of your backend logs.

---

### Post by malnon on 2009-07-23
Ok I have checked mythbackend.log and it is indeed the preview that is segfaulting here are a couple of instances from the log:-

2009-07-23 19:44:30.613 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 3002 --starttime 20090527232200 --outfile "/var/lib/mythtv/recordings/3002_20090527232200.mpg.64.png" '
2009-07-23 19:44:30.707 mythbackend version: trunk [Unknown] [www.mythtv.org](www.mythtv.org)
2009-07-23 19:44:30.709 Using runtime prefix = /usr
2009-07-23 19:44:30.710 Empty LocalHostName.
2009-07-23 19:44:30.713 Using localhost value of mal-tv
2009-07-23 19:44:30.722 New DB connection, total: 1
2009-07-23 19:44:30.727 Connected to database 'mythconverg' at host: localhost
2009-07-23 19:44:30.728 Closing DB connection named 'DBManager0'
2009-07-23 19:44:30.733 Connected to database 'mythconverg' at host: localhost
2009-07-23 19:44:30.745 Current Schema Version: 1237
2009-07-23 19:44:30.749 New DB connection, total: 2
2009-07-23 19:44:30.757 Connected to database 'mythconverg' at host: localhost
Segmentation fault
2009-07-23 19:44:30.849 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 3002 --starttime 20090516031400 --outfile "/var/lib/mythtv/recordings/3002_20090516031400.mpg.64.png" '
2009-07-23 19:44:30.944 mythbackend version: trunk [Unknown] [www.mythtv.org](www.mythtv.org)
2009-07-23 19:44:30.949 Using runtime prefix = /usr
2009-07-23 19:44:30.950 Empty LocalHostName.
2009-07-23 19:44:30.952 Using localhost value of mal-tv
2009-07-23 19:44:30.961 New DB connection, total: 1
2009-07-23 19:44:30.967 Connected to database 'mythconverg' at host: localhost
2009-07-23 19:44:30.968 Closing DB connection named 'DBManager0'
2009-07-23 19:44:30.973 Connected to database 'mythconverg' at host: localhost
2009-07-23 19:44:30.985 Current Schema Version: 1237
2009-07-23 19:44:30.989 New DB connection, total: 2
2009-07-23 19:44:30.996 Connected to database 'mythconverg' at host: localhost
Segmentation fault

Unfortunately it does not say why it is segfaulting, or maybe it does and i am not skilled enough to spot it :) !!

---

### Post by malnon on 2009-07-23
done some more checking and the recordings that are mentioned in the log play fine in VLC, I even used the asx button from mythweb to succesfully watch one of the segfaulting recordings just too make sure recordings are ok.

---

### Post by newlinux on 2009-07-23
try turning up the verbosity of your backend log. In the meantime I believe this a frontend setting to generate stills instead of preview pngs... Maybe that will help until the problem is solved.

Maybe run a DB repair. 

I can't tell because you truncated the log output, but is this happening after a recording, or when you go back to view a recording?

---

### Post by malnon on 2009-07-24
hi newlinux !! it was, and I now stress was, happening when I attempted to view a recording. But as of this morning after upgrading to 0.22.20090714-1 the problem has disappeared and normal services have resumed. I can only assume it was a problem in the last version of trunk, although I did check the buglists and found nothing. Thx for your assistance in the matter.

---

### Post by newlinux on 2009-07-24
as long as its fixed!

---

