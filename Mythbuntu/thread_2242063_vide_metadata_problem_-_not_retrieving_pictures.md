---
title: "vide metadata problem - not retrieving pictures"
date: 2014-08-30
forum: Mythbuntu
---

### Post by jrbless on 2014-08-30
I'm trying to load some of my kid's movies on the Mythbuntu 14.04 setup I have and am having problems getting it to retrieve the images.  mythbackend.log says it is a permissions problem.  Most of the mythtv-media folders are mounted on a NAS.  The NAS share is set up so that guest has full read/write access.  Below is the /etc/fstab that shows how they are being mounted:

```
//192.168.0.250/mythtv/banners /var/lib/mythtv/banners cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/coverart /var/lib/mythtv/coverart cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/fanart /var/lib/mythtv/fanart cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/music /var/lib/mythtv/music cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/screenshots /var/lib/mythtv/screenshots cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/trailers /var/lib/mythtv/trailers cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/videos /var/lib/mythtv/videos cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.250/mythtv/video_images /var/lib/mythtv/posters cifs guest,uid=1000,iocharset=utf8 0 0
```

In /var/lib/mythtv, this is the output of ls -laig:
```
 5112238 drwxr-xr-x  15 mythtv    4096 Aug 27 21:57 .
 5111922 drwxr-xr-x  68 root      4096 Jul  4 07:50 ..
90377317 drwxrwsrwx+  2 ssl-cert     0 Aug 30 07:57 banners
 5118489 drwxrwsr-x   2 mythtv    4096 Apr 17 18:34 bare-client
90377318 drwxrwsrwx+  2 ssl-cert     0 Aug 30 08:03 coverart
 5118491 drwxrwsr-x   2 mythtv    4096 Aug 30 07:57 db_backups
90377507 drwxrwsrwx+  2 ssl-cert     0 Aug 30 08:02 fanart
 5118493 drwxrwsr-x   2 mythtv    4096 Aug 30 07:57 livetv
90374146 drwxrwsrwx+ 29 ssl-cert     0 Jul  4 11:00 music
90376650 drwxrwxrwx+  2 ssl-cert     0 Oct 22  2011 posters
 5118496 drwxrwsr-x   2 mythtv   12288 Aug 30 07:57 recordings
90377356 drwxrwsrwx+  2 ssl-cert     0 Aug 30 07:57 screenshots
 5118498 drwxrwsr-x   2 mythtv    4096 Aug 30 07:57 streaming
90377357 drwxrwsrwx+  2 ssl-cert     0 Aug 30 07:57 trailers
90377005 drwxrwsrwx+ 92 ssl-cert     0 Aug 30 07:57 videos
```


Other outputs that may be useful:
james@mythtv:/var/lib/mythtv$ ps -fade |grep mythfrontend
```
james     1892     1  0 07:57 ?        00:00:00 /bin/sh /usr/bin/mythfrontend --service
james     1921  1892  1 07:57 ?        00:00:15 /usr/bin/mythfrontend.real --syslog local7
james     2428  2294  0 08:11 pts/1    00:00:00 grep --color=auto mythfrontend
```
james@mythtv:/var/lib/mythtv$ ps -fade |grep mythbackend
```
mythtv    1462     1  0 07:57 ?        00:00:01 /usr/bin/mythbackend --syslog local7 --user mythtv --daemon
james     2430  2294  0 08:12 pts/1    00:00:00 grep --color=auto mythbackend
```

james@mythtv:/var/lib/mythtv$ id james
```
uid=1000(james) gid=1000(james) groups=1000(james),4(adm),24(cdrom),27(sudo),30(dip),44(video),46(plugdev),110(sambashare),117(ssl-cert),124(mythtv),125(lpadmin)
```
james@mythtv:/var/lib/mythtv$ id mythtv
```
uid=115(mythtv) gid=124(mythtv) groups=124(mythtv),4(adm),20(dialout),24(cdrom),29(audio),44(video),110(sambashare),117(ssl-cert),1000(james)
```

james is the user account created when I installed Mythbuntu.

