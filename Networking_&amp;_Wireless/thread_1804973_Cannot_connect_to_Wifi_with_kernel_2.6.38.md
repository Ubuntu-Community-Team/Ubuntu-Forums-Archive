---
title: "Cannot connect to Wifi with kernel 2.6.38"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2011-07-15
I've had this problem for a while, but I'm only reminded of it when an update includes a new kernel version.

Basically the wifi on my Dell D600 laptop works fine if I stick with kernel 2.6.35-28. But it won't work with recent versions such as 2.6.38-8 or 2.6.38-10.

The network manager icon in Gnome is displayed as an empty pie (i.e. no curved signal bars). Clicking on he icon does not give me an option to connect to my wifi ap. If I connect a network cable, the icon changes to twin arrows and I have wired network access.

Running:-
```

cat /sys/bus/pci/drivers/ipw2100/*/rf_kill

```
returns: 0
...showing that wifi interface is not switched off.

And running:-
```

iwlist {interface} scan

```
returns information about local access points including my own.

So it looks like the wireless interface is OK, and it is as if network manager is not hooking up the interface to the system.

I have the same problem when loading LXDE or Gnome.

Any ideas?

---

### Post by chili555 on 2011-07-15
Let's do some diagnostics. Please run and post:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep ipw
```Thanks.

---

### Post by jbrefort on 2011-07-16
I have the same issue with both my laptop and desktop computers.  With the laptop, things work when I am very close to the source. The issue is not specific to ubuntu, I tested with debian and fedora too. Things worked perfectly up to kernel 2.6.37.

dmesg generally shows lines like:
[ 1770.721427] wlan0: direct probe to d2:34:1a:95:65:c0 (try 1/3)
[ 1770.920099] wlan0: direct probe to d2:34:1a:95:65:c0 (try 2/3)
[ 1771.120115] wlan0: direct probe to d2:34:1a:95:65:c0 (try 3/3)
[ 1771.320106] wlan0: direct probe to d2:34:1a:95:65:c0 timed out

---

### Post by SteveDee on 2011-07-16
Thanks for your input chili555:-
```

steve@steve-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
steve@steve-laptop:~$ lspci -nn | grep 0280
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
steve@steve-laptop:~$ dmesg | grep ipw
[   29.050028] libipw: 802.11 data/management/control stack, git-1.1.13
[   29.050032] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   29.400930] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   29.400935] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   29.565548] ipw2100 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[   29.566204] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
steve@steve-laptop:~$ 

```
I think "rfkill list all" is similar to "cat /sys/bus/pci/drivers/ipw2100/*/rf_kill" but with friendly text output instead of just a return code.

+++++++++
Thanks jbrefort
> 
....things worked perfectly up to kernel 2.6.37.

...this confirms that I'm not alone and the issue is probably due to a bug in the kernel.

I had a similar problem with a previous kernel (2.6.30-xx I think) which was eventually fixed in a subsequent release.

I'll file a report on LaunchPad.

---

### Post by houserparker on 2011-07-16
Was this after the update from kernel 2.6.38-8 to 2.6.38-10. If so I may be having the same problem. Can you post the link to the bug report you created?

For now I managed to get it connected by switching the interface using:

```
ifconfig wlan1 down
```
```
ifconfig wlan1 up
```

Not sure whether this will help you.

---

### Post by houserparker on 2011-07-16
Sorry my mistake wrong thread.

---

### Post by chili555 on 2011-07-16
> I think "rfkill list all" is similar to "cat /sys/bus/pci/drivers/ipw2100/*/rf_kill" but with friendly text output instead of just a return code.Correct; however, it often suggests the cause of a software block, such as the notorious dell-laptop: [http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)> 0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: [COLOR="Red"]dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/COLOR]

Your dmesg is remarkably free of any problems! Is /etc/network/interfaces empty, except for loopback? That will inform Network Manager that it is not to control your listed interface. Is your interface eth1? What does syslog say?```
sudo cat /var/log/syslog | grep eth1 | tail -n25
```If this is sparse, grep syslog.1. I use an Intel 2200 device and it's quite reliable. This is therefor quite puzzling to me.

---

### Post by SteveDee on 2011-07-16
The story continues on LaunchPad: [https://answers.launchpad.net/ubuntu/+question/165006](https://answers.launchpad.net/ubuntu/+question/165006)

I've provided them with a truck load of data by following this: [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

...and will update this post if I discover anything useful.

---

### Post by chili555 on 2011-07-16
I regret that my offer of assistance was declined. Good luck.

---

### Post by SteveDee on 2011-07-17
> 
chili555...
I regret that my offer of assistance was declined....


Hey! it was not my intention to upset anyone or decline an offer of help (I need all the help I can get), and I've seen the great work that you do on this forum (...how do you find the time?).

Theres a lot of stuff in the system log, but when I boot using 2.6.38-xx and run:-
```

