---
title: "Upgrade caused errors playing DVDs"
date: 2011-06-14
forum: Mythbuntu
---

### Post by bcg30506 on 2011-06-14
After performing the upgrades reported by apt yesterday, my DVD playing now is off.  It stutters every few minutes and I see a series of this in the frontend log:
```
2011-06-14 09:07:31.269 AFD Warning: Audio 54187 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 09:07:31.315 AFD Warning: Audio 54220 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 09:07:31.316 AFD Warning: Audio 54189 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 09:07:31.316 AFD Warning: Audio 54223 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 09:07:31.316 AFD Warning: Audio 54256 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 09:07:31.317 AFD Warning: Audio 54225 ms behind video but already 180 video frames queued. AV-Sync might be broken.

```
It's happened on different discs that I know to be okay.  This is in 0.24.1 running under 10.04.

---

### Post by superm1 on 2011-06-14
Have you already restarted?  Just to make sure any other services that needed to be restarted are covered.

If it persists, please file a bug like this:

#ubuntu-bug mythtv

It will get lodged in Launchpad at which point the relevant details can be forwarded upstream.

---

### Post by bcg30506 on 2011-06-14
I did reboot, but noticed there was another update reported by apt today, so I did it and rebooted again.  Then tried the same DVD again, the problem is still there but the log looked a bit different:
```
*** libdvdread: CHECK_VALUE failed in dvdread/nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

2011-06-14 13:40:10.660 Player(0): Waited 100ms for video buffers AAAAAAAddAAALAADA
2011-06-14 13:40:10.668 Player(0): Waited 100ms for video buffers AAAAAAAddAAALAADA

*** libdvdread: CHECK_VALUE failed in dvdread/nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

2011-06-14 13:40:10.677 Player(0): Waited 100ms for video buffers AAAAAAAddAAALAADA
2011-06-14 13:40:10.685 Player(0): Waited 100ms for video buffers AAAAAAAddAAALAADA
2011-06-14 13:40:10.763 AFD Warning: Audio 54441 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.764 AFD Warning: Audio 54410 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.764 AFD Warning: Audio 54444 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.777 AFD Warning: Audio 54413 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.777 AFD Warning: Audio 54383 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.777 AFD Warning: Audio 54416 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.778 AFD Warning: Audio 54449 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.810 AFD Warning: Audio 54483 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-14 13:40:10.811 AFD Warning: Audio 54452 ms behind video but already 180 video frames queued. AV-Sync might be broken.

*** libdvdread: CHECK_VALUE failed in dvdread/nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

```
This happens every few minutes and it coincides with a noticeable pause in the action for a split second.

I guess I do not understand your notation about how and where I report bugs.  Sorry, this is something I've not done before.

---

### Post by bcg30506 on 2011-06-19
Just performed 2 more reported upgrades this weekend to now 0.24.1-15 and it is still happening, though not as frequently.  Also, the frontend log shows a bit more and different info.  This occurred while trying to watch the Angel series DVD.
```
2011-06-19 21:57:08.235 AFD: Warning, audio codec 0xac9bce70 id(AC3) type (Audio) already open, leaving it alone.
2011-06-19 21:57:08.235 AFD: codec AC3 has 2 channels
2011-06-19 21:57:08.235 AFD: Opened codec 0xaedef720, id(DVD_SUBTITLE) type(Subtitle)
2011-06-19 21:57:18.528 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:57:21.014 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:57:37.598 Player(0): Waited 100ms for video buffers AAAAAALAAAAffAAAA
2011-06-19 21:57:37.607 Player(0): Waited 100ms for video buffers AAAAAALAAAAffAAAA
2011-06-19 21:57:37.615 Player(0): Waited 100ms for video buffers AAAAAALAAAAffAAAA
2011-06-19 21:57:37.726 Player(0): Waited 100ms for video buffers AAAAAALAAAAffAAAA
2011-06-19 21:57:37.850 AFD Warning: Audio 420684 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 21:57:37.850 AFD Warning: Audio 420734 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 21:57:37.874 AFD Warning: Audio 420671 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 21:57:38.320 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:57:49.968 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:58:38.233 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:58:43.238 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:59:34.288 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 21:59:34.788 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:00:35.013 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:00:39.635 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:01:33.187 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:01:39.593 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:02:07.287 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:02:08.288 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:02:58.120 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:03:32.370 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:04:18.249 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:05:09.799 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:05:34.273 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:06:45.676 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:07:30.186 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:07:34.023 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:07:50.273 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:07:51.774 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:08:50.649 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:08:51.650 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:08:57.848 AFD Warning: Audio 363252 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 22:08:57.870 AFD Warning: Audio 363222 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 22:08:57.870 AFD Warning: Audio 363272 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 22:08:57.871 AFD Warning: Audio 363305 ms behind video but already 180 video frames queued. AV-Sync might be broken.
2011-06-19 22:09:07.715 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-19 22:09:19.577 Starting update of NWS-XML
2011-06-19 22:09:19.601 Starting update of yrno-XML
2011-06-19 22:09:19.608 Starting update of wunderground-maps
2011-06-19 22:09:20.126 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground-maps.pl -u ENG -d /home/me/.mythtv/MythWeather/wunderground-maps FFC' has exited
2011-06-19 22:09:20.388 'nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/me/.mythtv/MythWeather/NWS-XML KGVL' has exited
2011-06-19 22:09:45.987 AudioPlayer: Disabling Audio, params(0,-1,-1)
2011-06-19 22:09:46.081 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.090 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.098 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.107 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.209 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.214 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2011-06-19 22:09:46.217 Player(0): Waited 100ms for video buffers dAAAADAAALAAAADAA
2011-06-19 22:09:46.582 AFD: codec AC3 has 0 channels
2011-06-19 22:09:46.582 AFD: Opened codec 0xaeda7f40, id(AC3) type(Audio)
2011-06-19 22:09:46.718 AO: Opening audio device 'default:CARD=NVidia' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-06-19 22:09:46.755 ALSA, Error: Setting hardware audio buffer size to 6016
2011-06-19 22:09:46.755 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-06-19 22:09:46.755 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-06-19 22:09:46.755 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-06-19 22:09:46.796 AudioPlayer: Enabling Audio

```
Of interest is the end of the attached log where it says unable to increase buffer size.  Why is it trying to and how can I help it to do so?

---

