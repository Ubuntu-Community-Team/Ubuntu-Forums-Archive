---
title: "Right click on desktop up and left"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by russ553 on 2011-04-24
Well, dang.  I had a really nice desktop set up with launchers for all my most used programs using custom icons, right click worked on the desktop to add launchers, folders and documents and the places, bookmarks, help on the top panel worked.

All of a sudden, poof, gone.  Right click no longer works, the top panel doesn't work and my launchers are gone.  What happened?

I am fully updated and upgraded.  Natty/Unity.

I tried logging out, logging in, restarted, shut down and rebooted.  Nothing works.

Now I am also getting random crashes and restarts.  Had one when clicking on the upload button to include the screenshot of my desktop.  Had to start this over.

---

### Post by 3rdalbum on 2011-04-24
```
unity --reset
```

Might help. (don't worry, this just restarts Unity, it doesn't destroy your settings or anything).

---

### Post by russ553 on 2011-04-24
Thanks. tried that.  Terminal churns out a bunch of stuff then sits there.  When I close it, it tells me there is a process still running, then clears the Unity desktop and I have to restart.

---

### Post by russ553 on 2011-04-24
```
russell@russell-TECRA-A8:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:6551): DEBUG: Unity accessibility initialization
** (<unknown>:6551): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:6551): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:6551): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:6551): DEBUG: PlaceEntry: Applications
** (<unknown>:6551): DEBUG: PlaceEntry: Commands
** (<unknown>:6551): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:6551): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:6551): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:6551): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:6551): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:6551): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window60817859: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:6551): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window60817859: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:6551): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:6551): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:6551): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:6551): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:6551): DEBUG: IndicatorAdded: libme.so
** (<unknown>:6551): DEBUG: IndicatorAdded: libsession.so
```

This is what i get and it's still just sitting there.  Manual close of terminal closes Unity.

---

### Post by MightyMouse2817 on 2011-04-25
I just had this problem tonight - try opening gconf-editor, go to apps->nautilus->preferences, and make sure show_desktop is checked.

---

### Post by russ553 on 2011-04-25
That's ticked.

---