sudo cat /var/log/syslog | grep eth0-eth2 | tail -n25

```
there are only 2 lines that apply to this particular boot attempt:-
```

Jul 17 12:01:24 steve-laptop kernel: [   30.545446] <30>udev[273]: renamed network interface eth0 to eth0-eth2
Jul 17 12:02:54 steve-laptop udevd-work[273]: error changing net interface name eth0-eth2 to eth2: File exists

```

whereas if I boot using 2.6.35 I get this:-
```

Jul 17 12:20:59 steve-laptop kernel: [   29.390674] <30>udev[362]: renamed network interface eth0 to eth0-eth2
Jul 17 12:20:59 steve-laptop NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/net/eth0-eth2, iface: eth0-eth2)
Jul 17 12:20:59 steve-laptop NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/net/eth0-eth2, iface: eth0-eth2): no ifupdown configuration found.
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <error> [1310901660.196529] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth0-eth2): unable to read permanent MAC address (error 0)
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): driver does not support SSID scans (scan_capa 0x00).
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): new 802.11 WiFi device (driver: 'ipw2100' ifindex: 3)
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): now managed
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 1 -> 2 (reason 2)
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): bringing up device.
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): preparing device.
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): deactivating device (reason: 2).
Jul 17 12:21:00 steve-laptop kernel: [   30.765671] ADDRCONF(NETDEV_UP): eth0-eth2: link is not ready
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant manager state:  down -> idle
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 2 -> 3 (reason 0)
Jul 17 12:21:00 steve-laptop udevd-work[362]: error changing net interface name eth0-eth2 to eth2: Device or resource busy
Jul 17 12:21:00 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant interface state:  starting -> ready
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) starting connection 'Auto LINUX LIVES HERE'
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 3 -> 4 (reason 0)
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 1 of 5 (Device Prepare) started...
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 2 of 5 (Device Configure) scheduled...
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 1 of 5 (Device Prepare) complete.
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 2 of 5 (Device Configure) starting...
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 4 -> 5 (reason 0)
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2/wireless): connection 'Auto LINUX LIVES HERE' has security, and secrets exist.  No new secrets needed.
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 2 of 5 (Device Configure) complete.
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  inactive -> scanning
Jul 17 12:21:08 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  scanning -> associating
Jul 17 12:21:09 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  associating -> associated
Jul 17 12:21:09 steve-laptop kernel: [   39.712294] ADDRCONF(NETDEV_CHANGE): eth0-eth2: link becomes ready
Jul 17 12:21:10 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  associated -> 4-way handshake
Jul 17 12:21:10 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  4-way handshake -> group handshake
Jul 17 12:21:10 steve-laptop avahi-daemon[800]: Joining mDNS multicast group on interface eth0-eth2.IPv6 with address fe80::20c:f1ff:fe3c:1536.
Jul 17 12:21:10 steve-laptop avahi-daemon[800]: New relevant interface eth0-eth2.IPv6 for mDNS.
Jul 17 12:21:10 steve-laptop avahi-daemon[800]: Registering new address record for fe80::20c:f1ff:fe3c:1536 on eth0-eth2.*.
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> (eth0-eth2): supplicant connection state:  group handshake -> completed
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'LINUX LIVES HERE'.
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 3 of 5 (IP Configure Start) started...
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 5 -> 7 (reason 0)
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 3 of 5 (IP Configure Start) complete.
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> (eth0-eth2): DHCPv4 state changed nbi -> preinit
Jul 17 12:21:11 steve-laptop dhclient: Listening on LPF/eth0-eth2/00:0c:f1:3c:15:36
Jul 17 12:21:11 steve-laptop dhclient: Sending on   LPF/eth0-eth2/00:0c:f1:3c:15:36
Jul 17 12:21:11 steve-laptop dhclient: DHCPREQUEST of 192.168.0.6 on eth0-eth2 to 255.255.255.255 port 67
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> (eth0-eth2): DHCPv4 state changed preinit -> reboot
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 4 of 5 (IP4 Configure Get) started...
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 17 12:21:11 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 5 of 5 (IP Configure Commit) started...
Jul 17 12:21:11 steve-laptop avahi-daemon[800]: Joining mDNS multicast group on interface eth0-eth2.IPv4 with address 192.168.0.6.
Jul 17 12:21:11 steve-laptop avahi-daemon[800]: New relevant interface eth0-eth2.IPv4 for mDNS.
Jul 17 12:21:11 steve-laptop avahi-daemon[800]: Registering new address record for 192.168.0.6 on eth0-eth2.IPv4.
Jul 17 12:21:12 steve-laptop NetworkManager[806]: <info> (eth0-eth2): device state change: 7 -> 8 (reason 0)
Jul 17 12:21:12 steve-laptop NetworkManager[806]: <info> Policy set 'Auto LINUX LIVES HERE' (eth0-eth2) as default for IPv4 routing and DNS.
Jul 17 12:21:12 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) successful, device activated.
Jul 17 12:21:12 steve-laptop NetworkManager[806]: <info> Activation (eth0-eth2) Stage 5 of 5 (IP Configure Commit) complete.
Jul 17 12:21:19 steve-laptop kernel: [   50.048023] eth0-eth2: no IPv6 routers present

