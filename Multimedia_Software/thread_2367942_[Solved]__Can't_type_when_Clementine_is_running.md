---
title: "[Solved]  Can't type when Clementine is running"
date: 2017-08-05
forum: Multimedia Software
---

### Post by d3fau1t2 on 2017-08-05
Hi, 

When I am running Clementine, I noticed that I can't type anything other than in Clementine. If I type in a terminal, the cursor flashes but it doesn't make letters. 

It's probably my system, compiling Clementine from source had the same results. 

How can I troubleshoot this? 

Cheers

---

### Post by mc4man on 2017-08-05
No clue, don't see here.
Maybe read about xev [https://linux.die.net/man/1/xev](https://linux.die.net/man/1/xev)
and possibly start it, then open clem & see what happens when you type in the event window.

---

### Post by vasa1 on 2017-08-05
Can you set up another user account and try with that?

Or can you rename, temporarily, clementine-associated files in your home and ~/.config folders and see if the issue persists?

If Clementine is "hijacking" the keyboard, OP may not be able to run *xev*.

---

### Post by mc4man on 2017-08-05
> **vasa1 said:**
> Can you set up another user account and try with that?

Or can you rename, temporarily, clementine-associated files in your home and ~/.config folders and see if the issue persists?

If Clementine is "hijacking" the keyboard, OP may not be able to run *xev*.
Another user or guest user (if available)  sounds like a good idea.
I was thinking to start xev before clem..

---

### Post by d3fau1t2 on 2017-08-06
Hey guys, thanks for the replies. I tried xev. This is is what it spits out:

```
# DISPLAY=:0 xev
Outer window is 0x3000001, inner window is 0x3000002

PropertyNotify event, serial 8, synthetic NO, window 0x3000001,
    atom 0x27 (WM_NAME), time 37882877, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3000001,
    atom 0x22 (WM_COMMAND), time 37882877, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3000001,
    atom 0x28 (WM_NORMAL_HINTS), time 37882877, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3000001,
    parent 0x3000001, window 0x3000002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x3000001,
    atom 0x11c (WM_PROTOCOLS), time 37882877, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x3000001,
    event 0x3000001, window 0x3000002, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x159 (_NET_WM_VISIBLE_NAME), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x15a (_NET_WM_VISIBLE_ICON_NAME), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x180 (_OB_APP_ROLE), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x182 (_OB_APP_NAME), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x183 (_OB_APP_CLASS), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x184 (_OB_APP_GROUP_NAME), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x185 (_OB_APP_GROUP_CLASS), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x181 (_OB_APP_TITLE), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x186 (_OB_APP_TYPE), time 37882878, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x3000001,
    atom 0x125 (_NET_WM_ICON), time 37882879, state PropertyNewValue

ReparentNotify event, serial 20, synthetic NO, window 0x3000001,
    event 0x3000001, window 0x3000001, parent 0x600d50,
    (0,0), override NO

PropertyNotify event, serial 21, synthetic NO, window 0x3000001,
    atom 0x129 (_NET_WM_STATE), time 37882879, state PropertyNewValue

ConfigureNotify event, serial 21, synthetic NO, window 0x3000001,
    event 0x3000001, window 0x3000001, (0,0), width 178, height 178,
    border_width 0, above 0x600d7c, override NO

ConfigureNotify event, serial 21, synthetic NO, window 0x3000001,
    event 0x3000001, window 0x3000001, (2,24), width 178, height 178,
    border_width 0, above 0x600d7c, override NO

PropertyNotify event, serial 21, synthetic NO, window 0x3000001,
    atom 0x121 (_NET_FRAME_EXTENTS), time 37882880, state PropertyNewValue

PropertyNotify event, serial 21, synthetic NO, window 0x3000001,
    atom 0x160 (_KDE_NET_WM_FRAME_STRUT), time 37882880, state PropertyNewValue

PropertyNotify event, serial 21, synthetic NO, window 0x3000001,
    atom 0x15e (_NET_WM_ALLOWED_ACTIONS), time 37882880, state PropertyNewValue

ConfigureNotify event, serial 21, synthetic YES, window 0x3000001,
    event 0x3000001, window 0x3000001, (0,52), width 178, height 178,
    border_width 2, above 0x0, override NO

PropertyNotify event, serial 21, synthetic NO, window 0x3000001,
    atom 0x124 (_NET_WM_DESKTOP), time 37882880, state PropertyNewValue

MapNotify event, serial 28, synthetic NO, window 0x3000001,
    event 0x3000001, window 0x3000001, override NO

VisibilityNotify event, serial 28, synthetic NO, window 0x3000001,
    state VisibilityUnobscured

Expose event, serial 28, synthetic NO, window 0x3000001,
    (0,0), width 178, height 10, count 3

Expose event, serial 28, synthetic NO, window 0x3000001,
    (0,10), width 10, height 58, count 2

Expose event, serial 28, synthetic NO, window 0x3000001,
    (68,10), width 110, height 58, count 1

Expose event, serial 28, synthetic NO, window 0x3000001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 28, synthetic NO, window 0x3000001,
    atom 0x143 (WM_STATE), time 37882888, state PropertyNewValue

FocusIn event, serial 29, synthetic NO, window 0x3000001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  0   0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ColormapNotify event, serial 44, synthetic NO, window 0x3000001,
    colormap 0x20, new NO, state ColormapInstalled

PropertyNotify event, serial 44, synthetic NO, window 0x3000001,
    atom 0x15d (_NET_WM_ICON_GEOMETRY), time 37882916, state PropertyNewValue

PropertyNotify event, serial 45, synthetic NO, window 0x3000001,
    atom 0x15d (_NET_WM_ICON_GEOMETRY), time 37882927, state PropertyNewValue

KeyRelease event, serial 45, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37882947, (295,615), root:(297,669),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

FocusOut event, serial 48, synthetic NO, window 0x3000001,
    mode NotifyGrab, detail NotifyNonlinear

VisibilityNotify event, serial 48, synthetic NO, window 0x3000001,
    state VisibilityPartiallyObscured

FocusIn event, serial 48, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyNonlinear

KeymapNotify event, serial 48, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

VisibilityNotify event, serial 48, synthetic NO, window 0x3000001,
    state VisibilityUnobscured

Expose event, serial 48, synthetic NO, window 0x3000001,
    (4,0), width 174, height 10, count 3

Expose event, serial 48, synthetic NO, window 0x3000001,
    (4,10), width 6, height 58, count 2

Expose event, serial 48, synthetic NO, window 0x3000001,
    (68,10), width 110, height 58, count 1

Expose event, serial 48, synthetic NO, window 0x3000001,
    (4,68), width 174, height 110, count 0

EnterNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904200, (117,156), root:(119,210),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 48, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904200, (117,156), root:(119,210),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904213, (106,128), root:(108,182),
    state 0x0, is_hint 0, same_screen YES

FocusOut event, serial 48, synthetic NO, window 0x3000001,
    mode NotifyNormal, detail NotifyNonlinear

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904221, (90,91), root:(92,145),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904234, (74,49), root:(76,103),
    state 0x0, is_hint 0, same_screen YES

LeaveNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x0, time 37904243, (62,31), root:(64,85),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus NO, state 0

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x3000002, time 37904243, (62,31), root:(64,85),
    state 0x0, is_hint 0, same_screen YES

PropertyNotify event, serial 48, synthetic NO, window 0x3000001,
    atom 0x15d (_NET_WM_ICON_GEOMETRY), time 37904245, state PropertyNewValue

MotionNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x3000002, time 37904254, (58,15), root:(60,69),
    state 0x0, is_hint 0, same_screen YES

LeaveNotify event, serial 48, synthetic NO, window 0x3000001,
    root 0x49c, subw 0x3000002, time 37904266, (52,-5), root:(54,49),
    mode NotifyNormal, detail NotifyNonlinearVirtual, same_screen YES,
    focus NO, state 0

VisibilityNotify event, serial 48, synthetic NO, window 0x3000001,
    state VisibilityFullyObscured

ColormapNotify event, serial 48, synthetic NO, window 0x3000001,
    colormap 0x20, new NO, state ColormapUninstalled

PropertyNotify event, serial 48, synthetic NO, window 0x3000001,
    atom 0x15d (_NET_WM_ICON_GEOMETRY), time 37906996, state PropertyNewValue
```

I do not know how to intrepret this, but it didn't seem to change when I pushed the buttons on the keyboard.

I also tried renaming the clementine config folder, no dice.

---

### Post by d3fau1t2 on 2017-08-06
Here's the output when starting Clementine in a terminal:

```
# clementine
20:17:17.823 INFO  main:334                         Clementine 1.3.1 
20:17:18.107 DEBUG WorkerPool<HandlerType>:281      Starting worker 0xae9fec0c "/usr/bin/clementine-tagreader" "/tmp/clementine_385501921" 
20:17:18.110 DEBUG WorkerPool<HandlerType>:281      Starting worker 0xae9fec0c "/usr/bin/clementine-tagreader" "/tmp/clementine_1277598875" 
20:17:18.113 DEBUG WorkerPool<HandlerType>:281      Starting worker 0xae9fec0c "/usr/bin/clementine-tagreader" "/tmp/clementine_347102772" 
20:17:18.116 DEBUG WorkerPool<HandlerType>:281      Starting worker 0xae9fec0c "/usr/bin/clementine-tagreader" "/tmp/clementine_1979270335" 
20:17:18.120 INFO  Database:282                     Creating initial database schema 
20:17:18.128 DEBUG Database:444                     Applying database schema update 0 from ":/schema/schema.sql" 
20:17:18.140 DEBUG Database:444                     Applying database schema update 1 from ":/schema/schema-1.sql" 
20:17:18.147 DEBUG Database:444                     Applying database schema update 2 from ":/schema/schema-2.sql" 
20:17:18.154 DEBUG Database:444                     Applying database schema update 3 from ":/schema/schema-3.sql" 
20:17:18.157 INFO  main:48                          TagReader worker connecting to "/tmp/clementine_385501921" 
20:17:18.158 DEBUG WorkerPool<HandlerType>:301      Worker 0xae00b970 connected to "/tmp/clementine_385501921" 
20:17:18.162 DEBUG Database:444                     Applying database schema update 4 from ":/schema/schema-4.sql" 
20:17:18.165 INFO  main:48                          TagReader worker connecting to "/tmp/clementine_1277598875" 
20:17:18.166 DEBUG WorkerPool<HandlerType>:301      Worker 0xae00c650 connected to "/tmp/clementine_1277598875" 
20:17:18.170 DEBUG Database:444                     Applying database schema update 5 from ":/schema/schema-5.sql" 
20:17:18.172 DEBUG Database:444                     Applying database schema update 6 from ":/schema/schema-6.sql" 
20:17:18.173 DEBUG Database:444                     Applying database schema update 7 from ":/schema/schema-7.sql" 
20:17:18.174 DEBUG Database:444                     Applying database schema update 8 from ":/schema/schema-8.sql" 
20:17:18.175 DEBUG Database:444                     Applying database schema update 9 from ":/schema/schema-9.sql" 
20:17:18.176 DEBUG Database:444                     Applying database schema update 10 from ":/schema/schema-10.sql" 
20:17:18.181 DEBUG Database:444                     Applying database schema update 11 from ":/schema/schema-11.sql" 
20:17:18.186 DEBUG Database:444                     Applying database schema update 12 from ":/schema/schema-12.sql" 
20:17:18.192 DEBUG Database:444                     Applying database schema update 13 from ":/schema/schema-13.sql" 
20:17:18.195 INFO  main:48                          TagReader worker connecting to "/tmp/clementine_1979270335" 
20:17:18.196 INFO  main:48                          TagReader worker connecting to "/tmp/clementine_347102772" 
20:17:18.196 DEBUG WorkerPool<HandlerType>:301      Worker 0xae00df20 connected to "/tmp/clementine_1979270335" 
20:17:18.197 DEBUG WorkerPool<HandlerType>:301      Worker 0xae00d2c8 connected to "/tmp/clementine_347102772" 
20:17:18.198 DEBUG Database:444                     Applying database schema update 14 from ":/schema/schema-14.sql" 
20:17:18.200 DEBUG Database:444                     Applying database schema update 15 from ":/schema/schema-15.sql" 
20:17:18.202 DEBUG Database:444                     Applying database schema update 16 from ":/schema/schema-16.sql" 
20:17:18.211 DEBUG Database:444                     Applying database schema update 17 from ":/schema/schema-17.sql" 
20:17:18.214 DEBUG Database:444                     Applying database schema update 18 from ":/schema/schema-18.sql" 
20:17:18.215 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.217 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.217 DEBUG Database:444                     Applying database schema update 19 from ":/schema/schema-19.sql" 
20:17:18.219 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.219 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.221 DEBUG Database:444                     Applying database schema update 20 from ":/schema/schema-20.sql" 
20:17:18.224 DEBUG Database:444                     Applying database schema update 21 from ":/schema/schema-21.sql" 
20:17:18.229 DEBUG Database:444                     Applying database schema update 22 from ":/schema/schema-22.sql" 
20:17:18.231 DEBUG Database:444                     Applying database schema update 23 from ":/schema/schema-23.sql" 
20:17:18.233 DEBUG Database:444                     Applying database schema update 24 from ":/schema/schema-24.sql" 
20:17:18.235 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.236 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.237 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.246 DEBUG Database:444                     Applying database schema update 25 from ":/schema/schema-25.sql" 
20:17:18.247 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.248 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.249 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.250 DEBUG Database:444                     Applying database schema update 26 from ":/schema/schema-26.sql" 
20:17:18.255 DEBUG Database:444                     Applying database schema update 27 from ":/schema/schema-27.sql" 
20:17:18.258 DEBUG Database:444                     Applying database schema update 28 from ":/schema/schema-28.sql" 
20:17:18.259 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.259 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.260 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.260 DEBUG Database:444                     Applying database schema update 29 from ":/schema/schema-29.sql" 
20:17:18.281 DEBUG Database:444                     Applying database schema update 30 from ":/schema/schema-30.sql" 
20:17:18.286 DEBUG Database:439                     Applying database schema update 31 from ":/schema/schema-31.sql" 
20:17:18.288 DEBUG Database:444                     Applying database schema update 32 from ":/schema/schema-32.sql" 
20:17:18.290 DEBUG Database:444                     Applying database schema update 33 from ":/schema/schema-33.sql" 
20:17:18.292 DEBUG Database:444                     Applying database schema update 34 from ":/schema/schema-34.sql" 
20:17:18.294 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.295 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.296 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.297 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.298 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.299 DEBUG Database:444                     Applying database schema update 35 from ":/schema/schema-35.sql" 
20:17:18.302 DEBUG Database:444                     Applying database schema update 36 from ":/schema/schema-36.sql" 
20:17:18.305 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.306 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.306 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.307 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.308 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.310 DEBUG Database:444                     Applying database schema update 37 from ":/schema/schema-37.sql" 
20:17:18.314 DEBUG Database:444                     Applying database schema update 38 from ":/schema/schema-38.sql" 
20:17:18.316 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.316 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.318 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.318 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.320 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.324 DEBUG Database:444                     Applying database schema update 39 from ":/schema/schema-39.sql" 
20:17:18.327 DEBUG Database:444                     Applying database schema update 40 from ":/schema/schema-40.sql" 
20:17:18.332 DEBUG Database:444                     Applying database schema update 41 from ":/schema/schema-41.sql" 
20:17:18.336 DEBUG Database:444                     Applying database schema update 42 from ":/schema/schema-42.sql" 
20:17:18.344 DEBUG Database:444                     Applying database schema update 43 from ":/schema/schema-43.sql" 
20:17:18.347 DEBUG Database:444                     Applying database schema update 44 from ":/schema/schema-44.sql" 
20:17:18.349 DEBUG Database:444                     Applying database schema update 45 from ":/schema/schema-45.sql" 
20:17:18.351 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.351 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.351 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.351 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.351 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.351 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.352 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.352 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.352 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.352 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.352 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.353 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.353 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.354 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.355 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.356 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.356 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.357 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.358 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.358 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.359 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.360 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.360 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.361 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.361 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.361 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.362 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.362 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.363 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.363 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.363 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.364 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.364 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.365 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.365 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.366 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.366 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.366 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.367 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.367 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.368 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.368 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.368 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.369 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.369 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.370 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.371 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.372 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.373 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.374 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.375 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.375 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.376 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.377 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.378 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.379 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.379 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.379 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.380 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.381 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.381 DEBUG Database:444                     Applying database schema update 46 from ":/schema/schema-46.sql" 
20:17:18.383 DEBUG Database:444                     Applying database schema update 47 from ":/schema/schema-47.sql" 
20:17:18.385 DEBUG Database:444                     Applying database schema update 48 from ":/schema/schema-48.sql" 
20:17:18.388 DEBUG Database:444                     Applying database schema update 49 from ":/schema/schema-49.sql" 
20:17:18.388 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.389 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.389 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.390 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.390 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.391 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.391 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.392 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.392 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.393 INFO  Database:524                     Updating "seafile_songs" for %allsongstables 
20:17:18.393 INFO  Database:524                     Updating "amazon_cloud_drive_songs" for %allsongstables 
20:17:18.394 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.394 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.395 DEBUG Database:444                     Applying database schema update 50 from ":/schema/schema-50.sql" 
20:17:18.396 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.396 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.397 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.397 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.398 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.398 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.399 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.399 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.400 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.400 INFO  Database:524                     Updating "seafile_songs" for %allsongstables 
20:17:18.401 INFO  Database:524                     Updating "amazon_cloud_drive_songs" for %allsongstables 
20:17:18.401 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.402 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.402 INFO  Database:524                     Updating "songs" for %allsongstables 
20:17:18.403 INFO  Database:524                     Updating "magnatune_songs" for %allsongstables 
20:17:18.403 INFO  Database:524                     Updating "spotify_search_songs" for %allsongstables 
20:17:18.404 INFO  Database:524                     Updating "google_drive_songs" for %allsongstables 
20:17:18.404 INFO  Database:524                     Updating "ubuntu_one_songs" for %allsongstables 
20:17:18.404 INFO  Database:524                     Updating "dropbox_songs" for %allsongstables 
20:17:18.405 INFO  Database:524                     Updating "skydrive_songs" for %allsongstables 
20:17:18.405 INFO  Database:524                     Updating "subsonic_songs" for %allsongstables 
20:17:18.406 INFO  Database:524                     Updating "box_songs" for %allsongstables 
20:17:18.406 INFO  Database:524                     Updating "seafile_songs" for %allsongstables 
20:17:18.407 INFO  Database:524                     Updating "amazon_cloud_drive_songs" for %allsongstables 
20:17:18.407 INFO  Database:524                     Updating "jamendo.songs" for %allsongstables 
20:17:18.407 INFO  Database:524                     Updating "playlist_items" for %allsongstables 
20:17:18.459 INFO  Player:627                       Registered URL handler for "di" 
20:17:18.460 DEBUG InternetModel:140                Adding internet service: "DigitallyImported" 
20:17:18.512 DEBUG InternetModel:140                Adding internet service: "Icecast" 
20:17:18.780 DEBUG InternetModel:140                Adding internet service: "Jamendo" 
20:17:18.793 INFO  Player:627                       Registered URL handler for "jazzradio" 
20:17:18.794 DEBUG InternetModel:140                Adding internet service: "JazzRadio" 
20:17:18.796 INFO  Player:627                       Registered URL handler for "magnatune" 
20:17:18.810 DEBUG InternetModel:140                Adding internet service: "Magnatune" 
20:17:18.851 DEBUG InternetModel:140                Adding internet service: "Podcasts" 
20:17:18.864 INFO  Player:627                       Registered URL handler for "rockradio" 
20:17:18.865 DEBUG InternetModel:140                Adding internet service: "RockRadio" 
20:17:18.880 DEBUG InternetModel:140                Adding internet service: "SavedRadio" 
20:17:18.892 INFO  Player:627                       Registered URL handler for "radiotunes" 
20:17:18.893 DEBUG InternetModel:140                Adding internet service: "RadioTunes" 
20:17:18.905 INFO  Player:627                       Registered URL handler for "somafm" 
20:17:18.906 DEBUG InternetModel:140                Adding internet service: "SomaFM" 
20:17:18.924 DEBUG InternetModel:140                Adding internet service: "SoundCloud" 
20:17:18.926 DEBUG SpotifyService:108               Spotify system blob path: "/usr/bin/clementine-spotifyblob" 
20:17:18.926 DEBUG SpotifyService:109               Spotify local blob path: "/root/.config/Clementine/spotifyblob/version16-32bit/blob" 
20:17:18.940 DEBUG InternetModel:140                Adding internet service: "Spotify" 
20:17:18.940 INFO  Player:627                       Registered URL handler for "subsonic" 
20:17:19.026 DEBUG InternetModel:140                Adding internet service: "Subsonic" 
20:17:19.042 INFO  Player:627                       Registered URL handler for "box" 
20:17:19.043 DEBUG InternetModel:140                Adding internet service: "Box" 
20:17:19.057 INFO  Player:627                       Registered URL handler for "dropbox" 
20:17:19.057 DEBUG InternetModel:140                Adding internet service: "Dropbox" 
20:17:19.071 INFO  Player:627                       Registered URL handler for "googledrive" 
20:17:19.072 DEBUG InternetModel:140                Adding internet service: "Google Drive" 
20:17:19.086 INFO  Player:627                       Registered URL handler for "seafile" 
20:17:19.086 DEBUG InternetModel:140                Adding internet service: "Seafile" 
20:17:19.100 INFO  Player:627                       Registered URL handler for "skydrive" 
20:17:19.100 DEBUG InternetModel:140                Adding internet service: "OneDrive" 
20:17:19.116 INFO  Player:627                       Registered URL handler for "vk" 
20:17:19.116 DEBUG InternetModel:140                Adding internet service: "Vk.com" 
20:17:19.132 INFO  Player:627                       Registered URL handler for "amazonclouddrive" 
20:17:19.132 DEBUG InternetModel:140                Adding internet service: "Amazon Cloud Drive" 
20:17:19.137 WARN  DeviceKitLister:55               Error enumerating DeviceKit-disks devices: "org.freedesktop.DBus.Error.Disconnected" "Not connected to D-Bus server" 
20:17:19.144 DEBUG CoverProviders:35                Registered cover provider "last.fm" 
20:17:19.145 DEBUG NetworkProxyFactory:49           Detected system proxy URLs: ("", "", "", "") 
20:17:19.145 DEBUG CoverProviders:35                Registered cover provider "Amazon" 
20:17:19.145 DEBUG CoverProviders:35                Registered cover provider "MusicBrainz" 
20:17:19.176 WARN  IconLoader:103                   Couldn't load icon "clementine-panel" 
20:17:19.189 WARN  IconLoader:103                   Couldn't load icon "clementine-panel-grey" 
20:17:19.207 DEBUG GnomeGlobalShortcutBackend:52    registering 
20:17:19.207 WARN  GnomeGlobalShortcutBackend:56    gnome settings daemon not registered 
20:17:19.207 DEBUG QxtGlobalShortcutBackend:32      registering 
20:17:19.695 DEBUG MainWindow:199                   Starting 
20:17:19.733 WARN  IconLoader:103                   Couldn't load icon "find" 
20:17:19.749 WARN  IconLoader:103                   Couldn't load icon "find" 
20:17:19.758 WARN  unknown                          QPainter::begin: Paint device returned engine == 0, type: 2 
20:17:19.847 DEBUG MainWindow:273                   Initialising player 
20:17:19.852 DEBUG MainWindow:279                   Creating models 
20:17:19.860 DEBUG MainWindow:301                   Creating UI 
20:17:19.947 INFO  GstEngine:171                    Skipping DeviceFinder for "pulsesink" known plugins: QSet("autoaudiosink", "avdtpsink", "ladspasink-cmt-so-track-peak", "alsasink", "ladspasink-cmt-so-peak", "interaudiosink", "openalsink", "ladspasink-cmt-so-track-max-peak", "ladspasink-cmt-so-track-rms", "oss4sink", "jackaudiosink", "ladspasink-cmt-so-null-ai", "osssink", "a2dpsink", "ladspasink-cmt-so-track-max-rms") 
20:17:20.311 DEBUG MainWindow:846                   Creating equalizer 
20:17:20.313 DEBUG MainWindow:875                   Creating now playing widget 
20:17:20.456 DEBUG MainWindow:937                   Loading settings 
20:17:20.464 INFO  NetworkRemote:80                 Network Remote deactivated 
20:17:20.502 DEBUG MainWindow:1016                  Started 
20:17:20.521 INFO  DeviceManager:405                Device added: "/dev/sr0" 

```

---

### Post by d3fau1t2 on 2017-08-10
Anybody? 

Clementine is my favorite player, but when I run it I can't type in a browser or anything. It's very frustrating.

---

### Post by mc4man on 2017-08-10
Did you test a new user account?

---

### Post by d3fau1t2 on 2017-08-10
Yes. I tried that, deleting the config folder, renistalling with different deb packages. I even managed to compile it from source. But it's always the same

---

### Post by vasa1 on 2017-08-10
What is the output when you start Clementine from a terminal? There may be some clues there.

And please elaborate on "but when I run it I can't type in a browser or anything." What about typing in gedit or in some other editor?

---

### Post by d3fau1t2 on 2017-08-10
ALL typing, outside of Clementine itself, does not work. I attached the terminal output in an above post.

---

### Post by vasa1 on 2017-08-10
> **d3fau1t2 said:**
> ... I attached the terminal output in an above post.
Sorry! I overlooked that. I wonder if```
20:17:19.137 WARN  DeviceKitLister:55               Error enumerating DeviceKit-disks devices: "org.freedesktop.DBus.Error.Disconnected" "Not connected to D-Bus server" 
```is significant.

BTW, when you run *sudo apt-get update* and *sudo apt-get upgrade* are there any warnings or untoward messages?

---

### Post by d3fau1t2 on 2017-08-10
I solved this by deactivating keyboard shortcuts. Now everything works fine. 

Thanks for your help

---

