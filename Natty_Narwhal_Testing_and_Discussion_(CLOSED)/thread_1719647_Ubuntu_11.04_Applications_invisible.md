---
title: "Ubuntu 11.04 Applications invisible"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aljazek on 2011-04-02
Hi! When I press Applications thumb on new unity panel and then "See ## more results", entire dash is invisible untill I cross it with cursor. Is that just unity bug or I have to change the settings?

Thank you!

---

### Post by aljazek on 2011-04-02
Photo of a problem:
[[img]http://www.shrani.si/t/35/iC/1ewIez3T/02042011.jpg[/img]](http://www.shrani.si/?35/iC/1ewIez3T/02042011.jpg)

---

### Post by Krytarik on 2011-04-02
It seems to be an issue with the video driver, we may try to get a more proper driver for your video card/chip.

What video card/chip do you have?

Check with
```
lspci |grep VGA
```if you don't know.

What driver are you running?
How did you install those?

---

### Post by aljazek on 2011-04-02
I have ATI Mobility X1600
(01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600])

Drivers I use:
[[img]http://www.shrani.si/t/2d/BS/1uaF3puC/screenshot-5.jpg[/img]](http://www.shrani.si/?2d/BS/1uaF3puC/screenshot-5.png)

They were installed during ubuntu installation.

---

### Post by Krytarik on 2011-04-02
You may try upgrading the driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos, even in the case of Natty, as it turned out:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```And just in case, anybody is going to suggest installing/running the proprietary driver: Your video chip isn't covered by it anymore!

---

### Post by aljazek on 2011-04-02
I don't know what's wrong, this still doesn't help... Thanks anyway.

---

### Post by howefield on 2011-04-02
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by Krytarik on 2011-04-02
Check with
```
lshw -c video
```what driver is actually running.

Also, check the log files "/var/log/Xorg.0.log" and "~/.xsession-errors" for related error messages. You may post their contents here, in code-tags please, the #-button in the editor.

---

### Post by aljazek on 2011-04-02
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:c0000000-cfffffff ioport:b000(size=256) memory:fdff0000-fdffffff memory:fdfc0000-fdfdffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by dmillerw on 2011-04-02
Sorry to kinda butt in, but I had the same problem.

Did you happen to change the "Dash Blur" setting in the "Compiz Settings Manager"?

---

### Post by christoph411 on 2011-04-02
> **dmillerw said:**
> Sorry to kinda butt in, but I had the same problem.

Did you happen to change the "Dash Blur" setting in the "Compiz Settings Manager"?
Awww! You beat me to it! :lolflag:

---

### Post by aljazek on 2011-04-02
Yes, but still not better. I had "no blur" from the start.

---

### Post by Krytarik on 2011-04-02
Ok, I took a closer look on how the driver is actually called. In your case "radeon" is correct. "ati" is actually a 'wrapper' that loads the different appropriate drivers depending on the card/chip, I forgot about those details:
[http://packages.ubuntu.com/natty/xserver-xorg-video-ati](http://packages.ubuntu.com/natty/xserver-xorg-video-ati)

As for your still existing issue, how about the mentioned logs?

---

### Post by aljazek on 2011-04-03
This is written in Xorg.0.log file:

```
[    22.301] (II) LoadModule: "fglrx"
[    22.302] (WW) Warning, couldn't open module fglrx
[    22.302] (II) UnloadModule: "fglrx"
[    22.302] (II) Unloading fglrx
[    22.302] (EE) Failed to load module "fglrx" (module does not exist, 0)
```

There is no other (EE) error messages.

---

### Post by Krytarik on 2011-04-03
Check if any "fglrx" package is installed:
```
dpkg -l |grep fglrx
```
If anything turns up, purge them:
```
sudo apt-get purge fglrx*
```
How about "~/.xsession-errors"?

---

### Post by aljazek on 2011-04-03
I purged fglrx, but I don't have /.xsession-errors file on my computer.

---

### Post by rajeev1204 on 2011-04-03
This has nothing to do with the fglrx driver.I have this issue with the OSS driver also.


Ah read on other thread is due to static blur in compiz settings.Will try disabling it.

---

### Post by aljazek on 2011-04-03
Yeah, that didn't work for me.

---

### Post by Krytarik on 2011-04-03
> **aljazek said:**
> but I don't have /.xsession-errors file on my computer.
It's definitely there, it's a hidden file in your home directory.

---

### Post by aljazek on 2011-04-03
OK, found it:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-LNVZge
SSH_AUTH_SOCK=/tmp/keyring-LNVZge/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-LNVZge
GNOME_KEYRING_CONTROL=/tmp/keyring-LNVZge
SSH_AUTH_SOCK=/tmp/keyring-LNVZge/ssh
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
Initializing imgjpeg options...done
Initializing vpswitch options...done
Initializing gnomecompat options...done
Initializing move options...done
Initializing grid options...done
Initializing resize options...done
Initializing place options...done
Initializing imgsvg options...done
Initializing animation options...done
Initializing mousepoll options...done
Initializing workarounds options...done
Initializing unitymtgrabhandles options...done
Initializing expo options...done
I/O warning : failed to load external entity "/home/aljazek/.compiz/session/1012f3d86b86a1762f13018209599224600000012430037"
Initializing session options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
Starting Dropbox...Initializing nautilus-gdu extension
** (nm-applet:1319): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-dropbox 0.6.7

(nautilus:1313): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:1313): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (<unknown>:1308): DEBUG: Unity accessibility initialization

** (<unknown>:1308): WARNING **: Unable to load GDesktopAppInfo for 'gnome-terminal.desktop'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Screen geometry changed:
  Monitor 0(primary)
   0x0x1440x900

unity-panel-service: no process found

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Dropbox isn't running!
Done!
Initializing unityshell options...done
** (<unknown>:1308): DEBUG: PlaceEntry: Applications
** (<unknown>:1308): DEBUG: PlaceEntry: Commands
** (<unknown>:1308): DEBUG: PlaceEntry: Files & Folders
Starting unity-window-decorator

(<unknown>:1308): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:1308): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.

(<unknown>:1308): libindicator-WARNING **: Shortcut Group does not have key 'TargetEnvironment' falling back to deprecated use of 'OnlyShowIn' and 'NotShowIn'.
extents are 1 1 29 1 129
** (<unknown>:1308): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:1308): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
extents are 1 1 29 1 129
** (<unknown>:1308): DEBUG: Connected to proxy
** (<unknown>:1308): DEBUG: TrayChild Rejected: dropbox dropbox Dropbox

** (<unknown>:1308): WARNING **: Unable to load GDesktopAppInfo for 'gnome-terminal.desktop'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:1308): WARNING **: Unable to load GDesktopAppInfo for 'gnome-terminal.desktop'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:1308): DEBUG: Setting to primary screen rect: x=0 y=0 w=1440 h=900
** (<unknown>:1308): DEBUG: Connected to proxy
** (<unknown>:1308): DEBUG: Connected to proxy

(<unknown>:1308): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1308): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1308): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1308): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed
** (<unknown>:1308): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1308): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1308): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1308): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1308): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1308): DEBUG: IndicatorAdded: libsession.so

(<unknown>:1308): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1308): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
Setting Update "texture_filter"
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Exception in thread Fetcher:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 505, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/indicator-weather", line 1117, in get_new_weather_data
    weather = self.get_weather()
  File "/usr/bin/indicator-weather", line 1179, in get_weather
    self.current_location.update_weather_data(self.weather_source)
  File "/usr/bin/indicator-weather", line 308, in update_weather_data
    self.weather = Weather(self.location_details['google id'], source, self.metric_system, self.wind_unit, self.location_details['latitude'], self.location_details['longitude'])
  File "/usr/bin/indicator-weather", line 479, in __init__
    self.__report = pywapi.get_weather_from_google (location_id, hl = 'en')
  File "/usr/lib/pymodules/python2.7/pywapi.py", line 55, in get_weather_from_google
    handler = urllib2.urlopen(url)
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1185, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1160, in do_open
    raise URLError(err)
URLError: <urlopen error [Errno -2] Name or service not known>

** (nm-applet:1319): DEBUG: foo_client_state_changed_cb
** (nm-applet:1319): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1319): DEBUG: foo_client_state_changed_cb
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (gnome-screensaver:1611): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_application_handlers

** (gnome-screensaver:1611): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_command_line

** (gnome-screensaver:1611): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_printing

** (gnome-screensaver:1611): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_print_setup

** (gnome-screensaver:1611): WARNING **: Config key not handled: /desktop/gnome/lockdown/disable_save_to_disk

(evolution:1679): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:1679): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (<unknown>:1308): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1308): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1308): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1308): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1815): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(<unknown>:1308): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(firefox-bin:1815): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1815): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

(<unknown>:1308): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (<unknown>:1308): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

** (<unknown>:1308): WARNING **: Unable to load GDesktopAppInfo for 'gnome-terminal.desktop'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1313): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

** (<unknown>:1308): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1308): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1308): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1308): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1308): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1308): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1308): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1323): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/aljazek/.xsession-errors
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1308): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

** (<unknown>:1308): WARNING **: Unable to load GDesktopAppInfo for 'gnome-terminal.desktop'

(<unknown>:1308): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (process:1323): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1313): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```

---

### Post by Krytarik on 2011-04-03
Ok, there are a lot of Nautilus errors, I found a fresh bug report here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203)