```

If I have any time today I'll research "udevd-work"

---

### Post by chili555 on 2011-07-17
> renamed network interface eth0 to eth0-eth2
unable to read permanent MAC address (error 0)
driver does not support SSID scans (scan_capa 0x00)These are the lines that look uglier than my ex-wife's lawyer to me. Let's compare:```
lshw -C network
```Along side of:```
/etc/udev/rules.d/70-persistent-net.rules
```I'm thinking we may need to edit the latter file to show the proper MAC address as well as force ethernet to eth0 and wireless to eth1.

Have you had another wireless card in the machine? Not that there is anything wrong with that! I have a few old miniPCI wireless cards laying around, too.

I am shocked that syslog doesn't think the card supports scans. Does it respond?```
sudo iwlist eth2 scan
```Or does it show as eth2 in *iwconfig*?

---

### Post by SteveDee on 2011-07-18
> **chili555 said:**
> ...Have you had another wireless card in the machine?...

This is a 2nd hand laptop with no service history. However the HDD was taken out of my previous laptop (a Dell 500m), so I'm thinking that the original (500m) install is screwing things up on the D600. It probably accounts for the duplication in "70-persistent-net.rules".
I've got use to the idea that you can take a Linux drive out of one computer & pop it straight into another...but maybe you can't?

The wifi interface logical name is: eth0-eth2
...so it scans with:-
```

sudo iwlist eth0-eth2 scan

```

Network info:-
```

steve@steve-laptop:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:0f:1f:b4:6f:bc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.16 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0-eth2
       version: 04
       serial: 00:0c:f1:3c:15:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.2 latency=32 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:7 memory:fafef000-fafeffff

```

70-persistent-net.rules:-
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:56:de:19:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1043 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:04:23:99:45:9f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0846:0x4260 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:2a:3a:21:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0ace:0x1215 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:72:65:00:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x1043 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:f1:3c:15:36", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x14e4:0x165d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:1f:b4:6f:bc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```

---

### Post by chili555 on 2011-07-18
You generally can change drives easily. There are sometimes unexpected quirks and sometimes they are inconsequential; sometimes they require a tweak to get going.

You have these devices in place now:```
product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: [COLOR="Red"]00:0f:1f:b4:6f:bc[/COLOR]
```And aslo:```
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0-eth2
       version: 04
       serial: [COLOR="Red"]00:0c:f1:3c:15:36[/COLOR]
```Therefore, I suggest you edit the rules file to read:```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1043 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:f1:3c:15:36", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth1[/COLOR]"

# PCI device 0x14e4:0x165d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:1f:b4:6f:bc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="Red"]eth0[/COLOR]"
```I noticed there was a USB device in there; if you are using one, remove it temporarily. As soon as the changes are made, reboot.

My suspicion is that somewhere in Network Manager or wpa_supplicant, interfaces of wlan% or eth% or ra% etc. are allowed. I suspect no provision was made for eth%-eth%, etc.

After reboot, let us have your report.

---

### Post by SteveDee on 2011-07-20
> **chili555 said:**
> ...After reboot, let us have your report.

After tidying up the rules file I can now boot with 2.6.38 and wifi works every time. So thanks very much for your time & expertise chili555.

Output from the 3 commands now looks like this:-

```

steve@steve-laptop:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:b4:6f:bc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5705-v3.16 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:3c:15:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.2 latency=32 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:7 memory:fafef000-fafeffff

steve@steve-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"LINUX LIVES HERE"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1E:2A:1F:23:DE   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=81/100  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

vboxnet0  no wireless extensions.

steve@steve-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1E:2A:1F:23:DE
                    ESSID:"LINUX LIVES HERE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1984ms ago

steve@steve-laptop:~$ 

```

---

### Post by chili555 on 2011-07-20
Awesome! I am very glad it's working well. Would you please help the searchers by using thread tools at the top and Mark Solved?

---

