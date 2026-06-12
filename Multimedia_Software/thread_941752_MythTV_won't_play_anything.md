---
title: "MythTV won't play anything"
date: 2008-10-08
forum: Multimedia Software
---

### Post by vipasane on 2008-10-08
I had a previous installation of ubuntu 7.04 and I upgraded it to 7.10 and immediatly to 8.04.

When I choose to watch tv --> frontend dies with following exceptions:
2008-10-08 19:48:18.708 DPMS Deactivated 
2008-10-08 19:48:18.734 NVP: Disabling Audio, params(-1,2,44100)
Segmentation fault

When I try to play previously recorded files (BTW: minifeed works fine in this window) I get following error: message:
2008-10-08 20:04:54.226 Opening audio device '/dev/dsp'. ch 2(2) sr 48000
2008-10-08 20:04:54.226 Opening OSS audio device '/dev/dsp'.
Segmentation fault

I've deleted and added all inputs & sources, and checked that starting channel has a valid stream. Which has usually been the problem with similar error messages.

I tested my sound cards through System tools and they seem to work fine

Any idea how to fix this?

---

### Post by vipasane on 2008-10-08
MPlayer will play *.mpg files fine...

---

### Post by vipasane on 2008-10-08
mythbackend version: 0.21.20080304-1
mythbackend.log
...
2008-10-08 19:45:56.263 MainServer::HandleAnnounce Monitor
2008-10-08 19:45:56.268 adding: MediaStation as a client (events: 0)
2008-10-08 19:45:56.270 MainServer::HandleAnnounce Monitor
2008-10-08 19:45:56.271 adding: MediaStation as a client (events: 1)
2008-10-08 19:45:56.292 Reloading backend settings
2008-10-08 19:46:45.350 Expiring 0 MBytes for 1001 @ Wed Oct 8 19:00:00 2008 => Basaari: Ura
2008-10-08 19:47:06.755 Reschedule requested for id -1.
2008-10-08 19:47:06.932 Scheduled 0 items in 0.2 = 0.01 match + 0.16 place
2008-10-08 19:48:17.150 MainServer::HandleAnnounce Playback
2008-10-08 19:48:17.157 adding: MediaStation as a client (events: 0)
2008-10-08 19:48:17.254 TVRec(3): Changing from None to WatchingLiveTV
2008-10-08 19:48:17.279 TVRec(3): HW Tuner: 3->3
2008-10-08 19:48:18.639 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-10-08 19:48:18.831 TVRec(3): Changing from WatchingLiveTV to None
2008-10-08 19:48:19.004 Finished recording Historiaa: Pearl Harbor - kumpi aloitti?: channel 1001
2008-10-08 19:48:45.365 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-08 19:49:20.172 Program #113 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(49) extension(0x1001)
      version(15) current(1) section(0) last_section(0)
         tsid: 4097
 programCount: 10
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number    17 has PID 0x 100   data  0x 0 0x11 0xe1 0x 0
  program number    33 has PID 0x 101   data  0x 0 0x21 0xe1 0x 1
  program number    81 has PID 0x 103   data  0x 0 0x51 0xe1 0x 3
  program number   145 has PID 0x 102   data  0x 0 0x91 0xe1 0x 2
  program number  4369 has PID 0x 105   data  0x11 0x11 0xe1 0x 5
  program number  4433 has PID 0x 109   data  0x11 0x51 0xe1 0x 9
  program number  4401 has PID 0x 107   data  0x11 0x31 0xe1 0x 7
  program number   353 has PID 0x 104   data  0x 1 0x61 0xe1 0x 4
  program number  3347 has PID 0x 10e   data  0x d 0x13 0xe1 0x e

