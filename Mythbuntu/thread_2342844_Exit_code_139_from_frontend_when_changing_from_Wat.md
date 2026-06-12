---
title: "Exit code 139 from frontend when changing from WatchingPreRecorded to None"
date: 2016-11-10
forum: Mythbuntu
---

### Post by noscgag on 2016-11-10
For the past week or so when I stop playing a pre-recorded show, the frontend exits and a dialog box displays that says "Restarting Frontend The front-end crashed unexpectedly (exit code 139) and is restarting. Please wait."

Searching for "exit code 139" hasn't revealed much in the way of help. One person said the time zone may be different between the frontend and the backend, but I'm running them both on the same machine. However, we did just transition from daylight savings back to standard time, so that may have something to do with it. I'm not sure, but I think the problem may have started about then.

I am running Ubuntu 14.04.01, mythfrontend version: fixes/0.27 [v0.27-193-g8ee257c].

Neither the backend nor the frontend logs indicate any problem when the crash occurs. A portion of the frontend log is here:

Nov 10 10:05:33 mythtv mythfrontend.real: mythfrontend[2709]: I CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from WatchingPreRecorded to None
Nov 10 10:05:33 mythtv mythfrontend.real: mythfrontend[2709]: I CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
Nov 10 10:05:33 mythtv mythfrontend.real: mythfrontend[2709]: N CoreContext mythmainwindow.cpp:2643 (PauseIdleTimer) Resuming idle timer
Nov 10 10:05:35 mythtv mythfrontend.real: mythfrontend[2795]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 10 10:05:35 mythtv mythfrontend.real: mythfrontend[2795]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler

At 10:05:35 it appears that the frontend is restarting, but there is no intervening error message. The crash message above is only displayed in a small window on the frontend immediately after the crash.

---

### Post by noscgag on 2016-11-13
While I don't think I've solved this problem, I do have a workaround. If I go to the frontend Setup and navigate to Video --> Playback --> Playback Profiles (screen 3/8) and change the "Current Video Playback Profile" from "OpenGL Normal" to just "Normal", I no longer have the problem. As far as I can tell this doesn't affect playback adversely.

I suspect the problem was caused the the recent NVidia update from 304.131 to 304.132, but I was unable to revert to 304.131 due to a kernel update.

---

