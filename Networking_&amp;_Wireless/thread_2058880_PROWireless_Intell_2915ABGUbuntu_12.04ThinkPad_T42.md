---
title: "PRO/Wireless Intell 2915ABG/Ubuntu 12.04/ThinkPad T42p"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by FrugalGuy on 2012-09-16
Wireless was working great until I upgraded from 10.04 LTS to 12.04 LTS.

It sort of seemed I'd needed to rename the device from eth1 to wlan0, but maybe was another laptop.  Anyhow, I tried that, and went from a quick boot that could see the AP but would not connect to a 2-3 minute boot with no network config.  Obviously, I switched back to eth1.  Now I just still cannot connect.  Here's the info the HOW-TO-POST suggested I provide...

**1 ) Machine Brand and Model (PC/Laptop)**:
     IBM Thinkpad T42p
[B]
2 ) Wireless Brand, Model and Wireless Chipset:
[/B]lspci:
```
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4224] (rev 05)
```[B]

3) Interface:[/B]
ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:13:ce:9b:23:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1950 (1.9 KB)
          Interrupt:11 Base address:0x6000 Memory:c0214000-c0214fff
```iwconfig:
```
eth1      IEEE 802.11abg  ESSID:"int.ronandjoy.com"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:AA:07:CF   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**NOTE:** At first try, the ESSID was some odd unicode string. I set it with iwconfig, then the Access Point filled in, but I'm still getting prompted over and over for the key, and it won't connect.

[B]4 ) Check for modules:
[/B]```
$ lsmod | grep ipw
ipw2200               146210  0 
libipw                 46701  1 ipw2200
cfg80211              178679  2 ipw2200,libipw
lib80211               14040  3 lib80211_crypt_wep,ipw2200,libipw
```**5) Kernel Boot messages:**
```
[    0.000000] Linux version 3.2.0-30-generic (buildd@aatxe) (gcc version 4.6.3 
(Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 (Ub
untu 3.2.0-30.48-generic 3.2.27)
. . .
[   18.384905] lib80211: common routines for IEEE802.11 drivers
[   18.384908] lib80211_crypt: registered algorithm 'NULL'
[   18.423489] cfg80211: Calling CRDA to update world regulatory domain
[   18.430780] type=1400 audit(1347816882.795:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=642 comm="apparmor_parser"
[   18.456713] libipw: 802.11 data/management/control stack, git-1.1.13
[   18.456718] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.468198] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   18.468203] ipw2200: Copyright(c) 2003-2006 Intel Corporation
. . . 
[   19.128994] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   19.129025] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
. . . 
[   19.316785] cfg80211: World regulatory domain updated:
[   19.316790] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.316794] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
. . . 
[   19.507781] cfg80211: failed to add phy80211 symlink to netdev!
[   19.510902] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.511379] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.513603] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.513608] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
. . . 
[   19.514024] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
. . . 
[   21.844767] lib80211_crypt: registered algorithm 'WEP'
. . . 

```**6. Network Configuration:**
```
$ sudo lshw -C network
. . . wired eth0 deleted for brevity. . .
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:9b:23:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:c0214000-c0214fff
```**7. Network Scan:**
```
$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:AA:07:CF
                    ESSID:"int.ronandjoy.com"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-30 dBm  
                    Extra: Last beacon: 4ms ago
          Cell 02 - Address: 3C:EA:4F:CA:83:11
                    ESSID:"2WIRE978"
. . . Neighbor Network deleted. . .
          Cell 03 - Address: B8:E6:25:B5:BC:A9
                    ESSID:"2WIRE636"
. . . Neighbor Network deleted. . . 

```**8. Ubuntu Version:**
```
$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
$ uname -mr
3.2.0-30-generic i686
```[B]10 ) Restarting the network:
[/B]```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
$
```**11) Config files:**
/etc/network/interfaces: (changed some key values to '??') **IS THE FORMAT RIGHT?**
<EDIT> Actually, I've used colons and without colons, and neither is working for me.</EDIT>
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
wireless-key1 62:??:b0:6b:6f:??:6d:??:2c:??:b2:d7:46
wireless-defaultkey 1
wireless-keymode shared
```So the wired works fine, and wireless worked fine BEFORE the upgrade.
I'm using WEB 104/128-bit 26 Hex digits key.
Auth is Shared Key
SSID is int.ronandjoy.com
Channel 6 2.437 GHz
(from the WAP54G router admin console)

Since the upgrade, choosing to connect to int.ronandjoy.com prompts me for the key over and over and over and over, but never connects.

Help, please?  Thanks!

---

### Post by chili555 on 2012-09-17
> 11) Config files:
/etc/network/interfaces: (changed some key values to '??') **IS THE FORMAT RIGHT?**
<EDIT> Actually, I've used colons and without colons, and neither is working for me.</EDIT>


```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
wireless-key1 62:??:b0:6b:6f:??:6d:??:2c:??:b2:d7:46
wireless-defaultkey 1
wireless-keymode shared
```

Oh my! No, it is not correct. First, you need to decide if you are going to use Network Manager or manual methods. Almost every attempt I've seen to mix and match has failed. If you have a stay-at-home computer, it's perfectly valid to remove NM altogether. If you do, then the format would be:```
auto lo
iface lo inet loopback