2008-10-08 19:51:01.582 Reschedule requested for id -1.
2008-10-08 19:51:01.618 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-10-08 19:56:29.140 Reschedule requested for id -1.
2008-10-08 19:56:29.171 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-08 20:01:08.387 Reschedule requested for id -1.
2008-10-08 20:01:08.419 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-08 20:03:45.463 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-08 20:04:01.257 Reschedule requested for id -1.
2008-10-08 20:04:01.292 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2008-10-08 20:04:45.483 Expiring 0 MBytes for 1001 @ Wed Oct 8 19:30:17 2008 => Historiaa: Pearl Harbor - kumpi aloitti?
2008-10-08 20:04:47.239 MainServer::HandleAnnounce Monitor
2008-10-08 20:04:47.245 adding: MediaStation as a client (events: 0)
2008-10-08 20:04:47.248 MainServer::HandleAnnounce Monitor
2008-10-08 20:04:47.252 adding: MediaStation as a client (events: 1)
2008-10-08 20:09:57.996 Program #113 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(49) extension(0x1001)
      version(15) current(1) section(0) last_section(0)
         tsid: 4097
 programCount: 10
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number    17 has PID 0x 100   data  0x 0 0x11 0xe1 0x 0
  program number    33 has PID 0x 101   data  0x 0 0x21 0xe1 0x 1
  program number    81 has PID 0x 103   data  0x 0 0x51 0xe1 0x 3
  program number   145 has PID 0x 102   data  0x 0 0x91 0xe1 0x 2
  program number  4369 has PID 0x 105   data  0x11 0x11 0xe1 0x 5
  program number  4433 has PID 0x 109   data  0x11 0x51 0xe1 0x 9
  program number  4401 has PID 0x 107   data  0x11 0x31 0xe1 0x 7
  program number   353 has PID 0x 104   data  0x 1 0x61 0xe1 0x 4
  program number  3347 has PID 0x 10e   data  0x d 0x13 0xe1 0x e

2008-10-08 20:10:59.151 Reschedule requested for id -1.
2008-10-08 20:10:59.312 Scheduled 0 items in 0.2 = 0.01 match + 0.14 place
2008-10-08 20:15:06.816 Reschedule requested for id -1.
2008-10-08 20:15:06.981 Scheduled 0 items in 0.2 = 0.07 match + 0.09 place
2008-10-08 20:15:19.629 Program #1585 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(65) extension(0x3001)
      version(8) current(1) section(0) last_section(0)
         tsid: 12289
 programCount: 14
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number   113 has PID 0x 104   data  0x 0 0x71 0xe1 0x 4
  program number   161 has PID 0x 103   data  0x 0 0xa1 0xe1 0x 3
  program number   193 has PID 0x 10d   data  0x 0 0xc1 0xe1 0x d
  program number   401 has PID 0x 105   data  0x 1 0x91 0xe1 0x 5
  program number   417 has PID 0x 10a   data  0x 1 0xa1 0xe1 0x a
  program number   433 has PID 0x 109   data  0x 1 0xb1 0xe1 0x 9
  program number   449 has PID 0x 10b   data  0x 1 0xc1 0xe1 0x b
  program number   465 has PID 0x 10e   data  0x 1 0xd1 0xe1 0x e
  program number   481 has PID 0x 111   data  0x 1 0xe1 0xe1 0x11
  program number   817 has PID 0x 100   data  0x 3 0x31 0xe1 0x 0
  program number   833 has PID 0x 110   data  0x 3 0x41 0xe1 0x10
  program number  1089 has PID 0x 10f   data  0x 4 0x41 0xe1 0x f
  program number  1105 has PID 0x 10c   data  0x 4 0x51 0xe1 0x c

2008-10-08 20:17:53.245 Reschedule requested for id -1.
2008-10-08 20:17:53.275 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-08 20:18:45.531 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-08 20:22:03.171 Reschedule requested for id -1.
2008-10-08 20:22:03.199 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-08 20:25:26.163 Reschedule requested for id -1.
2008-10-08 20:25:26.336 Scheduled 0 items in 0.2 = 0.05 match + 0.12 place
2008-10-08 20:30:36.291 Reschedule requested for id -1.
2008-10-08 20:30:36.416 Scheduled 0 items in 0.1 = 0.06 match + 0.06 place
2008-10-08 20:33:45.584 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-08 20:40:56.093 Program #17 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(49) extension(0x5001)
      version(20) current(1) section(0) last_section(0)
         tsid: 20481
 programCount: 10
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number   225 has PID 0x 100   data  0x 0 0xe1 0xe1 0x 0
  program number   273 has PID 0x 101   data  0x 1 0x11 0xe1 0x 1
  program number   289 has PID 0x 102   data  0x 1 0x21 0xe1 0x 2
  program number   305 has PID 0x 103   data  0x 1 0x31 0xe1 0x 3
  program number   385 has PID 0x 106   data  0x 1 0x81 0xe1 0x 6
  program number   497 has PID 0x 109   data  0x 1 0xf1 0xe1 0x 9
  program number   337 has PID 0x 104   data  0x 1 0x51 0xe1 0x 4
  program number   369 has PID 0x 107   data  0x 1 0x71 0xe1 0x 7
  program number  1585 has PID 0x 108   data  0x 6 0x31 0xe1 0x 8

