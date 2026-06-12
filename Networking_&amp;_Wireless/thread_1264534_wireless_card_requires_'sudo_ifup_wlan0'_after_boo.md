---
title: "wireless card requires 'sudo ifup wlan0' after boot"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by iherbivore on 2009-09-12
My pc does not have wireless ability at boot. I have lived for this problem for several years now. I must do 'sudo ifup wlan0' in order to start it.  As a workaround I can add a script to the init.d stuff that runs this command for me.  This works in that my wirelss network is running when upon boot, however the networkmanager applet says 'device not managed' , and so I can't use it to switch wireless networks.

I have followed the sticky diagnosing thread in this forum: there were no abnormal results from the tests contained therein save for this:
```
drew@drew-desktop:~$ lshw -C Network
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:17:31:f0:5b:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmw    
are=0.3-2 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:b8:99:67
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.5            
3+,07/08/2005,4.2.0.52 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:dc:2a:1e:c8:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A            
 multicast=yes
```here is the dmesg output:

```
drew@drew-desktop:/var/log$ dmesg |grep -e wlan -e ndis
 [   18.107853] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
 [   18.995039] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
 [   18.996266] ndiswrapper: driver net5211 (,07/08/2005,4.2.0.52) loaded
 [   18.996506] ndiswrapper 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
 [   19.478023] ndiswrapper: using IRQ 19
 [   19.676685] wlan0: ethernet device 00:c0:a8:b8:99:67 using serialized NDIS driver: net5211, version: 0x40002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001B.5.conf
 [   19.680068] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
 [   23.543210] usbcore: registered new interface driver ndiswrapper
 [  502.615526] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 [  524.036566] wlan0: no IPv6 routers present
```and here are the lines from the general area of the syslog: (disregard the X issues, that is a new problem that I will start another thread for when I have gathered up as much info as I can)