Here is a part of the /var/log/mythtv/mythfrontend.log that shows part of the error:
```
Aug 30 08:02:59 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatagrabber.cpp:455 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -a US -M Rio 2
Aug 30 08:03:00 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatacommon.cpp:1188 (ParseMetadataItem) Result Found, Season 0 Episode 0
Aug 30 08:03:00 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatagrabber.cpp:455 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a US -M Rio 2
Aug 30 08:03:00 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatadownload.cpp:176 (run) Returning Metadata Results: Rio 2 0 0
Aug 30 08:03:02 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatagrabber.cpp:455 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -a US -D 172385
Aug 30 08:03:03 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatacommon.cpp:1188 (ParseMetadataItem) Result Found, Season 0 Episode 0
Aug 30 08:03:03 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataDownload metadatadownload.cpp:176 (run) Returning Metadata Results: Rio 2 0 0
Aug 30 08:03:03 mythtv mythfrontend.real: mythfrontend[1921]: I MetadataImageDownload metadataimagedownload.cpp:244 (run) Metadata Image Download: http://image.tmdb.org/t/p/original/3U5aKvnnZcAmDm9VMK4eWuERSRV.jpg -> myth://Coverart@192.168.0.20/tmdb3.py_172385_coverart.jpg
Aug 30 08:03:03 mythtv mythfrontend.real: mythfrontend[1921]: E MetadataImageDownload metadataimagedownload.cpp:284 (run) Image Download: Error Writing Image to file: myth://Coverart@192.168.0.20/tmdb3.py_172385_coverart.jpg
Aug 30 08:03:04 mythtv mythfrontend.real: mythfrontend[1921]: E ImageLoad mythuihelper.cpp:1388 (LoadScaleImage) MythUIHelper: LoadScaleImage(myth://Coverart@192.168.0.20/tmdb3.py_172385_coverart.jpg) failed to load image
```


Here is a part of the /var/log/mythtv/mythbackend.log file that shows the permissions error:
```
Aug 30 08:03:03 mythtv mythbackend: mythbackend[1462]: E ProcessRequest threadedfilewriter.cpp:129 (Open) TFW(/var/lib/mythtv/coverart//tmdb3.py_172385_coverart.jpg:-1): Opening file '/var/lib/mythtv/coverart//tmdb3.py_172385_coverart.jpg'.#012#011#011#011eno: Permission denied (13)
Aug 30 08:03:03 mythtv mythbackend: mythbackend[1462]: E ProcessRequest ringbuffer.cpp:1691 (Write) RingBuf(/var/lib/mythtv/coverart//tmdb3.py_172385_coverart.jpg): Tried to write to a read only file.
Aug 30 08:03:03 mythtv mythbackend: mythbackend[1462]: E ProcessRequest mainserver.cpp:2308 (OpenAndUnlink) Error deleting '/var/lib/mythtv/coverart/tmdb3.py_172385_coverart.jpg' could not open #012#011#011#011eno: Permission denied (13)
Aug 30 08:03:03 mythtv mythbackend: mythbackend[1462]: E ProcessRequest mainserver.cpp:2286 (DeleteFile) Delete Error '/var/lib/mythtv/coverart/tmdb3.py_172385_coverart.jpg'#012#011#011#011eno: Permission denied (13)
Aug 30 08:03:03 mythtv mythbackend: mythbackend[1462]: E ProcessRequest mainserver.cpp:4839 (HandleDeleteFile) Error deleting file: /var/lib/mythtv/coverart/tmdb3.py_172385_coverart.jpg.
Aug 30 08:03:04 mythtv mythbackend: mythbackend[1462]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Playback
Aug 30 08:03:04 mythtv mythbackend: mythbackend[1462]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: mythtv as a client (events: 0)
Aug 30 08:03:04 mythtv mythbackend: mythbackend[1462]: I ProcessRequest mainserver.cpp:1561 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Aug 30 08:03:04 mythtv mythbackend: mythbackend[1462]: I ProcessRequest mainserver.cpp:1563 (HandleAnnounce) adding: mythtv as a remote file transfer
Aug 30 08:03:04 mythtv mythbackend: mythbackend[1462]: E ProcessRequest fileringbuffer.cpp:300 (OpenFile) FileRingBuf(/var/lib/mythtv/coverart//tmdb3.py_172385_coverart.jpg): OpenFile(): File too small (0B).
Aug 30 08:14:08 mythtv mythbackend: mythbackend[1462]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```


Immediately prior to this, I rebooted the mythtv and was able to retrieve the pictures for one of them (Rio), but when I tried the second (Rio 2), this happened.  I have been fighting this for a week and am not sure where to look now for fixing it.  This happens on all of the different movies I've tried, not just kids movies.  I get the metadata details, but no coverart/fanart to go with them.  When I try running a wget <url of image>, the picture is downloaded without any problem, so it doesn't seem to be a network connectivity issue.

James

---

