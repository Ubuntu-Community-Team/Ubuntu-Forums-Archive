---
title: "MythVideo can't find coverart"
date: 2014-04-02
forum: Mythbuntu
---

### Post by nhtrader on 2014-04-02
Mythbuntu v0.26.1-33 (FE&BE)
Ubuntu 12.04.4 LTS (x64)

Occasionally MythVideo Crashes and serves up a "report a problem" window.
Today this occurred when I tried to add the coverart for the Movie "Anchorman 2". I also tried another variation "Anchorman 2: The Legend Continues".
Below are the log entries:

```

I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running  Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M Anchorman 2
Apr   2 14:14:25 myth1 mythlogserver: mythfrontend[4432]: I CoreContext  videodlg.cpp:3265 (customEvent) No results found for Anchorman 2 0 0

Apr   2 14:19:23 myth1 mythlogserver: mythfrontend[4432]: I MetadataDownload  metadatadownload.cpp:222 (runGrabber) Running Grabber:  /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M Anchorman 2: The  Legend Continues
Apr  2 14:19:23 myth1 mythlogserver:  mythfrontend[4432]: I CoreContext videodlg.cpp:3265 (customEvent) No  results found for Anchorman 2: The Legend Continues 0 0
Apr  2  14:19:44 myth1 mythlogserver: mythfrontend[4432]: N CoreContext  mythmainwindow.cpp:2606 (PauseIdleTimer) Resuming idle timer
Apr  2  14:19:44 myth1 mythlogserver: mythfrontend[4432]: N CoreContext  mythmainwindow.cpp:2606 (PauseIdleTimer) Resuming idle timer
Apr  2  14:19:44 myth1 mythlogserver: mythfrontend[4432]: I CoreContext  bonjourregister.cpp:26 (~BonjourRegister) Bonjour: De-registering  service '_mythfrontend._tcp.' on 'Mythfrontend on myth1'
Apr  2  14:19:44 myth1 mythlogserver: mythfrontend[4432]: I CoreContext  AirPlay/mythraopdevice.cpp:68 (Cleanup) RAOP Device: Cleaning up.
Apr   2 14:19:44 myth1 mythlogserver: mythfrontend[4432]: I CoreContext  AirPlay/mythairplayserver.cpp:369 (Cleanup) AirPlay: Cleaning up.
Apr  2 14:19:44 myth1 mythlogserver: mythfrontend[4432]: I CoreContext main.cpp:251 (cleanup) Deleting UPnP client...
Apr   2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr   2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr   2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault  handler
Apr  2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted  handler
Apr  2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus  error handler
Apr  2 16:18:16 myth1 mythlogserver:  mythfrontend[5669]: I thread_unknown signalhandling.cpp:194  (SetHandlerPrivate) Setup Floating point exception handler
Apr  2  16:18:16 myth1 mythlogserver: mythfrontend[5669]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction  handler
Apr  2 16:18:16 myth1 mythlogserver: mythfrontend[5669]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Real-time signal 0 handler
Apr  2 16:18:16 myth1 mythlogserver:  mythfrontend[5669]: I thread_unknown signalhandling.cpp:194  (SetHandlerPrivate) Setup User defined signal 1 handler
Apr  2  16:18:16 myth1 mythlogserver: mythfrontend[5669]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2  handler

```

After reviewing the log, I opened a terminal and used the following command:
```

  /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M "Anchorman 2: The Legend Continues"
Traceback (most recent call last):
  File "/usr/share/mythtv/metadata/Movie/tmdb3.py", line 278, in <module>
    main()
  File "/usr/share/mythtv/metadata/Movie/tmdb3.py", line 269, in main
    buildList(args[0], opts)
  File "/usr/share/mythtv/metadata/Movie/tmdb3.py", line 121, in buildList
    for res in results:
  File "/usr/lib/python2.7/dist-packages/MythTV/tmdb3/pager.py", line 24, in next
    return self._parent[self._index]
  File "/usr/lib/python2.7/dist-packages/MythTV/tmdb3/pager.py", line 67, in __getitem__
    return self._data[index]
IndexError: list index out of range

```

As you can see, all sorts of problems arose. So I wondered if the image exists on "themoviedb.org". It does. Below is the URL for the image:
[http://image.tmdb.org/t/p/original/h1F7NF7h6IPnH1Xu4OcsDa8lryA.jpg](http://image.tmdb.org/t/p/original/h1F7NF7h6IPnH1Xu4OcsDa8lryA.jpg)


Two questions:
1. Why did this request for "Anchorman 2" cause a critical failure?

2. How can I manually add an image to MythTV's database? (to both coverart and fanart)

Below is the log from a successful gab  of "2 Guns" whereby MythVideo adds the image to both coverart and fanart:
```

Dec 20 01:07:47 myth1 mythlogserver: mythfrontend[4082]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M 2 Guns
Dec 20 01:07:50 myth1 mythlogserver: mythfrontend[4082]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: 2 Guns 0 0
Dec 20 01:07:51 myth1 mythlogserver: mythfrontend[4082]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb3.py -l en -D 136400
Dec 20 01:07:55 myth1 mythlogserver: mythfrontend[4082]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: 2 Guns 0 0
Dec 20 01:07:55 myth1 mythlogserver: mythfrontend[4082]: I MetadataImageDownload metadataimagedownload.cpp:223 (run) Metadata Image Download: http://image.tmdb.org/t/p/original/30lM3Uvzs6HOG5l4hzhwxYTWgd3.jpg -> myth://Coverart@10.10.10.10:6543/136400_coverart.jpg
Dec 20 01:07:56 myth1 mythlogserver: mythfrontend[4082]: I MetadataImageDownload metadataimagedownload.cpp:223 (run) Metadata Image Download: http://image.tmdb.org/t/p/original/oCWHk50Rq4UBNGXf20eX7JaXEgO.jpg -> myth://Fanart@10.10.10.10:6543/136400_fanart.jpg
Dec 20 01:07:57 myth1 mythlogserver: mythfrontend[4082]: I ImageLoad mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Dec 20 01:07:57 myth1 mythlogserver: mythfrontend[4082]: I ImageLoad mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75

```

---

### Post by blm-ubunet on 2014-04-05
I think the critical failure (your words) are just an error message that reveals the script found 0 matches/result.

In a terminal this:
```

/usr/share/mythtv/metadata/Movie/tmdb3.py -l en -M "Anchorman 2: The Legend Continues"
```
works just fine here...(my script lives in /usr/local/...)

Does the this folder/file exist for your BE user "mythtv" & FE user (if different) ?
```
/home/<user>/.mythtv/cache/pytmdb3.cache
```

If the file does not exist just create an empty file (with right name).

---

