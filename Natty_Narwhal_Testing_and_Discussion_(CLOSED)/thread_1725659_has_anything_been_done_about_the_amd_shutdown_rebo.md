---
title: "has anything been done about the amd shutdown reboot"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-04-10
my machine wont reboot from natty I hit reboot and it shuts down partially will only reboot when I press the reset button on the tower also when I shut natty down it tries to start when i press the power button but then i have to hit the reset button on the tower to get it to load. I thought it was a  video card driver problem but I have installed fglrx and it hasnt sorted the problem

---

### Post by rbrick49 on 2011-04-10
nothing I guess no replies

---

### Post by CaptainMark on 2011-04-10
[already got a thread on it]("http://ubuntuforums.org/showthread.php?t=1715776"), and no, i keep updating but nothing so far,

---

### Post by rbrick49 on 2011-04-10
> **CaptainMark said:**
> [already got a thread on it]("http://ubuntuforums.org/showthread.php?t=1715776"), and no, i keep updating but nothing so far,
thanks mate its just rather anoying but not to worry I guess it will come good
by the way when I boot into windows it wont reboot on the first reboot but second time ok this is starting to make me wonder

---

### Post by MAFoElffen on 2011-04-10
> **rbrick49 said:**
> my machine wont reboot from natty I hit reboot and it shuts down partially will only reboot when I press the reset button on the tower also when I shut natty down it tries to start when i press the power button but then i have to hit the reset button on the tower to get it to load. I thought it was a  video card driver problem but I have installed fglrx and it hasnt sorted the problem
What happens if you go to a terminal sessions and type:
```
sudo shutdown 0 -r
```Previous version of Ubuntu did this on some of my boxes here, but it seemed like later xorg updates seemed to iron things out in them... and yes, it seemed to me that it was video related and by coincidence, all those boxes just happened to all have nvidia caeds in them.

I was having problems shutting down tty sessions... yes, I've noticed that there seems to be some changes in the shutdown process, but no-one is saying what.  I have had to adjust to them here.

If you start in a text or single user mode (dynamically edit gub menu item, append the kernel boot line w/ " single " or " text "... then start the Xsession via--
```
sudo start gdm
```then stop the GUI by opening a terminal session and typing ```
sudo stop gdm
```Does the Xsession go cleanly back down to the text console prompt without errors?  Or does it hang with errors?

If so... then there should be some sign of those errors recorded in " .xseesion.errors " located in your home directory.  Why not post that file here and we'll see what it says...

---

### Post by rbrick49 on 2011-04-10
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-UoD8CZ
GNOME_KEYRING_CONTROL=/tmp/keyring-UoD8CZ
GNOME_KEYRING_CONTROL=/tmp/keyring-UoD8CZ
SSH_AUTH_SOCK=/tmp/keyring-UoD8CZ/ssh
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
** (process:1586): DEBUG: zeitgeist-datahub.vala:174: Inserting 15 events
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing wall options...done
Initializing vpswitch options...done
Initializing nautilus-gdu extension
Initializing resize options...done
Initializing unitymtgrabhandles options...done
Initializing gnomecompat options...done
I/O warning : failed to load external entity "/home/ron/.compiz/session/101e95092d42ad6302130246383257179700000015100029"
Initializing session options...done
Initializing move options...done
Initializing grid options...done
Initializing animation options...done
Initializing wobbly options...done
Initializing expo options...done
Initializing workarounds options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done

(nautilus:1583): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:1583): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (<unknown>:1576): DEBUG: Unity accessibility initialization

Screen geometry changed:
  Monitor 0(primary)
   0x0x1920x1080

unity-panel-service: no process found
** (<unknown>:1576): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
Starting unity-window-decorator
** (<unknown>:1576): DEBUG: PlaceEntry: Applications
** (<unknown>:1576): DEBUG: PlaceEntry: Commands
** (<unknown>:1576): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1576): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1576): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1576): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:1576): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
** (<unknown>:1576): DEBUG: Connected to proxy

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1583): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(<unknown>:1576): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:1576): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:1576): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.
** (<unknown>:1576): DEBUG: Connected to proxy
** (<unknown>:1576): DEBUG: Connected to proxy

(<unknown>:1576): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1576): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1576): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1576): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1576): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1576): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:1576): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1576): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1576): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1576): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1576): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1576): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:1576): DEBUG: Setting to primary screen rect: x=0 y=0 w=1920 h=1080
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (process:1586): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
[1760:1760:40018898:ERROR:extension_prefs.cc(734)] Bad or missing pref 'state' for extension 'hpibmhghjndideebpackbdlpncgkcppp'
[1760:1760:40019087:ERROR:extension_prefs.cc(734)] Bad or missing pref 'state' for extension 'lncjcfkpannmofmpgdfoonkniofdnaba'
** (<unknown>:1576): DEBUG: MaximizeIfBigEnough: Chromium-browser window size doesn't fit

** (<unknown>:1576): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1576): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1576): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1576): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1586): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1576): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1576): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit
Asus M3A78-CM main board
radeon 6950 graphics card
fglrx driver
8 gig of ram
amd dual core processor 5000+

---

### Post by MAFoElffen on 2011-04-10
IMHO-- Seems to me that this log does seem to be what needs to submitted up at Ubuntu Launchpad to try to help resolve this problem- Along with the info on your setup, especially on video hardware and video drivers.

---

### Post by rbrick49 on 2011-04-11
after upgrades today my reboot shutdown restart works just fine thank you

---

### Post by rbrick49 on 2011-04-11
after todays 160 odd updates all is ok I guess I have beta 2 now

---

### Post by cariboo on 2011-04-11
> **rbrick49 said:**
> after todays 160 odd updates all is ok I guess I have beta 2 now

Beta 2 isn't due until the 14th.

---

### Post by rbrick49 on 2011-04-12
well it seemed an awful lot of upgrades as I update everyday

---

