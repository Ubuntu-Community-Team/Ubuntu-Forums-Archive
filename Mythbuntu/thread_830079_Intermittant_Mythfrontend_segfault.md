---
title: "Intermittant Mythfrontend segfault"
date: 2008-06-15
forum: Mythbuntu
---

### Post by tohc1 on 2008-06-15
I've been trying to get mythbuntu 8.04 installed on my mediapc and have run into a problem. 

When the computer boots mythfrontend sometimes starts but mostly doesn't, looking the system messages shows a segfault:
> 
[   90.413066] mythfrontend.re[6492]: segfault at fc1dfd80 rip 7f0d04fbc330 rsp 7fff1476a3b8 error 6

Running mythfrontend from a consoles gives the following:

> 2008-06-15 16:55:52.185 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-15 16:55:52.721 XScreenSaver support enabled
2008-06-15 16:55:52.722 DPMS is active.
2008-06-15 16:55:52.723 Empty LocalHostName.
2008-06-15 16:55:52.723 Using localhost value of mediapc
2008-06-15 16:55:52.742 New DB connection, total: 1
2008-06-15 16:55:52.749 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:55:52.754 Closing DB connection named 'DBManager0'
2008-06-15 16:55:52.791 Primary screen 0.
2008-06-15 16:55:52.792 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:55:52.794 Using screen 0, 1280x1024 at 0,0
2008-06-15 16:55:52.805 New DB connection, total: 2
2008-06-15 16:55:52.806 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:55:52.808 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-06-15 16:55:52.808 Enabled verbose msgs:  important general
2008-06-15 16:55:52.926 Unable to parse themeinfo.xml for glass-wide
2008-06-15 16:55:52.926 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-15 16:55:53.142 Unable to parse themeinfo.xml for glass-wide
2008-06-15 16:55:53.143 The theme (glass-wide) is missing a themeinfo.xml file
DisplaResX: Unable to XRRgetScreenInfo
DisplaResX: Unable to XRRgetScreenInfo
2008-06-15 16:55:53.490 Primary screen 0.
2008-06-15 16:55:53.491 Using screen 0, 1280x1024 at 0,0
2008-06-15 16:55:53.494 Switching to wide mode (Mythbuntu-8.04-wide)
Segmentation fault

There is nothing in /var/crash and ocasionaly (about 1 in 3 times) the frontend will start.

