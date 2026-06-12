---
title: "Unity broke?"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jerry421 on 2011-03-31
So i installed fglrx from repo which is a prerelease that supports Natty and after reboot everything is perfect but no Unity so i ran it from Terminal and this is what i got =/ any help?
```
erry@jerry-desktop:~$ unity
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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
** (<unknown>:2447): DEBUG: Unity accessibility initialization

Screen geometry changed:
  Monitor 0(primary)
   0x0x1680x1050

Initializing unityshell options...done
** (<unknown>:2447): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2447): DEBUG: PlaceEntry: Applications
** (<unknown>:2447): DEBUG: PlaceEntry: Commands
** (<unknown>:2447): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:2447): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:2447): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2447): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2447): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2447): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2447): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2447): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2447): DEBUG: Connected to proxy
** (<unknown>:2447): DEBUG: Connected to proxy
** (<unknown>:2447): DEBUG: Connected to proxy

(<unknown>:2447): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2447): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2447): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:2447): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:2447): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:2447): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:2447): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:2447): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:2447): DEBUG: Setting to primary screen rect: x=0 y=0 w=1680 h=1050

** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window62914605: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window62914605: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65011715: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65011715: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65011713: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:2447): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65011713: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



```

---

### Post by Koterpillar on 2011-03-31
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta)

---

### Post by Jerry421 on 2011-03-31
Still broken =P

---

### Post by Jerry421 on 2011-03-31
when i restart my computer i can still see the gnome panels and unity doesnt auto start unless i start it in Terminal any idea?

---

### Post by GratefulTony on 2011-04-01
I get the same message running nvidia restricted drivers. also, I get windows not displaying correctly after losing focus. Perhaps related.

---

### Post by Jerry421 on 2011-04-01
bump

---

### Post by Jerry421 on 2011-04-01
@ Anyone who is rebooting after installed Nvidia/Ati drivers and seeing the classic Gnome Menu when you clearly want your unity menu. This is a temporary fix that came to mind. It hides the gnome panel so you cant see it. Hope this Helps! I will be reposting a new thread about this also
**First:** ```
**sudo add-apt-repository** **ppa:unity/daily**
``` 
**Second: **```
**sudo apt-get update**
```[B]
Third: [/B]Open Update Manager and update.
**Forth:** Restart Delete **_BOTTOM_** bar
**Fifth: **right click top bar properties and change size to 21.
**Sixth:** Uncheck Expand Check Autohide Drag to right corner.
**Seventh:** System Settings>Startup Applications>Add> Name: Unity        Command: Unity
**Eighth:** Reboot
**Ninth:  **Enjoy :popcorn:

---

