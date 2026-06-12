---
title: "Mythbuntu 0.27 slow boot"
date: 2015-03-04
forum: Mythbuntu
---

### Post by ceesquared on 2015-03-04
I have a combined FE/BE. Since upgrading? to 14.04/0.27 the boot is noticeably slower. Looking at the FE and BE logs there are two gaps. Can anybody explain why and how do I solve it?
FE log extract:-
Mar  3 09:12:12 mythtv mythfrontend.real: mythfrontend[1453]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Mar  3 09:12:**13** mythtv mythfrontend.real: mythfrontend[1453]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Mar  3 09:12:**50** mythtv mythfrontend.real: mythfrontend[1453]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Mar  3 09:12:50 mythtv mythfrontend.real: mythfrontend[1453]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Mar  3 09:12:50 mythtv mythfrontend.real: mythfrontend[1453]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Mar  3 09:12:50 mythtv mythfrontend.real: mythfrontend[1453]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.


BE log extract:-

Mar  3 09:12:10 mythtv mythbackend: mythbackend[1946]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: mythtv as a client (events: 1)
Mar  3 09:12:**11** mythtv mythbackend: mythbackend[1946]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Mar  3 09:12:**29** mythtv mythbackend: mythbackend[1946]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 23 items in 17.8 = 16.65 match + 0.95 check + 0.21 place
Mar  3 09:12:29 mythtv mythbackend: mythbackend[1946]: I Scheduler scheduler.cpp:2278 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Mar  3 09:12:29 mythtv mythbackend: mythbackend[1946]: N Scheduler scheduler.cpp:2678 (HandleIdleShutdown) Client is connected, removing startup block on shutdown
Mar  3 09:12:**56** mythtv mythbackend: mythbackend[1946]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback

---