The DisplaResX bit is because I found some posts suggesting disabling RandR in xorg.conf (I've also tried disable xinerama and combinations) but this didn't solve the problem.

My systems specs:

Biostar Ta690G motherboard (onboard ati x1250 graphics)
AMD X2 BE-2300
1Gb ram
logilink wl0006 (rtl8187b) usb wirless stick
Hauppague Nova-T 500
Hauppague hvr 1100

Other possibly relevant things...
I've installed the latest Ati drivers using the envyNG script.
The wlan drivers I had to compile manually using a patch for the 8187b chips and for the nova-T I've installed the latest drivers from v4linux with a patch to stop a remote key-press problem. These all seem to be working fine and I'm pretty sure are not causing the problem as it also happened with a fresh install.

Here are the full outputs of "mythfrontend -v all" and "dmesg"

```
2008-06-15 16:45:45.041 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-15 16:45:45.041 UPnp - Constructor
2008-06-15 16:45:45.041 MediaRenderer::Begin
2008-06-15 16:45:45.043 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2008-06-15 16:45:45.044 HttpServer( 6547 ) - SharePath = /usr/share/mythtv/
2008-06-15 16:45:45.044 UPnp::Initialize - Begin
2008-06-15 16:45:45.044 UPnp::Initialize - Starting TaskQueue
2008-06-15 16:45:45.045 UPnp::Initialize - Creating SSDP Thread at port 6547
2008-06-15 16:45:45.047 UPnp::Initialize - End
2008-06-15 16:45:45.047 MediaRenderer::Creating UPnp Description
2008-06-15 16:45:45.047 MediaRenderer::Registering CMGR Service.
2008-06-15 16:45:45.048 UPnp::Start - Starting SSDP Thread (Multicast)
2008-06-15 16:45:45.048 UPnp::Start - Enabling Notifications
2008-06-15 16:45:45.048 SSDP::EnableNotifications() - creating new task
2008-06-15 16:45:45.048 SSDP::EnableNotifications() - sending NTS_byebye
2008-06-15 16:45:45.048 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=eb85d5b1-1aea-40d2-9dea-761fdbac711b
2008-06-15 16:45:45.049 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.050 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::upnp:rootdevice
Cache  =max-age=3600
2008-06-15 16:45:45.183 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.184 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::upnp:rootdevice
Cache  =max-age=3600
2008-06-15 16:45:45.184 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.184 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
Cache  =max-age=3600
2008-06-15 16:45:45.332 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.332 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
Cache  =max-age=3600
2008-06-15 16:45:45.333 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.333 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-15 16:45:45.544 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.544 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-15 16:45:45.544 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.545 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-15 16:45:45.562 SSDP::EnableNotifications() - sending NTS_alive
2008-06-15 16:45:45.562 SSDP::EnableNotifications() - Task added to UPnP queue
2008-06-15 16:45:45.562 UPnp::Start - Returning
2008-06-15 16:45:45.562 MediaRenderer::End
2008-06-15 16:45:45.565 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.566 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-15 16:45:45.579 XScreenSaver support enabled
2008-06-15 16:45:45.580 DPMS is active.
2008-06-15 16:45:45.581 Empty LocalHostName.
2008-06-15 16:45:45.581 Using localhost value of mediapc
2008-06-15 16:45:45.582 MCP::DefaultUPnP() - No default UPnP backend
2008-06-15 16:45:45.598 New DB connection, total: 1
2008-06-15 16:45:45.605 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:45:45.608 Closing DB connection named 'DBManager0'
2008-06-15 16:45:45.608 Clearing Settings Cache.
2008-06-15 16:45:45.610 Primary screen 0.
2008-06-15 16:45:45.611 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:45:45.613 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.613 Using screen 0, 1280x1024 at 0,0
2008-06-15 16:45:45.614 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.615 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-06-15 16:45:45.616 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.617 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-06-15 16:45:45.618 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.619 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-06-15 16:45:45.620 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.621 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-06-15 16:45:45.622 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.622 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-06-15 16:45:45.629 Enabling Settings Cache.
2008-06-15 16:45:45.629 Clearing Settings Cache.
2008-06-15 16:45:45.629 user: 1000 effective user: 1000 before privileged thread
2008-06-15 16:45:45.629 user: 1000 effective user: 1000 run_priv_thread
2008-06-15 16:45:45.629 user: 1000 effective user: 1000 after privileged thread
2008-06-15 16:45:45.630 Disabling Settings Cache.
2008-06-15 16:45:45.630 Clearing Settings Cache.
2008-06-15 16:45:45.630 MSqlQuery: CREATE TABLE IF NOT EXISTS schemalock ( schemalock int(1));
2008-06-15 16:45:45.631 MSqlQuery: LOCK TABLE schemalock WRITE;
2008-06-15 16:45:45.632 New DB connection, total: 2
2008-06-15 16:45:45.633 Connected to database 'mythconverg' at host: localhost
2008-06-15 16:45:45.634 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.635 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname IS NULL;
2008-06-15 16:45:45.635 MSqlQuery: UNLOCK TABLES;
2008-06-15 16:45:45.636 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaAutoUpgrade' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.637 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaAutoUpgrade' AND hostname IS NULL;
2008-06-15 16:45:45.637 Enabling Settings Cache.
2008-06-15 16:45:45.637 Clearing Settings Cache.
2008-06-15 16:45:45.637 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-06-15 16:45:45.637 Enabled verbose msgs: all
2008-06-15 16:45:45.638 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerHost' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.639 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerHost' AND hostname IS NULL;
2008-06-15 16:45:45.640 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.641 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname IS NULL;
2008-06-15 16:45:45.642 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDEnable' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.643 MSqlQuery: SELECT data FROM settings WHERE value = 'Language' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.645 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.646 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::upnp:rootdevice
Cache  =max-age=3600
2008-06-15 16:45:45.647 MSqlQuery: SELECT name FROM displayprofilegroups WHERE hostname = 'mediapc'
2008-06-15 16:45:45.648 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultVideoPlaybackProfile' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.649 MSqlQuery: SELECT name FROM displayprofilegroups WHERE hostname = 'mediapc'
2008-06-15 16:45:45.650 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'CPU+' AND       hostname = 'mediapc'
2008-06-15 16:45:45.650 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 2 ORDER BY profileid
2008-06-15 16:45:45.654 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'CPU++' AND       hostname = 'mediapc'
2008-06-15 16:45:45.654 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 1 ORDER BY profileid
2008-06-15 16:45:45.655 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'CPU--' AND       hostname = 'mediapc'
2008-06-15 16:45:45.656 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 3 ORDER BY profileid
2008-06-15 16:45:45.659 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'High Quality' AND       hostname = 'mediapc'
2008-06-15 16:45:45.659 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 4 ORDER BY profileid
2008-06-15 16:45:45.661 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'Mine' AND       hostname = 'mediapc'
2008-06-15 16:45:45.662 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 7 ORDER BY profileid
2008-06-15 16:45:45.663 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'Normal' AND       hostname = 'mediapc'
2008-06-15 16:45:45.663 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 5 ORDER BY profileid
2008-06-15 16:45:45.666 MSqlQuery: SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'Slim' AND       hostname = 'mediapc'
2008-06-15 16:45:45.666 MSqlQuery: SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = 6 ORDER BY profileid
2008-06-15 16:45:45.669 MSqlQuery: SELECT DISTINCT recgroup from recorded;
2008-06-15 16:45:45.669 MSqlQuery: SELECT DISTINCT category from recorded;
2008-06-15 16:45:45.680 MSqlQuery: SELECT data FROM settings WHERE value = 'RealtimePriority' AND hostname = 'mediapc'
2008-06-15 16:45:45.681 MSqlQuery: SELECT data FROM settings WHERE value = 'DecodeExtraAudio' AND hostname = 'mediapc'
2008-06-15 16:45:45.682 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioNag' AND hostname = 'mediapc'
2008-06-15 16:45:45.683 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoTimebase' AND hostname = 'mediapc'
2008-06-15 16:45:45.684 MSqlQuery: SELECT data FROM settings WHERE value = 'ClearSavedPosition' AND hostname = 'mediapc'
2008-06-15 16:45:45.685 MSqlQuery: SELECT data FROM settings WHERE value = 'AltClearSavedPosition' AND hostname = 'mediapc'
2008-06-15 16:45:45.686 MSqlQuery: SELECT data FROM settings WHERE value = 'JumpToProgramOSD' AND hostname = 'mediapc'
2008-06-15 16:45:45.687 MSqlQuery: SELECT data FROM settings WHERE value = 'ContinueEmbeddedTVPlay' AND hostname = 'mediapc'
2008-06-15 16:45:45.689 MSqlQuery: SELECT data FROM settings WHERE value = 'AutomaticSetWatched' AND hostname = 'mediapc'
2008-06-15 16:45:45.690 MSqlQuery: SELECT data FROM settings WHERE value = 'AlwaysStreamFiles' AND hostname = 'mediapc'
2008-06-15 16:45:45.691 MSqlQuery: SELECT data FROM settings WHERE value = 'UseOpenGLVSync' AND hostname = 'mediapc'
2008-06-15 16:45:45.692 MSqlQuery: SELECT data FROM settings WHERE value = 'UseOutputPictureControls' AND hostname = 'mediapc'
2008-06-15 16:45:45.693 MSqlQuery: SELECT data FROM settings WHERE value = 'VertScanPercentage' AND hostname = 'mediapc'
2008-06-15 16:45:45.694 MSqlQuery: SELECT data FROM settings WHERE value = 'HorizScanPercentage' AND hostname = 'mediapc'
2008-06-15 16:45:45.695 MSqlQuery: SELECT data FROM settings WHERE value = 'XScanDisplacement' AND hostname = 'mediapc'
2008-06-15 16:45:45.696 MSqlQuery: SELECT data FROM settings WHERE value = 'YScanDisplacement' AND hostname = 'mediapc'
2008-06-15 16:45:45.697 MSqlQuery: SELECT data FROM settings WHERE value = 'AspectOverride' AND hostname = 'mediapc'
2008-06-15 16:45:45.698 MSqlQuery: SELECT data FROM settings WHERE value = 'AdjustFill' AND hostname = 'mediapc'
2008-06-15 16:45:45.699 MSqlQuery: SELECT data FROM settings WHERE value = 'LetterboxColour' AND hostname = 'mediapc'
2008-06-15 16:45:45.700 MSqlQuery: SELECT data FROM settings WHERE value = 'PIPLocation' AND hostname = 'mediapc'
2008-06-15 16:45:45.702 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackExitPrompt' AND hostname = 'mediapc'
2008-06-15 16:45:45.703 MSqlQuery: SELECT data FROM settings WHERE value = 'EndOfRecordingExitPrompt' AND hostname = 'mediapc'
2008-06-15 16:45:45.703 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultVideoPlaybackProfile' AND hostname = 'mediapc'
2008-06-15 16:45:45.704 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayBoxOrdering' AND hostname = 'mediapc'
2008-06-15 16:45:45.705 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayBoxEpisodeSort' AND hostname = 'mediapc'
2008-06-15 16:45:45.706 MSqlQuery: SELECT data FROM settings WHERE value = 'GeneratePreviewPixmaps' AND hostname = 'mediapc'
2008-06-15 16:45:45.707 MSqlQuery: SELECT data FROM settings WHERE value = 'PreviewPixmapOffset'
2008-06-15 16:45:45.708 MSqlQuery: SELECT data FROM settings WHERE value = 'PreviewFromBookmark' AND hostname = 'mediapc'
2008-06-15 16:45:45.710 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackPreview' AND hostname = 'mediapc'
2008-06-15 16:45:45.711 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackBoxStartInTitle' AND hostname = 'mediapc'
2008-06-15 16:45:45.712 MSqlQuery: SELECT data FROM settings WHERE value = 'ShowGroupInfo' AND hostname = 'mediapc'
2008-06-15 16:45:45.713 MSqlQuery: SELECT data FROM settings WHERE value = 'AllRecGroupPassword'
2008-06-15 16:45:45.714 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplayRecGroup' AND hostname = 'mediapc'
2008-06-15 16:45:45.715 MSqlQuery: SELECT data FROM settings WHERE value = 'QueryInitialFilter' AND hostname = 'mediapc'
2008-06-15 16:45:45.716 MSqlQuery: SELECT data FROM settings WHERE value = 'RememberRecGroup' AND hostname = 'mediapc'
2008-06-15 16:45:45.717 MSqlQuery: SELECT data FROM settings WHERE value = 'DispRecGroupAsAllProg' AND hostname = 'mediapc'
2008-06-15 16:45:45.718 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVInAllPrograms' AND hostname = 'mediapc'
2008-06-15 16:45:45.719 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplayGroupDefaultView' AND hostname = 'mediapc'
2008-06-15 16:45:45.720 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplayGroupTitleSort' AND hostname = 'mediapc'
2008-06-15 16:45:45.721 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackWatchList' AND hostname = 'mediapc'
2008-06-15 16:45:45.723 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackWLStart' AND hostname = 'mediapc'
2008-06-15 16:45:45.724 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackWLAutoExpire' AND hostname = 'mediapc'
2008-06-15 16:45:45.725 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackWLMaxAge' AND hostname = 'mediapc'
2008-06-15 16:45:45.726 MSqlQuery: SELECT data FROM settings WHERE value = 'PlaybackWLBlackOut' AND hostname = 'mediapc'
2008-06-15 16:45:45.727 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartForward' AND hostname = 'mediapc'
2008-06-15 16:45:45.728 MSqlQuery: SELECT data FROM settings WHERE value = 'StickyKeys' AND hostname = 'mediapc'
2008-06-15 16:45:45.729 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReposTime' AND hostname = 'mediapc'
2008-06-15 16:45:45.730 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReverse' AND hostname = 'mediapc'
2008-06-15 16:45:45.731 MSqlQuery: SELECT data FROM settings WHERE value = 'ExactSeeking' AND hostname = 'mediapc'
2008-06-15 16:45:45.732 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommercialSkip' AND hostname = 'mediapc'
2008-06-15 16:45:45.733 MSqlQuery: SELECT data FROM settings WHERE value = 'CommRewindAmount' AND hostname = 'mediapc'
2008-06-15 16:45:45.734 MSqlQuery: SELECT data FROM settings WHERE value = 'CommNotifyAmount' AND hostname = 'mediapc'
2008-06-15 16:45:45.735 MSqlQuery: SELECT data FROM settings WHERE value = 'MaximumCommercialSkip'
2008-06-15 16:45:45.736 MSqlQuery: SELECT data FROM settings WHERE value = 'MergeShortCommBreaks'
2008-06-15 16:45:45.737 MSqlQuery: SELECT data FROM settings WHERE value = 'CommSkipAllBlanks'
2008-06-15 16:45:45.738 MSqlQuery: SELECT data FROM settings WHERE value = 'PVR350OutputEnable' AND hostname = 'mediapc'
2008-06-15 16:45:45.739 MSqlQuery: SELECT data FROM settings WHERE value = 'PVR350VideoDev' AND hostname = 'mediapc'
2008-06-15 16:45:45.740 MSqlQuery: SELECT data FROM settings WHERE value = 'PVR350EPGAlphaValue' AND hostname = 'mediapc'
2008-06-15 16:45:45.741 MSqlQuery: SELECT data FROM settings WHERE value = 'PVR350InternalAudioOnly' AND hostname = 'mediapc'
2008-06-15 16:45:45.805 Unable to parse themeinfo.xml for glass-wide
2008-06-15 16:45:45.805 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-15 16:45:45.821 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.821 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::upnp:rootdevice
Cache  =max-age=3600
2008-06-15 16:45:45.821 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:45.822 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
Cache  =max-age=3600
2008-06-15 16:45:45.934 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDTheme' AND hostname = 'mediapc'
2008-06-15 16:45:45.935 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDGeneralTimeout' AND hostname = 'mediapc'
2008-06-15 16:45:45.936 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDProgramInfoTimeout' AND hostname = 'mediapc'
2008-06-15 16:45:45.937 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.939 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDThemeFontSizeType' AND hostname = 'mediapc'
2008-06-15 16:45:45.940 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableMHEG' AND hostname = 'mediapc'
2008-06-15 16:45:45.941 MSqlQuery: SELECT data FROM settings WHERE value = 'PersistentBrowseMode' AND hostname = 'mediapc'
2008-06-15 16:45:45.942 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDNotifyTimeout' AND hostname = 'mediapc'
2008-06-15 16:45:45.943 MSqlQuery: SELECT data FROM settings WHERE value = 'UDPNotifyPort' AND hostname = 'mediapc'
2008-06-15 16:45:45.944 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCCFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.945 MSqlQuery: SELECT data FROM settings WHERE value = 'CCBackground' AND hostname = 'mediapc'
2008-06-15 16:45:45.946 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultCCMode' AND hostname = 'mediapc'
2008-06-15 16:45:45.947 MSqlQuery: SELECT data FROM settings WHERE value = 'Prefer708Captions' AND hostname = 'mediapc'
2008-06-15 16:45:45.948 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708TextZoom' AND hostname = 'mediapc'
2008-06-15 16:45:45.950 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708DefaultFontType' AND hostname = 'mediapc'
2008-06-15 16:45:45.951 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708MonoSerifFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.952 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708PropSerifFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.953 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708MonoSansSerifFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.954 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708PropSansSerifFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.955 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CasualFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.956 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CursiveFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.957 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CapitalsFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.958 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708MonoSerifItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.959 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708PropSerifItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.961 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708MonoSansSerifItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.962 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708PropSansSerifItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.963 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CasualItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.964 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CursiveItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.965 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDCC708CapitalsItalicFont' AND hostname = 'mediapc'
2008-06-15 16:45:45.967 MSqlQuery: SELECT name, id FROM recordingprofiles WHERE profilegroup = 6 ORDER BY id
2008-06-15 16:45:45.969 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc1' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.970 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc1' AND hostname IS NULL;
2008-06-15 16:45:45.971 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc2' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.972 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc2' AND hostname IS NULL;
2008-06-15 16:45:45.973 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc3' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.974 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc3' AND hostname IS NULL;
2008-06-15 16:45:45.975 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc4' AND hostname = 'mediapc' ;
2008-06-15 16:45:45.976 MSqlQuery: SELECT data FROM settings WHERE value = 'UserJobDesc4' AND hostname IS NULL;
2008-06-15 16:45:45.978 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelOrdering' AND hostname = 'mediapc'
2008-06-15 16:45:45.979 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelFormat' AND hostname = 'mediapc'
2008-06-15 16:45:45.980 MSqlQuery: SELECT data FROM settings WHERE value = 'LongChannelFormat' AND hostname = 'mediapc'
2008-06-15 16:45:45.981 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartChannelChange' AND hostname = 'mediapc'
2008-06-15 16:45:45.982 MSqlQuery: SELECT data FROM settings WHERE value = 'LastFreeCard'
2008-06-15 16:45:45.983 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVPriority'
2008-06-15 16:45:45.984 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireMethod'
2008-06-15 16:45:45.985 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireDefault'
2008-06-15 16:45:45.986 MSqlQuery: SELECT data FROM settings WHERE value = 'RerecordWatched'
2008-06-15 16:45:45.987 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireWatchedPriority'
2008-06-15 16:45:45.988 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireLiveTVMaxAge'
2008-06-15 16:45:45.989 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireDayPriority'
2008-06-15 16:45:45.990 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireExtraSpace'
2008-06-15 16:45:45.990 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoExpireInsteadOfDelete'
2008-06-15 16:45:45.991 MSqlQuery: SELECT data FROM settings WHERE value = 'DeletedFifoOrder'
2008-06-15 16:45:45.992 MSqlQuery: SELECT data FROM settings WHERE value = 'DeletedMaxAge'
2008-06-15 16:45:45.993 MSqlQuery: SELECT data FROM settings WHERE value = 'CommercialSkipMethod'
2008-06-15 16:45:45.994 MSqlQuery: SELECT data FROM settings WHERE value = 'AggressiveCommDetect'
2008-06-15 16:45:45.995 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultTranscoder'
2008-06-15 16:45:45.996 MSqlQuery: SELECT data FROM settings WHERE value = 'DeferAutoTranscodeDays'
2008-06-15 16:45:45.997 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommercialFlag'
2008-06-15 16:45:45.998 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoTranscode'
2008-06-15 16:45:45.999 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoRunUserJob1'
2008-06-15 16:45:46.000 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoRunUserJob2'
2008-06-15 16:45:46.001 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoRunUserJob3'
2008-06-15 16:45:46.002 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoRunUserJob4'
2008-06-15 16:45:46.003 MSqlQuery: SELECT data FROM settings WHERE value = 'RecordPreRoll'
2008-06-15 16:45:46.004 MSqlQuery: SELECT data FROM settings WHERE value = 'RecordOverTime'
2008-06-15 16:45:46.005 MSqlQuery: SELECT data FROM settings WHERE value = 'OverTimeCategory'
2008-06-15 16:45:46.006 MSqlQuery: SELECT data FROM settings WHERE value = 'CategoryOverTime'
2008-06-15 16:45:46.008 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGFillType' AND hostname = 'mediapc'
2008-06-15 16:45:46.009 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGShowCategoryColors' AND hostname = 'mediapc'
2008-06-15 16:45:46.010 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGShowCategoryText' AND hostname = 'mediapc'
2008-06-15 16:45:46.011 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGScrollType' AND hostname = 'mediapc'
2008-06-15 16:45:46.012 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGShowChannelIcon' AND hostname = 'mediapc'
2008-06-15 16:45:46.013 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGShowFavorites' AND hostname = 'mediapc'
2008-06-15 16:45:46.014 MSqlQuery: SELECT data FROM settings WHERE value = 'WatchTVGuide' AND hostname = 'mediapc'
2008-06-15 16:45:46.015 MSqlQuery: SELECT data FROM settings WHERE value = 'chanPerPage' AND hostname = 'mediapc'
2008-06-15 16:45:46.017 MSqlQuery: SELECT data FROM settings WHERE value = 'timePerPage' AND hostname = 'mediapc'
2008-06-15 16:45:46.018 MSqlQuery: SELECT data FROM settings WHERE value = 'UnknownTitle' AND hostname = 'mediapc'
2008-06-15 16:45:46.019 MSqlQuery: SELECT data FROM settings WHERE value = 'UnknownCategory' AND hostname = 'mediapc'
2008-06-15 16:45:46.020 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultTVChannel' AND hostname = 'mediapc'
2008-06-15 16:45:46.021 MSqlQuery: SELECT data FROM settings WHERE value = 'SelectChangesChannel' AND hostname = 'mediapc'
2008-06-15 16:45:46.022 MSqlQuery: SELECT data FROM settings WHERE value = 'SelChangeRecThreshold' AND hostname = 'mediapc'
2008-06-15 16:45:46.023 MSqlQuery: SELECT data FROM settings WHERE value = 'EPGEnableJumpToChannel'
2008-06-15 16:45:46.049 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:46.050 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b
Cache  =max-age=3600
2008-06-15 16:45:46.050 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:46.050 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-15 16:45:46.084 Unable to parse themeinfo.xml for glass-wide
2008-06-15 16:45:46.084 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-15 16:45:46.226 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:46.226 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-06-15 16:45:46.226 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:46.227 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-15 16:45:46.260 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.261 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeRefreshRate' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.262 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeRefreshRate' AND hostname IS NULL;
2008-06-15 16:45:46.263 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeForceAspect' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.264 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeForceAspect' AND hostname IS NULL;
2008-06-15 16:45:46.266 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.267 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname IS NULL;
2008-06-15 16:45:46.268 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.269 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname IS NULL;
2008-06-15 16:45:46.270 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.271 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname IS NULL;
2008-06-15 16:45:46.272 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.273 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeRefreshRate' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.274 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeForceAspect' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.275 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.276 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname IS NULL;
2008-06-15 16:45:46.277 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.277 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname IS NULL;
2008-06-15 16:45:46.278 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.279 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname IS NULL;
2008-06-15 16:45:46.280 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.281 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeRefreshRate0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.282 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeForceAspect0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.284 max_width: 0 max_height: 0
2008-06-15 16:45:46.286 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language0' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.336 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language1' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.353 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-06-15 16:45:46.354 SSDP::ProcessNotify
DescURL=http://192.168.1.2:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:eb85d5b1-1aea-40d2-9dea-761fdbac711b::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-06-15 16:45:46.389 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'mediapc'
2008-06-15 16:45:46.391 MSqlQuery: SELECT data FROM settings WHERE value = 'RandomTheme' AND hostname = 'mediapc'
2008-06-15 16:45:46.392 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemeCacheSize' AND hostname = 'mediapc'
2008-06-15 16:45:46.393 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemePainter' AND hostname = 'mediapc'
2008-06-15 16:45:46.396 MSqlQuery: SELECT data FROM settings WHERE value = 'Style' AND hostname = 'mediapc'
2008-06-15 16:45:46.397 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemeFontSizeType' AND hostname = 'mediapc'
2008-06-15 16:45:46.399 MSqlQuery: SELECT data FROM settings WHERE value = 'MenuTheme' AND hostname = 'mediapc'
2008-06-15 16:45:46.399 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'mediapc'
2008-06-15 16:45:46.400 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'mediapc'
2008-06-15 16:45:46.401 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiSizeForTV' AND hostname = 'mediapc'
2008-06-15 16:45:46.401 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'mediapc'
2008-06-15 16:45:46.402 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'mediapc'
2008-06-15 16:45:46.403 MSqlQuery: SELECT data FROM settings WHERE value = 'HideMouseCursor' AND hostname = 'mediapc'
2008-06-15 16:45:46.403 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'mediapc'
2008-06-15 16:45:46.404 MSqlQuery: SELECT data FROM settings WHERE value = 'Language' AND hostname = 'mediapc'
2008-06-15 16:45:46.404 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language0' AND hostname = 'mediapc'
2008-06-15 16:45:46.405 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language1' AND hostname = 'mediapc'
2008-06-15 16:45:46.406 MSqlQuery: SELECT data FROM settings WHERE value = 'DateFormat' AND hostname = 'mediapc'
2008-06-15 16:45:46.407 MSqlQuery: SELECT data FROM settings WHERE value = 'ShortDateFormat' AND hostname = 'mediapc'
2008-06-15 16:45:46.408 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'mediapc'
2008-06-15 16:45:46.409 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontSmall' AND hostname = 'mediapc'
2008-06-15 16:45:46.410 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontMedium' AND hostname = 'mediapc'
2008-06-15 16:45:46.411 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontBig' AND hostname = 'mediapc'
2008-06-15 16:45:46.412 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFonTweak' AND hostname = 'mediapc'
2008-06-15 16:45:46.413 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayBoxTransparency' AND hostname = 'mediapc'
2008-06-15 16:45:46.414 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayBoxShading' AND hostname = 'mediapc'
2008-06-15 16:45:46.415 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVirtualKeyboard' AND hostname = 'mediapc'
2008-06-15 16:45:46.416 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDEnable' AND hostname = 'mediapc'
2008-06-15 16:45:46.417 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowTime' AND hostname = 'mediapc'
2008-06-15 16:45:46.418 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMenu' AND hostname = 'mediapc'
2008-06-15 16:45:46.419 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMusic' AND hostname = 'mediapc'
2008-06-15 16:45:46.420 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowMusicItems' AND hostname = 'mediapc'
2008-06-15 16:45:46.421 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowChannel' AND hostname = 'mediapc'
2008-06-15 16:45:46.423 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowRecStatus' AND hostname = 'mediapc'
2008-06-15 16:45:46.424 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowVolume' AND hostname = 'mediapc'
2008-06-15 16:45:46.425 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDShowGeneric' AND hostname = 'mediapc'
2008-06-15 16:45:46.426 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDBacklightOn' AND hostname = 'mediapc'
2008-06-15 16:45:46.427 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDHeartBeatOn' AND hostname = 'mediapc'
2008-06-15 16:45:46.428 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDBigClock' AND hostname = 'mediapc'
2008-06-15 16:45:46.429 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDKeyString' AND hostname = 'mediapc'
2008-06-15 16:45:46.430 MSqlQuery: SELECT data FROM settings WHERE value = 'LCDPopupTime' AND hostname = 'mediapc'
2008-06-15 16:45:46.455 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioOutputDevice' AND hostname = 'mediapc'
2008-06-15 16:45:46.456 MSqlQuery: SELECT data FROM settings WHERE value = 'PassThruOutputDevice' AND hostname = 'mediapc'
2008-06-15 16:45:46.457 MSqlQuery: SELECT data FROM settings WHERE value = 'MaxChannels' AND hostname = 'mediapc'
2008-06-15 16:45:46.459 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioUpmixType' AND hostname = 'mediapc'
2008-06-15 16:45:46.460 MSqlQuery: SELECT data FROM settings WHERE value = 'AC3PassThru' AND hostname = 'mediapc'
2008-06-15 16:45:46.461 MSqlQuery: SELECT data FROM settings WHERE value = 'DTSPassThru' AND hostname = 'mediapc'
2008-06-15 16:45:46.462 MSqlQuery: SELECT data FROM settings WHERE value = 'AggressiveSoundcardBuffer' AND hostname = 'mediapc'
2008-06-15 16:45:46.463 MSqlQuery: SELECT data FROM settings WHERE value = 'MythControlsVolume' AND hostname = 'mediapc'
2008-06-15 16:45:46.464 MSqlQuery: SELECT data FROM settings WHERE value = 'MixerDevice' AND hostname = 'mediapc'
2008-06-15 16:45:46.465 MSqlQuery: SELECT data FROM settings WHERE value = 'MixerControl' AND hostname = 'mediapc'
2008-06-15 16:45:46.466 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterMixerVolume' AND hostname = 'mediapc'
2008-06-15 16:45:46.467 MSqlQuery: SELECT data FROM settings WHERE value = 'PCMMixerVolume' AND hostname = 'mediapc'
2008-06-15 16:45:46.468 MSqlQuery: SELECT data FROM settings WHERE value = 'IndividualMuteControl' AND hostname = 'mediapc'
2008-06-15 16:45:46.469 MSqlQuery: SELECT data FROM settings WHERE value = 'LircKeyPressedApp' AND hostname = 'mediapc'
2008-06-15 16:45:46.470 MSqlQuery: SELECT data FROM settings WHERE value = 'AllowQuitShutdown' AND hostname = 'mediapc'
2008-06-15 16:45:46.471 MSqlQuery: SELECT data FROM settings WHERE value = 'NoPromptOnExit' AND hostname = 'mediapc'
2008-06-15 16:45:46.472 MSqlQuery: SELECT data FROM settings WHERE value = 'UseArrowAccels' AND hostname = 'mediapc'
2008-06-15 16:45:46.474 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlEnabled' AND hostname = 'mediapc'
2008-06-15 16:45:46.475 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlPort' AND hostname = 'mediapc'
2008-06-15 16:45:46.476 MSqlQuery: SELECT data FROM settings WHERE value = 'MonitorDrives' AND hostname = 'mediapc'
2008-06-15 16:45:46.477 MSqlQuery: SELECT data FROM settings WHERE value = 'MediaChangeEvents' AND hostname = 'mediapc'
2008-06-15 16:45:46.478 MSqlQuery: SELECT data FROM settings WHERE value = 'IgnoreDevices' AND hostname = 'mediapc'
2008-06-15 16:45:46.479 MSqlQuery: SELECT data FROM settings WHERE value = 'SetupPinCodeRequired' AND hostname = 'mediapc'
2008-06-15 16:45:46.480 MSqlQuery: SELECT data FROM settings WHERE value = 'SetupPinCode' AND hostname = 'mediapc'
2008-06-15 16:45:46.481 MSqlQuery: SELECT data FROM settings WHERE value = 'OverrideExitMenu' AND hostname = 'mediapc'
2008-06-15 16:45:46.482 MSqlQuery: SELECT data FROM settings WHERE value = 'HaltCommand' AND hostname = 'mediapc'
2008-06-15 16:45:46.483 MSqlQuery: SELECT data FROM settings WHERE value = 'RebootCommand' AND hostname = 'mediapc'
2008-06-15 16:45:46.484 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableXbox' AND hostname = 'mediapc'
2008-06-15 16:45:46.486 MSqlQuery: SELECT data FROM settings WHERE value = 'LogEnabled'
2008-06-15 16:45:46.487 MSqlQuery: SELECT data FROM settings WHERE value = 'LogMaxCount' AND hostname = 'mediapc'
2008-06-15 16:45:46.488 MSqlQuery: SELECT data FROM settings WHERE value = 'LogPrintLevel' AND hostname = 'mediapc'
2008-06-15 16:45:46.489 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanEnabled' AND hostname = 'mediapc'
2008-06-15 16:45:46.490 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanPeriod' AND hostname = 'mediapc'
2008-06-15 16:45:46.491 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanDays' AND hostname = 'mediapc'
2008-06-15 16:45:46.492 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanMax' AND hostname = 'mediapc'
2008-06-15 16:45:46.493 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillEnabled'
2008-06-15 16:45:46.494 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabasePath'
2008-06-15 16:45:46.495 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabaseArgs'
2008-06-15 16:45:46.496 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabaseLog'
2008-06-15 16:45:46.497 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillPeriod'
2008-06-15 16:45:46.498 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillMinHour'
2008-06-15 16:45:46.499 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillMaxHour'
2008-06-15 16:45:46.500 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillGrabberSuggestsTime'
2008-06-15 16:45:46.502 MSqlQuery: SELECT data FROM settings WHERE value = 'SchedMoveHigher'
2008-06-15 16:45:46.504 MSqlQuery: SELECT data FROM settings WHERE value = 'SchedOpenEnd'
2008-06-15 16:45:46.505 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultStartOffset'
2008-06-15 16:45:46.506 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultEndOffset'
2008-06-15 16:45:46.506 MSqlQuery: SELECT data FROM settings WHERE value = 'ComplexPriority'
2008-06-15 16:45:46.507 MSqlQuery: SELECT data FROM settings WHERE value = 'PrefInputPriority'
2008-06-15 16:45:46.508 MSqlQuery: SELECT data FROM settings WHERE value = 'HDTVRecPriority'
2008-06-15 16:45:46.509 MSqlQuery: SELECT data FROM settings WHERE value = 'SingleRecordRecPriority'
2008-06-15 16:45:46.510 MSqlQuery: SELECT data FROM settings WHERE value = 'OverrideRecordRecPriority'
2008-06-15 16:45:46.511 MSqlQuery: SELECT data FROM settings WHERE value = 'FindOneRecordRecPriority'
2008-06-15 16:45:46.512 MSqlQuery: SELECT data FROM settings WHERE value = 'WeekslotRecordRecPriority'
2008-06-15 16:45:46.513 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeslotRecordRecPriority'
2008-06-15 16:45:46.514 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelRecordRecPriority'
2008-06-15 16:45:46.515 MSqlQuery: SELECT data FROM settings WHERE value = 'AllRecordRecPriority'
2008-06-15 16:45:46.516 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.516 MSqlQuery: SELECT data FROM settings WHERE value = 'RandomTheme' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.517 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoModes' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.518 Primary screen 0.
2008-06-15 16:45:46.519 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.519 Using screen 0, 1280x1024 at 0,0
2008-06-15 16:45:46.520 MSqlQuery: SELECT data FROM settings WHERE value = 'Style' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.523 Switching to wide mode (Mythbuntu-8.04-wide)
2008-06-15 16:45:46.523 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.524 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-06-15 16:45:46.524 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.524 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-06-15 16:45:46.525 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.525 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-06-15 16:45:46.526 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.526 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-06-15 16:45:46.526 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.527 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-06-15 16:45:46.528 MSqlQuery: SELECT data FROM settings WHERE value = 'MenuTheme' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.529 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontBig' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.529 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontMedium' AND hostname = 'mediapc' ;
2008-06-15 16:45:46.530 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontSmall' AND hostname = 'mediapc' ;

```

and from dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] Command line: root=UUID=3348e316-d139-4b64-b238-ca795391515c ro quiet splash xforcevesa
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fee0000 (usable)
[    0.000000]  BIOS-e820: 000000002fee0000 - 000000002fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fee3000 - 000000002fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fef0000 - 000000002ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196320) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7E00 checksum 0
[    0.000000] ACPI: RSDP 000F7E00, 0024 (r2 RS690 )
[    0.000000] ACPI: XSDT 2FEE30C0, 004C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 2FEE7B80, 00F4 (r3 RS690  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 2FEE3240, 48D3 (r1 RS690  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 2FEE0000, 0040
[    0.000000] ACPI: SSDT 2FEE7D80, 01C4 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 2FEE7FC0, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 2FEE8040, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 2FEE7CC0, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000002fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 196320) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000002fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   196320
[    0.000000] On node 0 totalpages: 196223
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1234 pages reserved
[    0.000000]   DMA zone: 2709 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 2628 pages used for memmap
[    0.000000]   DMA32 zone: 189596 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:b0100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 192305
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=3348e316-d139-4b64-b238-ca795391515c ro quiet splash xforcevesa
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   13.884218] Marking TSC unstable due to TSCs unsynchronized
[   13.884220] time.c: Detected 1900.080 MHz processor.
[   13.884917] Console: colour VGA+ 80x25
[   13.884921] console [tty0] enabled
[   13.884938] Checking aperture...
[   13.884941] CPU 0: aperture @ 0 size 32 MB
[   13.894046] No AGP bridge found
[   13.904835] Memory: 761388k/785280k available (2488k kernel code, 23504k reserved, 1319k data, 320k init)
[   13.904879] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.982030] Calibrating delay using timer specific routine.. 3803.01 BogoMIPS (lpj=7606038)
[   13.982068] Security Framework initialized
[   13.982075] SELinux:  Disabled at boot.
[   13.982092] AppArmor: AppArmor initialized
[   13.982096] Failure registering capabilities with primary security module.
[   13.982198] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.983118] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   13.983562] Mount-cache hash table entries: 256
[   13.983718] Initializing cgroup subsys ns
[   13.983722] Initializing cgroup subsys cpuacct
[   13.983736] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.983738] CPU: L2 Cache: 512K (64 bytes/line)
[   13.983741] CPU 0/0 -> Node 0
[   13.983743] CPU: Physical Processor ID: 0
[   13.983744] CPU: Processor Core ID: 0
[   13.983772] SMP alternatives: switching to UP code
[   13.984468] Early unpacking initramfs... done
[   14.316579] ACPI: Core revision 20070126
[   14.316633] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.626623] Using local APIC timer interrupts.
[   14.679169] APIC timer calibration result 12500527
[   14.679171] Detected 12.500 MHz APIC timer.
[   14.679303] SMP alternatives: switching to SMP code
[   14.679800] Booting processor 1/2 APIC 0x1
[   14.690174] Initializing CPU#1
[   14.767324] Calibrating delay using timer specific routine.. 3800.21 BogoMIPS (lpj=7600428)
[   14.767331] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.767333] CPU: L2 Cache: 512K (64 bytes/line)
[   14.767336] CPU 1/1 -> Node 0
[   14.767338] CPU: Physical Processor ID: 0
[   14.767339] CPU: Processor Core ID: 1
[   14.767448] AMD Athlon(tm) 64 X2 Dual Core Processor BE-2300 stepping 01
[   14.767253] Brought up 2 CPUs
[   14.767379] CPU0 attaching sched-domain:
[   14.767382]  domain 0: span 03
[   14.767384]   groups: 01 02
[   14.767386]   domain 1: span 03
[   14.767388]    groups: 03
[   14.767390] CPU1 attaching sched-domain:
[   14.767391]  domain 0: span 03
[   14.767393]   groups: 02 01
[   14.767395]   domain 1: span 03
[   14.767396]    groups: 03
[   14.767651] net_namespace: 120 bytes
[   14.768063] Time: 15:40:50  Date: 06/15/08
[   14.768099] NET: Registered protocol family 16
[   14.768307] ACPI: bus type pci registered
[   14.768383] PCI: Using configuration type 1
[   14.769724] ACPI: EC: Look up EC in DSDT
[   14.774946] ACPI: Interpreter enabled
[   14.774953] ACPI: (supports S0 S1 S4 S5)
[   14.774975] ACPI: Using IOAPIC for interrupt routing
[   14.780218] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.780407] pci 0000:00:12.0: set SATA to AHCI mode
[   14.781768] PCI: Transparent bridge - 0000:00:14.4
[   14.781793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.782026] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   14.782148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[   14.782235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   14.799894] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800005] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800112] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800219] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800326] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800432] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800539] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800646] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   14.800784] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.800817] pnp: PnP ACPI init
[   14.800825] ACPI: bus type pnp registered
[   14.804058] pnp: PnP ACPI: found 16 devices
[   14.804061] ACPI: ACPI bus type pnp unregistered
[   14.804309] PCI: Using ACPI for IRQ routing
[   14.804312] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.815018] NET: Registered protocol family 8
[   14.815020] NET: Registered protocol family 20
[   14.815113] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   14.815117] hpet0: 4 32-bit timers, 14318180 Hz
[   14.816177] AppArmor: AppArmor Filesystem Enabled
[   14.818941] Time: hpet clocksource has been installed.
[   14.818956] Switched to high resolution mode on CPU 0
[   14.819389] Switched to high resolution mode on CPU 1
[   14.826933] system 00:01: ioport range 0x4100-0x411f has been reserved
[   14.826937] system 00:01: ioport range 0x228-0x22f has been reserved
[   14.826940] system 00:01: ioport range 0x40b-0x40b has been reserved
[   14.826943] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   14.826946] system 00:01: ioport range 0xc00-0xc01 has been reserved
[   14.826949] system 00:01: ioport range 0xc14-0xc14 has been reserved
[   14.826952] system 00:01: ioport range 0xc50-0xc52 has been reserved
[   14.826955] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[   14.826958] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[   14.826961] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[   14.826964] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[   14.826967] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[   14.826970] system 00:01: ioport range 0x4000-0x40fe has been reserved
[   14.826973] system 00:01: ioport range 0x4210-0x4217 has been reserved
[   14.826976] system 00:01: ioport range 0xb10-0xb1f has been reserved
[   14.826987] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   14.826990] system 00:08: ioport range 0x220-0x225 has been reserved
[   14.827000] system 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.827007] system 00:0f: iomem range 0xf0000-0xfffff could not be reserved
[   14.827010] system 00:0f: iomem range 0x2ff00000-0x2fffffff has been reserved
[   14.827014] system 00:0f: iomem range 0xfed00000-0xfed000ff has been reserved
[   14.827017] system 00:0f: iomem range 0x2fee0000-0x2fefffff could not be reserved
[   14.827020] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[   14.827023] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   14.827027] system 00:0f: iomem range 0x100000-0x2fedffff could not be reserved
[   14.827030] system 00:0f: iomem range 0x30000000-0x3fffffff has been reserved
[   14.827033] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.827036] system 00:0f: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.827039] system 00:0f: iomem range 0xfff80000-0xfffeffff has been reserved
[   14.827455] PCI: Bridge: 0000:00:01.0
[   14.827457]   IO window: d000-dfff
[   14.827460]   MEM window: fdd00000-fdefffff
[   14.827462]   PREFETCH window: d0000000-dfffffff
[   14.827467] PCI: Bridge: 0000:00:07.0
[   14.827469]   IO window: e000-efff
[   14.827471]   MEM window: fdc00000-fdcfffff
[   14.827473]   PREFETCH window: fdf00000-fdffffff
[   14.827478] PCI: Bridge: 0000:00:14.4
[   14.827480]   IO window: c000-cfff
[   14.827485]   MEM window: f9000000-fcffffff
[   14.827489]   PREFETCH window: fdb00000-fdbfffff
[   14.827511] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   14.827528] NET: Registered protocol family 2
[   14.862937] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   14.863466] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   14.865355] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.866250] TCP: Hash tables configured (established 131072 bind 65536)
[   14.866254] TCP reno registered
[   14.874978] checking if image is initramfs... it is
[   15.519722] Freeing initrd memory: 7718k freed
[   15.527066] audit: initializing netlink socket (disabled)
[   15.527080] audit(1213544450.336:1): initialized
[   15.529108] VFS: Disk quotas dquot_6.5.1
[   15.529192] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.529337] io scheduler noop registered
[   15.529339] io scheduler anticipatory registered
[   15.529341] io scheduler deadline registered
[   15.529442] io scheduler cfq registered (default)
[   15.669969] Boot video device is 0000:01:05.0
[   15.670574] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   15.670594] assign_interrupt_mode Found MSI capability
[   15.670616] Allocate Port Service[0000:00:07.0:pcie00]
[   15.700616] Real Time Clock Driver v1.12ac
[   15.700818] hpet_resources: 0xfed00000 is busy
[   15.700888] hpet_resources: 0xfed00000 is busy
[   15.700911] Linux agpgart interface v0.102
[   15.700914] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.701061] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.701720] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.702469] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.702540] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.702638] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.703307] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.703317] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.722721] mice: PS/2 mouse device common for all mice
[   15.722769] cpuidle: using governor ladder
[   15.722771] cpuidle: using governor menu
[   15.722914] NET: Registered protocol family 1
[   15.723028] registered taskstats version 1
[   15.723175]   Magic number: 12:848:689
[   15.723310] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.723314] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.723316] EDD information not available.
[   15.723329] Freeing unused kernel memory: 320k freed
[   15.766565] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.918779] fuse init (API version 7.9)
[   16.935349] ACPI: Fan [FAN] (on)
[   16.942677] ACPI: Thermal Zone [THRM] (-127 C)
[   17.243541] SCSI subsystem initialized
[   17.262605] libata version 3.00 loaded.
[   17.275011] ahci 0000:00:12.0: version 3.0
[   17.275050] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   17.275251] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   17.275258] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   17.293557] usbcore: registered new interface driver usbfs
[   17.293583] usbcore: registered new interface driver hub
[   17.293610] usbcore: registered new device driver usb
[   17.294919] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.363220] USB Universal Host Controller Interface driver v3.0
[   17.471351] FDC 0 is a post-1991 82077
[   18.276830] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   18.276835] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   18.278004] scsi0 : ahci
[   18.278300] scsi1 : ahci
[   18.278456] scsi2 : ahci
[   18.278596] scsi3 : ahci
[   18.278678] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[   18.278681] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[   18.278685] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[   18.278688] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[   18.751958] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.753187] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7KP, max UDMA/100
[   18.753192] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   18.754271] ata1.00: configured for UDMA/100
[   19.064691] ata2: SATA link down (SStatus 0 SControl 300)
[   19.376138] ata3: SATA link down (SStatus 0 SControl 300)
[   19.687579] ata4: SATA link down (SStatus 0 SControl 300)
[   19.687413] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   19.688177] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.688402] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   19.688704] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   19.688733] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[   19.695864] Driver 'sd' needs updating - please use bus_type methods
[   19.703325] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   19.703337] sd 0:0:0:0: [sda] Write Protect is off
[   19.703340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.703355] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.703400] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   19.703408] sd 0:0:0:0: [sda] Write Protect is off
[   19.703410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.703422] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.703427]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   19.746648] hub 1-0:1.0: USB hub found
[   19.746659] hub 1-0:1.0: 2 ports detected
[   19.847413] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.847642] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   19.847709] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   19.847733] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[   19.906319] usb usb2: configuration #1 chosen from 1 choice
[   19.906347] hub 2-0:1.0: USB hub found
[   19.906357] hub 2-0:1.0: 2 ports detected
[   20.007112] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.007331] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   20.007406] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   20.007431] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[   20.066009] usb usb3: configuration #1 chosen from 1 choice
[   20.066034] hub 3-0:1.0: USB hub found
[   20.066043] hub 3-0:1.0: 2 ports detected
[   20.117347]  sda1 sda2 sda3
[   20.137852] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.142390] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.162760] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   20.166835] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   20.167123] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   20.167206] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   20.167226] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[   20.228258] usb usb4: configuration #1 chosen from 1 choice
[   20.228283] hub 4-0:1.0: USB hub found
[   20.228293] hub 4-0:1.0: 2 ports detected
[   20.330539] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   20.330757] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   20.330827] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   20.330846] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[   20.390477] usb usb5: configuration #1 chosen from 1 choice

