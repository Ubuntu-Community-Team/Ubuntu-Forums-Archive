---
title: "Intermittent wireless on startup"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by michael81 on 2009-06-19
Hello,

I installed Jaunty a few weeks ago and I've been having intermittent problems with the wireless connection.  Sometimes (at random) when I startup the wlan0 interface isn't available at all. And I have no way of enabling it. I checked lsmod and I can see the iwl3945 module hasn't been loaded. Also the following modules are missing which are normally loaded automatically:

arc4
cfg80211
ecb
iwl3945
led_class
mac80211

Even if I load all of these manually, and restart NetworkManager it still doesn't work. I've also tried switching the wireless switch off and on and it doesn't make any difference. I have to restart the computer (usually several times) until wlan0 is started automatically.

I've checked all of the log files and I can't find any errors. I've included an extract of the syslog from a successul boot with wireless and a boot with no wireless:

wiress:
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  starting... 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/iwl_wlan_switch 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2') 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_a9_a5_90_6a 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_19_d2_82_51_94 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 19 20:40:51 michael-laptop NetworkManager: <WARN>  killswitch_getpower_reply(): Error getting killswitch power: Method "GetPower" with signature "" on interface "org.freedesktop.Hal.Device.KillSwitch" doesn't exist . 
Jun 19 20:40:51 michael-laptop avahi-daemon[4098]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jun 19 20:40:51 michael-laptop avahi-daemon[4098]: Successfully dropped root privileges.
Jun 19 20:40:51 michael-laptop avahi-daemon[4098]: avahi-daemon 0.6.23 starting up.
Jun 19 20:40:51 michael-laptop avahi-daemon[4098]: Successfully called chroot().
Jun 19 20:40:51 michael-laptop avahi-daemon[4098]: Successfully dropped remaining capabilities.
Jun 19 20:40:51 michael-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_a9_a5_90_6a, iface: eth0): not well known
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_19_d2_82_51_94, iface: wlan0): not well known
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 19 20:40:52 michael-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 19 20:40:52 michael-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: (145544504) ... get_connections.
Jun 19 20:40:52 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: (145544504) ... get_connections (managed=false): return empty list.
Jun 19 20:40:52 michael-laptop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun 19 20:40:52 michael-laptop avahi-daemon[4098]: No service file found in /etc/avahi/services.
Jun 19 20:40:52 michael-laptop avahi-daemon[4098]: Network interface enumeration completed.
Jun 19 20:40:52 michael-laptop avahi-daemon[4098]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 19 20:40:52 michael-laptop avahi-daemon[4098]: Server startup complete. Host name is michael-laptop.local. Local service cookie is 1579739002.
Jun 19 20:40:52 michael-laptop kernel: [  124.750278] ppdev: user-space parallel port driver
Jun 19 20:40:53 michael-laptop anacron[4213]: Anacron 2.3 started on 2009-06-19
Jun 19 20:40:53 michael-laptop anacron[4213]: Normal exit (0 jobs run)
Jun 19 20:40:53 michael-laptop /usr/sbin/cron[4256]: (CRON) INFO (pidfile fd = 3)
Jun 19 20:40:53 michael-laptop /usr/sbin/cron[4257]: (CRON) STARTUP (fork ok)
Jun 19 20:40:54 michael-laptop /usr/sbin/cron[4257]: (CRON) INFO (Running @reboot jobs)
Jun 19 20:40:55 michael-laptop acpid: client connected from 4053[0:0] 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (eth0): preparing device. 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Jun 19 20:40:56 michael-laptop NetworkManager: <info>  (wlan0): bringing up device. 
.....

No wireless:
Jun 19 21:59:28 michael-laptop NetworkManager: <info>  starting... 
Jun 19 21:59:28 michael-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2') 
Jun 19 21:59:28 michael-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_a9_a5_90_6a 
Jun 19 21:59:28 michael-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jun 19 21:59:28 michael-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_a9_a5_90_6a, iface: eth0): not well known
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 19 21:59:28 michael-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 19 21:59:28 michael-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: (165795072) ... get_connections.
Jun 19 21:59:28 michael-laptop nm-system-settings:    SCPlugin-Ifupdown: (165795072) ... get_connections (managed=false): return empty list.
Jun 19 21:59:28 michael-laptop avahi-daemon[2972]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jun 19 21:59:28 michael-laptop avahi-daemon[2972]: Successfully dropped root privileges.
Jun 19 21:59:28 michael-laptop avahi-daemon[2972]: avahi-daemon 0.6.23 starting up.
Jun 19 21:59:28 michael-laptop avahi-daemon[2972]: Successfully called chroot().
Jun 19 21:59:28 michael-laptop avahi-daemon[2972]: Successfully dropped remaining capabilities.
Jun 19 21:59:28 michael-laptop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun 19 21:59:29 michael-laptop avahi-daemon[2972]: No service file found in /etc/avahi/services.
Jun 19 21:59:29 michael-laptop avahi-daemon[2972]: Network interface enumeration completed.
Jun 19 21:59:29 michael-laptop avahi-daemon[2972]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 19 21:59:29 michael-laptop avahi-daemon[2972]: Server startup complete. Host name is michael-laptop.local. Local service cookie is 4057898644.
Jun 19 21:59:29 michael-laptop kernel: [   22.271266] ppdev: user-space parallel port driver
Jun 19 21:59:30 michael-laptop anacron[3087]: Anacron 2.3 started on 2009-06-19
Jun 19 21:59:30 michael-laptop anacron[3087]: Normal exit (0 jobs run)
Jun 19 21:59:30 michael-laptop /usr/sbin/cron[3130]: (CRON) INFO (pidfile fd = 3)
Jun 19 21:59:30 michael-laptop /usr/sbin/cron[3131]: (CRON) STARTUP (fork ok)
Jun 19 21:59:30 michael-laptop /usr/sbin/cron[3131]: (CRON) INFO (Running @reboot jobs)
Jun 19 21:59:33 michael-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 19 21:59:33 michael-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jun 19 21:59:33 michael-laptop NetworkManager: <info>  (eth0): preparing device. 
Jun 19 21:59:33 michael-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 19 21:59:33 michael-laptop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_13_a9_a5_90_6a
Jun 19 21:59:33 michael-laptop kernel: [   26.075885] sky2 eth0: enabling interface
Jun 19 21:59:33 michael-laptop kernel: [   26.076123] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 21:59:33 michael-laptop acpid: client connected from 2924[0:0] 
Jun 19 21:59:37 michael-laptop console-kit-daemon[2722]: WARNING: Couldn't read /proc/2721/environ: Failed to open file '/proc/2721/environ': No such file or directory 
Jun 19 21:59:52 michael-laptop anacron[3539]: Anacron 2.3 started on 2009-06-19
Jun 19 21:59:52 michael-laptop anacron[3539]: Normal exit (0 jobs run)


Does anyone have any idea what the problem might be? Any suggestions would be great.

I apologise if someone has already asked the same questions but I had a search through the forum and I couldn't find any similar problems.

Thanks,
Michael

---

