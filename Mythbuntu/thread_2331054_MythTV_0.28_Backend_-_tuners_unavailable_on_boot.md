---
title: "MythTV 0.28 Backend - tuners unavailable on boot"
date: 2016-07-17
forum: Mythbuntu
---

### Post by sylvester3 on 2016-07-17
After finding out the newest kernel supports my DVB capture card out of the box I decided to upgrade to the latest MythBuntu 16.04 LTS / MythTV 0.28

I'll try to keep this brief, will post more details if needed.

Previously running was 14.04 LTS / 0.27 without major problems. I've run a dist-upgrade and haven't changed any settings apart from reconfigure capture card(s) in the backend configuration.

The problem is on boot I have the message "all tuners are busy" when trying to watch live tv, and under System Status it shows "Tuner X has an error" for each device.

Issuing "sudo service mythtv-backend restart" fixes the problem until the next reboot.

From mythbackend.log:

```
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_AU.UTF-8
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of mythtv-1
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jul 17 16:20:50 mythtv-1 mythbackend: mythbackend[865]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:11): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jul 17 16:20:51 mythtv-1 mythbackend: mythbackend[1188]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-43-g04650e0] www.mythtv.org

```

netstat -a | grep LISTEN shows MySQL listening on localhost:

```
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 localhost:5100          *:*                     LISTEN
tcp        0      0 localhost:6543          *:*                     LISTEN
tcp        0      0 localhost:6544          *:*                     LISTEN
tcp        0      0 localhost:6547          *:*                     LISTEN
tcp        0      0 localhost:6549          *:*                     LISTEN
tcp        0      0 mythtv-1:domain         *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost:6554          *:*                     LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:5100 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:5100      [::]:*                  LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:6543 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:6543      [::]:*                  LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:6544 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:6544      [::]:*                  LISTEN
tcp6       0      0 [::]:http               [::]:*                  LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:6547 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:6547      [::]:*                  LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:6549 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:6549      [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 fe80::e8b:fdff:fee:6554 [::]:*                  LISTEN
tcp6       0      0 ip6-localhost:6554      [::]:*                  LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     19628    @/tmp/.ICE-unix/1104
unix  2      [ ACC ]     STREAM     LISTENING     18837    /run/user/1000/systemd/private
unix  2      [ ACC ]     SEQPACKET  LISTENING     2039     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     19632    /run/user/1000/keyring/control
unix  2      [ ACC ]     STREAM     LISTENING     19633    /run/user/1000/keyring/ssh
unix  2      [ ACC ]     STREAM     LISTENING     19638    /run/user/1000/keyring/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     19306    /run/user/1000/pulse/native
unix  2      [ ACC ]     STREAM     LISTENING     12843    /sys/fs/cgroup/cgmanager/sock
unix  2      [ ACC ]     STREAM     LISTENING     18351    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     17744    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     20217    @/tmp/dbus-CwI2kMrRys
unix  2      [ ACC ]     STREAM     LISTENING     19629    /tmp/.ICE-unix/1104
unix  2      [ ACC ]     STREAM     LISTENING     2035     /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     2046     /run/systemd/journal/stdout
unix  2      [ ACC ]     STREAM     LISTENING     9616     /run/systemd/fsck.progress
unix  2      [ ACC ]     STREAM     LISTENING     21685    /var/run/NetworkManager/private-dhcp
unix  2      [ ACC ]     STREAM     LISTENING     18381    /tmp/ssh-a6IQdk8v0Xob/agent.1034
unix  2      [ ACC ]     STREAM     LISTENING     12829    /run/uuidd/request
unix  2      [ ACC ]     STREAM     LISTENING     12830    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12831    /run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     18397    @/tmp/dbus-OeayU3jecX
unix  2      [ ACC ]     STREAM     LISTENING     12832    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     17745    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18128    /run/lirc/lircd

```

Edit: I first though the problem was mysql not being ready at boot when the backend first tries to connect to it, but now I'm not sure.

I've uploaded fresh logs of the system right after boot:
[http://www.aupcgroup.com/mythbackend.log](http://www.aupcgroup.com/mythbackend.log)
[http://www.aupcgroup.com/mythfrontend.log](http://www.aupcgroup.com/mythfrontend.log)
[http://www.aupcgroup.com/mythshutdown.log](http://www.aupcgroup.com/mythshutdown.log)
[http://www.aupcgroup.com/mythwelcome.log](http://www.aupcgroup.com/mythwelcome.log)

Also from the same session, after restarting the backend:
[http://www.aupcgroup.com/mythbackend2.log](http://www.aupcgroup.com/mythbackend2.log)
[http://www.aupcgroup.com/mythfrontend2.log](http://www.aupcgroup.com/mythfrontend2.log)

Can someone suggest where the problem might be?

Thanks,

---

### Post by sylvester3 on 2016-07-20
Turns out it was nothing to do with mySQL. Mythbackend needs to wait for TV capture cards to be initialised before starting up.

The issue was MythBuntu init switching over from upstart to systemd, and my existing scripts were no longer being called.

This guide has the correct setup: [https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration#Delay_starting_the_backend_until_tuners_have_initialized](https://www.mythtv.org/wiki/Systemd_mythbackend_Configuration#Delay_starting_the_backend_until_tuners_have_initialized)

---