[   20.390503] hub 5-0:1.0: USB hub found
[   20.390512] hub 5-0:1.0: 2 ports detected
[   20.390582] usb 1-2: configuration #1 chosen from 1 choice
[   20.414846] Attempting manual resume
[   20.414851] swsusp: Resume From Partition 8:3
[   20.414853] PM: Checking swsusp image.
[   20.415312] PM: Resume from disk failed.
[   20.451851] kjournald starting.  Commit interval 5 seconds
[   20.451870] EXT3-fs: mounted filesystem with ordered data mode.
[   20.493987] r8169 Gigabit Ethernet driver 2.2LK loaded
[   20.494025] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   20.494047] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.494334] eth0: RTL8168b/8111b at 0xffffc200004f8000, 00:e0:4d:2b:b2:06, XID 38000000 IRQ 510
[   20.495723] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   20.495960] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   20.496037] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   20.496079] ehci_hcd 0000:00:13.5: debug port 1
[   20.496098] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[   20.496154] usb 1-2: USB disconnect, address 2
[   20.506111] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.506212] usb usb6: configuration #1 chosen from 1 choice
[   20.506233] hub 6-0:1.0: USB hub found
[   20.506238] hub 6-0:1.0: 10 ports detected
[   20.609071] ACPI: PCI Interrupt 0000:03:06.2[C] -> GSI 23 (level, low) -> IRQ 23
[   20.609378] ehci_hcd 0000:03:06.2: EHCI Host Controller
[   20.609447] ehci_hcd 0000:03:06.2: new USB bus registered, assigned bus number 7
[   20.609508] ehci_hcd 0000:03:06.2: irq 23, io mem 0xfcfff000
[   20.621947] ehci_hcd 0000:03:06.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.622061] usb usb7: configuration #1 chosen from 1 choice
[   20.622084] hub 7-0:1.0: USB hub found
[   20.622089] hub 7-0:1.0: 4 ports detected
[   20.726004] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
[   20.726022] uhci_hcd 0000:03:06.0: UHCI Host Controller
[   20.726054] uhci_hcd 0000:03:06.0: new USB bus registered, assigned bus number 8
[   20.726094] uhci_hcd 0000:03:06.0: irq 21, io base 0x0000cf00
[   20.726224] usb usb8: configuration #1 chosen from 1 choice
[   20.726251] hub 8-0:1.0: USB hub found
[   20.726258] hub 8-0:1.0: 2 ports detected
[   20.829670] ACPI: PCI Interrupt 0000:03:06.1[B] -> GSI 22 (level, low) -> IRQ 22
[   20.829686] uhci_hcd 0000:03:06.1: UHCI Host Controller
[   20.829712] uhci_hcd 0000:03:06.1: new USB bus registered, assigned bus number 9
[   20.829745] uhci_hcd 0000:03:06.1: irq 22, io base 0x0000ce00
[   20.829867] usb usb9: configuration #1 chosen from 1 choice
[   20.829889] hub 9-0:1.0: USB hub found
[   20.829895] hub 9-0:1.0: 2 ports detected
[   20.860492] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   21.000918] usb 6-2: configuration #1 chosen from 1 choice
[   21.240827] usb 7-1: new high speed USB device using ehci_hcd and address 2
[   21.373546] usb 7-1: configuration #1 chosen from 1 choice
[   25.380410] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.457134] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.517353] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.833969] logips2pp: Detected unknown logitech mouse model 74
[   26.072417] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.072425] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.084714] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   26.084729] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   26.084742] SB600_PATA: not 100% native mode: will probe irqs later
[   26.084751]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
[   26.084763] Probing IDE interface ide0...
[   26.141733] input: Power Button (FF) as /devices/virtual/input/input3
[   26.177737] ACPI: Power Button (FF) [PWRF]
[   26.177798] input: Power Button (CM) as /devices/virtual/input/input4

