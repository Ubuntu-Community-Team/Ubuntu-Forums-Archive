---
title: "xorg.conf vanishes"
date: 2014-11-06
forum: Mythbuntu
---

### Post by khPWXxF on 2014-11-06
I've had a problem of my xorg.conf being renamed xorg.conf.mmddyyyy about once a month since I installed 14.04, and it's happened again. It's loss causes the irritating blank HDMI screen if myth is started before the TV.
I have had a work-round of making xorg.conf immutable, but I stupidly forgot to re-apply it after a restore of my root partition on 1st Nov.  Since it has happened again and I have the evidence still spinning on the disk, I thought I'd investigate to try and nail this one once and for all.  Sadly, I don't see anything interesting (other than the nvidia licence issue) in the logs but I ask if anyone can see anything suspicious.   Is there any other log I should examine or save if it happens again?

Phil

The renamed xorg.conf file has the following 'stat':
```

  File: ‘xorg.conf.11052014’
  Size: 1580          Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 131891      Links: 1
Access: (0444/-r--r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2014-11-04 18:53:46.974328908 +0000
Modify: 2014-10-30 16:16:48.884381234 +0000
Change: 2014-11-05 09:13:29.656174664 +0000
 Birth: -
```


I no longer have any dmesg files but the syslog  is rather quiet at modification time:
 
```
Oct 30 16:09:01 myth CRON[2651]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 30 16:14:12 myth lircd-0.9.0[616]: removed client
Oct 30 16:14:25 myth lircd-0.9.0[616]: accepted new client on /run/lirc/lircd
Oct 30 16:14:33 myth lircd-0.9.0[616]: removed client
Oct 30 16:17:01 myth CRON[3004]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 30 16:39:01 myth CRON[4382]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))


```
At access time it's:


```
Nov  4 18:53:45 myth kernel: [   12.304596] input: HDA NVidia HDMI/DP,pcm=7 Phantom as /devices/pci0000:00/0000:00:07.0/sound/card0/input21
Nov  4 18:53:45 myth kernel: [   12.304741] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input20
Nov  4 18:53:45 myth kernel: [   12.304803] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input19
Nov  4 18:53:45 myth kernel: [   12.304868] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input18
Nov  4 18:53:45 myth kernel: [   12.304928] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
Nov  4 18:53:45 myth kernel: [   12.304986] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input16
Nov  4 18:53:45 myth kernel: [   12.305073] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input15
Nov  4 18:53:45 myth kernel: [   12.305129] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
Nov  4 18:53:45 myth kernel: [   12.305187] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
Nov  4 18:53:45 myth kernel: [   12.305554] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  4 18:53:45 myth kernel: [   12.305785] EDAC amd64: DRAM ECC disabled.
Nov  4 18:53:45 myth kernel: [   12.305790] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Nov  4 18:53:45 myth kernel: [   12.305790]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Nov  4 18:53:45 myth kernel: [   12.305790]  (Note that use of the override may cause unknown side effects.)
Nov  4 18:53:45 myth kernel: [   12.324346] nvidia: module license 'NVIDIA' taints kernel.
Nov  4 18:53:45 myth kernel: [   12.324353] Disabling lock debugging due to kernel taint
Nov  4 18:53:45 myth kernel: [   12.336426] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Nov  4 18:53:45 myth kernel: [   12.343932] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
Nov  4 18:53:45 myth kernel: [   12.343952] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Nov  4 18:53:45 myth kernel: [   12.344615] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.117  Tue Nov 26 21:25:36 PST 2013
Nov  4 18:53:46 myth NetworkManager[811]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Nov  4 18:53:46 myth NetworkManager[811]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  4 18:53:46 myth NetworkManager[811]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov  4 18:53:46 myth NetworkManager[811]: <info> NetworkManager state is now CONNECTED_GLOBAL
Nov  4 18:53:46 myth NetworkManager[811]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  4 18:53:46 myth NetworkManager[811]: <info> DNS: starting dnsmasq...
Nov  4 18:53:46 myth NetworkManager[811]: <warn> dnsmasq not available on the bus, can't update servers.
Nov  4 18:53:46 myth NetworkManager[811]: <error> [1415127226.274624] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Nov  4 18:53:46 myth NetworkManager[811]: <warn> DNS: plugin dnsmasq update failed
Nov  4 18:53:46 myth NetworkManager[811]: <info> Writing DNS information to /sbin/resolvconf
Nov  4 18:53:46 myth dnsmasq[1324]: started, version 2.68 cache disabled
Nov  4 18:53:46 myth dnsmasq[1324]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Nov  4 18:53:46 myth dnsmasq[1324]: DBus support enabled: connected to system bus
Nov  4 18:53:46 myth dnsmasq[1324]: warning: no upstream servers configured
Nov  4 18:53:46 myth NetworkManager[811]: <info> Activation (eth0) successful, device activated.
Nov  4 18:53:46 myth dbus[666]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  4 18:53:46 myth NetworkManager[811]: <warn> dnsmasq appeared on DBus: :1.9
Nov  4 18:53:46 myth NetworkManager[811]: <info> Writing DNS information to /sbin/resolvconf
Nov  4 18:53:46 myth dnsmasq[1324]: setting upstream servers from DBus
Nov  4 18:53:46 myth dnsmasq[1324]: using nameserver 192.168.1.254#53
Nov  4 18:53:46 myth dbus[666]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  4 18:53:46 myth ntpd[1168]: ntpd exiting on signal 15
Nov  4 18:53:46 myth ModemManager[691]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:0a.0': not supported by any plugin
Nov  4 18:53:46 myth dbus[666]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Nov  4 18:53:46 myth accounts-daemon[1502]: started daemon version 0.6.35
Nov  4 18:53:46 myth dbus[666]: [system] Successfully activated service 'org.freedesktop.Accounts'
Nov  4 18:53:47 myth /etc/mysql/debian-start[1548]: Upgrading MySQL tables if necessary.
Nov  4 18:53:47 myth ntpd_intres[1171]: parent died before we finished, exiting
Nov  4 18:53:47 myth /etc/mysql/debian-start[1551]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Nov  4 18:53:47 myth /etc/mysql/debian-start[1551]: Looking for 'mysql' as: /usr/bin/mysql

```