Are you running the default/official version of Nautilus, or maybe Nautilus Elementary?

If you don't know, check its version:
```
dpkg -l |grep nautilus
```
current version of the default/official Nautilus: 2.32.2.1-0ubuntu11.1

those of Nautilus Elementary: 2.32.2.2-0ubuntu3~ppa170

---

### Post by aljazek on 2011-04-03
I am running current default version of nautilus 2.32.2.1-0ubuntu11.1

---

### Post by Krytarik on 2011-04-03
Usually, I wouldn't suggest this, because Nautilus Elementary apparently causes issues at number of systems, incl. mine, but since the official version also causes issues at your system, you may indeed try NE.

To 'upgrade' to it, run those commands:
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade

```[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa")

To 'downgrade' Nautilus to the official version again, run those:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```After either operation, restart Nautilus:
```
killall nautilus
```

---

### Post by aljazek on 2011-04-03
OK, thank you. I will wait a few days for possible updates before getting NE.

---

### Post by aljazek on 2011-04-03
I also found this problem on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033)

---

### Post by Krytarik on 2011-04-03
Ah, I see! I didn't mind searching for the terms regarding those issue. Fortunately, it is marked as "High", and even Mark Shuttleworth pays attention to it. So the chances are high that it will get really fixed in the near future.