[   26.240077] ACPI: Power Button (CM) [PWRB]
[   26.240147] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.303932] ACPI: Sleep Button (CM) [SLPB]
[   26.312570] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input6
[   26.370647] parport_pc 00:0b: reported by Plug and Play ACPI
[   26.370710] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   26.627467] Linux video capture interface: v2.00
[   26.871234] hdb: HL-DT-STDVD-RAM GSA-H22N, ATAPI CD/DVD-ROM drive
[   26.953506] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   26.967007] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   27.150374] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   27.150640] hdb: UDMA/66 mode selected
[   27.150935] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.153579] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   27.153691] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   27.153770] cx88[0]: subsystem: 0070:9800, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile) [card=41,autodetected]
[   27.153774] cx88[0]: TV tuner type 63, Radio tuner type -1
[   27.211175] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   27.235893] [fglrx] Maximum main memory to use for locked dma buffers: 674 MBytes.
[   27.235927] [fglrx] ASYNCIO init succeed!
[   27.236265] [fglrx] PAT is enabled successfully!
[   27.262372] [fglrx] module loaded - fglrx 8.47.3 [Mar 29 2008] on minor 0
[   27.387587] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   27.388398] tuner' 1-0063: chip found @ 0xc6 (cx88[0])
[   27.472856] tveeprom 1-0050: Hauppauge model 98559, rev A1A0, serial# 127522
[   27.472861] tveeprom 1-0050: MAC address is 00-0D-FE-01-F2-22
[   27.472864] tveeprom 1-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   27.472867] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   27.472870] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   27.472872] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   27.472875] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   27.472877] cx88[0]: hauppauge eeprom: model=98559
[   27.472688] ieee80211_crypt: registered algorithm 'NULL'
[   27.759009] r8187: no version for "ieee80211_reset_queue" found: kernel tainted.
[   27.763418] 
[   27.763421] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
[   27.763424] Copyright (c) 2004-2005, Andrea Merello
[   27.763426] rtl8187: Initializing module
[   27.763427] rtl8187: Wireless extensions version 22
[   27.763429] rtl8187: Initializing proc filesystem
[   27.764510] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[   27.776855] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[   27.776859] cx88_alsa: Unknown symbol videobuf_dma_free
[   27.776908] cx88_alsa: disagrees about version of symbol cx88_core_put
[   27.776910] cx88_alsa: Unknown symbol cx88_core_put
[   27.777004] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   27.777038] cx88_alsa: disagrees about version of symbol cx88_core_irq
[   27.777040] cx88_alsa: Unknown symbol cx88_core_irq
[   27.777084] cx88_alsa: disagrees about version of symbol cx88_core_get
[   27.777086] cx88_alsa: Unknown symbol cx88_core_get
[   27.777287] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[   27.777289] cx88_alsa: Unknown symbol btcx_riscmem_free
[   27.777398] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[   27.777399] cx88_alsa: Unknown symbol videobuf_dma_init
[   27.777475] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[   27.777478] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   27.777521] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[   27.777524] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   27.777561] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   27.777563] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[   27.777622] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   27.777702] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   27.777745] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[   27.777747] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   27.777782] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   27.777784] cx88_alsa: Unknown symbol videobuf_to_dma
[   27.805601] tuner-simple 1-0061: creating new instance
[   27.805608] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   27.807005] cx88[0]/0: found at 0000:03:05.0, rev: 5, irq: 20, latency: 64, mmio: 0xf9000000
[   27.807078] cx88[0]/0: registered device video0 [v4l2]
[   27.807101] cx88[0]/0: registered device vbi0
[   27.807123] cx88[0]/0: registered device radio0
[   27.808117] cx88[0]/2: cx2388x 8802 Driver Manager
[   27.808143] ACPI: PCI Interrupt 0000:03:05.2[A] -> GSI 20 (level, low) -> IRQ 20
[   27.808154] cx88[0]/2: found at 0000:03:05.2, rev: 5, irq: 20, latency: 64, mmio: 0xfa000000
[   27.808286] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   27.835032] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   27.838941] dib0700: loaded with support for 7 different device-types
[   27.871214] ACPI: PCI Interrupt 0000:01:05.2[B] -> GSI 19 (level, low) -> IRQ 19
[   27.882997] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   27.883003] cx88/2: registering cx8802 driver, type: dvb access: shared
[   27.883007] cx88[0]/2: subsystem: 0070:9800, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile) [card=41]
[   27.883011] cx88[0]/2: cx2388x based DVB/ATSC card
[   27.916378] tuner-simple 1-0061: attaching existing instance
[   27.916384] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   27.919045] DVB: registering new adapter (cx88[0])
[   27.919055] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   28.091996] rtl8187: Card MAC address is 00:0e:2e:e4:5b:0c
[   28.363558] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   28.363568] Uniform CD-ROM driver Revision: 3.20
[   28.432325] rtl8187: WW:Forcing card id: 0x8189
[   28.432329] rtl8187: WW:(ID 0x8187 was detected)
[   28.432577] rtl8187: PAPE from CONFIG2: 0
[   28.432853] rtl8187: Driver probe completed
[   28.432854] 
[   28.432876] usbcore: registered new interface driver rtl8187
[   28.433545] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   28.450192] udev: renamed network interface wlan0 to wlan1
[   28.589104] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   28.660336] rtl8187: Card successfully reset
[   28.660340] This is RTL8187B Reset procedure
[   28.809827] dib0700: firmware started successfully.
[   29.313232] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   29.313298] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   29.313511] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   29.426853] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   29.795418] MT2060: successfully identified (IF1 = 1216)
[   30.338643] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   30.338863] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   30.347170] DVB: registering frontend 2 (DiBcom 3000MC/P)...
[   30.354784] MT2060: successfully identified (IF1 = 1218)
[   30.939033] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb7/7-1/input/input7
[   30.967435] dvb-usb: schedule remote query interval to 150 msecs.
[   30.967441] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   30.967702] usbcore: registered new interface driver dvb_usb_dib0700
[   31.466364] lp0: using parport0 (interrupt-driven).
[   31.735524] Adding 1951888k swap on /dev/sda3.  Priority:-1 extents:1 across:1951888k
[   32.398802] EXT3 FS on sda1, internal journal
[   33.361860] kjournald starting.  Commit interval 5 seconds
[   33.362360] EXT3 FS on sda2, internal journal
[   33.362368] EXT3-fs: mounted filesystem with ordered data mode.
[   34.017456] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.048007] WIRELESS_MODE_G
[   37.055495] Set chan.call ieee80211_start_bss.in start bss call check.<6>rtl8187: Setting SW wep key
[   37.237625] ieee80211_crypt: registered algorithm 'WEP'
[   37.424041] Set chan.call ieee80211_start_bss.in start bss call check.<6>No dock devices found.
[   38.873546] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor BE-2300 processors (2 cpu cores) (version 2.20.00)
[   38.873340] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xe
[   38.873346] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xf
[   38.873349] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   39.081651] NET: Registered protocol family 17
[   40.710018] NET: Registered protocol family 10
[   40.710288] lo: Disabled Privacy Extensions
[   40.710843] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   42.452788] Linking with Housenet
[   42.504448] Associated successfully
[   42.504451] Using G rates
[   42.555311] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   52.433050] Clocksource tsc unstable (delta = -189620750 ns)
[   52.606075] wlan1: no IPv6 routers present
[   53.368476] r8169: eth0: link down
[   53.369498] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.727406] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   55.178747] [fglrx] GART Table is not in FRAME_BUFFER range 
[   55.178761] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[   55.178765] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   55.377812] [fglrx] interrupt source 10000000 successfully enabled
[   55.377819] [fglrx] enable ID = 0x00000008
[   55.377827] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   90.413066] mythfrontend.re[6492]: segfault at fc1dfd80 rip 7f0d04fbc330 rsp 7fff1476a3b8 error 6
[  194.116486] mythfrontend.re[6743]: segfault at 901d4b00 rip 7f0f9ac3c330 rsp 7fffaa3ea038 error 6
```

---

### Post by laga on 2008-06-15
Hi,

I've just extended the "How to get help" thread: [http://ubuntuforums.org/showthread.php?t=736528](http://ubuntuforums.org/showthread.php?t=736528)

Go there if you want to find out how to create a bug report :)

---

### Post by tohc1 on 2008-06-16
Thanks for the link, I had realised that I had to turn apport on... bug report sent.
For anyone with the same problem.

I've done a clean install and the problem appears to be with the fglrx drivers, it worked ok using the vesa drivers but not fglrx.

---