2008-10-08 20:41:57.955 Reschedule requested for id -1.
2008-10-08 20:41:57.987 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-08 20:48:45.657 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by vipasane on 2008-10-09
Here is a mythfrontend -v all messages just before crash...any help would be appriciated


                 Device name/type | Current mountpoint
                 -----------------+-------------------
                 /dev/disk/by-uuid/0e35a829-b6d1-4ed0-8038-dd7a27b6c673 | /
                 /dev/disk/by-uuid/0e35a829-b6d1-4ed0-8038-dd7a27b6c673 | /dev/.static/dev
                        /dev/sda3 | /media/hda3
                        /dev/sdb1 | /media/hdb1
                        /dev/sdb5 | /media/hdb5
                        /dev/sdb6 | /media/hdb6
                 =================+===================
SIP listening on IP Address 10.0.0.6:5060 NAT address 84.251.7.186
2008-10-09 22:01:26.585 MSqlQuery: SELECT data FROM settings WHERE value = 'SipRegisterWithProxy' AND hostname = 'MediaStation' ;
2008-10-09 22:01:26.586 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyName' AND hostname = 'MediaStation' ;
2008-10-09 22:01:26.587 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthName' AND hostname = 'MediaStation' ;
2008-10-09 22:01:26.587 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthPassword' AND hostname = 'MediaStation' ;
SIP: Cannot register; proxy, username or password not set
2008-10-09 22:01:26.946 /dev/scd0 No disc
2008-10-09 22:01:27.508 /dev/scd0 No disc
2008-10-09 22:01:27.684 MSqlQuery: SELECT data FROM settings WHERE value = 'Language' AND hostname = 'MediaStation' ;
2008-10-09 22:01:28.069 /dev/scd0 No disc
2008-10-09 22:01:28.624 /dev/scd0 No disc
2008-10-09 22:01:29.179 /dev/scd0 No disc
2008-10-09 22:01:29.437 MSqlQuery: SELECT data FROM settings WHERE value = 'CustomFilters' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.439 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelFormat' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.440 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.442 MSqlQuery: SELECT data FROM settings WHERE value = 'ShortDateFormat' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.444 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartChannelChange' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.445 MSqlQuery: SELECT data FROM settings WHERE value = 'IndividualMuteControl' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.447 MSqlQuery: SELECT data FROM settings WHERE value = 'UseArrowAccels' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.452 MSqlQuery: SELECT data FROM settings WHERE value = 'PersistentBrowseMode' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.453 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDGeneralTimeout' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.455 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDProgramInfoTimeout' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.456 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommercialSkip' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.458 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.459 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname IS NULL;
2008-10-09 22:01:29.461 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartForward' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.462 MSqlQuery: SELECT data FROM settings WHERE value = 'StickyKeys' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.468 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReposTime' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.469 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReverse' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.470 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.472 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname IS NULL;
2008-10-09 22:01:29.473 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.474 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname IS NULL;
2008-10-09 22:01:29.476 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.477 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname IS NULL;
2008-10-09 22:01:29.479 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.480 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname IS NULL;
2008-10-09 22:01:29.481 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.482 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname IS NULL;
2008-10-09 22:01:29.484 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.485 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname IS NULL;
2008-10-09 22:01:29.487 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.488 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname IS NULL;
2008-10-09 22:01:29.490 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.491 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname IS NULL;
2008-10-09 22:01:29.492 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.497 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname IS NULL;
2008-10-09 22:01:29.499 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiSizeForTV' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.501 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoModes' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.502 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.503 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-10-09 22:01:29.505 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.507 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.517 MythEvent: PLAYBACK_START MediaStation
2008-10-09 22:01:29.518 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.520 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;
2008-10-09 22:01:29.525 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.526 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;
2008-10-09 22:01:29.526 MythSocket(8346c18:15): new socket
2008-10-09 22:01:29.528 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.529 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname IS NULL;
2008-10-09 22:01:29.531 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.532 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname IS NULL;
2008-10-09 22:01:29.533 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-09 22:01:29.533 MythSocket(844bfe8:19): new socket
2008-10-09 22:01:29.533 MythSocket(844bfe8:19): attempting connect() to (127.0.0.1:6543)
2008-10-09 22:01:29.534 MythSocket(844bfe8:19): state change Idle -> Connected
2008-10-09 22:01:29.534 write -> 19 21      MYTH_PROTO_VERSION 40
2008-10-09 22:01:29.535 read  <- 19 13      ACCEPT[]:[]40
2008-10-09 22:01:29.535 Using protocol version 40
2008-10-09 22:01:29.535 write -> 19 26      ANN Monitor MediaStation 0
2008-10-09 22:01:29.548 read  <- 19 2       OK
2008-10-09 22:01:29.548 MythSocket(8346c18:15): attempting connect() to (127.0.0.1:6543)
2008-10-09 22:01:29.549 MythSocket(8346c18:15): state change Idle -> Connected
2008-10-09 22:01:29.549 write -> 15 26      ANN Monitor MediaStation 1
2008-10-09 22:01:29.552 read  <- 15 2       OK
2008-10-09 22:01:29.557 MythSocket: readyread thread start
2008-10-09 22:01:29.557 MythSocket(8346c18:15): UpRef: 1
2008-10-09 22:01:29.557 write -> 19 23      GET_FREE_RECORDER_COUNT
2008-10-09 22:01:29.558 read  <- 19 1       2
2008-10-09 22:01:29.559 write -> 19 29      GET_NEXT_FREE_RECORDER[]:[]-1
2008-10-09 22:01:29.565 read  <- 19 24      3[]:[]127.0.0.1[]:[]6543
2008-10-09 22:01:29.568 MSqlQuery: SELECT name, skipahead FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND skipahead <> 0 ORDER BY name = 'Default';
2008-10-09 22:01:29.572 MSqlQuery: SELECT name, skipback FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND skipback <> 0 ORDER BY name = 'Default';
2008-10-09 22:01:29.573 MSqlQuery: SELECT name, jump FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND jump <> 0 ORDER BY name = 'Default';
2008-10-09 22:01:29.575 MSqlQuery: SELECT name, timestretch FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND timestretch <> 0 ORDER BY name = 'Default';
2008-10-09 22:01:29.576 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVIdleTimeout' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.577 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVIdleTimeout' AND hostname IS NULL;
2008-10-09 22:01:29.579 MSqlQuery: SELECT data FROM settings WHERE value = 'WatchTVGuide' AND hostname = 'MediaStation' ;
2008-10-09 22:01:29.604 MSqlQuery: SELECT channel_timeout, cardtype FROM cardinput, capturecard WHERE cardinput.inputname = 'QUERY_RECORDER 3' AND       cardinput.cardid    = 3 AND       cardinput.cardid    = capturecard.cardid
2008-10-09 22:01:29.606 TV: Attempting to change from None to WatchingLiveTV
2008-10-09 22:01:29.606 MythSocket(b01019b8:24): new socket
2008-10-09 22:01:29.606 MythSocket(b01019b8:24): attempting connect() to (127.0.0.1:6543)
2008-10-09 22:01:29.607 MythSocket(b01019b8:24): state change Idle -> Connected
2008-10-09 22:01:29.607 write -> 24 21      MYTH_PROTO_VERSION 40
2008-10-09 22:01:29.607 read  <- 24 13      ACCEPT[]:[]40
2008-10-09 22:01:29.607 Using protocol version 40
2008-10-09 22:01:29.608 write -> 24 27      ANN Playback MediaStation 0
2008-10-09 22:01:29.611 read  <- 24 2       OK
2008-10-09 22:01:29.611 write -> 24 86      QUERY_RECORDER 3[]:[]SPAWN_LIVETV[]:[]live-MediaStation-2008-10-09T22:01:29[]:[]0[]:[]
2008-10-09 22:01:29.759 /dev/scd0 No disc
2008-10-09 22:01:30.321 /dev/scd0 No disc
2008-10-09 22:01:30.897 /dev/scd0 No disc
2008-10-09 22:01:30.960 read  <- 24 2       ok
2008-10-09 22:01:30.963 MSqlQuery: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = 'live-MediaStation-2008-10-09T22:01:29' ORDER BY chainpos;
2008-10-09 22:01:30.963 LiveTVChain(live-MediaStation-2008-10-09T22:01:29): ReloadAll(): Added new recording
2008-10-09 22:01:30.967 MSqlQuery: SELECT recorded.chanid,starttime,endtime,title, subtitle,description,channel.channum, channel.callsign,channel.name,channel.commmethod, channel.outputfilters,seriesid,programid,filesize, lastmodified,stars,previouslyshown,originalairdate, hostname,recordid,transcoder,playgroup, recorded.recpriority,progstart,progend,basename,recgroup, storagegroup FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recorded.chanid = '1001' AND starttime = '2008-10-09T22:01:29' ;
2008-10-09 22:01:30.970 MSqlQuery: SELECT commflagged, cutlist, autoexpire, editing, bookmark, watched, preserve FROM recorded LEFT JOIN recordedprogram ON (recorded.chanid = recordedprogram.chanid AND recorded.progstart = recordedprogram.starttime) WHERE recorded.chanid = '1001' AND recorded.starttime = '2008-10-09T22:01:29' ;
2008-10-09 22:01:30.976 MSqlQuery: SELECT audioprop+0, videoprop+0, subtitletypes+0 FROM recorded LEFT JOIN recordedprogram ON (recorded.chanid = recordedprogram.chanid AND recorded.progstart = recordedprogram.starttime) WHERE recorded.chanid = '1001' AND recorded.starttime = '2008-10-09T22:01:29' ;
2008-10-09 22:01:30.978 MSqlQuery: SELECT basename FROM recorded WHERE chanid = '1001' AND       starttime = '2008-10-09T22:01:29';
2008-10-09 22:01:30.980 MSqlQuery: SELECT data FROM settings WHERE value = 'AlwaysStreamFiles' AND hostname = 'MediaStation' ;
2008-10-09 22:01:30.982 MSqlQuery: SELECT DISTINCT dirname FROM storagegroup WHERE groupname = 'LiveTV'
2008-10-09 22:01:30.982 SG(LiveTV): Unable to find storage group 'LiveTV', trying 'Default' group!
2008-10-09 22:01:30.983 MSqlQuery: SELECT DISTINCT dirname FROM storagegroup WHERE groupname = 'Default'
2008-10-09 22:01:30.984 SG(Default): FindRecordingFile: Searching for '1001_20081009220129.mpg'
2008-10-09 22:01:30.984 SG(Default): FindRecordingDir: Checking '/media/hda3'
2008-10-09 22:01:30.984 SG(Default): FindRecordingFile: Found '/media/hda3/1001_20081009220129.mpg'
2008-10-09 22:01:30.988 MythSocket(8346c18:15): socket is readable
2008-10-09 22:01:30.992 MythSocket(8346c18:15): cb->readyRead()
2008-10-09 22:01:30.992 read  <- 15 51      BACKEND_MESSAGE[]:[]RECORDING_LIST_CHANGE[]:[]empty
2008-10-09 22:01:30.992 MythEvent: RECORDING_LIST_CHANGE
2008-10-09 22:01:30.992 read  <- 15 87      BACKEND_MESSAGE[]:[]LIVETV_CHAIN UPDATE live-MediaStation-2008-10-09T22:01:29[]:[]empty
2008-10-09 22:01:30.992 MythEvent: LIVETV_CHAIN UPDATE live-MediaStation-2008-10-09T22:01:29
2008-10-09 22:01:30.993 ProgramInfo: GetPlaybackURL: File is local: '/media/hda3/1001_20081009220129.mpg'
2008-10-09 22:01:30.993 write -> 24 33      QUERY_RECORDER 3[]:[]IS_RECORDING
2008-10-09 22:01:30.993 read  <- 24 1       1
2008-10-09 22:01:30.994 write -> 24 33      QUERY_RECORDER 3[]:[]IS_RECORDING
2008-10-09 22:01:30.994 read  <- 24 1       1
2008-10-09 22:01:30.994 TV: StartRecorder(): took 1 ms to start recorder.
2008-10-09 22:01:30.994 write -> 24 34      QUERY_RECORDER 3[]:[]GET_FRAMERATE
2008-10-09 22:01:30.995 read  <- 24 2       -1
2008-10-09 22:01:30.998 MythSocket(8346c18:15): socket is readable
2008-10-09 22:01:30.998 MythSocket(8346c18:15): cb->readyRead()
2008-10-09 22:01:30.998 read  <- 15 452     BACKEND_MESSAGE[]:[]SIGNAL 3[]:[]Signal Lock[]:[]slock 1 1 0 1 3000 1 1[]:[]Signal Power[]:[]signal 60878 0 0 65535 3000 1 1[]:[]Seen PAT[]:[]seen_pat 0 1 0 1 0 1 1[]:[]Matching PAT[]:[]matching_pat 0 1 0 1 0 1 1[]:[]Seen PMT[]:[]seen_pmt 0 1 0 1 0 1 1[]:[]Matching PMT[]:[]matching_pmt 0 1 0 1 0 1 1[]:[]Signal To Noise[]:[]snr 51399 0 0 65535 0 1 1[]:[]Bit Error Rate[]:[]ber 0 65535 0 65535 0 0 1[]:[]Uncorrected Blocks[]:[]ucb 0 65535 0 65535 0 0 1
2008-10-09 22:01:30.999 MythEvent: SIGNAL 3
2008-10-09 22:01:31.040 MSqlQuery: DELETE FROM inuseprograms WHERE chanid = '1001' AND starttime = '2008-10-09T22:01:29' AND hostname = 'MediaStation' AND recusage = 'player' ;
2008-10-09 22:01:31.041 MSqlQuery: SELECT basename FROM recorded WHERE chanid = '1001' AND       starttime = '2008-10-09T22:01:29';
2008-10-09 22:01:31.043 MSqlQuery: SELECT DISTINCT dirname FROM storagegroup WHERE groupname = 'LiveTV'
2008-10-09 22:01:31.043 SG(LiveTV): Unable to find storage group 'LiveTV', trying 'Default' group!
2008-10-09 22:01:31.045 New DB connection, total: 3
2008-10-09 22:01:31.046 Connected to database 'mythconverg' at host: localhost
2008-10-09 22:01:31.047 MSqlQuery: SELECT DISTINCT dirname FROM storagegroup WHERE groupname = 'Default'
2008-10-09 22:01:31.048 SG(Default): FindRecordingFile: Searching for '1001_20081009220129.mpg'
2008-10-09 22:01:31.048 SG(Default): FindRecordingDir: Checking '/media/hda3'
2008-10-09 22:01:31.048 SG(Default): FindRecordingFile: Found '/media/hda3/1001_20081009220129.mpg'
2008-10-09 22:01:31.048 ProgramInfo: GetPlaybackURL: File is local: '/media/hda3/1001_20081009220129.mpg'
2008-10-09 22:01:31.050 MythSocket(8346c18:15): socket is readable
2008-10-09 22:01:31.051 MythSocket(8346c18:15): cb->readyRead()
2008-10-09 22:01:31.051 read  <- 15 452     BACKEND_MESSAGE[]:[]SIGNAL 3[]:[]Signal Lock[]:[]slock 1 1 0 1 3000 1 1[]:[]Signal Power[]:[]signal 60878 0 0 65535 3000 1 1[]:[]Seen PAT[]:[]seen_pat 0 1 0 1 0 1 1[]:[]Matching PAT[]:[]matching_pat 0 1 0 1 0 1 1[]:[]Seen PMT[]:[]seen_pmt 0 1 0 1 0 1 1[]:[]Matching PMT[]:[]matching_pmt 0 1 0 1 0 1 1[]:[]Signal To Noise[]:[]snr 51399 0 0 65535 0 1 1[]:[]Bit Error Rate[]:[]ber 0 65535 0 65535 0 0 1[]:[]Uncorrected Blocks[]:[]ucb 0 65535 0 65535 0 0 1
2008-10-09 22:01:31.051 MythEvent: SIGNAL 3
2008-10-09 22:01:31.055 MSqlQuery: INSERT INTO inuseprograms  (chanid, starttime, recusage, hostname, lastupdatetime,  rechost, recdir )  VALUES  ('1001', '2008-10-09T22:01:29', 'player', 'MediaStation', '2008-10-09T22:01:31',  'MediaStation', '/media/hda3');
2008-10-09 22:01:31.055 write -> 19 33      MESSAGE[]:[]RECORDING_LIST_CHANGE
2008-10-09 22:01:31.056 MythSocket(8346c18:15): socket is readable
2008-10-09 22:01:31.056 MythSocket(8346c18:15): cb->readyRead()
2008-10-09 22:01:31.056 read  <- 15 51      BACKEND_MESSAGE[]:[]RECORDING_LIST_CHANGE[]:[]empty
2008-10-09 22:01:31.056 MythEvent: RECORDING_LIST_CHANGE
2008-10-09 22:01:31.057 read  <- 19 2       OK
2008-10-09 22:01:31.058 MSqlQuery: SELECT data FROM settings WHERE value = 'CommRewindAmount' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.060 MSqlQuery: SELECT data FROM settings WHERE value = 'CommNotifyAmount' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.062 MSqlQuery: SELECT data FROM settings WHERE value = 'DecodeExtraAudio' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.063 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableMHEG' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.065 MSqlQuery: SELECT data FROM settings WHERE value = 'Prefer708Captions' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.071 MSqlQuery: SELECT data FROM settings WHERE value = 'VBIpageNr' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.072 MSqlQuery: SELECT data FROM settings WHERE value = 'VBIpageNr' AND hostname IS NULL;
2008-10-09 22:01:31.074 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioSampleRate' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.075 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioSampleRate' AND hostname IS NULL;
2008-10-09 22:01:31.077 MSqlQuery: SELECT data FROM settings WHERE value = 'PassThruOutputDevice' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.078 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioOutputDevice' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.080 MSqlQuery: SELECT data FROM settings WHERE value = 'ExactSeeking' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.083 DPMS Deactivated 
2008-10-09 22:01:31.085 MSqlQuery: SELECT data FROM settings WHERE value = 'xscreensaverInterval' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.087 MSqlQuery: SELECT data FROM settings WHERE value = 'UDPNotifyPort' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.088 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2008-10-09 22:01:31.090 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language0' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.091 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language1' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.093 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language2' AND hostname = 'MediaStation' ;
2008-10-09 22:01:31.094 MSqlQuery: SELECT data FROM settings WHERE value = 'ISO639Language2' AND hostname IS NULL;
2008-10-09 22:01:31.095 NVP: Disabling Audio, params(-1,2,44100)
Segmentation fault

---

### Post by vipasane on 2008-10-11
Can watch dvb-t stream on Me-tv...
What could be the problem why mythfrontend is not functioning correctly?

---

### Post by m_duck on 2008-10-11
I've only used mythtv a small amount (and not for a while), but when videos wouldn't play on mine, it was because the file permissions were not correct on certain directories (though unfortunately I cannot remember which ones). If you look through the mythbackend setup thing and check all the directories mentioned there have the correct permissions for the user that runs mythtv on your box.

If you run "mythtv-frontend" from the terminal, and try to play a video for example, check what the terminal output is, it may shed some light on the problem.

---

### Post by vipasane on 2008-10-11
I'm running mythfrontend with same user account as I've usually login, so if I can play 'em with a different program and since these small preview videos are visible...
I think there would be problems with sounds more likely...
Allways something like opening audio message before tilt, but sounds are working fine when using others programs

---