auto eth1
iface inet eth1 dhcp
wireless-essid int.ronandjoy.com
wireless-key 62??b06b6f??6d??2c??b2d746 restricted

```Even better is to set your router to use WPA2-PSK assuming your card supports it:```
sudo iwlist eth1 auth
```Then the format would be:```
auto lo
iface lo inet loopback

auto eth1
iface inet eth1 dhcp
wpa-ssid int.ronandjoy.com
wpa-psk 001122334455
```If you want to use NM, then the format is:```
auto lo
iface lo inet loopback
```

---

### Post by FrugalGuy on 2012-09-17
Thanks for the response.

I eventually tired of trying NM, so removed it:
```
apt-get remove network-manager
```I'd read that wicd was more flexible in allowing me to use eth1 (instead of wlan0, which is not what I have).

So, I trimmed down /etc/network/interfaces to just
```
auto lo
iface lo inet loopback
```I installed wicd, added a couple lines back to interfaces and tried using wicd-client -n.
I got failures when wicd called wpa_supplicant. The authentication failed, and wicd assumed that meant the password was bad.
interfaces now reads:
```
auto lo
iface lo inet loopback
wpa-driver wext
wpa-conf /var/lib/wicd/configurations/001217aa07cf
```supposedly so that ifup and ifdown will still do the DHCP work. <shrug>

I have logs of wicd and logs of wpa_supplicant if they'll help.

One really, really frustrating thing is that I got it to connect correctly for just a bit...

I did everything manually, and it came up fine!
```
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "int.ronandjoy.com"
sudo iwconfig eth1 key 6261xxxxxxxxxxxxxxxxx <26 hex characters>
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
```And it WORKED immediately!!  I even had added the wicd applet to the Unity desktop by adding it to the whitelist (another saga), and that icon suddenly showed a big green level bar!

For fun, I opened wicd's GUI, disconnected and connected again. PERFECT!

Then I rebooted, and now it doesn't work again.  :mad:

So, I **KNOW **it can work. How do I replicate that, though, and make it permanent??

What should I try next?  Any more data y'all need?

The config file for wicd above contains this:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
     ssid="myactualid"
     scan_ssid=1
     key_mgmt=NONE
     auth_alg=SHARED
    wep_key0=6261...
    wep_tx_keyidx=0
    priority=5
}
```The manual sequence above goes fine, except the final dhclient command never completes.  Adding -d and -v to get verbose output from dhclient just shows DHCPDISCOVER broadcasts on eth1 to 255.255.255.255. port 67 at different intervals... never completing.

So do you suggest trying again to set up the interfaces by adding more stuff, and trying somehow to NOT use wicd?

---

### Post by chili555 on 2012-09-17
> interfaces now reads:
```
auto lo
iface lo inet loopback
wpa-driver wext
wpa-conf /var/lib/wicd/configurations/001217aa07cf

```
I thought it was clear from my first post that you need to declare eth1:```
auto lo
iface lo inet loopback

[COLOR="Red"]auto eth1
iface inet eth1 dhcp[/COLOR]
wireless-essid int.ronandjoy.com
wireless-key 62??b06b6f??6d??2c??b2d746 restricted
```I also wonder why you are setting up wpa-conf when your network doesn't use WPA at all, although I recommend you do.> I'd read that wicd was more flexible in allowing me to use eth1 (instead of wlan0, which is not what I have).Wicd is no more or less flexible in this regard than NM. It is amazing the urban lore that gets spread around the internet and accepted as truth.> ctrl_interface=/var/run/[COLOR="Red"]wpa_supplicant[/COLOR]Why??

---

### Post by FrugalGuy on 2012-09-18
> I thought it was clear from my first post that you need to declare eth1:Actually, I'd changed my interfaces file for use with wicd before your reply was posted, so I didn't ignore you. :-)

