---
title: "Loss Mediatomb when installing Upside-Down-Ternet"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by spursncowboys on 2009-09-01
Yesterday my mediatomb was running perfect. Then I read a story about how to install Upside-Down-Ternet (when people steal my wifi then their webpages for the most part are upside down). I used this how-to
[HTML]https://help.ubuntu.com/community/Upside-Down-TernetHowTo[/HTML]
Now mediatomb will not work. here is my mediatomb log

```
2009-08-28 11:26:15    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 11:26:15    INFO: UUID generated: e588824d-7fd2-4dfe-b87e-fe73b63cbefc
2009-08-28 11:26:15    INFO: Checking configuration...
2009-08-28 11:26:15    INFO: Setting filesystem import charset to UTF-8
2009-08-28 11:26:15    INFO: Setting metadata import charset to UTF-8
2009-08-28 11:26:15    INFO: Setting playlist charset to UTF-8
2009-08-28 11:26:15    INFO: Configuration check succeeded.
2009-08-28 11:26:15 WARNING: Sqlite3 database seems to be corrupt or doesn't exist yet.
2009-08-28 11:26:15    INFO: no sqlite3 backup is available or backup is corrupt. automatically creating database...
2009-08-28 11:26:15    INFO: database created successfully.
2009-08-28 11:26:15    INFO: Initialized port: 49152
2009-08-28 11:26:15    INFO: Server bound to: 192.168.1.101
2009-08-28 11:26:16    INFO: MediaTomb Web UI can be reached by following this link:
2009-08-28 11:26:16    INFO: http://192.168.1.101:49152/
2009-08-28 12:08:39    INFO: MediaTomb shutting down. Please wait...
2009-08-28 12:08:40    INFO: Server terminating
2009-08-28 12:09:47    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 12:09:47    INFO: Checking configuration...
2009-08-28 12:09:48    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-08-28 12:09:48    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-08-28 12:09:48    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-08-28 12:09:48    INFO: Configuration check succeeded.
2009-08-28 12:09:48   ERROR: main: upnp error -117
2009-08-28 12:09:48   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
2009-08-28 12:12:30    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 12:12:30    INFO: Checking configuration...
2009-08-28 12:12:30    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-08-28 12:12:30    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-08-28 12:12:30    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-08-28 12:12:30    INFO: Configuration check succeeded.
2009-08-28 12:12:31   ERROR: main: upnp error -117
2009-08-28 12:12:31   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
2009-08-28 12:14:43    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 12:14:43    INFO: Checking configuration...
2009-08-28 12:14:43    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-08-28 12:14:43    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-08-28 12:14:43    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-08-28 12:14:43    INFO: Configuration check succeeded.
2009-08-28 12:14:43   ERROR: main: upnp error -117
2009-08-28 12:14:43   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
2009-08-28 12:16:44    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 12:16:44    INFO: Checking configuration...
2009-08-28 12:16:44    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-08-28 12:16:44    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-08-28 12:16:44    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-08-28 12:16:44    INFO: Configuration check succeeded.
2009-08-28 12:16:44   ERROR: main: upnp error -117
2009-08-28 12:16:44   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
2009-08-28 12:23:08    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 12:23:08    INFO: Checking configuration...
2009-08-28 12:23:08    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-08-28 12:23:08    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-08-28 12:23:08    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-08-28 12:23:08    INFO: Configuration check succeeded.
2009-08-28 12:23:08   ERROR: main: upnp error -117
2009-08-28 12:23:08   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
2009-08-28 14:34:20    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-08-28 14:34:20    INFO: Checking configuration...
2009-08-28 14:34:20    INFO: Setting filesystem import charset to UTF-8
2009-08-28 14:34:20    INFO: Setting metadata import charset to UTF-8
2009-08-28 14:34:20    INFO: Setting playlist charset to UTF-8
2009-08-28 14:34:20    INFO: Configuration check succeeded.
2009-08-28 14:34:20    INFO: Initialized port: 49153
2009-08-28 14:34:20    INFO: Server bound to: 192.168.1.101
2009-08-28 14:34:21    INFO: MediaTomb Web UI can be reached by following this link:
2009-08-28 14:34:21    INFO: http://192.168.1.101:49153/
2009-08-28 17:43:30    INFO: MediaTomb shutting down. Please wait...
2009-08-28 17:43:31    INFO: Server terminating
```

---