And for the file change time it's:

```
Nov  5 09:13:27 myth NetworkManager[786]: <info> (eth0): DHCPv4 state changed preinit -> bound
Nov  5 09:13:27 myth NetworkManager[786]: <info>   address 192.168.1.67
Nov  5 09:13:27 myth NetworkManager[786]: <info>   prefix 24 (255.255.255.0)
Nov  5 09:13:27 myth NetworkManager[786]: <info>   gateway 192.168.1.254
Nov  5 09:13:27 myth NetworkManager[786]: <info>   nameserver '192.168.1.254'
Nov  5 09:13:27 myth NetworkManager[786]: <info>   domain name 'lan'
Nov  5 09:13:27 myth NetworkManager[786]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov  5 09:13:27 myth NetworkManager[786]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Nov  5 09:13:27 myth avahi-daemon[881]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.67.
Nov  5 09:13:27 myth avahi-daemon[881]: New relevant interface eth0.IPv4 for mDNS.
Nov  5 09:13:27 myth avahi-daemon[881]: Registering new address record for 192.168.1.67 on eth0.IPv4.
Nov  5 09:13:28 myth kernel: [   16.548361] init: nvidia-prime main process (992) terminated with status 127
Nov  5 09:13:28 myth anacron[1059]: Anacron 2.3 started on 2014-11-05
Nov  5 09:13:28 myth cron[982]: (CRON) INFO (pidfile fd = 3)
Nov  5 09:13:28 myth anacron[1059]: Will run job `cron.daily' in 5 min.
Nov  5 09:13:28 myth anacron[1059]: Jobs will be executed sequentially
Nov  5 09:13:28 myth acpid: starting up with netlink and the input layer
Nov  5 09:13:28 myth cron[1078]: (CRON) STARTUP (fork ok)
Nov  5 09:13:28 myth acpid: 9 rules loaded
Nov  5 09:13:28 myth acpid: waiting for events: event logging is off
Nov  5 09:13:28 myth cron[1078]: (CRON) INFO (Running @reboot jobs)
Nov  5 09:13:28 myth kernel: [   16.872734] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov  5 09:13:28 myth kernel: [   16.873175] NFSD: starting 90-second grace period (net ffffffff81cda040)
Nov  5 09:13:28 myth rpc.mountd[1196]: Version 1.2.8 starting
Nov  5 09:13:28 myth NetworkManager[786]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Nov  5 09:13:28 myth NetworkManager[786]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov  5 09:13:28 myth NetworkManager[786]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov  5 09:13:29 myth NetworkManager[786]: <info> NetworkManager state is now CONNECTED_GLOBAL
Nov  5 09:13:29 myth NetworkManager[786]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  5 09:13:29 myth NetworkManager[786]: <info> DNS: starting dnsmasq...
Nov  5 09:13:29 myth NetworkManager[786]: <warn> dnsmasq not available on the bus, can't update servers.
Nov  5 09:13:29 myth NetworkManager[786]: <error> [1415178809.24669] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Nov  5 09:13:29 myth NetworkManager[786]: <warn> DNS: plugin dnsmasq update failed
Nov  5 09:13:29 myth NetworkManager[786]: <info> Writing DNS information to /sbin/resolvconf
Nov  5 09:13:29 myth dnsmasq[1292]: started, version 2.68 cache disabled
Nov  5 09:13:29 myth dnsmasq[1292]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Nov  5 09:13:29 myth dnsmasq[1292]: DBus support enabled: connected to system bus
Nov  5 09:13:29 myth dnsmasq[1292]: warning: no upstream servers configured
Nov  5 09:13:29 myth NetworkManager[786]: <info> Activation (eth0) successful, device activated.
Nov  5 09:13:29 myth dbus[689]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  5 09:13:29 myth NetworkManager[786]: <warn> dnsmasq appeared on DBus: :1.9
Nov  5 09:13:29 myth NetworkManager[786]: <info> Writing DNS information to /sbin/resolvconf
Nov  5 09:13:29 myth dnsmasq[1292]: setting upstream servers from DBus
Nov  5 09:13:29 myth dnsmasq[1292]: using nameserver 192.168.1.254#53
Nov  5 09:13:29 myth dbus[689]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  5 09:13:29 myth avahi-daemon[881]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:8cff:fe88:54fb.
Nov  5 09:13:29 myth avahi-daemon[881]: New relevant interface eth0.IPv6 for mDNS.
Nov  5 09:13:29 myth avahi-daemon[881]: Registering new address record for fe80::224:8cff:fe88:54fb on eth0.*.
Nov  5 09:13:29 myth ntpd[900]: ntpd exiting on signal 15
Nov  5 09:13:29 myth dbus[689]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Nov  5 09:13:29 myth ModemManager[753]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:0a.0': not supported by any plugin
Nov  5 09:13:29 myth accounts-daemon[1497]: started daemon version 0.6.35
Nov  5 09:13:29 myth dbus[689]: [system] Successfully activated service 'org.freedesktop.Accounts'
Nov  5 09:13:29 myth ntpd_intres[904]: parent died before we finished, exiting
Nov  5 09:13:30 myth acpid: client connected from 1509[0:0]
Nov  5 09:13:30 myth acpid: 1 client rule loaded
Nov  5 09:13:30 myth kernel: [   19.182966] init: plymouth-upstart-bridge main process ended, respawning
Nov  5 09:13:31 myth lircd-0.9.0[606]: accepted new client on /run/lirc/lircd
```

---

### Post by dannyboy79 on 2014-11-06
i have no clue what would be renaming it to be honest, in all my years of using ubuntu (9 years) i've never heard of xorg.conf being renamed except by the nvidia installer, it asks you though if you want it to rename your current xorg and make a new one.

have you made the file read only after making it the way you want? also about the issue of X server not working if you start your computer when the tv is off, there's an xorg.conf option to force X server to output to a certain device using the "ConnectedMonitor" option, it's detailed here: [http://ubuntuforums.org/showthread.php?t=2200907](http://ubuntuforums.org/showthread.php?t=2200907)
you could even create a button press on your remote to force a xrandr mode in case you start the frontend before the tv is on.

---

### Post by khPWXxF on 2014-11-07
Thanks Dannyboy,
 
That’s an interesting link.  I’ll try it – my ‘power down back to welcome’ code looks a good place to add it!
 
There are a number of issues:
 
How do you prevent the ‘blank screen’ if the TV is turned on after myth?   I’ve seen a number of solutions, but I used
     ```
