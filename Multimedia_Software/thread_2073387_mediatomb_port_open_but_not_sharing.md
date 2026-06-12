---
title: "mediatomb port open but not sharing"
date: 2012-10-19
forum: Multimedia Software
---

### Post by 65 mustang on 2012-10-19
Mediatomb had been working but had stoped one day after an update or a reboot.  I portscanned myself "localhost" and saw the port was open.  Then i looked at the log file while i restarted.

```
me@computer:/var/log$ tail -f mediatomb.log
                             to watch YouTube videos on your UPnP device!
                             Please check http://www.youtube.com/t/terms
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2012-10-19 11:56:56    INFO: Configuration check succeeded.
2012-10-19 11:56:56    INFO: Initialized port: 49152
2012-10-19 11:56:56    INFO: Server bound to: 192.168.122.1
2012-10-19 11:56:57    INFO: MediaTomb Web UI can be reached by following this link:
2012-10-19 11:56:57    INFO: http://192.168.122.1:49152/

```
```
sudo service mediatomb restart
```

Saw it was binding to a nic that i was not using.
Forced the interface to eth0 in /etc/mediatomb/config.xml
```

<server>
    <interface>eth0</interface>

```

```

2012-10-19 12:02:01    INFO: MediaTomb shutting down. Please wait...
2012-10-19 12:02:02    INFO: Server terminating
2012-10-19 12:02:03    INFO: Loading configuration from: /etc/mediatomb/config.xml
2012-10-19 12:02:03    INFO: Checking configuration...
2012-10-19 12:02:03    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2012-10-19 12:02:03    INFO: Setting metadata import charset to ANSI_X3.4-1968
2012-10-19 12:02:03    INFO: Setting playlist charset to ANSI_X3.4-1968
2012-10-19 12:02:03 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check http://www.youtube.com/t/terms
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2012-10-19 12:02:03    INFO: Configuration check succeeded.
2012-10-19 12:02:03    INFO: Initialized port: 49152
2012-10-19 12:02:03    INFO: Server bound to: 10.0.50.129
2012-10-19 12:02:04    INFO: MediaTomb Web UI can be reached by following this link:
2012-10-19 12:02:04    INFO: http://10.0.50.129:49152/
```

Much better!  My network is on the 10.0.50.0/24 subnet.  Everything works!

I did follow the guide on itinital setup that tells you to uncomment things in the config.xml also to get it to work with the PS3.:)

---

