---
title: "Frequent frontend lockups on 0.25 / 10.04 LTS"
date: 2012-05-05
forum: Mythbuntu
---

### Post by andrewc6l on 2012-05-05
I see someone else has a thread ([http://ubuntuforums.org/showthread.php?t=1971260](http://ubuntuforums.org/showthread.php?t=1971260)) on frequent frontend lockups on 0.25 with Precise. But I'm using 10.04 LTS and see something similar: at random times, mythfrontend just goes away - I get a blank screen and nothing in the log. It's still running, though.

If I kill mythfrontend.real and restart it, then things work again... but the WAF is getting lowered :-(

Logs aren't really helpful:

```
May  5 10:35:03 mythtv mythfrontend[5095]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingPreRecorded to None
May  5 10:35:03 mythtv mythfrontend[5095]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
May  5 10:35:03 mythtv mythfrontend[5095]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
May  5 10:39:47 mythtv mythfrontend[5095]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of yrno-XML
May  5 10:39:47 mythtv mythfrontend[5095]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of wunderground-animaps
May  5 10:44:47 mythtv mythfrontend[5095]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of NWS-XML
May  5 10:44:48 mythtv mythfrontend[5095]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of wunderground-maps
May  5 10:44:48 mythtv mythfrontend[5095]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of NWS-Alerts

```
(at this point I killed mythfrontend.real, and it restarted with no problems):
```

May  5 12:52:11 mythtv mythfrontend[9450]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-65-g2e2f02e] www.mythtv.org

```

I'd be suprised if the NWS-Alerts update is the culprit (but maybe it is... that seems to be what's happening before every crash in my log). I am using NVIDIA as well. Is turning off realtime priority threads an option on 10.04? Has anyone else run into this?

Maybe I'll try uninstalling mythweather to see if that solves the problem.

---

### Post by andrewc6l on 2012-05-21
Disabling the NWS alerts helped somewhat, but I still get crashes in weatherSource.cpp. So now I'm removing all of MythWeather (shame) to see if that helps.

---

### Post by andrewc6l on 2012-06-11
No crashes in two weeks with MythWeather removed.

---

### Post by jmeissen on 2012-10-08
I have the same problem. dpkg shows 
mythweather     2:0.25.2+fixes.20120802.46cab93-0ubuntu1
mythtv-frontend 2:0.25.2+fixes.20120802.46cab93-0ubuntu1

In every case the last entry in mythfrontend.log is one of the wunderground updates (Starting update of wunderground-maps/wunderground-animaps/wunderground)

I've tried selecting and un-selecting the "update in background" option, with no apparent effect. I finally removed all of the weather data from the config, and so far, so good.

---

