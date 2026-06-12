---
title: "Iplayer streams ok but cannot download - Licence failed - error 3344"
date: 2011-01-08
forum: Multimedia Software
---

### Post by fitzy30 on 2011-01-08
Hi

I have just installed Ubuntu 10.10 Netbook Remix on a new Asus EEE PC 1015PEM. Very pleased so far but have spent too many hours trying to fix what looks like a Licence error - any help appreciated in suggestions to fix, driving me nuts.....

Iplayer.log shows

1/8/2011 10:44:28.631 [INFO] uk.co.bbc.LoggerStartupTask Application initialized. 61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1 BBCiPlayerDesktop
1/8/2011 10:44:30.164 [INFO] uk.co.bbc.LoggerStartupTask 
APPLICATION
  Application Version                      : 3.0.10
  Application Revision                     : 330009
  Application ID                           : BBCiPlayerDesktop
  Publisher ID                             : 61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1
  Application memory in use                : 18591744
  VM Version                               : 1.4 cyclone
  Application frame rate                   : 
  Script Timeout limit                     : 

PATHS
  Application storage                      : /home/netbook/.appdata/BBCiPlayerDesktop.61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1/Local Store
  Application directory                    : /opt/BBC iPlayer Desktop/share

RUNTIME
  AIR Runtime Patch Level                  : 17730
  AIR Runtime Version                      : 2.5.1.17730
  Flash Runtime Version                    : LNX 10,1,102,64
  Flash Runtime Type                       : Desktop

SYSTEM
  System OS                                : Linux
  Manufacturer                             : Adobe Linux
  CPU Architecture                         : x86
  Supports 32 Bit Processes                : true
  Supports 64 Bit Processes                : 
  Supports Docck Icon                      : 
  Supports System Tray Icon                : true
  Supports Menu                            : 
  Has Accessibility aids                   : 
  Has Audio Encoder                        : true
  Has Video Encoder                        : true
  Has MP3 Decoder                          : true
  Has Streaming audio                      : true
  Has Streaming video                      : true
  Max H.264 Level IDC supported            : 5.1
  Has Printing                             : true
  Has SSL socket via NetConnection         : true
  Running a debugger                       : 
  User has disk access                     : 
  App start at login                       : true

LANGUAGES
  System default langauge                  : en
  Preferred UI langagues in order          : en-GB

SCREENS
  Num screens                              : 1

SCREEN 0
   Color Depth                             : 24
   Visible Bounds                          : l:58 r:1024 t:24 b:600
   Bounds                                  : l:0 r:1024 t:0 b:600

