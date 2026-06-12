---
title: "knetworkmanager can't connect eth0 (wired connection)"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by neymac on 2009-04-25
Kubuntu 9.04 fresh installation (KDE4.2.2).
Networkmanager shows no network connections (I have just one eth0 wired).
My internet connection is pppoe. As I coudn't configure it by NetWorkManager plasma (it showed ADSL tab but didn't let me select it), I did pppoeconf to setup my internet conection.
It worked with pon dsl-provider and poff dsl-provider.
But everytime I boot the computer did not accept pon dsl-provider unless I killall pppd before do it.
I wrote a script to kill pppd and call dsl-provider, but only works if I run it manually after the boot.
My syslog is:
> Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  starting... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the supplicant... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the system settings daemon... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Found user 'avahi' (UID 107) and group 'avahi' (GID 114).
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped root privileges.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: avahi-daemon 0.6.23 starting up.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully called chroot().
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped remaining capabilities.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: No service file found in /etc/avahi/services.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Network interface enumeration completed.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering new address record for fe80::213:d4ff:fe78:738b on eth0.*.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Server startup complete. Host name is YouKnowMe.local. Local service cookie is 2426806579.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 25 18:38:16 YouKnowMe acpid: client connected from 2829[0:0] 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: init!
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_system_hostnameAvahi
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (dsl-provider) = ppp
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:dsl-provider, type:ppp, autoconnect:0, id:Ifupdown (dsl-provider), uuid: 7f0642ca-0000-0000-0000-000039000000
Apr 25 18:38:17 YouKnowMe nm-system-settings: <WARN>  ifupdown_update_connection_from_if_block(): connection broken: type (3) 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugiApr 25 18:38:16 YouKnowMe NetworkManager: <info>  starting... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the supplicant... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the system settings daemon... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Found user 'avahi' (UID 107) and group 'avahi' (GID 114).
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped root privileges.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: avahi-daemon 0.6.23 starting up.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully called chroot().
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped remaining capabilities.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: No service file found in /etc/avahi/services.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Network interface enumeration completed.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering new address record for fe80::213:d4ff:fe78:738b on eth0.*.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Server startup complete. Host name is YouKnowMe.local. Local service cookie is 2426806579.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 25 18:38:16 YouKnowMe acpid: client connected from 2829[0:0] 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: init!
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_system_hostnameAvahi
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (dsl-provider) = ppp
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:dsl-provider, type:ppp, autoconnect:0, id:Ifupdown (dsl-provider), uuid: 7f0642ca-0000-0000-0000-000039000000
Apr 25 18:38:17 YouKnowMe nm-system-settings: <WARN>  ifupdown_update_connection_from_if_block(): connection broken: type (3) 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000011000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (eth1000) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth1000, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth1000Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  starting... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (ttyS1): ignoring due to lack of mobile broadband capabilties 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the supplicant... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  Trying to start the system settings daemon... 
Apr 25 18:38:16 YouKnowMe NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Found user 'avahi' (UID 107) and group 'avahi' (GID 114).
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped root privileges.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: avahi-daemon 0.6.23 starting up.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully called chroot().
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Successfully dropped remaining capabilities.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: No service file found in /etc/avahi/services.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Network interface enumeration completed.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering new address record for fe80::213:d4ff:fe78:738b on eth0.*.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Server startup complete. Host name is YouKnowMe.local. Local service cookie is 2426806579.
Apr 25 18:38:16 YouKnowMe avahi-daemon[2854]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 25 18:38:16 YouKnowMe acpid: client connected from 2829[0:0] 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: init!
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_system_hostnameAvahi
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (dsl-provider) = ppp
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:dsl-provider, type:ppp, autoconnect:0, id:Ifupdown (dsl-provider), uuid: 7f0642ca-0000-0000-0000-000039000000
Apr 25 18:38:17 YouKnowMe nm-system-settings: <WARN>  ifupdown_update_connection_from_if_block(): connection broken: type (3) 
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000011000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (eth1000) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth1000, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth1000), uuid: 12ca32c9-0000-0000-0000-000000000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe kernel: [   17.561633] ppdev: user-space parallel port driver
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b, iface: eth0): well known
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections (managed=false): return empty list.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: end _init.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe NetworkManager: <info>  (eth0): now unmanaged 
Apr 25 18:38:17 YouKnowMe anacron[2950]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:17 YouKnowMe anacron[2950]: Normal exit (0 jobs run)
Apr 25 18:38:17 YouKnowMe kernel: [   18.373677] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Apr 25 18:38:17 YouKnowMe kernel: [   18.373698] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:17 YouKnowMe kernel: [   18.373744] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2993]: (CRON) INFO (pidfile fd = 3)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) STARTUP (fork ok)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) INFO (Running @reboot jobs)
Apr 25 18:38:18 YouKnowMe ntpdate[2912]: adjust time server 91.189.94.4 offset -0.001088 sec
Apr 25 18:38:19 YouKnowMe console-kit-daemon[2597]: WARNING: Couldn't read /proc/2596/environ: Failed to open file '/proc/2596/environ': No such file or directory 
Apr 25 18:38:22 YouKnowMe kernel: [   23.068009] eth0: no IPv6 routers present
Apr 25 18:38:26 YouKnowMe anacron[3235]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:26 YouKnowMe anacron[3235]: Normal exit (0 jobs run)
Apr 25 18:38:32 YouKnowMe NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 25 18:38:32 YouKnowMe last message repeated 2 times
Apr 25 18:38:32 YouKnowMe NetworkManager: <WARN>  list_connections_cb(): Couldn't retrieve connections: No such method 'ListConnections' in interface 'org.freedesktop.NetworkManagerSettings' at object path '/org/freedesktop/NetworkManagerSettings' (signature ''). ), uuid: 12ca32c9-0000-0000-0000-000000000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe kernel: [   17.561633] ppdev: user-space parallel port driver
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b, iface: eth0): well known
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections (managed=false): return empty list.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: end _init.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe NetworkManager: <info>  (eth0): now unmanaged 
Apr 25 18:38:17 YouKnowMe anacron[2950]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:17 YouKnowMe anacron[2950]: Normal exit (0 jobs run)
Apr 25 18:38:17 YouKnowMe kernel: [   18.373677] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Apr 25 18:38:17 YouKnowMe kernel: [   18.373698] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:17 YouKnowMe kernel: [   18.373744] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2993]: (CRON) INFO (pidfile fd = 3)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) STARTUP (fork ok)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) INFO (Running @reboot jobs)
Apr 25 18:38:18 YouKnowMe ntpdate[2912]: adjust time server 91.189.94.4 offset -0.001088 sec
Apr 25 18:38:19 YouKnowMe console-kit-daemon[2597]: WARNING: Couldn't read /proc/2596/environ: Failed to open file '/proc/2596/environ': No such file or directory 
Apr 25 18:38:22 YouKnowMe kernel: [   23.068009] eth0: no IPv6 routers present
Apr 25 18:38:26 YouKnowMe anacron[3235]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:26 YouKnowMe anacron[3235]: Normal exit (0 jobs run)
Apr 25 18:38:32 YouKnowMe NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 25 18:38:32 YouKnowMe last message repeated 2 times
Apr 25 18:38:32 YouKnowMe NetworkManager: <WARN>  list_connections_cb(): Couldn't retrieve connections: No such method 'ListConnections' in interface 'org.freedesktop.NetworkManagerSettings' at object path '/org/freedesktop/NetworkManagerSettings' (signature ''). nIfupdown: guessed connection type (eth0) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000011000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: guessed connection type (eth1000) = 802-3-ethernet
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth1000, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth1000), uuid: 12ca32c9-0000-0000-0000-000000000000
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Apr 25 18:38:17 YouKnowMe kernel: [   17.561633] ppdev: user-space parallel port driver
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_d4_78_73_8b, iface: eth0): well known
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: (149235456) ... get_connections (managed=false): return empty list.
Apr 25 18:38:17 YouKnowMe nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Apr 25 18:38:17 YouKnowMe nm-system-settings:    SCPlugin-Ifupdown: end _init.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 25 18:38:17 YouKnowMe NetworkManager: <info>  (eth0): now unmanaged 
Apr 25 18:38:17 YouKnowMe anacron[2950]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:17 YouKnowMe anacron[2950]: Normal exit (0 jobs run)
Apr 25 18:38:17 YouKnowMe kernel: [   18.373677] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Apr 25 18:38:17 YouKnowMe kernel: [   18.373698] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:17 YouKnowMe kernel: [   18.373744] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2993]: (CRON) INFO (pidfile fd = 3)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) STARTUP (fork ok)
Apr 25 18:38:18 YouKnowMe /usr/sbin/cron[2994]: (CRON) INFO (Running @reboot jobs)
Apr 25 18:38:18 YouKnowMe ntpdate[2912]: adjust time server 91.189.94.4 offset -0.001088 sec
Apr 25 18:38:19 YouKnowMe console-kit-daemon[2597]: WARNING: Couldn't read /proc/2596/environ: Failed to open file '/proc/2596/environ': No such file or directory 
Apr 25 18:38:22 YouKnowMe kernel: [   23.068009] eth0: no IPv6 routers present
Apr 25 18:38:26 YouKnowMe anacron[3235]: Anacron 2.3 started on 2009-04-25
Apr 25 18:38:26 YouKnowMe anacron[3235]: Normal exit (0 jobs run)
Apr 25 18:38:32 YouKnowMe NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 25 18:38:32 YouKnowMe last message repeated 2 times
Apr 25 18:38:32 YouKnowMe NetworkManager: <WARN>  list_connections_cb(): Couldn't retrieve connections: No such method 'ListConnections' in interface 'org.freedesktop.NetworkManagerSettings' at object path '/org/freedesktop/NetworkManagerSettings' (signature ''). 

The above is the exact transcription of part of my syslog related to NetworkManager issues.
Note that for the first time I see syslog telling me about a bug URL site (although my problem is not related with Firefox, I use Konqueror).

My /etc/network/interfaces:
> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
I need help, please.

---

### Post by neymac on 2009-04-26
[SOLVED]
Solved after add the DNS IPs to file /etc/resolv.conf, although NetworkManager is still not working but I got pppoe connection with internet at startup.

---

