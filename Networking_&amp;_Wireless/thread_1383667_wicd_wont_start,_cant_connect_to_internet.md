---
title: "wicd wont start, cant connect to internet"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Defiant Rat on 2010-01-17
Hi guys, hope someone can help me because I'm all out of ideas :(

So, i start up my computer and wicd dosnt start. Its was working fine, and i was watching tv on the internet, then my dad turned off the power (fitting a light or something). When the power was back on, i started it up (expecting everything to be fine) but wicd hadnt started.

When i run:
```
wicd-client -n
```
I get:
```
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/share/wicd/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/share/wicd/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service file
```

Any ideas how to get it working again? I would be willing to switch back to network manager if it got me back on the internet, but am not sure how to install it without internet access. Can i install it from the Live CD?

Thanks.

---

### Post by raffaele181188 on 2010-01-17
Did you starti wicd daemon? Try
```

ps aux | grep wicd

```

---

### Post by Defiant Rat on 2010-01-18
> **raffaele181188 said:**
> Did you starti wicd daemon? Try
```

ps aux | grep wicd

```

Tried that, and got;
```
dave      4371  0.0  0.0   7340   900 pts/1    S+   13:00   0:00 grep --color=auto [COLOR="Red"]wicd[/COLOR]
```
Then tried wicd-client -n again and got the same response as before :(

---

### Post by raffaele181188 on 2010-01-18
You should start da daemon before... On Slackware it's /etc/rc.d/rc.wicd start, on Ubuntu you should try
```

sudo /etc/init.d/wicd start

```

---

### Post by Defiant Rat on 2010-01-18
> **raffaele181188 said:**
> You should start da daemon before... On Slackware it's /etc/rc.d/rc.wicd start, on Ubuntu you should try
```

sudo /etc/init.d/wicd start

```
Tried that, with the response;
```
 * Starting Network Connection manager wicd
```
Which looked hopeful, but wicd-client still gives the same response, and i still cant connect to the internet :???:

---

### Post by raffaele181188 on 2010-01-18
If the daemon is running the error message cannot be the same.. Please try again launching wicd-client and post error message. Usually the error in this phase is that your user is not in the "netdev" group. Check it and post your log :)

---

### Post by Defiant Rat on 2010-01-18
> **raffaele181188 said:**
> If the daemon is running the error message cannot be the same.. Please try again launching wicd-client and post error message. Usually the error in this phase is that your user is not in the "netdev" group. Check it and post your log :)
The error message:
```
dave@dave-desktop:~$ sudo /etc/init.d/wicd start
 * Starting Network connection manager wicd                              [ OK ] 
dave@dave-desktop:~$ wicd-client -n
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/share/wicd/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/share/wicd/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files
dave@dave-desktop:~$ 

```
wicd.log :
```
2010/01/18 17:13:57 :: ---------------------------
2010/01/18 17:13:57 :: wicd initializing...
2010/01/18 17:13:57 :: ---------------------------
2010/01/18 17:13:57 :: Automatically detected wireless interface ra0
2010/01/18 17:13:57 :: found wireless_interface in configuration ra0
2010/01/18 17:13:57 :: setting wireless interface ra0
2010/01/18 17:13:57 :: automatically detected wired interface eth0
2010/01/18 17:13:57 :: found wired_interface in configuration eth0
2010/01/18 17:13:57 :: setting wired interface eth0
2010/01/18 17:13:57 :: found wpa_driver in configuration wext
2010/01/18 17:13:57 :: setting wpa driver wext
2010/01/18 17:13:57 :: found always_show_wired_interface in configuration False
2010/01/18 17:13:57 :: found use_global_dns in configuration False
2010/01/18 17:13:57 :: setting use global dns to False
2010/01/18 17:13:57 :: setting use global dns to boolean False
2010/01/18 17:13:57 :: found global_dns_1 in configuration None
2010/01/18 17:13:57 :: found global_dns_2 in configuration None
2010/01/18 17:13:57 :: found global_dns_3 in configuration None
2010/01/18 17:13:57 :: setting global dns
2010/01/18 17:13:57 :: global dns servers are None None None
2010/01/18 17:13:57 :: found auto_reconnect in configuration True
2010/01/18 17:13:57 :: setting automatically reconnect when connection drops
2010/01/18 17:13:57 :: found debug_mode in configuration False
2010/01/18 17:13:57 :: found wired_connect_mode in configuration 1
2010/01/18 17:13:57 :: found signal_display_type in configuration 0
2010/01/18 17:13:57 :: found dhcp_client in configuration 0
2010/01/18 17:13:57 :: Setting dhcp client to 0
2010/01/18 17:13:57 :: found link_detect_tool in configuration 0
2010/01/18 17:13:57 :: found flush_tool in configuration 0
2010/01/18 17:13:57 :: Wireless configuration file found...
2010/01/18 17:13:57 :: Wired configuration file found...
2010/01/18 17:13:57 :: chmoding configuration files 0600...
2010/01/18 17:13:57 :: chowning configuration files root:root...
2010/01/18 17:13:57 :: Using wired interface...eth0
2010/01/18 17:13:57 :: Using wireless interface...ra0
2010/01/18 17:13:57 :: autoconnecting... ra0
2010/01/18 17:13:58 :: Traceback (most recent call last):
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 1660, in <module>
2010/01/18 17:13:58 ::     main(sys.argv)
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 1631, in main
2010/01/18 17:13:58 ::     obj = ConnectionWizard(d_bus_name, auto_connect=auto_connect)
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 191, in __init__
2010/01/18 17:13:58 ::     self.AutoConnect(True)
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 382, in AutoConnect
2010/01/18 17:13:58 ::     self._wired_autoconnect()
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 395, in _wired_autoconnect
2010/01/18 17:13:58 ::     network = self.GetDefaultWiredNetwork()
2010/01/18 17:13:58 ::   File "/usr/share/wicd/wicd-daemon.py", line 1074, in GetDefaultWiredNetwork
2010/01/18 17:13:58 ::     config.read(self.wired_conf)
2010/01/18 17:13:58 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/01/18 17:13:58 ::     self._read(fp, filename)
2010/01/18 17:13:58 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/01/18 17:13:58 ::     raise e
2010/01/18 17:13:58 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/01/18 17:13:58 :: 	[line  4]: '[]\n'
```

---

### Post by raffaele181188 on 2010-01-18
There are parsing errors in /etc/wicd/wired-settings.conf
Try remove that file and restart the daemon (it could be auto recreated). If it fails, try reinstall wicd

---