options ‘UseHotPlugEvents” false
```
in the device section of xorg.conf.
 
Why does xorg.conf get deleted though?   There’s a bit of sticky toffee implementation here.  It does get renamed by a reload after a fresh install (because authors think driver defaults should suffice).  Once that’s done, renames on subsequent reboots should be inhibited by the presence of a trigger file /var/lib/ubuntu-drivers-common/last_gfx_boot. 
 
The file gets renamed occasionally even if permissions are only 444.  Setting immutability seems to prevent it but I can’t be sure because proving a negative is difficult.  The file  /var/lib/dpkg/info/nvidia-prime.postrm was my chief suspect, but putting a log statement in this exonerates it.
 
Why my xorg.conf gets zapped and nobody else has said ‘me too’ is odd.  Likewise, the xfce taskbar across top of screen persists with me and needs a bash type work-round – upgrades did remove this bug but it came back after I changed host name and did a database restore.  Don’t know if the two are related.
 
I’m doing this with an on-mobo  nvidia 8300 – driver support seems to be drying up for this and I’m using 304.  Maybe I can expect more fun like this in the future!
 
My setup seems to be stable if I use 304 drivers, include the xfce work-round and make xorg.conf immutable.  I’d still like to get to the bottom of it all though because all this should not be necessary!  I don’t like unsolved mysteries.
 
Phil

---

