---
title: "dhcp server not starting"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by andrewhamming on 2012-08-28
I cant seem to get my dhcp server starting at boot. It starts fine when run at terminal. sudo service ics-dhcp-server start.

my /etc/ltsp/dhcpd.conf
authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.250;
#    option domain-name "example.com";
    option domain-name-servers 139.130.4.4, 202.83.95.227, 203.50.2.71;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
    next-server 192.168.1.53;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

my /etc/default/isc-dhcpd-server
INTERFACES="eth0"

error log showing relevant lines

```
Aug 29 00:23:58 ltspserver NetworkManager[913]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lxcbr0, iface: lxcbr0)
Aug 29 00:23:58 ltspserver NetworkManager[913]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lxcbr0, iface: lxcbr0): no ifupdown configuration found.
Aug 29 00:23:58 ltspserver NetworkManager[913]: <warn> /sys/devices/virtual/net/lxcbr0: couldn't determine device driver; ignoring...
Aug 29 00:23:58 ltspserver kernel: [   11.004874] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 29 00:23:58 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver cron[1098]: (CRON) STARTUP (fork ok)
Aug 29 00:23:59 ltspserver cron[1098]: (CRON) INFO (Running @reboot jobs)
Aug 29 00:23:59 ltspserver dnsmasq[1106]: started, version 2.59 cachesize 150
Aug 29 00:23:59 ltspserver dnsmasq[1106]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug 29 00:23:59 ltspserver dnsmasq-dhcp[1106]: DHCP, IP range 10.0.3.2 -- 10.0.3.254, lease time 1h
Aug 29 00:23:59 ltspserver dnsmasq[1106]: no servers found in /etc/resolv.conf, will retry
Aug 29 00:23:59 ltspserver dnsmasq[1106]: read /etc/hosts - 7 addresses
Aug 29 00:23:59 ltspserver anacron[1073]: Normal exit (0 jobs run)
Aug 29 00:23:59 ltspserver acpid: client connected from 1129[0:0]
Aug 29 00:23:59 ltspserver acpid: 1 client rule loaded
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.304496] init: isc-dhcp-server main process (1058) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.304514] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver kernel: [   11.369762] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
Aug 29 00:23:59 ltspserver kernel: [   11.370225] [fglrx] Firegl kernel thread PID: 1139
Aug 29 00:23:59 ltspserver kernel: [   11.370287] [fglrx] Firegl kernel thread PID: 1140
Aug 29 00:23:59 ltspserver kernel: [   11.370330] [fglrx] Firegl kernel thread PID: 1141
Aug 29 00:23:59 ltspserver kernel: [   11.370408] [fglrx] IRQ 48 Enabled
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.379791] init: isc-dhcp-server main process (1134) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.379810] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver udev-configure-printer: add /module/lp
Aug 29 00:23:59 ltspserver udev-configure-printer: Failed to get parent
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.430102] init: isc-dhcp-server main process (1147) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.430119] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.497039] init: isc-dhcp-server main process (1159) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.497054] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.555686] init: isc-dhcp-server main process (1209) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.555708] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver anacron[1280]: Anacron 2.3 started on 2012-08-29
Aug 29 00:23:59 ltspserver anacron[1280]: Normal exit (0 jobs run)
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.614335] init: isc-dhcp-server main process (1254) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.614351] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.656442] init: isc-dhcp-server main process (1286) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.656466] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.706818] init: isc-dhcp-server main process (1322) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.706834] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.776280] init: isc-dhcp-server main process (1404) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.776294] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver kernel: [   11.812897] [fglrx] Gart USWC size:1280 M.
Aug 29 00:23:59 ltspserver kernel: [   11.812899] [fglrx] Gart cacheable size:508 M.
Aug 29 00:23:59 ltspserver kernel: [   11.812902] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug 29 00:23:59 ltspserver kernel: [   11.812903] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Aug 29 00:23:59 ltspserver kernel: [   11.812905] [fglrx] Reserved FB block: Unshared offset:7ffef000, size:11000 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.854003] init: isc-dhcp-server main process (1423) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.854019] init: isc-dhcp-server main process ended, respawning
Aug 29 00:23:59 ltspserver dhcpd: Wrote 3 leases to leases file.
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 00:23:59 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 00:23:59 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 00:23:59 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 00:23:59 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: 
Aug 29 00:23:59 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 00:23:59 ltspserver kernel: [   11.912651] init: isc-dhcp-server main process (1430) terminated with status 1
Aug 29 00:23:59 ltspserver kernel: [   11.912666] init: isc-dhcp-server respawning too fast, stopped
```

---

### Post by rukiaEnix on 2012-08-28
Add your line without sudo:

```

service ics-dhcp-server start.

```

To this file: /etc/rc.local (you need to be root or use sudo to edit it)
above the line of exit 0

Reboot and see if your service is started

---

### Post by andrewhamming on 2012-08-28
added line the reboot.


*****@ltspserver:~$ sudo service isc-dhcp-server status
[sudo] password for *****: 
isc-dhcp-server stop/waiting

*****@ltspserver:~$ sudo service isc-dhcp-server start
isc-dhcp-server start/running, process 2527

hmmm.