```
Sep 12 08:03:49 drew-desktop NetworkManager: <info>  starting... 
Sep 12 08:03:49 drew-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e') 
Sep 12 08:03:49 drew-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_17_31_f0_5b_50 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper') 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_c0_a8_b8_99_67 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  Trying to start the supplicant... 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Sep 12 08:03:50 drew-desktop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Sep 12 08:03:54 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Sep 12 08:03:54 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Successfully dropped root privileges.
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: avahi-daemon 0.6.23 starting up.
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Successfully called chroot().
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Successfully dropped remaining capabilities.
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: No service file found in /etc/avahi/services.
Sep 12 08:03:54 drew-desktop nm-system-settings:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Network interface enumeration completed.
Sep 12 08:03:54 drew-desktop avahi-daemon[9560]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep 12 08:03:54 drew-desktop acpid: client connected from 9534[0:0] 
Sep 12 08:03:54 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, autoconnect:0, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-0000-000000000000
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: wireless setting key: (null)='MBR-1fc'
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Sep 12 08:03:56 drew-desktop nm-system-settings: no (wireless) mapping found for key: wireless-essid
Sep 12 08:03:56 drew-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Sep 12 08:03:56 drew-desktop nm-system-settings: <WARN>  ifupdown_update_connection_from_if_block(): connection broken: ssid (2) 
Sep 12 08:03:56 drew-desktop NetworkManager: <info>  (eth0): bringing up device. 
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Sep 12 08:03:56 drew-desktop avahi-daemon[9560]: Server startup complete. Host name is drew-desktop.local. Local service cookie is 1323535366.
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_17_31_f0_5b_50, iface: eth0): not well known
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_c0_a8_b8_99_67, iface: wlan0): well known
Sep 12 08:03:56 drew-desktop NetworkManager: <info>  (eth0): preparing device. 
Sep 12 08:03:56 drew-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Sep 12 08:03:56 drew-desktop NetworkManager: <info>  Setting system hostname to 'localhost.localdomain' (no default device) 
Sep 12 08:03:56 drew-desktop kernel: [  500.220736] e1000e 0000:00:19.0: irq 2300 for MSI/MSI-X
Sep 12 08:03:56 drew-desktop kernel: [  500.276572] e1000e 0000:00:19.0: irq 2300 for MSI/MSI-X
Sep 12 08:03:56 drew-desktop kernel: [  500.277016] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 12 08:03:56 drew-desktop kernel: [  500.916546] ppdev: user-space parallel port driver
Sep 12 08:03:56 drew-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: (31265232) ... get_connections.
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: (31265232) ... get_connections (managed=false): return empty list.
Sep 12 08:03:56 drew-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Sep 12 08:03:56 drew-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Sep 12 08:03:56 drew-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 12 08:03:56 drew-desktop hal_lpadmin: Running hal_lpadmin
Sep 12 08:03:56 drew-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 12 08:03:57 drew-desktop hal_lpadmin: hal_lpadmin triggered by low-level USB device
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): bringing up device. 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): preparing device. 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): now unmanaged 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): cleaning up... 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  (wlan0): taking down device. 
Sep 12 08:03:57 drew-desktop kernel: [  502.615526] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Sep 12 08:03:57 drew-desktop NetworkManager: <info>  Setting system hostname to 'drew-desktop' (from system configuration) 
Sep 12 08:03:57 drew-desktop hal_lpadmin: Getting device ID from the usblp HAL entry ...
Sep 12 08:03:57 drew-desktop hal_lpadmin: Device ID for /dev/usb/lp0: MFG:HP;MDL:Deskjet F2200 series;DES:;CMD:LDL,MLC,PML,DYN;
Sep 12 08:03:57 drew-desktop hal_lpadmin: Written device ID into HAL database entry: MFG:HP;MDL:Deskjet F2200 series;DES:;CMD:LDL,MLC,PML,DYN;
Sep 12 08:03:57 drew-desktop hal_lpadmin: Unable to connect to CUPS: 'httpConnectionEncrypt failed'.  Is CUPS running?
Sep 12 08:03:57 drew-desktop nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Sep 12 08:03:57 drew-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Sep 12 08:03:58 drew-desktop nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Sep 12 08:03:58 drew-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Sep 12 08:04:00 drew-desktop acpid: client connected from 9534[0:0] 
Sep 12 08:04:01 drew-desktop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_17_31_f0_5b_50
Sep 12 08:04:01 drew-desktop kernel: [  506.453733] lirc_dev: IR Remote Control driver registered, major 61 
Sep 12 08:04:01 drew-desktop kernel: [  506.596628] 
Sep 12 08:04:01 drew-desktop kernel: [  506.596630] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
Sep 12 08:04:01 drew-desktop kernel: [  506.596632] lirc_mceusb2: Daniel Melander <[EMAIL="lirc@rajidae.se"]lirc@rajidae.se[/EMAIL]>, Martin Blatter <[EMAIL="martin_a_blatter@yahoo.com"]martin_a_blatter@yahoo.com[/EMAIL]>
Sep 12 08:04:01 drew-desktop kernel: [  506.598186] usbcore: registered new interface driver lirc_mceusb2
Sep 12 08:04:01 drew-desktop lircd-0.8.4a[9709]: lircd(default) ready
Sep 12 08:04:02 drew-desktop anacron[9779]: Anacron 2.3 started on 2009-09-12
Sep 12 08:04:02 drew-desktop anacron[9779]: Normal exit (0 jobs run)
Sep 12 08:04:02 drew-desktop /usr/sbin/cron[9822]: (CRON) INFO (pidfile fd = 3)
Sep 12 08:04:02 drew-desktop /usr/sbin/cron[9823]: (CRON) STARTUP (fork ok)
Sep 12 08:04:02 drew-desktop /usr/sbin/cron[9823]: (CRON) INFO (Running @reboot jobs)
Sep 12 08:04:02 drew-desktop kdm[9513]: X server startup timeout, terminating
Sep 12 08:04:03 drew-desktop kdm[9513]: X server died during startup
Sep 12 08:04:03 drew-desktop kdm[9513]: Failed to start X server. Starting failsafe X server.
Sep 12 08:04:07 drew-desktop acpid: client 9534[0:0] has disconnected 
Sep 12 08:04:07 drew-desktop acpid: client 9534[0:0] has disconnected 
Sep 12 08:04:07 drew-desktop acpid: client connected from 9918[0:0] 
Sep 12 08:04:08 drew-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Sep 12 08:04:08 drew-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Sep 12 08:04:08 drew-desktop dhclient: All rights reserved.
Sep 12 08:04:08 drew-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 12 08:04:08 drew-desktop dhclient: 
Sep 12 08:04:09 drew-desktop avahi-daemon[9560]: Registering new address record for fe80::2c0:a8ff:feb8:9967 on wlan0.*.
Sep 12 08:04:10 drew-desktop dhclient: Listening on LPF/wlan0/00:c0:a8:b8:99:67
Sep 12 08:04:10 drew-desktop dhclient: Sending on   LPF/wlan0/00:c0:a8:b8:99:67
Sep 12 08:04:10 drew-desktop dhclient: Sending on   Socket/fallback
Sep 12 08:04:13 drew-desktop dhclient: DHCPREQUEST of 192.168.0.198 on wlan0 to 255.255.255.255 port 67
Sep 12 08:04:13 drew-desktop dhclient: DHCPACK of 192.168.0.198 from 192.168.0.1
Sep 12 08:04:13 drew-desktop avahi-daemon[9560]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.198.
Sep 12 08:04:13 drew-desktop avahi-daemon[9560]: New relevant interface wlan0.IPv4 for mDNS.
Sep 12 08:04:13 drew-desktop avahi-daemon[9560]: Registering new address record for 192.168.0.198 on wlan0.IPv4.
Sep 12 08:04:13 drew-desktop dhclient: bound to 192.168.0.198 -- renewal in 2147483648 seconds.
Sep 12 08:04:18 drew-desktop kdm[9513]: X server died during startup
Sep 12 08:04:18 drew-desktop kdm[9513]: Failed to start X server. Starting failsafe X server.
Sep 12 08:04:18 drew-desktop kernel: [  524.036566] wlan0: no IPv6 routers present
Sep 12 08:04:26 drew-desktop ntpdate[10107]: adjust time server 91.189.94.4 offset -0.045640 sec
Sep 12 08:04:33 drew-desktop acpid: client 9918[0:0] has disconnected 
Sep 12 08:04:33 drew-desktop acpid: client connected from 10311[0:0] 
Sep 12 08:04:34 drew-desktop acpid: client connected from 10311[0:0] 
Sep 12 08:04:37 drew-desktop kdm_greet[10336]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
Sep 12 08:04:41 drew-desktop console-kit-daemon[9114]: WARNING: Couldn't read /proc/9113/environ: Failed to open file '/proc/9113/environ': No such file or directory 
Sep 12 08:04:53 drew-desktop gnome-session[10463]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type' 
Sep 12 08:04:53 drew-desktop gnome-session[10463]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop 
Sep 12 08:05:03 drew-desktop pulseaudio[10432]: module-x11-xsmp.c: X11 session manager not running.
Sep 12 08:05:03 drew-desktop pulseaudio[10432]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Sep 12 08:05:06 drew-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
```I will be eternally grateful if someone can help me with this.

---

### Post by SagnaB on 2010-07-15
Bump

I too also need help with this exact same situation. I have a DLink DWL-G122  C1

Ubuntu Studio 9.1


Much appreciated all help

---