1/8/2011 10:44:38.763 [INFO] uk.co.bbc.NetworkMonitor Online: true
1/8/2011 10:44:38.907 [INFO] uk.co.bbc.UpdateScheduledDownloadsCommand Updating user schedule to Anytime
1/8/2011 10:44:38.912 [WARN] uk.co.bbc.CrashRecoveryStartupTask Crash detected!
1/8/2011 10:44:38.973 [INFO] uk.co.bbc.RepositoryManager Setting repository /home/netbook/Videos/BBC iPlayer/repository.
1/8/2011 10:44:39.824 [INFO] uk.co.bbc.NetworkMonitor Online: true
1/8/2011 10:44:39.878 [INFO] uk.co.bbc.IACManager BBC iPlayer Desktop domain is app#BBCiPlayerDesktop.61DB7A798358575D6A969CCD73DDBBD723A6DA9D.1
1/8/2011 10:44:39.966 [INFO] uk.co.bbc.TokenizerUtils Instructions ''
1/8/2011 10:44:39.967 [INFO] uk.co.bbc.TokenizerUtils Token[0] 'undefined'
1/8/2011 10:44:41.025 [INFO] uk.co.bbc.NetworkMonitor Online: false
1/8/2011 10:44:41.026 [INFO] uk.co.bbc.NetworkMonitor Online: false
1/8/2011 10:44:41.703 [INFO] uk.co.bbc.RepositoryManager Setting repository /home/netbook/Videos/BBC iPlayer/repository.
1/8/2011 10:44:44.868 [INFO] uk.co.bbc.ApplicationUpdater checkUpdates from [http://www.bbc.co.uk/iplayer/dm/live/update2.xml?1294483484866](http://www.bbc.co.uk/iplayer/dm/live/update2.xml?1294483484866)
1/8/2011 10:44:54.752 [INFO] uk.co.bbc.NetworkMonitor Online: true
1/8/2011 10:44:54.753 [INFO] uk.co.bbc.NetworkMonitor Online: true
1/8/2011 10:45:51.432 [INFO] uk.co.bbc.TokenizerUtils Instructions '-d aHR0cDovL3d3dy5iYmMuY28udWsvaXBsYXllci9wbGF5bGlzdC9iMDB3d3JndC8= b00wwqgd null null My4w b00wwrgt'
1/8/2011 10:45:51.436 [INFO] uk.co.bbc.TokenizerUtils Token[0] '-d aHR0cDovL3d3dy5iYmMuY28udWsvaXBsYXllci9wbGF5bGlzdC9iMDB3d3JndC8= b00wwqgd null null My4w b00wwrgt'
1/8/2011 10:45:51.451 [INFO] uk.co.bbc.ContentItemsProxy Getting content for version pid b00wwqgd from [http://www.bbc.co.uk/iplayer/playlist/b00wwrgt/b00wwqgd/media_set/pc-download](http://www.bbc.co.uk/iplayer/playlist/b00wwrgt/b00wwqgd/media_set/pc-download)
1/8/2011 10:45:51.464 [INFO] uk.co.bbc.ContentItemsProxy Resolving content items (playlist, media selector etc) for vpid: b00wwqgd
1/8/2011 10:45:53.452 [INFO] uk.co.bbc.ContentItemsProxy Playlist file obtained for b00wwqgd.
1/8/2011 10:45:53.490 [INFO] uk.co.bbc.ContentItem The content item with vpid b00wwqgd isPlayable state was false and is now false.
1/8/2011 10:45:53.493 [INFO] uk.co.bbc.ContentFactory The ondemand start time for {3} is set to: Fri Jan 7 21:00:00 GMT+0000 2011 The isPastOnDemandStartDate is set to: true
1/8/2011 10:45:53.499 [INFO] uk.co.bbc.ContentItem The content item with vpid b00wwqgd isPlayable state was false and is now false.
1/8/2011 10:45:53.623 [INFO] uk.co.bbc.components.air.download.Download Requesting HEAD to gather download information for [http://node2.bbcimg.co.uk/iplayer/images/episode/b00wwrgt_640_360.jpg](http://node2.bbcimg.co.uk/iplayer/images/episode/b00wwrgt_640_360.jpg)
1/8/2011 10:45:53.627 [INFO] uk.co.bbc.components.air.download.Download Requesting HEAD to gather download information for [http://www.bbc.co.uk/iplayer/subtitles/ng/b00w/wqgd/b00wwqgd_prepared.xml](http://www.bbc.co.uk/iplayer/subtitles/ng/b00w/wqgd/b00wwqgd_prepared.xml)
1/8/2011 10:45:53.631 [INFO] uk.co.bbc.components.air.download.Download Requesting HEAD to gather download information for [http://electradl.iplayer.bbc.co.uk/electra/cps/1500kbps/b00wwqgd_hi_185231981.mp4](http://electradl.iplayer.bbc.co.uk/electra/cps/1500kbps/b00wwqgd_hi_185231981.mp4)
1/8/2011 10:45:53.684 [INFO] uk.co.bbc.AbstractProgrammeInfo Creating ProgrammeDownloading
1/8/2011 10:45:54.591 [INFO] uk.co.bbc.ContentFactory The availability start date was determined from the media selector response header as: Sat Jan 8 10:45:54 GMT+0000 2011 for epid:b00wwrgt vpid:b00wwqgd
1/8/2011 10:45:54.595 [INFO] uk.co.bbc.ContentItemsProxy ContentManager initialization completed
1/8/2011 10:46:00.807 [INFO] uk.co.bbc.LicenceManager Getting licence for /home/netbook/Videos/BBC iPlayer/repository/b00wwqgd/b00wwqgd_hi_185231981.part
1/8/2011 10:46:01.209 [ERROR] uk.co.bbc.ContentItemsProxy Licence aquisition failed for b00wwqgd, because: undefinedErrorId: 3344. SuberrorId: 6. 
1/8/2011 10:46:01.218 [INFO] uk.co.bbc.ContentItemsProxy Removing content with vipd b00wwqgd
1/8/2011 10:46:01.655 [ERROR] uk.co.bbc.LicenceManager Licence failed. undefinedErrorId: 3344. SuberrorId: 6.

---

### Post by fitzy30 on 2011-01-15
Apparently some sort of ELS issue:

[http://kb2.adobe.com/cps/492/cpsid_49267.html](http://kb2.adobe.com/cps/492/cpsid_49267.html)

Switched to "desktop login" on the login manager and removed 'netbook-edition' in synaptic.

SOLVED

---