But still, there seems also to be a bug in Nautilus, but you shouldn't replace it by NE anymore, as long as you don't notice a significant issue/misbehaviour with it.

---

### Post by aljazek on 2011-04-18
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033)

The source of my problem are probably drivers for older ATI GPUs and they are looking for solution.

---

### Post by Krytarik on 2011-04-18
> **aljazek said:**
> [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033)

The source of my problem are probably drivers for older ATI GPUs and they are looking for solution.
Ah, they have narrowed down the issue since. Thanks for making me/us aware of this!

---

### Post by aljazek on 2011-04-20
```
[Launchpad Janitor]("https://launchpad.net/%7Ejanitor") wrote 43 minutes ago:                                    [ #97]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/726033/comments/97")                                                        

This bug was fixed in the package nux - 0.9.46-0ubuntu2
 ---------------
nux (0.9.46-0ubuntu2) natty; urgency=low
   * Cherry-pick:
    - fix for "does not display icons until hovered" on old ATI hardware
      (LP: [#726033]("https://bugs.launchpad.net/bugs/726033"))
 -- Didier Roche <didrocks@ubuntu.com>   Wed, 20 Apr 2011 10:06:03 +0200

```Reply from @Launchpad Janitor on "my" bug. Can somebody with this problem confirm, I still use 10.10 or I will try tomorrow with 11.04 daily build.

---

### Post by aljazek on 2011-04-21
I confirm this bux fixed and I propose marking this thread [Solved]. Thank you!

---

### Post by Krytarik on 2011-04-21
Thanks for confirming.

You're welcome!

---