log from boot.log after restart

 * Starting mDNS/DNS-SD daemon[154G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [160G 
[154G[ OK ]
 * Stopping System V initialisation compatibility[154G[ OK ]
 * Starting System V runlevel compatibility[154G[ OK ]
 * Starting ISC DHCP IPv4 server[154G[ OK ]
 * Starting LightDM Display Manager[154G[ OK ]
 * Starting ACPI daemon[154G[ OK ]
 * Starting anac(h)ronistic cron[154G[ OK ]
 * Starting save kernel messages[154G[ OK ]
 * Starting automatic crash report generation[154G[ OK ]
 * Starting crash report submission daemon[154G[ OK ]
 * Starting CPU interrupts balancing daemon[154G[ OK ]
 * Stopping ISC DHCP IPv6 server[154G[ OK ]
 * Starting configure network device[154G[ OK ]
 * Starting configure network device security[154G[ OK ]


log from syslog entire boot process

```
Aug 29 12:41:26 ltspserver kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 29 12:41:26 ltspserver rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="924" x-info="http://www.rsyslog.com"] start
Aug 29 12:41:26 ltspserver rsyslogd: rsyslogd's groupid changed to 103
Aug 29 12:41:26 ltspserver rsyslogd: rsyslogd's userid changed to 101
Aug 29 12:41:26 ltspserver rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> DNS: loaded plugin dnsmasq
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Found user 'avahi' (UID 109) and group 'avahi' (GID 121).
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Successfully dropped root privileges.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: avahi-daemon 0.6.30 starting up.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Successfully called chroot().
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Successfully dropped remaining capabilities.
Aug 29 12:41:26 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Loading service file /services/udisks.service.
Aug 29 12:41:26 ltspserver bluetoothd[900]: Failed to init alert plugin
Aug 29 12:41:26 ltspserver bluetoothd[900]: Failed to init time plugin
Aug 29 12:41:26 ltspserver bluetoothd[900]: Failed to init proximity plugin
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Network interface enumeration completed.
Aug 29 12:41:26 ltspserver cron[1022]: (CRON) INFO (pidfile fd = 3)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 (Ubuntu 3.2.0-29.46-generic-pae 3.2.24)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] KERNEL supported cpus:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Intel GenuineIntel
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   AMD AuthenticAMD
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   NSC Geode by NSC
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Cyrix CyrixInstead
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Centaur CentaurHauls
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   UMC UMC UMC UMC
Aug 29 12:41:26 ltspserver kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000df780000 (usable)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000df780000 - 00000000df7a3000 (ACPI NVS)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000df7a3000 - 00000000df7e0000 (ACPI data)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000df7e0000 - 00000000df800000 (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000041f800000 (usable)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 29 12:41:26 ltspserver kernel: [    0.000000] DMI 2.4 present.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. Z68XP-UD3R/Z68XP-UD3R, BIOS F6 02/21/2012
Aug 29 12:41:26 ltspserver kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] last_pfn = 0x41f800 max_arch_pfn = 0x1000000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] MTRR default type: uncachable
Aug 29 12:41:26 ltspserver kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   00000-9FFFF write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   C0000-CFFFF write-protect
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   D0000-EFFFF uncachable
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   F0000-FFFFF write-through
Aug 29 12:41:26 ltspserver kernel: [    0.000000] MTRR variable ranges enabled:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   2 base 100000000 mask F00000000 write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   3 base 200000000 mask E00000000 write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   4 base 300000000 mask F00000000 write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   5 base 400000000 mask FE0000000 write-back
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   6 disabled
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   7 disabled
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   8 disabled
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   9 disabled
Aug 29 12:41:26 ltspserver kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 29 12:41:26 ltspserver kernel: [    0.000000] original variable MTRRs
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 2, base: 4GB, range: 4GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 3, base: 8GB, range: 8GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 4, base: 12GB, range: 4GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 5, base: 16GB, range: 512MB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] total RAM covered: 16384M
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Found optimal setting for mtrr clean up
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 6  	lose cover RAM: 0G
Aug 29 12:41:26 ltspserver kernel: [    0.000000] New variable MTRRs
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 4, base: 8GB, range: 8GB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] reg 5, base: 16GB, range: 512MB, type WB
Aug 29 12:41:26 ltspserver kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] found SMP MP-table at [c00f5cd0] f5cd0
Aug 29 12:41:26 ltspserver kernel: [    0.000000] initial memory mapped : 0 - 02000000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Aug 29 12:41:26 ltspserver kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Aug 29 12:41:26 ltspserver kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Aug 29 12:41:26 ltspserver kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] RAMDISK: 364e2000 - 37269000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: RSDP 000f78c0 00014 (v00 GBT   )
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: RSDT df7a3040 00054 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: FACP df7a3100 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: DSDT df7a31c0 04D4C (v01 GBT    GBTUACPI 00001000 MSFT 04000000)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: FACS df780000 00040
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: MSDM df7a8080 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: HPET df7a8140 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: MCFG df7a81c0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: ASPT df7a8300 00034 (v07 GBT    PerfTune 312E3042 UTBG 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: SSPT df7a8340 02380 (v01 GBT    SsptHead 312E3042 UTBG 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: EUDS df7aa6c0 000C0 (v01 GBT             00000000      00000000)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: MATS df7aa780 00034 (v01 GBT             00000000      00000000)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: TAMG df7aa7e0 00A6A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: APIC df7a7f80 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: SSDT df7ab280 01F4C (v01  INTEL PPM RCM  80000001 INTL 20061109)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: MATS df7ad200 0A97D (v01        MATS RCM 80000001 INTL 20061109)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] 15996MB HIGHMEM available.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] 891MB LOWMEM available.
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   low ram: 0 - 37bfe000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Zone PFN ranges:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0041f800
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Movable zone start PFN for each node
Aug 29 12:41:26 ltspserver kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     0: 0x00000100 -> 0x000df780
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     0: 0x00100000 -> 0x0041f800
Aug 29 12:41:26 ltspserver kernel: [    0.000000] On node 0 totalpages: 4189967
Aug 29 12:41:26 ltspserver kernel: [    0.000000] free_area_init_node: node 0, pgdat c1866a40, node_mem_map ee0f2200
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   HighMem zone: 31993 pages used for memmap
Aug 29 12:41:26 ltspserver kernel: [    0.000000]   HighMem zone: 3929737 pages, LIFO batch:31
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Using APIC driver default
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver in.tftpd[1026]: cannot resolve local IPv4 bind address: 0.0.0.0, Name or service not known
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 29 12:41:26 ltspserver dnsmasq[1086]: started, version 2.59 cachesize 150
Aug 29 12:41:26 ltspserver acpid: starting up with proc fs
Aug 29 12:41:26 ltspserver dnsmasq[1086]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug 29 12:41:26 ltspserver dnsmasq-dhcp[1086]: DHCP, IP range 10.0.3.2 -- 10.0.3.254, lease time 1h
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Server startup complete. Host name is ltspserver.local. Local service cookie is 1508645784.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Service "ltspserver" (/services/udisks.service) successfully established.
Aug 29 12:41:26 ltspserver dnsmasq[1086]: no servers found in /etc/resolv.conf, will retry
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Joining mDNS multicast group on interface lxcbr0.IPv4 with address 10.0.3.1.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: New relevant interface lxcbr0.IPv4 for mDNS.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Registering new address record for 10.0.3.1 on lxcbr0.IPv4.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Withdrawing address record for 10.0.3.1 on lxcbr0.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Leaving mDNS multicast group on interface lxcbr0.IPv4 with address 10.0.3.1.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 29 12:41:26 ltspserver kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 29 12:41:26 ltspserver kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 29 12:41:26 ltspserver dnsmasq[1086]: read /etc/hosts - 7 addresses
Aug 29 12:41:26 ltspserver kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Aug 29 12:41:26 ltspserver kernel: [    0.000000] nr_irqs_gsi: 40
Aug 29 12:41:26 ltspserver kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Allocating PCI resources starting at df800000 (gap: df800000:10800000)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 29 12:41:26 ltspserver kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Aug 29 12:41:26 ltspserver kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7b7a000 s34240 r0 d23104 u57344
Aug 29 12:41:26 ltspserver kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Aug 29 12:41:26 ltspserver kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4156190
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=2ffc2468-ed81-49d5-a41c-bdf0b1d4a91b ro quiet splash vt.handoff=7
Aug 29 12:41:26 ltspserver kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Initializing CPU#0
Aug 29 12:41:26 ltspserver kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Aug 29 12:41:26 ltspserver kernel: [    0.000000] allocated 69172992 bytes of page_cgroup
Aug 29 12:41:26 ltspserver kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0041f800)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Memory: 16531672k/17293312k available (5814k kernel code, 228196k reserved, 2841k data, 740k init, 15846920k highmem)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] virtual kernel memory layout:
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]       .data : 0xc15adb64 - 0xc1874240   (2841 kB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000]       .text : 0xc1000000 - 0xc15adb64   (5814 kB)
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Hierarchical RCU implementation.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Aug 29 12:41:26 ltspserver kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
Aug 29 12:41:26 ltspserver kernel: [    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
Aug 29 12:41:26 ltspserver kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Console: colour dummy device 80x25
Aug 29 12:41:26 ltspserver kernel: [    0.000000] console [tty0] enabled
Aug 29 12:41:26 ltspserver kernel: [    0.000000] hpet clockevent registered
Aug 29 12:41:26 ltspserver kernel: [    0.000000] Fast TSC calibration using PIT
Aug 29 12:41:26 ltspserver kernel: [    0.004000] Detected 3309.534 MHz processor.
Aug 29 12:41:26 ltspserver kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6619.06 BogoMIPS (lpj=13238136)
Aug 29 12:41:26 ltspserver kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Aug 29 12:41:26 ltspserver kernel: [    0.000017] Security Framework initialized
Aug 29 12:41:26 ltspserver kernel: [    0.000027] AppArmor: AppArmor initialized
Aug 29 12:41:26 ltspserver kernel: [    0.000028] Yama: becoming mindful.
Aug 29 12:41:26 ltspserver kernel: [    0.000058] Mount-cache hash table entries: 512
Aug 29 12:41:26 ltspserver kernel: [    0.000133] Initializing cgroup subsys cpuacct
Aug 29 12:41:26 ltspserver kernel: [    0.000137] Initializing cgroup subsys memory
Aug 29 12:41:26 ltspserver kernel: [    0.000141] Initializing cgroup subsys devices
Aug 29 12:41:26 ltspserver kernel: [    0.000142] Initializing cgroup subsys freezer
Aug 29 12:41:26 ltspserver kernel: [    0.000144] Initializing cgroup subsys blkio
Aug 29 12:41:26 ltspserver kernel: [    0.000147] Initializing cgroup subsys perf_event
Aug 29 12:41:26 ltspserver kernel: [    0.000163] CPU: Physical Processor ID: 0
Aug 29 12:41:26 ltspserver kernel: [    0.000164] CPU: Processor Core ID: 0
Aug 29 12:41:26 ltspserver kernel: [    0.000167] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Aug 29 12:41:26 ltspserver kernel: [    0.000168] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Aug 29 12:41:26 ltspserver kernel: [    0.000170] mce: CPU supports 9 MCE banks
Aug 29 12:41:26 ltspserver kernel: [    0.000180] CPU0: Thermal monitoring enabled (TM1)
Aug 29 12:41:26 ltspserver kernel: [    0.000184] using mwait in idle threads.
Aug 29 12:41:26 ltspserver kernel: [    0.001743] ACPI: Core revision 20110623
Aug 29 12:41:26 ltspserver kernel: [    0.008351] ftrace: allocating 26545 entries in 52 pages
Aug 29 12:41:26 ltspserver kernel: [    0.015016] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 29 12:41:26 ltspserver kernel: [    0.015409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 29 12:41:26 ltspserver kernel: [    0.055039] CPU0: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz stepping 07
Aug 29 12:41:26 ltspserver kernel: [    0.160811] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Aug 29 12:41:26 ltspserver kernel: [    0.160815] PEBS disabled due to CPU errata.
Aug 29 12:41:26 ltspserver kernel: [    0.160816] ... version:                3
Aug 29 12:41:26 ltspserver kernel: [    0.160817] ... bit width:              48
Aug 29 12:41:26 ltspserver kernel: [    0.160818] ... generic registers:      8
Aug 29 12:41:26 ltspserver kernel: [    0.160819] ... value mask:             0000ffffffffffff
Aug 29 12:41:26 ltspserver kernel: [    0.160820] ... max period:             000000007fffffff
Aug 29 12:41:26 ltspserver kernel: [    0.160821] ... fixed-purpose events:   3
Aug 29 12:41:26 ltspserver kernel: [    0.160822] ... event mask:             00000007000000ff
Aug 29 12:41:26 ltspserver kernel: [    0.160922] NMI watchdog enabled, takes one hw-pmu counter.
Aug 29 12:41:26 ltspserver kernel: [    0.160970] CPU 1 irqstacks, hard=f753a000 soft=f753c000
Aug 29 12:41:26 ltspserver kernel: [    0.160971] Booting Node   0, Processors  #1
Aug 29 12:41:26 ltspserver kernel: [    0.160972] smpboot cpu 1: start_ip = 9b000
Aug 29 12:41:26 ltspserver kernel: [    0.171239] Initializing CPU#1
Aug 29 12:41:26 ltspserver kernel: [    0.268781] NMI watchdog enabled, takes one hw-pmu counter.
Aug 29 12:41:26 ltspserver kernel: [    0.268834] CPU 2 irqstacks, hard=f7566000 soft=f7568000
Aug 29 12:41:26 ltspserver kernel: [    0.268836]  #2
Aug 29 12:41:26 ltspserver kernel: [    0.268836] smpboot cpu 2: start_ip = 9b000
Aug 29 12:41:26 ltspserver kernel: [    0.279036] Initializing CPU#2
Aug 29 12:41:26 ltspserver kernel: [    0.376641] NMI watchdog enabled, takes one hw-pmu counter.
Aug 29 12:41:26 ltspserver kernel: [    0.376695] CPU 3 irqstacks, hard=f757c000 soft=f757e000
Aug 29 12:41:26 ltspserver kernel: [    0.376697]  #3
Aug 29 12:41:26 ltspserver kernel: [    0.376697] smpboot cpu 3: start_ip = 9b000
Aug 29 12:41:26 ltspserver kernel: [    0.386897] Initializing CPU#3
Aug 29 12:41:26 ltspserver kernel: [    0.484501] NMI watchdog enabled, takes one hw-pmu counter.
Aug 29 12:41:26 ltspserver kernel: [    0.484522] Brought up 4 CPUs
Aug 29 12:41:26 ltspserver kernel: [    0.484523] Total of 4 processors activated (26477.03 BogoMIPS).
Aug 29 12:41:26 ltspserver kernel: [    0.487145] devtmpfs: initialized
Aug 29 12:41:26 ltspserver kernel: [    0.487220] EVM: security.selinux
Aug 29 12:41:26 ltspserver kernel: [    0.487221] EVM: security.SMACK64
Aug 29 12:41:26 ltspserver kernel: [    0.487222] EVM: security.capability
Aug 29 12:41:26 ltspserver kernel: [    0.487236] PM: Registering ACPI NVS region at df780000 (143360 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.487821] print_constraints: dummy: 
Aug 29 12:41:26 ltspserver kernel: [    0.487848] RTC time: 12:41:14, date: 08/29/12
Aug 29 12:41:26 ltspserver kernel: [    0.487872] NET: Registered protocol family 16
Aug 29 12:41:26 ltspserver kernel: [    0.487932] Trying to unpack rootfs image as initramfs...
Aug 29 12:41:26 ltspserver kernel: [    0.487938] EISA bus registered
Aug 29 12:41:26 ltspserver kernel: [    0.487949] ACPI: bus type pci registered
Aug 29 12:41:26 ltspserver kernel: [    0.487996] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Aug 29 12:41:26 ltspserver kernel: [    0.487998] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Aug 29 12:41:26 ltspserver kernel: [    0.487999] PCI: Using MMCONFIG for extended config space
Aug 29 12:41:26 ltspserver kernel: [    0.488000] PCI: Using configuration type 1 for base access
Aug 29 12:41:26 ltspserver kernel: [    0.488624] bio: create slab <bio-0> at 0
Aug 29 12:41:26 ltspserver kernel: [    0.488671] ACPI: Added _OSI(Module Device)
Aug 29 12:41:26 ltspserver kernel: [    0.488673] ACPI: Added _OSI(Processor Device)
Aug 29 12:41:26 ltspserver kernel: [    0.488674] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug 29 12:41:26 ltspserver kernel: [    0.488675] ACPI: Added _OSI(Processor Aggregator Device)
Aug 29 12:41:26 ltspserver kernel: [    0.489236] ACPI: EC: Look up EC in DSDT
Aug 29 12:41:26 ltspserver kernel: [    0.491911] ACPI Warning: Incorrect checksum in table [TAMG] - 0x98, should be 0x97 (20110623/tbutils-314)
Aug 29 12:41:26 ltspserver kernel: [    0.492295] ACPI: Interpreter enabled
Aug 29 12:41:26 ltspserver kernel: [    0.492305] ACPI: (supports S0 S3 S4 S5)
Aug 29 12:41:26 ltspserver kernel: [    0.492315] ACPI: Using IOAPIC for interrupt routing
Aug 29 12:41:26 ltspserver kernel: [    0.494603] ACPI: No dock devices found.
Aug 29 12:41:26 ltspserver kernel: [    0.494604] HEST: Table not found.
Aug 29 12:41:26 ltspserver kernel: [    0.494608] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug 29 12:41:26 ltspserver kernel: [    0.494640] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
Aug 29 12:41:26 ltspserver kernel: [    0.494705] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Aug 29 12:41:26 ltspserver kernel: [    0.494707] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Aug 29 12:41:26 ltspserver kernel: [    0.494708] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug 29 12:41:26 ltspserver kernel: [    0.494709] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
Aug 29 12:41:26 ltspserver kernel: [    0.494711] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
Aug 29 12:41:26 ltspserver kernel: [    0.494712] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfebfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.494721] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
Aug 29 12:41:26 ltspserver kernel: [    0.494748] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.494773] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.494775] pci 0000:00:01.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.494812] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Aug 29 12:41:26 ltspserver kernel: [    0.494833] pci 0000:00:16.0: reg 10: [mem 0xfbfff000-0xfbfff00f 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.494904] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.494907] pci 0000:00:16.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.494935] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Aug 29 12:41:26 ltspserver kernel: [    0.494954] pci 0000:00:1a.0: reg 10: [mem 0xfbffe000-0xfbffe3ff]
Aug 29 12:41:26 ltspserver kernel: [    0.495039] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495043] pci 0000:00:1a.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495063] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Aug 29 12:41:26 ltspserver kernel: [    0.495077] pci 0000:00:1b.0: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.495139] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495142] pci 0000:00:1b.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495160] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495234] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495237] pci 0000:00:1c.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495259] pci 0000:00:1c.3: [8086:244e] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495334] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495337] pci 0000:00:1c.3: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495357] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495431] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495434] pci 0000:00:1c.4: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495455] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495528] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495531] pci 0000:00:1c.5: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495552] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495626] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495629] pci 0000:00:1c.6: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495649] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.495723] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495726] pci 0000:00:1c.7: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495750] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Aug 29 12:41:26 ltspserver kernel: [    0.495769] pci 0000:00:1d.0: reg 10: [mem 0xfbffd000-0xfbffd3ff]
Aug 29 12:41:26 ltspserver kernel: [    0.495854] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.495858] pci 0000:00:1d.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.495878] pci 0000:00:1f.0: [8086:1c44] type 0 class 0x000601
Aug 29 12:41:26 ltspserver kernel: [    0.495993] pci 0000:00:1f.2: [8086:1c00] type 0 class 0x000101
Aug 29 12:41:26 ltspserver kernel: [    0.496006] pci 0000:00:1f.2: reg 10: [io  0xff00-0xff07]
Aug 29 12:41:26 ltspserver kernel: [    0.496012] pci 0000:00:1f.2: reg 14: [io  0xfe00-0xfe03]
Aug 29 12:41:26 ltspserver kernel: [    0.496019] pci 0000:00:1f.2: reg 18: [io  0xfd00-0xfd07]
Aug 29 12:41:26 ltspserver kernel: [    0.496026] pci 0000:00:1f.2: reg 1c: [io  0xfc00-0xfc03]
Aug 29 12:41:26 ltspserver kernel: [    0.496032] pci 0000:00:1f.2: reg 20: [io  0xfb00-0xfb0f]
Aug 29 12:41:26 ltspserver kernel: [    0.496039] pci 0000:00:1f.2: reg 24: [io  0xfa00-0xfa0f]
Aug 29 12:41:26 ltspserver kernel: [    0.496079] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Aug 29 12:41:26 ltspserver kernel: [    0.496093] pci 0000:00:1f.3: reg 10: [mem 0xfbffc000-0xfbffc0ff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.496112] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
Aug 29 12:41:26 ltspserver kernel: [    0.496141] pci 0000:00:1f.5: [8086:1c08] type 0 class 0x000101
Aug 29 12:41:26 ltspserver kernel: [    0.496154] pci 0000:00:1f.5: reg 10: [io  0xf800-0xf807]
Aug 29 12:41:26 ltspserver kernel: [    0.496161] pci 0000:00:1f.5: reg 14: [io  0xf700-0xf703]
Aug 29 12:41:26 ltspserver kernel: [    0.496168] pci 0000:00:1f.5: reg 18: [io  0xf600-0xf607]
Aug 29 12:41:26 ltspserver kernel: [    0.496174] pci 0000:00:1f.5: reg 1c: [io  0xf500-0xf503]
Aug 29 12:41:26 ltspserver polkitd[973]: started daemon version 0.104 using authority implementation `local' version `0.104'
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Interface lxcbr0.IPv4 no longer relevant for mDNS.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Joining mDNS multicast group on interface lxcbr0.IPv4 with address 10.0.3.1.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: New relevant interface lxcbr0.IPv4 for mDNS.
Aug 29 12:41:26 ltspserver avahi-daemon[949]: Registering new address record for 10.0.3.1 on lxcbr0.IPv4.
Aug 29 12:41:26 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:26 ltspserver kernel: [    0.496181] pci 0000:00:1f.5: reg 20: [io  0xf400-0xf40f]
Aug 29 12:41:26 ltspserver kernel: [    0.496188] pci 0000:00:1f.5: reg 24: [io  0xf300-0xf30f]
Aug 29 12:41:26 ltspserver kernel: [    0.496248] pci 0000:01:00.0: [1002:6819] type 0 class 0x000300
Aug 29 12:41:26 ltspserver kernel: [    0.496257] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.496265] pci 0000:01:00.0: reg 18: [mem 0xfbb80000-0xfbbbffff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.496270] pci 0000:01:00.0: reg 20: [io  0xbe00-0xbeff]
Aug 29 12:41:26 ltspserver kernel: [    0.496279] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.496307] pci 0000:01:00.0: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.496309] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
Aug 29 12:41:26 ltspserver kernel: [    0.496311] pci 0000:01:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.496331] pci 0000:01:00.1: [1002:aab0] type 0 class 0x000403
Aug 29 12:41:26 ltspserver kernel: [    0.496340] pci 0000:01:00.1: reg 10: [mem 0xfbbfc000-0xfbbfffff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.496390] pci 0000:01:00.1: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.504379] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Aug 29 12:41:26 ltspserver kernel: [    0.504381] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
Aug 29 12:41:26 ltspserver kernel: [    0.504383] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbbfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.504386] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.504427] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug 29 12:41:26 ltspserver kernel: [    0.504497] pci 0000:03:00.0: [1283:8892] type 1 class 0x000604
Aug 29 12:41:26 ltspserver kernel: [    0.504653] pci 0000:03:00.0: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.504654] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.504660] pci 0000:03:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.504683] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504686] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.504689] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.504694] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504696] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504697] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504699] pci 0000:00:1c.3:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504700] pci 0000:00:1c.3:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504702] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.504792] pci 0000:04:00.0: [14f1:8800] type 0 class 0x000400
Aug 29 12:41:26 ltspserver kernel: [    0.504832] pci 0000:04:00.0: reg 10: [mem 0xf7000000-0xf7ffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.505050] pci 0000:04:00.1: [14f1:8811] type 0 class 0x000480
Aug 29 12:41:26 ltspserver kernel: [    0.505084] pci 0000:04:00.1: reg 10: [mem 0xf9000000-0xf9ffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.505278] pci 0000:04:00.2: [14f1:8802] type 0 class 0x000480
Aug 29 12:41:26 ltspserver kernel: [    0.505313] pci 0000:04:00.2: reg 10: [mem 0xf8000000-0xf8ffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.505523] pci 0000:04:02.0: [1106:3044] type 0 class 0x000c00
Aug 29 12:41:26 ltspserver kernel: [    0.505559] pci 0000:04:02.0: reg 10: [mem 0xfafff000-0xfafff7ff]
Aug 29 12:41:26 ltspserver kernel: [    0.505579] pci 0000:04:02.0: reg 14: [io  0xef00-0xef7f]
Aug 29 12:41:26 ltspserver kernel: [    0.505731] pci 0000:04:02.0: supports D2
Aug 29 12:41:26 ltspserver kernel: [    0.505732] pci 0000:04:02.0: PME# supported from D2 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.505739] pci 0000:04:02.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.505826] pci 0000:03:00.0: PCI bridge to [bus 04-04] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505836] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.505842] pci 0000:03:00.0:   bridge window [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.505853] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505855] pci 0000:03:00.0:   bridge window [mem 0xf7000000-0xfaffffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505856] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505858] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505859] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505860] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505862] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505863] pci 0000:03:00.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505865] pci 0000:03:00.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505866] pci 0000:03:00.0:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
Aug 29 12:41:26 ltspserver kernel: [    0.505941] pci 0000:05:00.0: [1b6f:7023] type 0 class 0x000c03
Aug 29 12:41:26 ltspserver kernel: [    0.505967] pci 0000:05:00.0: reg 10: [mem 0xfbaf8000-0xfbafffff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.506088] pci 0000:05:00.0: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.506089] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.506094] pci 0000:05:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.512373] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Aug 29 12:41:26 ltspserver kernel: [    0.512379] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
Aug 29 12:41:26 ltspserver kernel: [    0.512444] pci 0000:06:00.0: [1b6f:7023] type 0 class 0x000c03
Aug 29 12:41:26 ltspserver kernel: [    0.512469] pci 0000:06:00.0: reg 10: [mem 0xfbef8000-0xfbefffff 64bit]
Aug 29 12:41:26 ltspserver kernel: [    0.512592] pci 0000:06:00.0: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.512593] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.512597] pci 0000:06:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.520362] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
Aug 29 12:41:26 ltspserver kernel: [    0.520368] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
Aug 29 12:41:26 ltspserver kernel: [    0.520434] pci 0000:07:00.0: [10ec:8168] type 0 class 0x000200
Aug 29 12:41:26 ltspserver kernel: [    0.520454] pci 0000:07:00.0: reg 10: [io  0xde00-0xdeff]
Aug 29 12:41:26 ltspserver kernel: [    0.520487] pci 0000:07:00.0: reg 18: [mem 0xfbdff000-0xfbdfffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.520508] pci 0000:07:00.0: reg 20: [mem 0xfbdf8000-0xfbdfbfff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.520597] pci 0000:07:00.0: supports D1 D2
Aug 29 12:41:26 ltspserver kernel: [    0.520598] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 29 12:41:26 ltspserver kernel: [    0.520603] pci 0000:07:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.528355] pci 0000:00:1c.6: PCI bridge to [bus 07-07]
Aug 29 12:41:26 ltspserver kernel: [    0.528359] pci 0000:00:1c.6:   bridge window [io  0xd000-0xdfff]
Aug 29 12:41:26 ltspserver kernel: [    0.528366] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.528426] pci 0000:08:00.0: [1b4b:917a] type 0 class 0x000101
Aug 29 12:41:26 ltspserver kernel: [    0.528443] pci 0000:08:00.0: reg 10: [io  0xcf00-0xcf07]
Aug 29 12:41:26 ltspserver kernel: [    0.528455] pci 0000:08:00.0: reg 14: [io  0xce00-0xce03]
Aug 29 12:41:26 ltspserver kernel: [    0.528466] pci 0000:08:00.0: reg 18: [io  0xcd00-0xcd07]
Aug 29 12:41:26 ltspserver kernel: [    0.528478] pci 0000:08:00.0: reg 1c: [io  0xcc00-0xcc03]
Aug 29 12:41:26 ltspserver kernel: [    0.528490] pci 0000:08:00.0: reg 20: [io  0xcb00-0xcb0f]
Aug 29 12:41:26 ltspserver kernel: [    0.528502] pci 0000:08:00.0: reg 24: [mem 0xfbcff000-0xfbcff1ff]
Aug 29 12:41:26 ltspserver kernel: [    0.528514] pci 0000:08:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.528571] pci 0000:08:00.0: PME# supported from D3hot
Aug 29 12:41:26 ltspserver kernel: [    0.528575] pci 0000:08:00.0: PME# disabled
Aug 29 12:41:26 ltspserver kernel: [    0.536343] pci 0000:00:1c.7: PCI bridge to [bus 08-08]
Aug 29 12:41:26 ltspserver kernel: [    0.536346] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Aug 29 12:41:26 ltspserver kernel: [    0.536349] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.536381] pci_bus 0000:00: on NUMA node 0
Aug 29 12:41:26 ltspserver kernel: [    0.536386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536681] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
Aug 29 12:41:26 ltspserver kernel: [    0.536720]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug 29 12:41:26 ltspserver kernel: [    0.536722]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Aug 29 12:41:26 ltspserver kernel: [    0.536723] ACPI _OSC control for PCIe not granted, disabling ASPM
Aug 29 12:41:26 ltspserver kernel: [    0.541586] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541615] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541642] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541669] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541696] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 29 12:41:26 ltspserver kernel: [    0.541723] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 29 12:41:26 ltspserver kernel: [    0.541750] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541777] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Aug 29 12:41:26 ltspserver kernel: [    0.541850] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 29 12:41:26 ltspserver kernel: [    0.541854] vgaarb: loaded
Aug 29 12:41:26 ltspserver kernel: [    0.541855] vgaarb: bridge control possible 0000:01:00.0
Aug 29 12:41:26 ltspserver kernel: [    0.541917] i2c-core: driver [aat2870] using legacy suspend method
Aug 29 12:41:26 ltspserver kernel: [    0.541918] i2c-core: driver [aat2870] using legacy resume method
Aug 29 12:41:26 ltspserver kernel: [    0.541963] SCSI subsystem initialized
Aug 29 12:41:26 ltspserver kernel: [    0.541991] libata version 3.00 loaded.
Aug 29 12:41:26 ltspserver kernel: [    0.542018] usbcore: registered new interface driver usbfs
Aug 29 12:41:26 ltspserver kernel: [    0.542024] usbcore: registered new interface driver hub
Aug 29 12:41:26 ltspserver kernel: [    0.542036] usbcore: registered new device driver usb
Aug 29 12:41:26 ltspserver kernel: [    0.542084] PCI: Using ACPI for IRQ routing
Aug 29 12:41:26 ltspserver kernel: [    0.543418] PCI: pci_cache_line_size set to 64 bytes
Aug 29 12:41:26 ltspserver kernel: [    0.543513] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
Aug 29 12:41:26 ltspserver kernel: [    0.543514] reserve RAM buffer: 00000000df780000 - 00000000dfffffff 
Aug 29 12:41:26 ltspserver kernel: [    0.543516] reserve RAM buffer: 000000041f800000 - 000000041fffffff 
Aug 29 12:41:26 ltspserver kernel: [    0.543574] NetLabel: Initializing
Aug 29 12:41:26 ltspserver kernel: [    0.543575] NetLabel:  domain hash size = 128
Aug 29 12:41:26 ltspserver kernel: [    0.543576] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 29 12:41:26 ltspserver kernel: [    0.543582] NetLabel:  unlabeled traffic allowed by default
Aug 29 12:41:26 ltspserver kernel: [    0.543611] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Aug 29 12:41:26 ltspserver kernel: [    0.543615] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Aug 29 12:41:26 ltspserver kernel: [    0.545630] Switching to clocksource hpet
Aug 29 12:41:26 ltspserver kernel: [    0.550143] AppArmor: AppArmor Filesystem Enabled
Aug 29 12:41:26 ltspserver kernel: [    0.550157] pnp: PnP ACPI init
Aug 29 12:41:26 ltspserver kernel: [    0.550167] ACPI: bus type pnp registered
Aug 29 12:41:26 ltspserver kernel: [    0.550216] pnp 00:00: [bus 00-3f]
Aug 29 12:41:26 ltspserver kernel: [    0.550217] pnp 00:00: [io  0x0cf8-0x0cff]
Aug 29 12:41:26 ltspserver kernel: [    0.550219] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug 29 12:41:26 ltspserver kernel: [    0.550220] pnp 00:00: [io  0x0d00-0xffff window]
Aug 29 12:41:26 ltspserver kernel: [    0.550221] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug 29 12:41:26 ltspserver kernel: [    0.550223] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Aug 29 12:41:26 ltspserver kernel: [    0.550224] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Aug 29 12:41:26 ltspserver kernel: [    0.550225] pnp 00:00: [mem 0xe0000000-0xfebfffff window]
Aug 29 12:41:26 ltspserver kernel: [    0.550255] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550305] pnp 00:01: [io  0x0010-0x001f]
Aug 29 12:41:26 ltspserver kernel: [    0.550307] pnp 00:01: [io  0x0022-0x003f]
Aug 29 12:41:26 ltspserver kernel: [    0.550308] pnp 00:01: [io  0x0044-0x004d]
Aug 29 12:41:26 ltspserver kernel: [    0.550309] pnp 00:01: [io  0x0050-0x005f]
Aug 29 12:41:26 ltspserver kernel: [    0.550310] pnp 00:01: [io  0x0062-0x0063]
Aug 29 12:41:26 ltspserver kernel: [    0.550311] pnp 00:01: [io  0x0065-0x006f]
Aug 29 12:41:26 ltspserver kernel: [    0.550313] pnp 00:01: [io  0x0074-0x007f]
Aug 29 12:41:26 ltspserver kernel: [    0.550314] pnp 00:01: [io  0x0091-0x0093]
Aug 29 12:41:26 ltspserver kernel: [    0.550315] pnp 00:01: [io  0x00a2-0x00bf]
Aug 29 12:41:26 ltspserver kernel: [    0.550316] pnp 00:01: [io  0x00e0-0x00ef]
Aug 29 12:41:26 ltspserver kernel: [    0.550317] pnp 00:01: [io  0x04d0-0x04d1]
Aug 29 12:41:26 ltspserver kernel: [    0.550318] pnp 00:01: [io  0x0290-0x029f]
Aug 29 12:41:26 ltspserver kernel: [    0.550319] pnp 00:01: [io  0x0800-0x0805]
Aug 29 12:41:26 ltspserver kernel: [    0.550320] pnp 00:01: [io  0x0290-0x0294]
Aug 29 12:41:26 ltspserver kernel: [    0.550321] pnp 00:01: [io  0x0880-0x088f]
Aug 29 12:41:26 ltspserver kernel: [    0.550358] system 00:01: [io  0x04d0-0x04d1] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550360] system 00:01: [io  0x0290-0x029f] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550361] system 00:01: [io  0x0800-0x0805] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550362] system 00:01: [io  0x0290-0x0294] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550364] system 00:01: [io  0x0880-0x088f] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550366] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550373] pnp 00:02: [dma 4]
Aug 29 12:41:26 ltspserver kernel: [    0.550374] pnp 00:02: [io  0x0000-0x000f]
Aug 29 12:41:26 ltspserver kernel: [    0.550375] pnp 00:02: [io  0x0080-0x0090]
Aug 29 12:41:26 ltspserver kernel: [    0.550376] pnp 00:02: [io  0x0094-0x009f]
Aug 29 12:41:26 ltspserver kernel: [    0.550377] pnp 00:02: [io  0x00c0-0x00df]
Aug 29 12:41:26 ltspserver kernel: [    0.550394] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550422] pnp 00:03: [irq 0 disabled]
Aug 29 12:41:26 ltspserver kernel: [    0.550429] pnp 00:03: [irq 8]
Aug 29 12:41:26 ltspserver kernel: [    0.550430] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Aug 29 12:41:26 ltspserver kernel: [    0.550447] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550462] pnp 00:04: [io  0x0070-0x0073]
Aug 29 12:41:26 ltspserver kernel: [    0.550479] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550484] pnp 00:05: [io  0x0061]
Aug 29 12:41:26 ltspserver kernel: [    0.550500] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Aug 29 12:41:26 ltspserver acpid: 35 rules loaded
Aug 29 12:41:26 ltspserver kernel: [    0.550505] pnp 00:06: [io  0x00f0-0x00ff]
Aug 29 12:41:26 ltspserver kernel: [    0.550509] pnp 00:06: [irq 13]
Aug 29 12:41:26 ltspserver acpid: waiting for events: event logging is off
Aug 29 12:41:26 ltspserver kernel: [    0.550525] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550678] pnp 00:07: [io  0x03f8-0x03ff]
Aug 29 12:41:26 ltspserver kernel: [    0.550682] pnp 00:07: [irq 4]
Aug 29 12:41:26 ltspserver acpid: client connected from 1095[0:0]
Aug 29 12:41:26 ltspserver kernel: [    0.550720] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550758] pnp 00:08: [io  0x0400-0x04cf]
Aug 29 12:41:26 ltspserver kernel: [    0.550759] pnp 00:08: [io  0x04d2-0x04ff]
Aug 29 12:41:26 ltspserver acpid: 1 client rule loaded
Aug 29 12:41:26 ltspserver kernel: [    0.550788] system 00:08: [io  0x0400-0x04cf] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550789] system 00:08: [io  0x04d2-0x04ff] has been reserved
Aug 29 12:41:26 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug 29 12:41:26 ltspserver kernel: [    0.550791] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550798] pnp 00:09: [io  0x1000-0x107f]
Aug 29 12:41:26 ltspserver kernel: [    0.550799] pnp 00:09: [io  0x1080-0x10ff]
Aug 29 12:41:26 ltspserver kernel: [    0.550800] pnp 00:09: [io  0x1100-0x117f]
Aug 29 12:41:26 ltspserver kernel: [    0.550801] pnp 00:09: [io  0x1180-0x11ff]
Aug 29 12:41:26 ltspserver kernel: [    0.550830] system 00:09: [io  0x1000-0x107f] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550832] system 00:09: [io  0x1080-0x10ff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550833] system 00:09: [io  0x1100-0x117f] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550835] system 00:09: [io  0x1180-0x11ff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550836] system 00:09: Plug and Play ACPI device, IDs ICD0001 PNP0c02 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550944] pnp 00:0a: [io  0x0454-0x0457]
Aug 29 12:41:26 ltspserver kernel: [    0.550978] system 00:0a: [io  0x0454-0x0457] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.550980] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.550990] pnp 00:0b: [mem 0xf0000000-0xf3ffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551023] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551025] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.551135] pnp 00:0c: [mem 0x000d1000-0x000d3fff]
Aug 29 12:41:26 ltspserver kernel: [    0.551137] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
Aug 29 12:41:26 ltspserver kernel: [    0.551138] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
Aug 29 12:41:26 ltspserver kernel: [    0.551139] pnp 00:0c: [mem 0x000fc000-0x000fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551140] pnp 00:0c: [mem 0xdf780000-0xdf7dffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551141] pnp 00:0c: [mem 0x00000000-0x0009ffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551143] pnp 00:0c: [mem 0x00100000-0xdf77ffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551144] pnp 00:0c: [mem 0xdf7e0000-0xdf7fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551145] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
Aug 29 12:41:26 ltspserver kernel: [    0.551146] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
Aug 29 12:41:26 ltspserver kernel: [    0.551147] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551148] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
Aug 29 12:41:26 ltspserver kernel: [    0.551150] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551152] pnp 00:0c: [mem 0xfff00000-0xffffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551153] pnp 00:0c: [mem 0x000e0000-0x000effff]
Aug 29 12:41:26 ltspserver kernel: [    0.551154] pnp 00:0c: [mem 0x20000000-0x201fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551155] pnp 00:0c: [mem 0x40000000-0x400fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551156] pnp 00:0c: [mem 0xdf800000-0xdfffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551200] system 00:0c: [mem 0x000d1000-0x000d3fff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551202] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551203] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551205] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551206] system 00:0c: [mem 0xdf780000-0xdf7dffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551208] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551209] system 00:0c: [mem 0x00100000-0xdf77ffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551211] system 00:0c: [mem 0xdf7e0000-0xdf7fffff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551212] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551214] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551215] system 00:0c: [mem 0xfed20000-0xfed8ffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551217] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551218] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551220] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551221] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551223] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551224] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551226] system 00:0c: [mem 0xdf800000-0xdfffffff] could not be reserved
Aug 29 12:41:26 ltspserver kernel: [    0.551228] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.551238] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.551261] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
Aug 29 12:41:26 ltspserver kernel: [    0.551264] pnp: PnP ACPI: found 14 devices
Aug 29 12:41:26 ltspserver kernel: [    0.551265] ACPI: ACPI bus type pnp unregistered
Aug 29 12:41:26 ltspserver kernel: [    0.551268] PnPBIOS: Disabled by ACPI PNP
Aug 29 12:41:26 ltspserver kernel: [    0.587098] PCI: max bus depth: 2 pci_try_num: 3
Aug 29 12:41:26 ltspserver kernel: [    0.587165] pci 0000:00:1c.7: BAR 15: assigned [mem 0xf4000000-0xf40fffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587167] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf4100000-0xf42fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587169] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4300000-0xf44fffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587172] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587174] pci 0000:01:00.0: BAR 6: assigned [mem 0xfbb00000-0xfbb1ffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587176] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Aug 29 12:41:26 ltspserver kernel: [    0.587178] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587180] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbbfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587182] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587185] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug 29 12:41:26 ltspserver kernel: [    0.587187] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587191] pci 0000:00:1c.0:   bridge window [mem 0xf4100000-0xf42fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587194] pci 0000:00:1c.0:   bridge window [mem 0xf4300000-0xf44fffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587199] pci 0000:03:00.0: PCI bridge to [bus 04-04]
Aug 29 12:41:26 ltspserver kernel: [    0.587203] pci 0000:03:00.0:   bridge window [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.587211] pci 0000:03:00.0:   bridge window [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587227] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
Aug 29 12:41:26 ltspserver kernel: [    0.587229] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.587233] pci 0000:00:1c.3:   bridge window [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587240] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
Aug 29 12:41:26 ltspserver kernel: [    0.587244] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587251] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
Aug 29 12:41:26 ltspserver kernel: [    0.587255] pci 0000:00:1c.5:   bridge window [mem 0xfbe00000-0xfbefffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587262] pci 0000:00:1c.6: PCI bridge to [bus 07-07]
Aug 29 12:41:26 ltspserver kernel: [    0.587264] pci 0000:00:1c.6:   bridge window [io  0xd000-0xdfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587270] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587276] pci 0000:08:00.0: BAR 6: assigned [mem 0xf4000000-0xf400ffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587277] pci 0000:00:1c.7: PCI bridge to [bus 08-08]
Aug 29 12:41:26 ltspserver kernel: [    0.587279] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587283] pci 0000:00:1c.7:   bridge window [mem 0xfbc00000-0xfbcfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587287] pci 0000:00:1c.7:   bridge window [mem 0xf4000000-0xf40fffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587303] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [    0.587306] pci 0000:00:01.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587310] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Aug 29 12:41:26 ltspserver kernel: [    0.587312] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [    0.587316] pci 0000:00:1c.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587324] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    0.587327] pci 0000:00:1c.3: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587335] pci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    0.587341] pci 0000:03:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587347] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [    0.587350] pci 0000:00:1c.4: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587357] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 29 12:41:26 ltspserver kernel: [    0.587360] pci 0000:00:1c.5: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587367] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 29 12:41:26 ltspserver kernel: [    0.587370] pci 0000:00:1c.6: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587375] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    0.587378] pci 0000:00:1c.7: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.587380] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug 29 12:41:26 ltspserver kernel: [    0.587382] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587383] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587384] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587386] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587387] pci_bus 0000:00: resource 9 [mem 0xe0000000-0xfebfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587389] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587390] pci_bus 0000:01: resource 1 [mem 0xfbb00000-0xfbbfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587391] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587393] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587394] pci_bus 0000:02: resource 1 [mem 0xf4100000-0xf42fffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587395] pci_bus 0000:02: resource 2 [mem 0xf4300000-0xf44fffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587397] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.587398] pci_bus 0000:03: resource 1 [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587399] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Aug 29 12:41:26 ltspserver kernel: [    0.587401] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587402] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587403] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587404] pci_bus 0000:03: resource 8 [mem 0xfed40000-0xfed44fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587406] pci_bus 0000:03: resource 9 [mem 0xe0000000-0xfebfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587407] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.587408] pci_bus 0000:04: resource 1 [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587410] pci_bus 0000:04: resource 4 [io  0xe000-0xefff]
Aug 29 12:41:26 ltspserver kernel: [    0.587411] pci_bus 0000:04: resource 5 [mem 0xf7000000-0xfaffffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587412] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
Aug 29 12:41:26 ltspserver kernel: [    0.587413] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587415] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587416] pci_bus 0000:04: resource 11 [mem 0x000c0000-0x000dffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587417] pci_bus 0000:04: resource 12 [mem 0xfed40000-0xfed44fff]
Aug 29 12:41:26 ltspserver kernel: [    0.587419] pci_bus 0000:04: resource 13 [mem 0xe0000000-0xfebfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587420] pci_bus 0000:05: resource 1 [mem 0xfba00000-0xfbafffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587422] pci_bus 0000:06: resource 1 [mem 0xfbe00000-0xfbefffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587423] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587424] pci_bus 0000:07: resource 2 [mem 0xfbd00000-0xfbdfffff 64bit pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587426] pci_bus 0000:08: resource 0 [io  0xc000-0xcfff]
Aug 29 12:41:26 ltspserver kernel: [    0.587427] pci_bus 0000:08: resource 1 [mem 0xfbc00000-0xfbcfffff]
Aug 29 12:41:26 ltspserver kernel: [    0.587428] pci_bus 0000:08: resource 2 [mem 0xf4000000-0xf40fffff pref]
Aug 29 12:41:26 ltspserver kernel: [    0.587450] NET: Registered protocol family 2
Aug 29 12:41:26 ltspserver kernel: [    0.587486] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.587578] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.587724] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.587785] TCP: Hash tables configured (established 131072 bind 65536)
Aug 29 12:41:26 ltspserver kernel: [    0.587786] TCP reno registered
Aug 29 12:41:26 ltspserver kernel: [    0.587788] UDP hash table entries: 512 (order: 2, 16384 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.587791] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.587827] NET: Registered protocol family 1
Aug 29 12:41:26 ltspserver kernel: [    0.587839] pci 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 29 12:41:26 ltspserver kernel: [    0.601688] pci 0000:00:1a.0: PCI INT C disabled
Aug 29 12:41:26 ltspserver kernel: [    0.601713] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 29 12:41:26 ltspserver kernel: [    0.617666] pci 0000:00:1d.0: PCI INT A disabled
Aug 29 12:41:26 ltspserver kernel: [    0.617677] pci 0000:01:00.0: Boot video device
Aug 29 12:41:26 ltspserver kernel: [    0.617701] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [    0.617725] pci 0000:05:00.0: PCI INT A disabled
Aug 29 12:41:26 ltspserver kernel: [    0.617732] pci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 29 12:41:26 ltspserver kernel: [    0.617753] pci 0000:06:00.0: PCI INT A disabled
Aug 29 12:41:26 ltspserver kernel: [    0.617761] PCI: CLS 4 bytes, default 64
Aug 29 12:41:26 ltspserver kernel: [    0.618059] audit: initializing netlink socket (disabled)
Aug 29 12:41:26 ltspserver kernel: [    0.618065] type=2000 audit(1346244074.460:1): initialized
Aug 29 12:41:26 ltspserver kernel: [    0.640585] highmem bounce pool size: 64 pages
Aug 29 12:41:26 ltspserver kernel: [    0.640589] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug 29 12:41:26 ltspserver kernel: [    0.658134] VFS: Disk quotas dquot_6.5.2
Aug 29 12:41:26 ltspserver kernel: [    0.658176] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 29 12:41:26 ltspserver kernel: [    0.658487] fuse init (API version 7.17)
Aug 29 12:41:26 ltspserver kernel: [    0.658542] msgmni has been set to 1337
Aug 29 12:41:26 ltspserver kernel: [    0.658755] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 29 12:41:26 ltspserver kernel: [    0.658773] io scheduler noop registered
Aug 29 12:41:26 ltspserver kernel: [    0.658774] io scheduler deadline registered
Aug 29 12:41:26 ltspserver kernel: [    0.658777] io scheduler cfq registered (default)
Aug 29 12:41:26 ltspserver kernel: [    0.658848] pcieport 0000:00:01.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    0.658868] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [    0.659099] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 29 12:41:26 ltspserver kernel: [    0.659113] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 29 12:41:26 ltspserver kernel: [    0.659164] intel_idle: MWAIT substates: 0x1120
Aug 29 12:41:26 ltspserver kernel: [    0.659166] intel_idle: v0.4 model 0x2A
Aug 29 12:41:26 ltspserver kernel: [    0.659166] intel_idle: lapic_timer_reliable_states 0xffffffff
Aug 29 12:41:26 ltspserver kernel: [    0.659222] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Aug 29 12:41:26 ltspserver kernel: [    0.659225] ACPI: Power Button [PWRB]
Aug 29 12:41:26 ltspserver kernel: [    0.659255] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Aug 29 12:41:26 ltspserver kernel: [    0.659256] ACPI: Power Button [PWRF]
Aug 29 12:41:26 ltspserver kernel: [    0.662613] ERST: Table is not found!
Aug 29 12:41:26 ltspserver kernel: [    0.662615] GHES: HEST is not enabled!
Aug 29 12:41:26 ltspserver kernel: [    0.662650] isapnp: Scanning for PnP cards...
Aug 29 12:41:26 ltspserver kernel: [    0.662661] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug 29 12:41:26 ltspserver kernel: [    0.683033] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 29 12:41:26 ltspserver kernel: [    0.696409] Freeing initrd memory: 13852k freed
Aug 29 12:41:26 ltspserver kernel: [    1.017335] isapnp: No Plug & Play device found
Aug 29 12:41:26 ltspserver kernel: [    1.073647] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 29 12:41:26 ltspserver kernel: [    1.109273] Linux agpgart interface v0.103
Aug 29 12:41:26 ltspserver kernel: [    1.110251] brd: module loaded
Aug 29 12:41:26 ltspserver kernel: [    1.110691] loop: module loaded
Aug 29 12:41:26 ltspserver kernel: [    1.110774] ahci 0000:08:00.0: version 3.0
Aug 29 12:41:26 ltspserver kernel: [    1.110783] ahci 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    1.110836] ahci 0000:08:00.0: irq 41 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [    1.110894] ahci 0000:08:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl IDE mode
Aug 29 12:41:26 ltspserver kernel: [    1.110897] ahci 0000:08:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
Aug 29 12:41:26 ltspserver kernel: [    1.110901] ahci 0000:08:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.111080] scsi0 : ahci
Aug 29 12:41:26 ltspserver kernel: [    1.111128] scsi1 : ahci
Aug 29 12:41:26 ltspserver kernel: [    1.111156] ata1: SATA max UDMA/133 abar m512@0xfbcff000 port 0xfbcff100 irq 41
Aug 29 12:41:26 ltspserver kernel: [    1.111158] ata2: SATA max UDMA/133 abar m512@0xfbcff000 port 0xfbcff180 irq 41
Aug 29 12:41:26 ltspserver kernel: [    1.111182] ata_piix 0000:00:1f.2: version 2.13
Aug 29 12:41:26 ltspserver kernel: [    1.111191] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    1.111194] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Aug 29 12:41:26 ltspserver kernel: [    1.111216] ata_piix 0000:00:1f.2: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.111372] scsi2 : ata_piix
Aug 29 12:41:26 ltspserver kernel: [    1.111411] scsi3 : ata_piix
Aug 29 12:41:26 ltspserver kernel: [    1.111695] ata3: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 19
Aug 29 12:41:26 ltspserver kernel: [    1.111699] ata4: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 19
Aug 29 12:41:26 ltspserver kernel: [    1.111711] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [    1.111715] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Aug 29 12:41:26 ltspserver kernel: [    1.111741] ata_piix 0000:00:1f.5: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.111862] scsi4 : ata_piix
Aug 29 12:41:26 ltspserver kernel: [    1.111906] scsi5 : ata_piix
Aug 29 12:41:26 ltspserver kernel: [    1.112125] ata5: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
Aug 29 12:41:26 ltspserver kernel: [    1.112128] ata6: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
Aug 29 12:41:26 ltspserver kernel: [    1.112335] Fixed MDIO Bus: probed
Aug 29 12:41:26 ltspserver kernel: [    1.112347] tun: Universal TUN/TAP device driver, 1.6
Aug 29 12:41:26 ltspserver kernel: [    1.112348] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 29 12:41:26 ltspserver kernel: [    1.112377] PPP generic driver version 2.4.2
Aug 29 12:41:26 ltspserver kernel: [    1.112440] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 29 12:41:26 ltspserver kernel: [    1.112450] ehci_hcd 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 29 12:41:26 ltspserver kernel: [    1.112460] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.112462] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.112488] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Aug 29 12:41:26 ltspserver kernel: [    1.112507] ehci_hcd 0000:00:1a.0: debug port 2
Aug 29 12:41:26 ltspserver kernel: [    1.116378] ehci_hcd 0000:00:1a.0: cache line size of 4 is not supported
Aug 29 12:41:26 ltspserver kernel: [    1.116389] ehci_hcd 0000:00:1a.0: irq 18, io mem 0xfbffe000
Aug 29 12:41:26 ltspserver kernel: [    1.129013] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Aug 29 12:41:26 ltspserver kernel: [    1.129144] hub 1-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.129146] hub 1-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.129187] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 29 12:41:26 ltspserver kernel: [    1.129195] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.129197] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.129223] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug 29 12:41:26 ltspserver kernel: [    1.129239] ehci_hcd 0000:00:1d.0: debug port 2
Aug 29 12:41:26 ltspserver kernel: [    1.133110] ehci_hcd 0000:00:1d.0: cache line size of 4 is not supported
Aug 29 12:41:26 ltspserver kernel: [    1.133120] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbffd000
Aug 29 12:41:26 ltspserver kernel: [    1.148987] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Aug 29 12:41:26 ltspserver kernel: [    1.149104] hub 2-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.149106] hub 2-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.149144] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 29 12:41:26 ltspserver kernel: [    1.149152] uhci_hcd: USB Universal Host Controller Interface driver
Aug 29 12:41:26 ltspserver kernel: [    1.149172] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [    1.149184] xhci_hcd 0000:05:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.149187] xhci_hcd 0000:05:00.0: xHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.149213] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 3
Aug 29 12:41:26 ltspserver kernel: [    1.149325] xhci_hcd 0000:05:00.0: irq 16, io mem 0xfbaf8000
Aug 29 12:41:26 ltspserver kernel: [    1.149394] xhci_hcd 0000:05:00.0: irq 42 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [    1.149487] xHCI xhci_add_endpoint called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.149488] xHCI xhci_check_bandwidth called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.149504] hub 3-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.149509] hub 3-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.149548] xhci_hcd 0000:05:00.0: xHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.149571] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 4
Aug 29 12:41:26 ltspserver kernel: [    1.149620] xHCI xhci_add_endpoint called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.149621] xHCI xhci_check_bandwidth called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.149636] hub 4-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.149641] hub 4-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.196934] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 29 12:41:26 ltspserver kernel: [    1.196955] xhci_hcd 0000:06:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    1.196959] xhci_hcd 0000:06:00.0: xHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.197009] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 5
Aug 29 12:41:26 ltspserver kernel: [    1.197132] xhci_hcd 0000:06:00.0: irq 17, io mem 0xfbef8000
Aug 29 12:41:26 ltspserver kernel: [    1.197198] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [    1.197287] xHCI xhci_add_endpoint called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.197288] xHCI xhci_check_bandwidth called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.197302] hub 5-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.197307] hub 5-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.197344] xhci_hcd 0000:06:00.0: xHCI Host Controller
Aug 29 12:41:26 ltspserver kernel: [    1.197367] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 6
Aug 29 12:41:26 ltspserver kernel: [    1.197422] xHCI xhci_add_endpoint called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.197423] xHCI xhci_check_bandwidth called for root hub
Aug 29 12:41:26 ltspserver kernel: [    1.197437] hub 6-0:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.197442] hub 6-0:1.0: 2 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.228997] usbcore: registered new interface driver libusual
Aug 29 12:41:26 ltspserver kernel: [    1.229027] i8042: PNP: No PS/2 controller found. Probing ports directly.
Aug 29 12:41:26 ltspserver kernel: [    1.263366] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
Aug 29 12:41:26 ltspserver kernel: [    1.263367] i8042: If AUX port is really absent please use the 'i8042.noaux' option
Aug 29 12:41:26 ltspserver kernel: [    1.428674] ata2: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.428714] ata1: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.439372] ata5: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.440610] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Aug 29 12:41:26 ltspserver kernel: [    1.450077] ata6: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.512605] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 29 12:41:26 ltspserver kernel: [    1.512673] mousedev: PS/2 mouse device common for all mice
Aug 29 12:41:26 ltspserver kernel: [    1.512759] rtc_cmos 00:04: RTC can wake from S4
Aug 29 12:41:26 ltspserver kernel: [    1.512850] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Aug 29 12:41:26 ltspserver anacron[1053]: Anacron 2.3 started on 2012-08-29
Aug 29 12:41:26 ltspserver kernel: [    1.512874] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Aug 29 12:41:26 ltspserver kernel: [    1.512912] device-mapper: uevent: version 1.0.3
Aug 29 12:41:26 ltspserver kernel: [    1.512957] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Aug 29 12:41:26 ltspserver kernel: [    1.512976] EISA: Probing bus 0 at eisa.0
Aug 29 12:41:26 ltspserver kernel: [    1.512977] EISA: Cannot allocate resource for mainboard
Aug 29 12:41:26 ltspserver kernel: [    1.512978] Cannot allocate resource for EISA slot 1
Aug 29 12:41:26 ltspserver kernel: [    1.512979] Cannot allocate resource for EISA slot 2
Aug 29 12:41:26 ltspserver kernel: [    1.512980] Cannot allocate resource for EISA slot 3
Aug 29 12:41:26 ltspserver kernel: [    1.512981] Cannot allocate resource for EISA slot 4
Aug 29 12:41:26 ltspserver kernel: [    1.512982] Cannot allocate resource for EISA slot 5
Aug 29 12:41:26 ltspserver kernel: [    1.512983] Cannot allocate resource for EISA slot 6
Aug 29 12:41:26 ltspserver kernel: [    1.512984] Cannot allocate resource for EISA slot 7
Aug 29 12:41:26 ltspserver kernel: [    1.512985] Cannot allocate resource for EISA slot 8
Aug 29 12:41:26 ltspserver kernel: [    1.512986] EISA: Detected 0 cards.
Aug 29 12:41:26 ltspserver kernel: [    1.512991] cpufreq-nforce2: No nForce2 chipset.
Aug 29 12:41:26 ltspserver kernel: [    1.513054] cpuidle: using governor ladder
Aug 29 12:41:26 ltspserver kernel: [    1.513156] cpuidle: using governor menu
Aug 29 12:41:26 ltspserver kernel: [    1.513158] EFI Variables Facility v0.08 2004-May-17
Aug 29 12:41:26 ltspserver kernel: [    1.513269] TCP cubic registered
Aug 29 12:41:26 ltspserver kernel: [    1.513334] NET: Registered protocol family 10
Aug 29 12:41:26 ltspserver kernel: [    1.513597] NET: Registered protocol family 17
Aug 29 12:41:26 ltspserver kernel: [    1.513600] Registering the dns_resolver key type
Aug 29 12:41:26 ltspserver kernel: [    1.513611] Using IPI No-Shortcut mode
Aug 29 12:41:26 ltspserver kernel: [    1.513758] PM: Hibernation image not present or could not be loaded.
Aug 29 12:41:26 ltspserver kernel: [    1.513767] registered taskstats version 1
Aug 29 12:41:26 ltspserver kernel: [    1.527374]   Magic number: 8:596:684
Aug 29 12:41:26 ltspserver kernel: [    1.527399] mem full: hash matches
Aug 29 12:41:26 ltspserver kernel: [    1.527474] rtc_cmos 00:04: setting system clock to 2012-08-29 12:41:15 UTC (1346244075)
Aug 29 12:41:26 ltspserver kernel: [    1.528147] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 29 12:41:26 ltspserver kernel: [    1.528148] EDD information not available.
Aug 29 12:41:26 ltspserver kernel: [    1.581312] hub 1-1:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.581355] hub 1-1:1.0: 6 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.616435] Refined TSC clocksource calibration: 3309.719 MHz.
Aug 29 12:41:26 ltspserver kernel: [    1.616441] Switching to clocksource tsc
Aug 29 12:41:26 ltspserver kernel: [    1.692343] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Aug 29 12:41:26 ltspserver kernel: [    1.825005] hub 2-1:1.0: USB hub found
Aug 29 12:41:26 ltspserver kernel: [    1.825049] hub 2-1:1.0: 8 ports detected
Aug 29 12:41:26 ltspserver kernel: [    1.904097] ata4.00: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.904111] ata4.01: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.904235] ata3.00: SATA link down (SStatus 0 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.904247] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 29 12:41:26 ltspserver kernel: [    1.915206] ata4.00: ATA-8: WDC WD5000AAKX-329BA0, 15.01H15, max UDMA/133
Aug 29 12:41:26 ltspserver kernel: [    1.915211] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug 29 12:41:26 ltspserver kernel: [    1.920295] ata3.01: ATAPI: ASUS    DRW-1814BLT, 1.13, max UDMA/66
Aug 29 12:41:26 ltspserver kernel: [    1.928443] ata4.00: configured for UDMA/133
Aug 29 12:41:26 ltspserver kernel: [    1.936037] usb 5-1: new high-speed USB device number 2 using xhci_hcd
Aug 29 12:41:26 ltspserver kernel: [    1.936287] ata3.01: configured for UDMA/66
Aug 29 12:41:26 ltspserver kernel: [    1.937837] scsi 2:0:1:0: CD-ROM            ASUS     DRW-1814BLT      1.13 PQ: 0 ANSI: 5
Aug 29 12:41:26 ltspserver kernel: [    1.940456] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 29 12:41:26 ltspserver kernel: [    1.940460] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 29 12:41:26 ltspserver kernel: [    1.940639] sr 2:0:1:0: Attached scsi CD-ROM sr0
Aug 29 12:41:26 ltspserver kernel: [    1.940736] sr 2:0:1:0: Attached scsi generic sg0 type 5
Aug 29 12:41:26 ltspserver kernel: [    1.941014] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-3 15.0 PQ: 0 ANSI: 5
Aug 29 12:41:26 ltspserver kernel: [    1.941159] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Aug 29 12:41:26 ltspserver kernel: [    1.941162] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 29 12:41:26 ltspserver kernel: [    1.941393] sd 3:0:0:0: [sda] Write Protect is off
Aug 29 12:41:26 ltspserver kernel: [    1.941395] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 29 12:41:26 ltspserver kernel: [    1.941483] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 29 12:41:26 ltspserver kernel: [    1.977457]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
Aug 29 12:41:26 ltspserver kernel: [    1.978441] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 29 12:41:26 ltspserver kernel: [    1.978604] Freeing unused kernel memory: 740k freed
Aug 29 12:41:26 ltspserver kernel: [    1.978745] Write protecting the kernel text: 5816k
Aug 29 12:41:26 ltspserver kernel: [    1.978759] Write protecting the kernel read-only data: 2376k
Aug 29 12:41:26 ltspserver kernel: [    1.978760] NX-protecting the kernel data: 4424k
Aug 29 12:41:26 ltspserver kernel: [    2.004628] r8168 Gigabit Ethernet driver 8.028.00-NAPI loaded
Aug 29 12:41:26 ltspserver kernel: [    2.004644] r8168 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 29 12:41:26 ltspserver kernel: [    2.004665] r8168 0000:07:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [    2.004729] r8168 0000:07:00.0: irq 44 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [    2.005014] eth%d: RTL8168E-VL/8111E-VL at 0xf841c000, 50:e5:49:4a:26:bf, IRQ 44
Aug 29 12:41:26 ltspserver kernel: [    2.162696] firewire_ohci 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 29 12:41:26 ltspserver kernel: [    2.182265] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
Aug 29 12:41:26 ltspserver kernel: [    2.182267] eth0: Identified chip type is 'RTL8168E-VL/8111E-VL'.
Aug 29 12:41:26 ltspserver kernel: [    2.182268] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
Aug 29 12:41:26 ltspserver kernel: [    2.182269]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
Aug 29 12:41:26 ltspserver kernel: [    2.182270]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
Aug 29 12:41:26 ltspserver kernel: [    2.215686] firewire_ohci: Added fw-ohci device 0000:04:02.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Aug 29 12:41:26 ltspserver kernel: [    2.498138] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
Aug 29 12:41:26 ltspserver kernel: [    2.498140] EXT4-fs (sda6): write access will be enabled during recovery
Aug 29 12:41:26 ltspserver kernel: [    2.715161] firewire_core: created device fw0: GUID 0049e55098cc4a00, S400
Aug 29 12:41:26 ltspserver kernel: [    3.989271] EXT4-fs (sda6): recovery complete
Aug 29 12:41:26 ltspserver kernel: [    3.989705] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Aug 29 12:41:26 ltspserver kernel: [   11.064789] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 29 12:41:26 ltspserver kernel: [   11.103483] lp: driver loaded but no devices found
Aug 29 12:41:26 ltspserver kernel: [   11.108438] mei: module is from the staging directory, the quality is unknown, you have been warned.
Aug 29 12:41:26 ltspserver kernel: [   11.108666] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [   11.108671] mei 0000:00:16.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [   11.108716] mei 0000:00:16.0: irq 45 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [   11.112257] wmi: Mapper loaded
Aug 29 12:41:26 ltspserver kernel: [   11.118212] Adding 1636348k swap on /dev/sda5.  Priority:-1 extents:1 across:1636348k 
Aug 29 12:41:26 ltspserver kernel: [   11.133301] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug 29 12:41:26 ltspserver kernel: [   11.133304] Disabling lock debugging due to kernel taint
Aug 29 12:41:26 ltspserver kernel: [   11.135523] Linux video capture interface: v2.00
Aug 29 12:41:26 ltspserver kernel: [   11.137347] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
Aug 29 12:41:26 ltspserver kernel: [   11.137383] cx8800 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [   11.138196] cx88[0]: subsystem: 0070:9400, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected], frontend(s): 1
Aug 29 12:41:26 ltspserver kernel: [   11.138198] cx88[0]: TV tuner type 63, Radio tuner type -1
Aug 29 12:41:26 ltspserver kernel: [   11.141822] IR NEC protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.144089] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 29 12:41:26 ltspserver kernel: [   11.144127] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [   11.144146] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [   11.147059] IR RC5(x) protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.151758] [fglrx] Maximum main memory to use for locked dma buffers: 15781 MBytes.
Aug 29 12:41:26 ltspserver kernel: [   11.151896] IR RC6 protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.151904] [fglrx]   vendor: 1002 device: 6819 count: 1
Aug 29 12:41:26 ltspserver kernel: [   11.152170] [fglrx] ioport: bar 4, base 0xbe00, size: 0x100
Aug 29 12:41:26 ltspserver kernel: [   11.152178] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 29 12:41:26 ltspserver kernel: [   11.152181] pci 0000:01:00.0: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [   11.152427] [fglrx] Kernel PAT support is enabled
Aug 29 12:41:26 ltspserver kernel: [   11.152437] [fglrx] module loaded - fglrx 8.98.2 [Jul 27 2012] with 1 minors
Aug 29 12:41:26 ltspserver kernel: [   11.154263] IR JVC protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.156971] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
Aug 29 12:41:26 ltspserver kernel: [   11.160985] IR Sony protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.164066] IR MCE Keyboard/mouse protocol handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.167277] lirc_dev: IR Remote Control driver registered, major 248 
Aug 29 12:41:26 ltspserver kernel: [   11.167379] IR LIRC bridge handler initialized
Aug 29 12:41:26 ltspserver kernel: [   11.181744] hda_codec: ALC889: BIOS auto-probing.
Aug 29 12:41:26 ltspserver kernel: [   11.189814] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
Aug 29 12:41:26 ltspserver kernel: [   11.189938] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
Aug 29 12:41:26 ltspserver kernel: [   11.189982] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Aug 29 12:41:26 ltspserver kernel: [   11.190022] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Aug 29 12:41:26 ltspserver kernel: [   11.190059] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Aug 29 12:41:26 ltspserver kernel: [   11.190097] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Aug 29 12:41:26 ltspserver kernel: [   11.190134] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Aug 29 12:41:26 ltspserver kernel: [   11.190171] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Aug 29 12:41:26 ltspserver kernel: [   11.190325] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 29 12:41:26 ltspserver kernel: [   11.190370] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
Aug 29 12:41:26 ltspserver kernel: [   11.190385] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Aug 29 12:41:26 ltspserver kernel: [   11.193719] type=1400 audit(1346208085.173:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=605 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.193726] type=1400 audit(1346208085.173:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=667 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.193999] type=1400 audit(1346208085.173:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=605 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.194006] type=1400 audit(1346208085.173:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.194156] type=1400 audit(1346208085.173:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=605 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.194163] type=1400 audit(1346208085.173:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   11.231857] cx2388x alsa driver version 0.0.9 loaded
Aug 29 12:41:26 ltspserver kernel: [   11.257040] i2c-core: driver [tuner] using legacy suspend method
Aug 29 12:41:26 ltspserver kernel: [   11.257049] i2c-core: driver [tuner] using legacy resume method
Aug 29 12:41:26 ltspserver kernel: [   11.270478] tda9887 0-0043: creating new instance
Aug 29 12:41:26 ltspserver kernel: [   11.270480] tda9887 0-0043: tda988[5/6/7] found
Aug 29 12:41:26 ltspserver kernel: [   11.271678] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
Aug 29 12:41:26 ltspserver kernel: [   11.273791] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
Aug 29 12:41:26 ltspserver kernel: [   11.331740] tveeprom 0-0050: Hauppauge model 94500, rev C2A0, serial# 488852
Aug 29 12:41:26 ltspserver kernel: [   11.331742] tveeprom 0-0050: MAC address is 00:0d:fe:07:75:94
Aug 29 12:41:26 ltspserver kernel: [   11.331743] tveeprom 0-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
Aug 29 12:41:26 ltspserver kernel: [   11.331745] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Aug 29 12:41:26 ltspserver kernel: [   11.331746] tveeprom 0-0050: audio processor is CX882 (idx 33)
Aug 29 12:41:26 ltspserver kernel: [   11.331747] tveeprom 0-0050: decoder processor is CX882 (idx 25)
Aug 29 12:41:26 ltspserver kernel: [   11.331749] tveeprom 0-0050: has radio
Aug 29 12:41:26 ltspserver kernel: [   11.331750] cx88[0]: warning: unknown hauppauge model #94500
Aug 29 12:41:26 ltspserver kernel: [   11.331751] cx88[0]: hauppauge eeprom: model=94500
Aug 29 12:41:26 ltspserver kernel: [   11.336357] tuner-simple 0-0061: creating new instance
Aug 29 12:41:26 ltspserver kernel: [   11.336359] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Aug 29 12:41:26 ltspserver kernel: [   11.368047] Registered IR keymap rc-hauppauge
Aug 29 12:41:26 ltspserver kernel: [   11.368165] input: cx88 IR (Hauppauge WinTV-HVR110 as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/rc/rc0/input10
Aug 29 12:41:26 ltspserver kernel: [   11.368263] rc0: cx88 IR (Hauppauge WinTV-HVR110 as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/rc/rc0
Aug 29 12:41:26 ltspserver kernel: [   11.368381] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input11
Aug 29 12:41:26 ltspserver kernel: [   11.368476] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
Aug 29 12:41:26 ltspserver kernel: [   11.368482] cx88[0]/0: found at 0000:04:00.0, rev: 5, irq: 19, latency: 32, mmio: 0xf7000000
Aug 29 12:41:26 ltspserver kernel: [   11.372193] cx88[0]/0: registered device video0 [v4l2]
Aug 29 12:41:26 ltspserver kernel: [   11.372215] cx88[0]/0: registered device vbi0
Aug 29 12:41:26 ltspserver kernel: [   11.372254] cx88[0]/0: registered device radio0
Aug 29 12:41:26 ltspserver kernel: [   11.372313] cx88[0]/2: cx2388x 8802 Driver Manager
Aug 29 12:41:26 ltspserver kernel: [   11.372325] cx88-mpeg driver manager 0000:04:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [   11.372338] cx88[0]/2: found at 0000:04:00.2, rev: 5, irq: 19, latency: 32, mmio: 0xf8000000
Aug 29 12:41:26 ltspserver kernel: [   11.372442] cx88_audio 0000:04:00.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Aug 29 12:41:26 ltspserver kernel: [   11.372462] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
Aug 29 12:41:26 ltspserver kernel: [   11.374830] cx88/2: cx2388x dvb driver version 0.0.9 loaded
Aug 29 12:41:26 ltspserver kernel: [   11.374832] cx88/2: registering cx8802 driver, type: dvb access: shared
Aug 29 12:41:26 ltspserver kernel: [   11.374834] cx88[0]/2: subsystem: 0070:9400, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
Aug 29 12:41:26 ltspserver kernel: [   11.376323] cx88[0]/2: cx2388x based DVB/ATSC card
Aug 29 12:41:26 ltspserver kernel: [   11.376324] cx8802_alloc_frontends() allocating 1 frontend(s)
Aug 29 12:41:26 ltspserver kernel: [   11.382093] tuner-simple 0-0061: attaching existing instance
Aug 29 12:41:26 ltspserver kernel: [   11.382095] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Aug 29 12:41:26 ltspserver kernel: [   11.387685] DVB: registering new adapter (cx88[0])
Aug 29 12:41:26 ltspserver kernel: [   11.387687] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...
Aug 29 12:41:26 ltspserver kernel: [   11.709501] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709503] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709504] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709504] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709505] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709506] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709507] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709507] Too many HDMI devices
Aug 29 12:41:26 ltspserver kernel: [   11.709597] hda-codec: out of range cmd 0:0:7c34:707:0
Aug 29 12:41:26 ltspserver kernel: [   11.709599] hda-codec: out of range cmd 0:0:7c34:708:85
Aug 29 12:41:26 ltspserver kernel: [   11.709838] hda-codec: out of range cmd 0:0:7c34:f00:c
Aug 29 12:41:26 ltspserver kernel: [   11.709839] hda-codec: out of range cmd 0:0:7c34:709:0
Aug 29 12:41:26 ltspserver kernel: [   11.709840] hda-codec: out of range cmd 0:0:7c34:f09:0
Aug 29 12:41:26 ltspserver kernel: [   11.709902] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
Aug 29 12:41:26 ltspserver kernel: [   11.709918] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Aug 29 12:41:26 ltspserver kernel: [   11.709935] HDMI status: Codec=0 Pin=7 Presence_Detect=0 ELD_Valid=0
Aug 29 12:41:26 ltspserver kernel: [   11.709952] HDMI status: Codec=0 Pin=9 Presence_Detect=0 ELD_Valid=0
Aug 29 12:41:26 ltspserver kernel: [   11.709971] HDMI status: Codec=0 Pin=31796 Presence_Detect=1 ELD_Valid=1
Aug 29 12:41:26 ltspserver kernel: [   11.709972] hda-codec: out of range cmd 0:0:7c34:f2e:8
Aug 29 12:41:26 ltspserver kernel: [   11.709974] hda_codec: cannot build controls for #0 (error -16)
Aug 29 12:41:26 ltspserver kernel: [   11.773535] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
Aug 29 12:41:26 ltspserver kernel: [   11.773537] vesafb: scrolling: redraw
Aug 29 12:41:26 ltspserver kernel: [   11.773538] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Aug 29 12:41:26 ltspserver kernel: [   11.775508] vesafb: framebuffer at 0xe0000000, mapped to 0xf9d00000, using 5120k, total 5120k
Aug 29 12:41:26 ltspserver kernel: [   11.775654] Console: switching to colour frame buffer device 160x64
Aug 29 12:41:26 ltspserver kernel: [   11.775678] fb0: VESA VGA frame buffer device
Aug 29 12:41:26 ltspserver kernel: [   11.945626] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Aug 29 12:41:26 ltspserver kernel: [   12.503889] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Aug 29 12:41:26 ltspserver kernel: [   12.565889] init: failsafe main process (852) killed by TERM signal
Aug 29 12:41:26 ltspserver kernel: [   12.610196] ppdev: user-space parallel port driver
Aug 29 12:41:26 ltspserver kernel: [   12.623715] Bluetooth: Core ver 2.16
Aug 29 12:41:26 ltspserver kernel: [   12.623728] NET: Registered protocol family 31
Aug 29 12:41:26 ltspserver kernel: [   12.623729] Bluetooth: HCI device and connection manager initialized
Aug 29 12:41:26 ltspserver kernel: [   12.623730] Bluetooth: HCI socket layer initialized
Aug 29 12:41:26 ltspserver kernel: [   12.623731] Bluetooth: L2CAP socket layer initialized
Aug 29 12:41:26 ltspserver kernel: [   12.624365] type=1400 audit(1346208086.605:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=925 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   12.624369] Bluetooth: SCO socket layer initialized
Aug 29 12:41:26 ltspserver kernel: [   12.624690] type=1400 audit(1346208086.605:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=925 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   12.625490] Bluetooth: RFCOMM TTY layer initialized
Aug 29 12:41:26 ltspserver kernel: [   12.625493] Bluetooth: RFCOMM socket layer initialized
Aug 29 12:41:26 ltspserver kernel: [   12.625494] Bluetooth: RFCOMM ver 1.11
Aug 29 12:41:26 ltspserver kernel: [   12.640511] type=1400 audit(1346208086.621:10): apparmor="STATUS" operation="profile_load" name="lxc-container-default" pid=966 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   12.640732] type=1400 audit(1346208086.621:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=965 comm="apparmor_parser"
Aug 29 12:41:26 ltspserver kernel: [   12.696347] Bridge firewalling registered
Aug 29 12:41:26 ltspserver kernel: [   12.699202] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 29 12:41:26 ltspserver kernel: [   12.700909] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 29 12:41:26 ltspserver kernel: [   12.808005] init: tftpd-hpa main process (1026) terminated with status 66
Aug 29 12:41:26 ltspserver kernel: [   12.808022] init: tftpd-hpa main process ended, respawning
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: init!
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: update_system_hostname
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPluginIfupdown: management mode: unmanaged
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.6/0000:07:00.0/net/eth0, iface: eth0)
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.6/0000:07:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lxcbr0, iface: lxcbr0)
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lxcbr0, iface: lxcbr0): no ifupdown configuration found.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: end _init.
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    Ifupdown: get unmanaged devices count: 0
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: (167332688) ... get_connections.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    SCPlugin-Ifupdown: (167332688) ... get_connections (managed=false): return empty list.
Aug 29 12:41:26 ltspserver NetworkManager[923]:    keyfile: parsing Wired connection 1 ... 
Aug 29 12:41:26 ltspserver NetworkManager[923]:    keyfile:     read connection 'Wired connection 1'
Aug 29 12:41:26 ltspserver NetworkManager[923]:    Ifupdown: get unmanaged devices count: 0
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> modem-manager is now available
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 29 12:41:26 ltspserver bluetoothd[900]: Failed to init gatt_example plugin
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> Networking is enabled by state file
Aug 29 12:41:26 ltspserver NetworkManager[923]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): carrier is OFF
Aug 29 12:41:26 ltspserver kernel: [   12.811195] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 29 12:41:26 ltspserver kernel: [   12.811197] Bluetooth: BNEP filters: protocol multicast
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): new Ethernet device (driver: 'r8168' ifindex: 2)
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): now managed
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): bringing up device.
Aug 29 12:41:26 ltspserver cron[1115]: (CRON) STARTUP (fork ok)
Aug 29 12:41:26 ltspserver cron[1115]: (CRON) INFO (Running @reboot jobs)
Aug 29 12:41:26 ltspserver kernel: [   12.837714] r8168: eth0: link down
Aug 29 12:41:26 ltspserver kernel: [   12.837847] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 29 12:41:26 ltspserver anacron[1053]: Normal exit (0 jobs run)
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): preparing device.
Aug 29 12:41:26 ltspserver NetworkManager[923]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 29 12:41:26 ltspserver NetworkManager[923]: <warn> /sys/devices/virtual/net/lxcbr0: couldn't determine device driver; ignoring...
Aug 29 12:41:26 ltspserver kernel: [   12.989483] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 29 12:41:26 ltspserver kernel: [   12.989603] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
Aug 29 12:41:26 ltspserver NetworkManager[923]: <warn> /sys/devices/virtual/net/lxcbr0: couldn't determine device driver; ignoring...
Aug 29 12:41:26 ltspserver kernel: [   12.990169] [fglrx] Firegl kernel thread PID: 1125
Aug 29 12:41:26 ltspserver kernel: [   12.990317] [fglrx] Firegl kernel thread PID: 1126
Aug 29 12:41:26 ltspserver kernel: [   12.990483] [fglrx] Firegl kernel thread PID: 1127
Aug 29 12:41:26 ltspserver kernel: [   12.990580] [fglrx] IRQ 48 Enabled
Aug 29 12:41:26 ltspserver dhcpd: 
Aug 29 12:41:26 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:26 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:26 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:26 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:26 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:26 ltspserver dhcpd: 
Aug 29 12:41:26 ltspserver dhcpd: 
Aug 29 12:41:26 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:26 ltspserver kernel: [   13.002941] init: isc-dhcp-server main process (1048) terminated with status 1
Aug 29 12:41:26 ltspserver kernel: [   13.002958] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:26 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.094941] init: isc-dhcp-server main process (1131) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.094959] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver udev-configure-printer: add /module/lp
Aug 29 12:41:27 ltspserver udev-configure-printer: Failed to get parent
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.182544] init: isc-dhcp-server main process (1138) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.182559] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.437685] init: isc-dhcp-server main process (1153) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.437701] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.537947] init: isc-dhcp-server main process (1202) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.537962] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver kernel: [   13.577637] [fglrx] Gart USWC size:1280 M.
Aug 29 12:41:27 ltspserver kernel: [   13.577639] [fglrx] Gart cacheable size:508 M.
Aug 29 12:41:27 ltspserver kernel: [   13.577642] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug 29 12:41:27 ltspserver kernel: [   13.577643] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Aug 29 12:41:27 ltspserver kernel: [   13.577644] [fglrx] Reserved FB block: Unshared offset:7ffef000, size:11000 
Aug 29 12:41:27 ltspserver anacron[1274]: Anacron 2.3 started on 2012-08-29
Aug 29 12:41:27 ltspserver anacron[1274]: Normal exit (0 jobs run)
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.613252] init: isc-dhcp-server main process (1248) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.613267] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.680344] init: isc-dhcp-server main process (1280) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.680359] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.781109] init: isc-dhcp-server main process (1391) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.781125] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.864875] init: isc-dhcp-server main process (1413) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.864898] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:27 ltspserver avahi-daemon[949]: Joining mDNS multicast group on interface lxcbr0.IPv6 with address fe80::2467:13ff:fe09:b0e5.
Aug 29 12:41:27 ltspserver avahi-daemon[949]: New relevant interface lxcbr0.IPv6 for mDNS.
Aug 29 12:41:27 ltspserver avahi-daemon[949]: Registering new address record for fe80::2467:13ff:fe09:b0e5 on lxcbr0.*.
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:27 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:27 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:27 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:27 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: 
Aug 29 12:41:27 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:27 ltspserver kernel: [   13.935372] init: isc-dhcp-server main process (1420) terminated with status 1
Aug 29 12:41:27 ltspserver kernel: [   13.935389] init: isc-dhcp-server main process ended, respawning
Aug 29 12:41:27 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:41:28 ltspserver dhcpd: 
Aug 29 12:41:28 ltspserver dhcpd: No subnet declaration for eth0 (no IPv4 addresses).
Aug 29 12:41:28 ltspserver dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 12:41:28 ltspserver dhcpd:    you want, please write a subnet declaration
Aug 29 12:41:28 ltspserver dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 12:41:28 ltspserver dhcpd:    to which interface eth0 is attached. **
Aug 29 12:41:28 ltspserver dhcpd: 
Aug 29 12:41:28 ltspserver dhcpd: 
Aug 29 12:41:28 ltspserver dhcpd: Not configured to listen on any interfaces!
Aug 29 12:41:28 ltspserver kernel: [   14.019348] init: isc-dhcp-server main process (1427) terminated with status 1
Aug 29 12:41:28 ltspserver kernel: [   14.019363] init: isc-dhcp-server respawning too fast, stopped
Aug 29 12:41:28 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Aug 29 12:41:28 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug 29 12:41:28 ltspserver accounts-daemon[1438]: started daemon version 0.6.15
Aug 29 12:41:28 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug 29 12:41:28 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug 29 12:41:28 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug 29 12:41:28 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug 29 12:41:28 ltspserver anacron[1613]: Anacron 2.3 started on 2012-08-29
Aug 29 12:41:28 ltspserver anacron[1613]: Normal exit (0 jobs run)
Aug 29 12:41:28 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug 29 12:41:28 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug 29 12:41:29 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 29 12:41:29 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Successfully called chroot.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Successfully dropped privileges.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Successfully limited resources.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Running.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Watchdog thread running.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Canary thread running.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Successfully made thread 1772 of process 1772 (n/a) owned by '104' high priority at nice level -11.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Supervising 1 threads of 1 processes of 1 users.
Aug 29 12:41:29 ltspserver pulseaudio[1768]: [pulseaudio] main.c: Daemon startup failed.
Aug 29 12:41:29 ltspserver kernel: [   15.192656] BUG: unable to handle kernel NULL pointer dereference at   (null)
Aug 29 12:41:29 ltspserver kernel: [   15.192661] IP: [<  (null)>]   (null)
Aug 29 12:41:29 ltspserver kernel: [   15.192663] *pdpt = 00000000227e7001 *pde = 0000000000000000 
Aug 29 12:41:29 ltspserver kernel: [   15.192666] Oops: 0010 [#1] SMP 
Aug 29 12:41:29 ltspserver kernel: [   15.192668] Modules linked in: bnep ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables bridge stp rfcomm bluetooth parport_pc ppdev binfmt_misc vesafb snd_hda_codec_hdmi cx22702 cx88_dvb cx88_vp3054_i2c videobuf_dvb dvb_core rc_hauppauge tuner_simple tuner_types tda9887 tda8290 tuner cx88_alsa snd_hda_codec_realtek mxm_wmi ir_lirc_codec lirc_dev ir_mce_kbd_decoder ir_sony_decoder cx8802 ir_jvc_decoder ir_rc6_decoder fglrx(P) ir_rc5_decoder snd_hda_intel snd_hda_codec snd_hwdep ir_nec_decoder cx8800 cx88xx rc_core i2c_algo_bit tveeprom v4l2_common videodev videobuf_dma_sg videobuf_core btcx_risc mac_hid serio_raw snd_pcm wmi mei(C) snd_timer snd soundcore snd_page_alloc lp parport firewire_ohci firewire_core crc_itu_t r8168(O)
Aug 29 12:41:29 ltspserver kernel: [   15.192698] 
Aug 29 12:41:29 ltspserver kernel: [   15.192700] Pid: 1772, comm: pulseaudio Tainted: P         C O 3.2.0-29-generic-pae #46-Ubuntu Gigabyte Technology Co., Ltd. Z68XP-UD3R/Z68XP-UD3R
Aug 29 12:41:29 ltspserver kernel: [   15.192703] EIP: 0060:[<00000000>] EFLAGS: 00010282 CPU: 0
Aug 29 12:41:29 ltspserver kernel: [   15.192705] EIP is at 0x0
Aug 29 12:41:29 ltspserver kernel: [   15.192706] EAX: e2664e2c EBX: e17654d0 ECX: f6ccf400 EDX: e208f000
Aug 29 12:41:29 ltspserver kernel: [   15.192708] ESI: e311a000 EDI: e903064c EBP: e28a9d40 ESP: e28a9d18
Aug 29 12:41:29 ltspserver kernel: [   15.192709]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Aug 29 12:41:29 ltspserver kernel: [   15.192710] Process pulseaudio (pid: 1772, ti=e28a8000 task=e95b8000 task.ti=e28a8000)
Aug 29 12:41:29 ltspserver kernel: [   15.192711] Stack:
Aug 29 12:41:29 ltspserver kernel: [   15.192712]  f8c65b73 00000080 e1709638 e17654d0 e2664e2c e1709600 f6ccf400 e28a9d8c
Aug 29 12:41:29 ltspserver kernel: [   15.192716]  00000000 e1b2ce40 e28a9d58 f84ede93 e28a9d4c f6ccf400 e95b8000 00000000
Aug 29 12:41:29 ltspserver kernel: [   15.192720]  e28a9d9c f84edf8a e28a9d8c 000080d0 00000000 f6f662f4 f6f66200 f6f662e0
Aug 29 12:41:29 ltspserver kernel: [   15.192724] Call Trace:
Aug 29 12:41:29 ltspserver kernel: [   15.192728]  [<f8c65b73>] ? azx_pcm_open+0x1d3/0x280 [snd_hda_intel]
Aug 29 12:41:29 ltspserver kernel: [   15.192733]  [<f84ede93>] snd_pcm_open_substream+0x53/0x90 [snd_pcm]
Aug 29 12:41:29 ltspserver kernel: [   15.192737]  [<f84edf8a>] snd_pcm_open+0xba/0x240 [snd_pcm]
Aug 29 12:41:29 ltspserver kernel: [   15.192741]  [<c1053b90>] ? try_to_wake_up+0x190/0x190
Aug 29 12:41:29 ltspserver kernel: [   15.192745]  [<f8600044>] ? snd_lookup_minor_data+0x44/0x60 [snd]
Aug 29 12:41:29 ltspserver kernel: [   15.192749]  [<f84ee19b>] snd_pcm_playback_open+0x3b/0x50 [snd_pcm]
Aug 29 12:41:29 ltspserver kernel: [   15.192753]  [<f8600544>] snd_open+0xd4/0x260 [snd]
Aug 29 12:41:29 ltspserver kernel: [   15.192756]  [<c1386cec>] ? kobj_lookup+0xfc/0x1a0
Aug 29 12:41:29 ltspserver kernel: [   15.192760]  [<c11484e5>] chrdev_open+0xb5/0x1e0
Aug 29 12:41:29 ltspserver kernel: [   15.192763]  [<c114252e>] __dentry_open+0x25e/0x310
Aug 29 12:41:29 ltspserver kernel: [   15.192765]  [<c1148430>] ? cdev_put+0x20/0x20
Aug 29 12:41:29 ltspserver kernel: [   15.192767]  [<c1142aaa>] vfs_open+0x3a/0x50
Aug 29 12:41:29 ltspserver kernel: [   15.192769]  [<c11439b9>] nameidata_to_filp+0x39/0x40
Aug 29 12:41:29 ltspserver kernel: [   15.192772]  [<c1150e37>] do_last+0x367/0x660
Aug 29 12:41:29 ltspserver kernel: [   15.192773]  [<c1152164>] path_openat+0xa4/0x350
Aug 29 12:41:29 ltspserver kernel: [   15.192776]  [<c117be64>] ? fsnotify_put_event+0x44/0x60
Aug 29 12:41:29 ltspserver kernel: [   15.192778]  [<c117be64>] ? fsnotify_put_event+0x44/0x60
Aug 29 12:41:29 ltspserver kernel: [   15.192780]  [<c1152521>] do_filp_open+0x31/0x80
Aug 29 12:41:29 ltspserver kernel: [   15.192783]  [<c12b7888>] ? strncpy_from_user+0x38/0x70
Aug 29 12:41:29 ltspserver kernel: [   15.192785]  [<c115db03>] ? alloc_fd+0xa3/0xe0
Aug 29 12:41:29 ltspserver kernel: [   15.192787]  [<c1143aa1>] do_sys_open+0xe1/0x1f0
Aug 29 12:41:29 ltspserver kernel: [   15.192791]  [<f8605390>] ? snd_ctl_elem_add_user+0x70/0x70 [snd]
Aug 29 12:41:29 ltspserver kernel: [   15.192793]  [<c1143bde>] sys_open+0x2e/0x40
Aug 29 12:41:29 ltspserver kernel: [   15.192795]  [<c15ac7df>] sysenter_do_call+0x12/0x28
Aug 29 12:41:29 ltspserver kernel: [   15.192797] Code:  Bad EIP value.
Aug 29 12:41:29 ltspserver kernel: [   15.192799] EIP: [<00000000>] 0x0 SS:ESP 0068:e28a9d18
Aug 29 12:41:29 ltspserver kernel: [   15.192801] CR2: 0000000000000000
Aug 29 12:41:29 ltspserver kernel: [   15.192803] ---[ end trace e819a06765f96c52 ]---
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Successfully made thread 1779 of process 1779 (n/a) owned by '104' high priority at nice level -11.
Aug 29 12:41:29 ltspserver rtkit-daemon[1774]: Supervising 2 threads of 2 processes of 1 users.
Aug 29 12:41:29 ltspserver pulseaudio[1779]: [pulseaudio] pid.c: Daemon already running.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> (eth0): carrier now ON (device state 20)
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Auto-activating connection 'Wired connection 1'.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) starting connection 'Wired connection 1'
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Beginning IP6 addrconf.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 29 12:41:30 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug 29 12:41:30 ltspserver avahi-daemon[949]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.53.
Aug 29 12:41:30 ltspserver avahi-daemon[949]: New relevant interface eth0.IPv4 for mDNS.
Aug 29 12:41:30 ltspserver avahi-daemon[949]: Registering new address record for 192.168.1.53 on eth0.IPv4.
Aug 29 12:41:30 ltspserver kernel: [   16.070629] r8168: eth0: link up
Aug 29 12:41:30 ltspserver kernel: [   16.070746] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 29 12:41:30 ltspserver kernel: [   16.830053] r8168: eth0: link up
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> DNS: starting dnsmasq...
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug 29 12:41:31 ltspserver dnsmasq[1782]: started, version 2.59 cache disabled
Aug 29 12:41:31 ltspserver dnsmasq[1782]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug 29 12:41:31 ltspserver dnsmasq[1782]: using nameserver 192.168.1.1#53
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> Activation (eth0) successful, device activated.
Aug 29 12:41:31 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 29 12:41:31 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 29 12:41:31 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 29 12:41:31 ltspserver epoptes: Running epoptes-client, IFACE=eth0, pid=1836
Aug 29 12:41:31 ltspserver ltsp: # Creating dsa-hostkey for ltspserver
Aug 29 12:41:31 ltspserver ltsp: # Creating rsa-hostkey for ltspserver
Aug 29 12:41:31 ltspserver ltsp: # Creating ecdsa-hostkey for ltspserver
Aug 29 12:41:31 ltspserver ltsp: # Creating dsa-hostkey for 192.168.1.53
Aug 29 12:41:31 ltspserver ltsp: # Creating rsa-hostkey for 192.168.1.53
Aug 29 12:41:31 ltspserver ltsp: # Creating ecdsa-hostkey for 192.168.1.53
Aug 29 12:41:31 ltspserver ltsp: # Creating dsa-hostkey for 10.0.3.1
Aug 29 12:41:31 ltspserver ltsp: # Creating rsa-hostkey for 10.0.3.1
Aug 29 12:41:31 ltspserver ltsp: # Creating ecdsa-hostkey for 10.0.3.1
Aug 29 12:41:31 ltspserver avahi-daemon[949]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::52e5:49ff:fe4a:26bf.
Aug 29 12:41:31 ltspserver avahi-daemon[949]: New relevant interface eth0.IPv6 for mDNS.
Aug 29 12:41:31 ltspserver avahi-daemon[949]: Registering new address record for fe80::52e5:49ff:fe4a:26bf on eth0.*.
Aug 29 12:41:34 ltspserver rtkit-daemon[1774]: Successfully made thread 1938 of process 1938 (n/a) owned by '104' high priority at nice level -11.
Aug 29 12:41:34 ltspserver rtkit-daemon[1774]: Supervising 1 threads of 1 processes of 1 users.
Aug 29 12:41:34 ltspserver pulseaudio[1938]: [pulseaudio] pid.c: Stale PID file, overwriting.
Aug 29 12:41:35 ltspserver dnsmasq[1086]: reading /etc/resolv.conf
Aug 29 12:41:35 ltspserver dnsmasq[1086]: using nameserver 127.0.0.1#53
Aug 29 12:41:35 ltspserver kernel: [   21.910681] xhci_hcd 0000:06:00.0: Timeout while waiting for address device command
Aug 29 12:41:36 ltspserver kernel: [   22.925383] lxcbr0: no IPv6 routers present
Aug 29 12:41:40 ltspserver kernel: [   26.768516] eth0: no IPv6 routers present
Aug 29 12:41:41 ltspserver ntpdate[1924]: adjust time server 91.189.94.4 offset 0.172703 sec
Aug 29 12:41:50 ltspserver NetworkManager[923]: <info> (eth0): IP6 addrconf timed out or failed.
Aug 29 12:41:50 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 29 12:41:50 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 29 12:41:50 ltspserver NetworkManager[923]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 29 12:41:56 ltspserver kernel: [   42.082030] xhci_hcd 0000:06:00.0: Timeout while waiting for address device command
Aug 29 12:41:56 ltspserver kernel: [   42.285704] usb 5-1: device not accepting address 2, error -62
Aug 29 12:41:56 ltspserver kernel: [   42.286149] xhci_hcd 0000:06:00.0: Bad Slot ID 1
Aug 29 12:41:56 ltspserver kernel: [   42.286153] xhci_hcd 0000:06:00.0: Could not allocate xHCI USB device data structures
Aug 29 12:41:56 ltspserver kernel: [   42.286159] hub 5-0:1.0: couldn't allocate port 1 usb_device
Aug 29 12:41:56 ltspserver kernel: [   42.357647] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
Aug 29 12:41:56 ltspserver mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Aug 29 12:41:56 ltspserver mtp-probe: bus: 1, device: 3 was not an MTP device
Aug 29 12:41:56 ltspserver kernel: [   42.529997] uvcvideo: Found UVC 1.00 device ASUS USB2.0 Webcam (04f2:b086)
Aug 29 12:41:56 ltspserver kernel: [   42.546388] input: ASUS USB2.0 Webcam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input12
Aug 29 12:41:56 ltspserver kernel: [   42.546506] usbcore: registered new interface driver uvcvideo
Aug 29 12:41:56 ltspserver kernel: [   42.546507] USB Video Class driver (1.1.1)
Aug 29 12:41:56 ltspserver kernel: [   42.561401] usb 2-1.2: new full-speed USB device number 3 using ehci_hcd
Aug 29 12:41:56 ltspserver mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Aug 29 12:41:56 ltspserver mtp-probe: bus: 2, device: 3 was not an MTP device
Aug 29 12:41:56 ltspserver kernel: [   42.683127] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13
Aug 29 12:41:56 ltspserver kernel: [   42.683271] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
Aug 29 12:41:56 ltspserver kernel: [   42.685412] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14
Aug 29 12:41:56 ltspserver kernel: [   42.685808] generic-usb 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
Aug 29 12:41:56 ltspserver kernel: [   42.685819] usbcore: registered new interface driver usbhid
Aug 29 12:41:56 ltspserver kernel: [   42.685820] usbhid: USB HID core driver
Aug 29 12:42:06 ltspserver rtkit-daemon[1774]: Successfully made thread 2107 of process 2107 (n/a) owned by '1000' high priority at nice level -11.
Aug 29 12:42:06 ltspserver rtkit-daemon[1774]: Supervising 2 threads of 2 processes of 2 users.
Aug 29 12:42:08 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Aug 29 12:42:08 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.UDisks'
Aug 29 12:42:23 ltspserver kernel: [   69.020853] audit_printk_skb: 66 callbacks suppressed
Aug 29 12:42:23 ltspserver kernel: [   69.020856] type=1400 audit(1346208143.094:34): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2249 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Aug 29 12:42:23 ltspserver goa[2254]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Aug 29 12:43:01 ltspserver dhcpd: Wrote 4 leases to leases file.
Aug 29 12:43:05 ltspserver dhcpd: DHCPDISCOVER from 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:43:05 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.101 to 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:43:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:08 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:08 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:10 ltspserver dhcpd: DHCPREQUEST for 192.168.1.101 (192.168.1.53) from 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:43:10 ltspserver dhcpd: DHCPACK on 192.168.1.101 to 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:43:11 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:11 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:11 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Aug 29 12:43:12 ltspserver AptDaemon: INFO: Initializing daemon
Aug 29 12:43:12 ltspserver AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Aug 29 12:43:12 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Aug 29 12:43:12 ltspserver AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Aug 29 12:43:12 ltspserver AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/816063f6dae2457e89819c759ad6f249
Aug 29 12:43:12 ltspserver AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/816063f6dae2457e89819c759ad6f249
Aug 29 12:43:15 ltspserver AptDaemon.PackageKit: INFO: Get updates()
Aug 29 12:43:15 ltspserver AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/816063f6dae2457e89819c759ad6f249
Aug 29 12:43:23 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:23 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:26 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:26 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:29 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:29 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:41 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:41 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:44 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:44 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:47 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:47 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:59 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:43:59 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:02 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:02 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:05 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:05 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:17 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:17 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:20 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:20 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:23 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:23 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:35 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:35 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:38 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:38 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:41 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:41 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:53 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:53 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:56 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:56 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:59 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:44:59 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:11 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:11 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:14 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:14 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:17 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:17 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:29 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:29 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:32 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:32 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:35 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:35 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:47 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:47 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:50 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:50 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:53 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:53 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:45:57 ltspserver dhcpd: DHCPREQUEST for 192.168.1.101 from 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:45:57 ltspserver dhcpd: DHCPACK on 192.168.1.101 to 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:45:58 ltspserver dhcpd: DHCPDISCOVER from 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:45:58 ltspserver dhcpd: DHCPOFFER on 192.168.1.101 to 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:45:59 ltspserver dhcpd: DHCPREQUEST for 192.168.1.101 (192.168.1.53) from 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:45:59 ltspserver dhcpd: DHCPACK on 192.168.1.101 to 00:26:4a:2c:f1:32 (Heidz-Iphone) via eth0
Aug 29 12:46:05 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:05 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:08 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:08 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:11 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:11 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:23 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:23 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:26 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:26 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:29 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:29 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:41 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:41 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:44 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:44 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:47 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:47 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:59 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:46:59 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:02 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:02 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:05 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:05 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:17 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:17 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:20 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:20 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:23 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:23 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:39 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:39 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:57 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:47:57 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:15 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:15 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:33 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:33 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:51 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:51 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:48:55 ltspserver dbus[877]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Aug 29 12:48:55 ltspserver dbus[877]: [system] Successfully activated service 'org.freedesktop.locale1'
Aug 29 12:49:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:09 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:09 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:13 ltspserver AptDaemon: INFO: Quitting due to inactivity
Aug 29 12:49:13 ltspserver AptDaemon: INFO: Quitting was requested
Aug 29 12:49:15 ltspserver kernel: [  480.515095] gnome-control-c[2645]: segfault at 50 ip af35fe60 sp bfd49080 error 6 in libscreen.so[af35e000+3000]
Aug 29 12:49:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:27 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:27 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:45 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:45 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:49:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:03 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:03 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:21 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:21 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:39 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:39 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:57 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:50:57 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:15 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:15 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:33 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:33 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:51 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:51 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:51:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:09 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:09 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:27 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:27 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:45 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:45 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:52:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:03 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:03 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:21 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:21 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:39 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:39 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:57 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:53:57 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:15 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:15 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:33 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:33 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:51 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:51 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:54:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:09 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:09 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:12 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:12 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:27 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:27 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:30 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:30 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:45 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:45 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:48 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:55:48 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:03 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:03 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:06 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:06 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:18 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:18 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:21 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:21 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:24 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:24 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:36 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:36 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:39 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:39 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:42 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:42 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:54 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:54 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:57 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:56:57 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
Aug 29 12:57:00 ltspserver dhcpd: DHCPDISCOVER from 00:01:29:d4:ad:9f via eth0
Aug 29 12:57:00 ltspserver dhcpd: DHCPOFFER on 192.168.1.102 to 00:01:29:d4:ad:9f via eth0
```

---

### Post by rukiaEnix on 2012-08-29
Please post how does your /etc/rc.local file looks.

Also the log says you most declare a subnet for the eth0 interface, have you done that yet?

---

