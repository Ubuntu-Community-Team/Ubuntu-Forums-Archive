---
title: "Remote gnome-session"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by crush_157 on 2011-08-02
Hi,

I want to be able to log into a machine running ubuntu and create a new desktop session (i.e. gnome session).

I don't want to have to leave a desktop session running, so VNC isn't the answer.

I can use ssh -X and run individual graphical apps (e.g. gbrainy), but if I try to start a gnome session, I get a screen full of errors (see end of post).

I've googled around extensively and it seems that this should be possible, for example... 

[http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/](http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/)

[http://www.technovelty.org/linux/tips/xnest.html](http://www.technovelty.org/linux/tips/xnest.html)

...but I get a similar set of errors each time.

If anyone could explain what's going wrong and suggest or point me to how to make it go right that would be great.

Cheers,

Crush_157

<screen-full-of-errors>

gemma@gemma-VirtualBox:~$ ssh -X [email]lucinda@lucinda-virtualbox.local[/email]
[email]lucinda@lucinda-virtualbox.local[/email]'s password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-10-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Mon Aug  1 21:54:56 2011 from 192.168.1.9
[COLOR="Red"]lucinda@lucinda-VirtualBox:~$ gnome-session[/COLOR]
GNOME_KEYRING_CONTROL=/tmp/keyring-5nIrwM
GNOME_KEYRING_PID=3011
GNOME_KEYRING_CONTROL=/tmp/keyring-5nIrwM
GNOME_KEYRING_CONTROL=/tmp/keyring-5nIrwM
SSH_AUTH_SOCK=/tmp/keyring-5nIrwM/ssh

** (gnome-settings-daemon:3016): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:3016): WARNING **: Failed to connect context: Connection refused
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.

** (gnome-settings-daemon:3016): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:3016): WARNING **: Clipboard manager is already running.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.

** (bluetooth-applet:3039): WARNING **: Could not open RFKILL control device, please verify your installation
Failed to play sound: Not available
Initializing nautilus-gdu extension
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.

** (nm-applet:3042): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service.
  Error: (9) Connection ":1.62" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file


(nautilus:3030): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.

** (gnome-settings-daemon:3016): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:3016): WARNING **: Failed to connect context: Connection refused
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.

** (gnome-screensaver:3157): WARNING **: screensaver already running in this session
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
^CGConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
gnome-session[2993]: WARNING: Detected that screensaver has left the bus
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.gtk.Private.RemoteVolumeMonitor',sender='org.gtk.Private.GPhoto2VolumeMonitor',': org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.freedesktop.DBus',member='NameOwnerChanged',arg0='org.gtk.Private.GPhoto2VolumeMonitor'': org.freedesktop.DBus.Error.Disconnected: Connection is closed

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.gtk.Private.RemoteVolumeMonitor',sender='org.gtk.Private.AfcVolumeMonitor',': org.freedesktop.DBus.Error.Disconnected: Connection is closed

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.freedesktop.DBus',member='NameOwnerChanged',arg0='org.gtk.Private.AfcVolumeMonitor'': org.freedesktop.DBus.Error.Disconnected: Connection is closed

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.gtk.Private.RemoteVolumeMonitor',sender='org.gtk.Private.GduVolumeMonitor',': org.freedesktop.DBus.Error.Disconnected: Connection is closed

(gnome-settings-daemon:3016): GVFS-RemoteVolumeMonitor-WARNING **: cannot remove match rule 'type='signal',interface='org.freedesktop.DBus',member='NameOwnerChanged',arg0='org.gtk.Private.GduVolumeMonitor'': org.freedesktop.DBus.Error.Disconnected: Connection is closed
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
gnome-session[2993]: WARNING: Client '/org/gnome/SessionManager/Client86' failed to reply before timeout
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[2993]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: WARNING: Client '/org/gnome/SessionManager/Client6' failed to reply before timeout
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: WARNING: Client '/org/gnome/SessionManager/Client5' failed to reply before timeout
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[2993]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: WARNING: Client '(null)' failed to reply before timeout
gnome-session[2993]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed
gnome-session[2993]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-wAjo0zvt8J: Connection refused
gnome-session[2993]: WARNING: Unable to register inhibitor with session bus
gnome-session[2993]: WARNING: Error retrieving configuration key '/apps/gnome-session/options/auto_save_session': Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
system-config-printer-applet: failed to connect to session D-Bus
gnome-session[2993]: WARNING: Error retrieving configuration key '/apps/gnome-session/options/auto_save_session': Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Error connecting: Connection refused)
lucinda@lucinda-VirtualBox:~$ 


</screen-full-of-errors>

---