Secondly, you posted two approaches. In the past I've used NM with no trouble, and I'm willing to use it again if you believe it can be made to work for me... I DO carry my laptop to other locations, and so a hard-coded single config with no management will not work for me (though if you think it would be useful for debug as a first step, I'm certainly willing to try it).

I know that I was able to connect until a reboot using wicd, so if you or anybody else can help me to get that approach working, I'd like to try that as the end goal.

So... debug using interfaces and explicit interface config there, or some other first step?

Your help is deeply appreciated.

Just to answer your questions:
> I also wonder why you are setting up wpa-conf when your network doesn't use WPA at all, although I recommend you do.Since I am using wicd for management, I thought wpa_supplicant was required. Certainly it works with WEP shared keys as well as WPA.   I'll certainly switch to WPA at some point, but there are too many machines already config'd for WEP and I am out of transmit range of war drivers or the great unwashed. So I'll stay with WEP for now.

---

### Post by chili555 on 2012-09-19
Sorry for the delay in replying. There is apparently but one wire that comes up the mountain where we are staying for a while and last night it broke!>  I DO carry my laptop to other locations, and so a hard-coded single config with no management will not work for me Then, by all means, let's un-hard-code it. Please amend your interfaces file to:```
auto lo
iface lo inet loopback
```Proofread your changes, save and close the text editor. Reboot. Now open Wicd; do you see your network? Can you click it and try to connect? Are you challenged for your WEP key? Does it connect or fail?

Look for and post any interesting clues in /var/log/wicd/wicd.log.

---

### Post by FrugalGuy on 2012-09-20
Okay. Interfaces is as spec'd.  Rebooted.  Enet cable in during boot.  wicd tray showed connected to wired. pulled enet cable. opened wicd applet. hit refresh. wired went away as expected, and my wireless network showed up. Pressed connect. Got the usual wicd applet status bar messages... iface down, then iface up, then authenticating for about 40 secs, then authentication failed / bad password.

Not challenged for the key, but then, it's set in wicd, so I wouldn't expect to be. Looking in wicd applet at my wireless network properties, I verify it is set for [x] Use Encryption, "WEP Shared/Restricted", and Key is the proper 26 Hex characters. No quotes or dashes or colons.

If I press Information I get Signal strength: 84%, Encryption type: WEP, Access point address: 00:12:17:AA:07:CF, which is my AP's mac, Mode: Master, and Channel: Channel 6.

Here's the wicd log from the time I tried to connect while wired network was pulled:

```
2012/09/19 23:32:57 :: Connecting to wireless network int.ronandjoy.com
2012/09/19 23:32:57 :: attempting to set hostname with dhclient
2012/09/19 23:32:57 :: using dhcpcd or another supported client may work better
2012/09/19 23:32:58 :: attempting to set hostname with dhclient
2012/09/19 23:32:58 :: using dhcpcd or another supported client may work better
2012/09/19 23:32:58 :: Putting interface down
2012/09/19 23:32:58 :: Releasing DHCP leases...
2012/09/19 23:32:58 :: attempting to set hostname with dhclient
2012/09/19 23:32:58 :: using dhcpcd or another supported client may work better
2012/09/19 23:32:58 :: Setting false IP...
2012/09/19 23:32:58 :: Stopping wpa_supplicant
2012/09/19 23:32:58 :: Flushing the routing table...
2012/09/19 23:32:58 :: Putting interface up...
2012/09/19 23:33:00 :: Attempting to authenticate...
2012/09/19 23:33:06 :: wpa_supplicant rescan forced...
2012/09/19 23:33:41 :: wpa_supplicant authentication may have failed.
2012/09/19 23:33:41 :: connect result is failed
2012/09/19 23:33:41 :: exiting connection thread
2012/09/19 23:33:41 :: Sending connection attempt result bad_pass
2012/09/19 23:33:41 :: attempting to set hostname with dhclient
2012/09/19 23:33:41 :: using dhcpcd or another supported client may work better
2012/09/19 23:33:41 :: attempting to set hostname with dhclient
2012/09/19 23:33:41 :: using dhcpcd or another supported client may work better
```

syslog contains:
```
Sep 19 23:32:58 bader03 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep 19 23:32:58 bader03 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep 19 23:32:58 bader03 dhclient: All rights reserved.
Sep 19 23:32:58 bader03 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 19 23:32:58 bader03 dhclient: 
Sep 19 23:32:58 bader03 dhclient: Listening on LPF/eth1/00:13:ce:9b:23:02
Sep 19 23:32:58 bader03 dhclient: Sending on   LPF/eth1/00:13:ce:9b:23:02
Sep 19 23:32:58 bader03 dhclient: Sending on   Socket/fallback
Sep 19 23:32:58 bader03 dhclient: DHCPRELEASE on eth1 to 192.168.3.1 port 67
Sep 19 23:32:58 bader03 dhclient: send_packet: Network is unreachable
Sep 19 23:32:58 bader03 dhclient: send_packet: please consult README file regarding broadcast address.
Sep 19 23:33:00 bader03 avahi-daemon[897]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::213:ce
ff:fe9b:2302.
Sep 19 23:33:00 bader03 avahi-daemon[897]: New relevant interface eth1.IPv6 for mDNS.
Sep 19 23:33:00 bader03 avahi-daemon[897]: Registering new address record for fe80::213:ceff:fe9b:2302 on eth1.*.
Sep 19 23:33:01 bader03 kernel: [  137.453899] lib80211_crypt: registered algorithm 'WEP'
Sep 19 23:33:09 bader03 kernel: [  144.904039] eth1: no IPv6 routers present
Sep 19 23:33:14 bader03 dbus[843]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Sep 19 23:33:15 bader03 AptDaemon: INFO: Initializing daemon
Sep 19 23:33:16 bader03 AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Sep 19 23:33:16 bader03 dbus[843]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Sep 19 23:33:16 bader03 AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Sep 19 23:33:16 bader03 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e7e34814b30d41d3a384219041
96e33c
Sep 19 23:33:16 bader03 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/e7e34814b30d41d3a3842
1904196e33c
Sep 19 23:33:19 bader03 AptDaemon.PackageKit: INFO: Get updates()
Sep 19 23:33:20 bader03 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/e7e34814b30d41d3a384219
04196e33c
Sep 19 23:33:41 bader03 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep 19 23:33:41 bader03 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep 19 23:33:41 bader03 dhclient: All rights reserved.
Sep 19 23:33:41 bader03 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 19 23:33:41 bader03 dhclient: 
Sep 19 23:33:41 bader03 dhclient: Listening on LPF/eth1/00:13:ce:9b:23:02
Sep 19 23:33:41 bader03 dhclient: Sending on   LPF/eth1/00:13:ce:9b:23:02
Sep 19 23:33:41 bader03 dhclient: Sending on   Socket/fallback
Sep 19 23:33:41 bader03 dhclient: DHCPRELEASE on eth1 to 192.168.3.1 port 67
Sep 19 23:33:41 bader03 dhclient: send_packet: Network is unreachable
Sep 19 23:33:41 bader03 dhclient: send_packet: please consult README file regarding broadcast address.
Sep 19 23:33:41 bader03 avahi-daemon[897]: Interface eth1.IPv6 no longer relevant for mDNS.
Sep 19 23:33:41 bader03 avahi-daemon[897]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe9b:2302.
Sep 19 23:33:41 bader03 avahi-daemon[897]: Withdrawing address record for fe80::213:ceff:fe9b:2302 on eth1.
Sep 19 23:33:41 bader03 kernel: [  177.324153] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 19 23:33:41 bader03 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep 19 23:33:41 bader03 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep 19 23:33:41 bader03 dhclient: All rights reserved.
Sep 19 23:33:41 bader03 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 19 23:33:41 bader03 dhclient: 
Sep 19 23:33:41 bader03 dhclient: Listening on LPF/eth0/00:10:c6:de:b6:f6
Sep 19 23:33:41 bader03 dhclient: Sending on   LPF/eth0/00:10:c6:de:b6:f6
Sep 19 23:33:41 bader03 dhclient: Sending on   Socket/fallback
Sep 19 23:33:41 bader03 dhclient: DHCPRELEASE on eth0 to 192.168.3.1 port 67
Sep 19 23:33:41 bader03 dhclient: send_packet: Network is unreachable
Sep 19 23:33:41 bader03 dhclient: send_packet: please consult README file regarding broadcast address.
Sep 19 23:33:42 bader03 kernel: [  177.619650] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

What else can I show you?

Thanks!

---

### Post by chili555 on 2012-09-20
> using dhcpcd or another supported client may work betterI think I might try this first:```
sudo apt-get install dhcpcd
sudo service wicd restart
```Now see if the option to use dhcpcd rather that dhclient exists in the Wicd tabs; if so, select it. Then detach the ethernet and try to connect.

You might also try a driver parameter:```
sudo modprobe -r ipw2200
sudo modprobe ipw2200 hwcrypto=1
```If this helps, we can write one quick file and make it persistent.

I also might try resetting the router to WEP-open rather than WEP-shared to see if it has any effect.

---

### Post by FrugalGuy on 2012-09-21
Grrr.  I wrote a whole nice reply, then looked back at an earlier post for more data to add before I saved the reply. Lost it.  <sigh>  Here we go once more...

Thanks for your help!  I'm not there,  yet, though.

Did the install of dhcpcd, restarted wicd. 
```
$ sudo apt-get install dhcpcd
[sudo] password for roncraig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnm-glib-vpn1 libnl-route-3-200
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  dhcpcd
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 48.3 kB of archives.
After this operation, 159 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe dhcpcd i386 1:3.2.3-9ubuntu1 [48.3 kB]
Fetched 48.3 kB in 0s (129 kB/s)
Selecting previously unselected package dhcpcd.
(Reading database ... 200088 files and directories currently installed.)
Unpacking dhcpcd (from .../dhcpcd_1%3a3.2.3-9ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up dhcpcd (1:3.2.3-9ubuntu1) ...

$ sudo service wicd restart
 * Restarting Network connection manager wicd                            [ OK ] 
```

Finally found the Preferences and changed the DHCP Client setting from Auto to dhcpcd.  Pulled the ethernet.

Refreshed, saw the network. Tried to connect but it failed as before: if up/down, etc., authenticating.... , failed.  Lemme see if I can paste in the log w/out losing this...
From the restart to the failure:
```
2012/09/21 16:42:16 :: Daemon going down, killing wicd-monitor...
2012/09/21 16:42:16 :: Removing PID file...
2012/09/21 16:42:16 :: Shutting down...
2012/09/21 16:42:16 :: Exception KeyError: KeyError(-1217373440,) in <module 'th
reading' from '/usr/lib/python2.7/threading.pyo'> ignored
2012/09/21 16:42:17 :: ---------------------------
2012/09/21 16:42:17 :: wicd initializing...
2012/09/21 16:42:17 :: ---------------------------
2012/09/21 16:42:17 :: wicd is version 1.7.2.3 761
2012/09/21 16:42:17 :: setting backend to external
2012/09/21 16:42:17 :: trying to load backend external
2012/09/21 16:42:17 :: successfully loaded backend external
2012/09/21 16:42:17 :: trying to load backend external
2012/09/21 16:42:17 :: successfully loaded backend external
2012/09/21 16:42:17 :: Automatically detected wireless interface eth1
2012/09/21 16:42:17 :: setting wireless interface eth1
2012/09/21 16:42:17 :: automatically detected wired interface eth0
2012/09/21 16:42:17 :: setting wired interface eth0
2012/09/21 16:42:17 :: setting wpa driver wext
2012/09/21 16:42:17 :: setting use global dns to False
2012/09/21 16:42:17 :: setting global dns
2012/09/21 16:42:17 :: global dns servers are None None None
2012/09/21 16:42:17 :: domain is None
2012/09/21 16:42:17 :: search domain is None
2012/09/21 16:42:17 :: setting automatically reconnect when connection drops True
2012/09/21 16:42:17 :: Setting dhcp client to 0
2012/09/21 16:42:17 :: Wireless configuration file found...
2012/09/21 16:42:17 :: Wired configuration file found...
2012/09/21 16:42:17 :: chmoding configuration files 0600...
2012/09/21 16:42:17 :: chowning configuration files root:root...
2012/09/21 16:42:17 :: Using wireless interface...eth1
2012/09/21 16:42:17 :: Using wired interface...eth0
2012/09/21 16:42:56 :: trying to load backend external
2012/09/21 16:42:56 :: trying to load backend ioctl
2012/09/21 16:42:56 :: WARNING: python-iwscan not found, falling back to using iwlist scan.
2012/09/21 16:42:56 :: WARNING: python-wpactrl not found, falling back to using wpa_cli.
2012/09/21 16:45:39 :: setting use global dns to 0
2012/09/21 16:45:39 :: setting global dns
2012/09/21 16:45:39 :: global dns servers are   
2012/09/21 16:45:39 :: domain is 
2012/09/21 16:45:39 :: search domain is 
2012/09/21 16:45:39 :: setting wireless interface eth1
2012/09/21 16:45:39 :: setting wired interface eth0
2012/09/21 16:45:39 :: setting wpa driver wext
2012/09/21 16:45:39 :: setting automatically reconnect when connection drops 1
2012/09/21 16:45:39 :: setting backend to external
2012/09/21 16:45:39 :: Setting dhcp client to 2
2012/09/21 16:46:22 :: Connecting to wireless network int.ronandjoy.com
2012/09/21 16:46:22 :: Putting interface down
2012/09/21 16:46:22 :: Releasing DHCP leases...
2012/09/21 16:46:22 :: Setting false IP...
2012/09/21 16:46:22 :: Stopping wpa_supplicant
2012/09/21 16:46:22 :: Flushing the routing table...
2012/09/21 16:46:22 :: Putting interface up...
2012/09/21 16:46:24 :: Attempting to authenticate...
2012/09/21 16:46:31 :: wpa_supplicant rescan forced...
2012/09/21 16:47:05 :: wpa_supplicant authentication may have failed.
2012/09/21 16:47:05 :: connect result is failed
2012/09/21 16:47:05 :: exiting connection thread
2012/09/21 16:47:05 :: Sending connection attempt result bad_pass

```

Issued the sudo commands:
```
$ sudo modprobe -r ipw2200
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

$ sudo modprobe ipw2200 hwcrypto=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
```

Another failed connect attempt. Log:
```
2012/09/21 16:53:18 :: Connecting to wireless network int.ronandjoy.com
2012/09/21 16:53:18 :: Putting interface down
2012/09/21 16:53:19 :: Releasing DHCP leases...
2012/09/21 16:53:19 :: Setting false IP...
2012/09/21 16:53:19 :: Stopping wpa_supplicant
2012/09/21 16:53:19 :: Flushing the routing table...
2012/09/21 16:53:19 :: Putting interface up...
2012/09/21 16:53:21 :: Attempting to authenticate...
2012/09/21 16:53:27 :: wpa_supplicant rescan forced...
2012/09/21 16:54:01 :: wpa_supplicant authentication may have failed.
2012/09/21 16:54:01 :: connect result is failed
2012/09/21 16:54:01 :: exiting connection thread
2012/09/21 16:54:01 :: Sending connection attempt result bad_pass

```

Something I mentioned before but you may have missed is that the iwconfig shows garbage for the ssid even though it is set properly in wicd:
```
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

eth0      no wireless extensions.
```

I'll end this post.  I'm going to do the manual iwconfig steps again and see what happens... next post.

---

### Post by FrugalGuy on 2012-09-21
Yup. I'm writing this via wireless, but it won't last (again).

Here's what I did...
```
roncraig@bader03:~$ sudo ifconfig eth1 down
[sudo] password for roncraig: 
Sorry, try again.
[sudo] password for roncraig: 
roncraig@bader03:~$ sudo dhcpcd -r eth1
err, `eth1' is not a valid IP address
roncraig@bader03:~$ sudo dhclient -r eth1
roncraig@bader03:~$ sudo ifconfig eth1 up
roncraig@bader03:~$ sudo iwconfig eth1 essid "int.ronandjoy.com"
roncraig@bader03:~$ sudo iwconfig eth1 key 6261buhjkas5a6dxxbbd0b2d76
roncraig@bader03:~$ sudo iwconfig eth1 key restricted
roncraig@bader03:~$ sudo iwconfig eth1 mode Managed
roncraig@bader03:~$ sudo dhclient eth1
roncraig@bader03:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"int.ronandjoy.com"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:AA:07:CF   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6261-B06B-6F5A-6DE9-2C20-B2D7-46   Security mode:restricted
          Power Management:off
          Link Quality=100/100  Signal level=-17 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

eth0      no wireless extensions.

roncraig@bader03:~$ ping www.yahoo.com
connect: Network is unreachable
roncraig@bader03:~$ sudo dhclient eth1
RTNETLINK answers: File exists
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=51 time=242 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=2 ttl=50 time=146 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=3 ttl=50 time=66.4 ms
^C
--- ds-any-fp3-real.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 66.488/152.026/242.759/72.056 ms

```So the green signal strength indicator went up right away the first time, but web browser and ping didn't work until I did a dhclient eth1 a second time.

Just like before, I'm good, but probably only until a reboot.

I'll try disconnect, reconnect, disconnect, attach ethernet, use wired, pull cable, reconnect and show it's working.  Then I'll reboot and see...

But I'm closing this post first. :D

---

### Post by FrugalGuy on 2012-09-21
Yeah. I'm just good until a reboot.  Here's what I did after the last post. Remember, I'm starting with a working wireless connection...

```
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=51 time=569 ms
^C

roncraig@bader03:~$ # disconnect wireless in wicd...
roncraig@bader03:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com

roncraig@bader03:~$ # reconnect wireless in wicd...
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=50 time=342 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=2 ttl=50 time=411 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=3 ttl=51 time=599 ms
^C

roncraig@bader03:~$ #disconnect and attach ethernet then connect to wired..
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=50 time=614 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=2 ttl=50 time=690 ms
^C

roncraig@bader03:~$ #pull cable and reconnect to wireless...
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=50 time=454 ms
^C

roncraig@bader03:~$ #grabbing the wicd log...
roncraig@bader03:~$ less < /var/log/wicd/wicd.log
roncraig@bader03:~$ #rebooting ...

```

Here's the wicd.log:
```
2012/09/21 17:46:41 :: Connecting to wireless network int.ronandjoy.com
2012/09/21 17:46:42 :: Putting interface down
2012/09/21 17:46:42 :: Releasing DHCP leases...
2012/09/21 17:46:42 :: Setting false IP...
2012/09/21 17:46:42 :: Stopping wpa_supplicant
2012/09/21 17:46:42 :: Flushing the routing table...
2012/09/21 17:46:42 :: Putting interface up...
2012/09/21 17:46:44 :: Attempting to authenticate...
2012/09/21 17:46:46 :: Running DHCP with hostname bader03
2012/09/21 17:46:48 :: dhcpcd.sh: interface eth1 has been configured with new IP=192.168.3.215
2012/09/21 17:46:48 :: 
2012/09/21 17:46:48 :: 
2012/09/21 17:46:48 :: DHCP connection successful
2012/09/21 17:46:48 :: not verifying
2012/09/21 17:46:48 :: Connecting thread exiting.
2012/09/21 17:46:48 :: Sending connection attempt result success
2012/09/21 17:48:05 :: Putting interface down
2012/09/21 17:48:05 :: Releasing DHCP leases...
2012/09/21 17:48:05 :: Setting false IP...
2012/09/21 17:48:05 :: Stopping wpa_supplicant
2012/09/21 17:48:05 :: Flushing the routing table...
2012/09/21 17:48:05 :: Putting interface up...
2012/09/21 17:48:07 :: Running DHCP with hostname bader03
2012/09/21 17:48:12 :: dhcpcd.sh: interface eth0 has been configured with new IP=192.168.3.207
2012/09/21 17:48:12 :: 
2012/09/21 17:48:12 :: 
2012/09/21 17:48:12 :: DHCP connection successful
2012/09/21 17:48:12 :: Connecting thread exiting.
2012/09/21 17:48:12 :: Sending connection attempt result success
2012/09/21 17:49:14 :: Connecting to wireless network int.ronandjoy.com
2012/09/21 17:49:14 :: Putting interface down
2012/09/21 17:49:14 :: Releasing DHCP leases...
2012/09/21 17:49:14 :: Setting false IP...
2012/09/21 17:49:14 :: Stopping wpa_supplicant
2012/09/21 17:49:14 :: Flushing the routing table...
2012/09/21 17:49:14 :: Putting interface up...
2012/09/21 17:49:16 :: Attempting to authenticate...
2012/09/21 17:49:18 :: Running DHCP with hostname bader03
2012/09/21 17:49:20 :: dhcpcd.sh: interface eth1 has been configured with new IP=192.168.3.215
2012/09/21 17:49:20 :: 
2012/09/21 17:49:20 :: 
2012/09/21 17:49:20 :: DHCP connection successful
2012/09/21 17:49:20 :: not verifying
2012/09/21 17:49:20 :: Connecting thread exiting.
2012/09/21 17:49:21 :: Sending connection attempt result success

```

As I said, wireless now won't work... had to connect with cable after the reboot.

I'll post this, and try the manual iwconfig once again... bet it will not work this time, though.

---

### Post by FrugalGuy on 2012-09-21
I'm wrong. The manual steps did work this time, too.  That's not always been the case in the past.  Here's the blow-by-blow again...
```
roncraig@bader03:~$ sudo ifconfig eth1 down
[sudo] password for roncraig: 
roncraig@bader03:~$ sudo dhcpcd -r eth1
err, `eth1' is not a valid IP address
roncraig@bader03:~$ sudo dhclient -r eth1
roncraig@bader03:~$ sudo ifconfig eth1 up
roncraig@bader03:~$ sudo iwconfig eth1 essid "int.ronandjoy.com"
roncraig@bader03:~$ sudo iwconfig eth1 key xxxxxxxxxxxxxxxxxxxxxxxxxx
roncraig@bader03:~$ sudo iwconfig eth1 key restricted
roncraig@bader03:~$ sudo iwconfig eth1 mode Managed
roncraig@bader03:~$ sudo dhclient eth1
roncraig@bader03:~$ ping www.yahoo.com
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=1 ttl=51 time=409 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=2 ttl=50 time=699 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_req=3 ttl=51 time=527 ms
^C

```

And the log: huh. Of course, there are no more log entries, I did the config manually.

Now how to get it to work automatically?  To pick up at another wireless site?

---

### Post by chili555 on 2012-09-22
Just to satisfy my curiosity and a hunch, would you please enter the key *NOT* in WEP-Shared but WEP-HEX and report the result?

---

### Post by FrugalGuy on 2012-09-28
Precisely the same.
I think the key is that if I've been connected with a cable, then I can remove it and connect wireless. If I haven't connected with a cable since the last reboot, I cannot connect to the wireless.

---

### Post by chili555 on 2012-09-29
When you reboot without the cable and are not connected, please check if the driver is loaded:```
lsmod | grep ipw
```And check if Network Manager is running:```
ps aux | grep -i network
```Weird!

---

### Post by FrugalGuy on 2012-10-01
```
$ sudo lsmod | grep ipw
ipw2200                146210   0
libipw                  46701   1  ipw2200
cfg80211               178679   2  ipw2200,libipw
lib20211                14040   3  lib80211_crypt_web,ipw2200,libipw
```and no, ps confirms Network Manager is not running.

The key here is the authentication, I think. That's what continues to fail if I've not connnected before with ethernet.

Notice the difference in the traces pasted below...  first is if ethernet has been there, second is not.

In both you see: connecting, putting iface down, releasing, setting false IP, stopping, flushing putting up, attempting to authenticate,  then the traces are different...
**wpa_supplicant rescan forced** leads to failure. 
Running DHCP leads to 'not verifying' and success.


2012/09/21 16:46:22 :: Connecting to wireless network int.ronandjoy.com 2012/09/21 16:46:22 :: Putting interface down 2012/09/21 16:46:22 :: Releasing DHCP leases... 2012/09/21 16:46:22 :: Setting false IP... 2012/09/21 16:46:22 :: Stopping wpa_supplicant 2012/09/21 16:46:22 :: Flushing the routing table... 2012/09/21 16:46:22 :: Putting interface up... 2012/09/21 16:46:24 :: Attempting to authenticate... 2012/09/21 16:46:31 :: wpa_supplicant rescan forced... 2012/09/21 16:47:05 :: wpa_supplicant authentication may have failed. 2012/09/21 16:47:05 :: connect result is failed 2012/09/21 16:47:05 :: exiting connection thread 2012/09/21 16:47:05 :: Sending connection attempt result bad_pass

vs 

2012/09/21 17:49:14 :: Connecting to wireless network int.ronandjoy.com 2012/09/21 17:49:14 :: Putting interface down 2012/09/21 17:49:14 :: Releasing DHCP leases... 2012/09/21 17:49:14 :: Setting false IP... 2012/09/21 17:49:14 :: Stopping wpa_supplicant 2012/09/21 17:49:14 :: Flushing the routing table... 2012/09/21 17:49:14 :: Putting interface up... 2012/09/21 17:49:16 :: Attempting to authenticate... 2012/09/21 17:49:18 :: Running DHCP with hostname bader03 2012/09/21 17:49:20 :: dhcpcd.sh: interface eth1 has been configured with new IP=192.168.3.215 2012/09/21 17:49:20 ::  2012/09/21 17:49:20 ::  2012/09/21 17:49:20 :: DHCP connection successful 2012/09/21 17:49:20 :: not verifying 2012/09/21 17:49:20 :: Connecting thread exiting. 2012/09/21 17:49:21 :: Sending connection attempt result success

The machine keeps trying... I get a pop-up saying int.ronandjoy.com Establishing connection... and a ps shows wpa_supplicant is running for a while:
wpa_aupplicant -B -i eth1 -c /var/lib/wicd/configurations/001217aa07cf -Dwext

---

### Post by chili555 on 2012-10-01
> and no, ps confirms Network Manager is **not** running.
And so where, pray tell, is the pop-up coming from? If you start with the ethernet cable, is NM running?> The key here is the authentication, I think. And why isn't it NM which evidently fails to start and therefor to manage your wireless connection?

What, if anything, is here?```
cat /etc/network/interfaces
```

---

### Post by FrugalGuy on 2012-10-01
Network Manager isn't running at any time. We uninstalled it back at message #3 in this thread.   I've got wicd installed instead. You can't run both--it won't work.  I thought that was why you were double-checking that it was properly uninstalled.

> And so where, pray tell, is the pop-up coming from? If you start with the ethernet cable, is NM running?NM is uninstalled.
The pop-up is coming from wicd:
```
root      1076  0.0  0.7  15252  7864 ?        S    09:30   0:00 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
roncraig  1696  0.0  2.3 146148 23988 ?        Sl   09:30   0:00 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --tray
root      2349  0.0  0.0   2328   112 ?        Ss   09:31   0:00 /sbin/dhcpcd-bin -Y -N -R -h bader03 --noipv4ll eth0
```> What, if anything, is here?     Code:
     cat /etc/network/interfaces
It's still just as you suggested in note #6:
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```Once again, thank you for your help.

---

### Post by chili555 on 2012-10-01
I guess that's what happens when I am answering 27 threads, on vacation and old! I made an oops; sorry about that! So the question remains, why doesn't the wireless start independently of wired? Is Wicd running as expected if you boot without the ethernet connected?```
ps aux | grep wicd
```If you boot without ethernet, are there any interesting messages in wicd.log? In dmesg?> $ cat /etc/network/interfaces
auto lo
iface lo inet loopbackPerfect!

---

### Post by FrugalGuy on 2012-10-01
> So the question remains, why doesn't the wireless start independently  of wired? Is Wicd running as expected if you boot without the ethernet  connected?Yes, wicd is running as expected. The response #18 has the ps output I think you're looking for.

> If you boot without ethernet, are there any interesting messages in wicd.log? In dmesg?I think we covered those in earlier posts, but for completeness, I'm attaching the wicd.log from bootup through an episode or two of pop-up connecting... disconnected.
Also there is the dmesg.

I'm really thinking it is the authentication, so I monitored ps until wicd was trying to connect again, and caught the command to wpa_supplicant.  After it gave up, I issued the command myself in the foreground, capturing the debug output:

```
$ ps auxwww | grep -i wpa
root      3723  0.0  0.0   5944   964 ?        Ss   18:28   0:00 wpa_supplicant -B -i eth1 -c /var/lib/wicd/configurations/001217aa07cf -Dwext

$ sudo wpa_supplicant -i eth1 -c /var/lib/wicd/configurations/001217aa07cf -Dwext -dd > wpa_debug.txt 2>&1
```The debug output has errors about the authentication and driver failures to accept some settings.  Maybe you can make something out of it?

Attachments:
[ATTACH]224951[/ATTACH]

[ATTACH]224952[/ATTACH]

[ATTACH]224954[/ATTACH]

---

### Post by chili555 on 2012-10-02
I have no idea why or where wpa_supplicant is being invoked. When it specifically is *NOT* used, you evidently connect perfectly:> I did everything manually, and it came up fine!
```
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "int.ronandjoy.com"
sudo iwconfig eth1 key 6261xxxxxxxxxxxxxxxxx <26 hex characters>
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
[COLOR="Red"]Note that wpa_supplicant is not mentioned at all[/COLOR]

```

And it WORKED immediately!! Is there a setting in Wicd you are using to invoke wpa_supplicant? I'm not sure I have many more ideas.

Do you still have a wpa_supplicant.conf file lurking somewhere? I doubt it helps and may hurt Wicd's effectiveness.```
sudo updatedb
locate wpa_supplicant.conf
```

---

### Post by FrugalGuy on 2012-10-15
Let's call this one closed.
I switched to WPA2-Personal AES encryption, and everything works perfectly.

Thanks for the time and effort.

-FG

---

