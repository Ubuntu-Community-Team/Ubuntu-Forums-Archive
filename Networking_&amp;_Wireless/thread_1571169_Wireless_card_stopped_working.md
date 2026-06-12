---
title: "Wireless card stopped working"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by Quinoa Rex on 2010-09-09
I'm using Ubuntu 9.10 on a Lenovo ThinkPad T61 using an Intel PRO/Wireless 3945ABG. My laptop's ability to connect to a wireless network stopped last night, and I'm not sure why. It's definitely something on my end, as my roommate can connect to the internet on a Windows box. I can wire in without a problem, but that's a pain and my Ethernet cable got lost in the shuffle when I moved back to school. I've been able to get into this network before and nothing about it has changed. I've been able to hibernate and restart and such and nothing has ever needed to be reset. The router's a D-Link WBR-2310.

Wicd and Network Manager see the network (I'm back to using wicd) , but wicd appears to get stuck at "Obtaining IP address..." and says "Unable to connect: Cannot obtain IP address". I know my password is correct (I set up the router and I'm the CS undergrad in the apartment so I manage it), lspci sees the wireless card, ifconfig and iwconfig return information about the interface, dmesg|grep wlan0 doesn't seem to have anything terribly out of the ordinary, but here's that output:
```
allyanncah@taliesin:~% dmesg | grep wlan0
[   23.514202] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.609016] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.756143] wlan0: direct probe to AP 00:24:01:cb:4e:7e (try 1)
[   38.758791] wlan0: direct probe responded
[   38.758796] wlan0: authenticate with AP 00:24:01:cb:4e:7e (try 1)
[   38.760587] wlan0: authenticated
[   38.760609] wlan0: associate with AP 00:24:01:cb:4e:7e (try 1)
[   38.763318] wlan0: RX AssocResp from 00:24:01:cb:4e:7e (capab=0x431 status=0 aid=1)
[   38.763322] wlan0: associated
[   38.765502] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.888075] wlan0: no IPv6 routers present
[  130.368277] wlan0: deauthenticating from 00:24:01:cb:4e:7e by local choice (reason=3)
[  130.518099] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  437.397992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  441.538182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  441.647778] wlan0: direct probe to AP 00:24:01:cb:4e:7e (try 1)
[  441.651884] wlan0: direct probe responded
[  441.651890] wlan0: authenticate with AP 00:24:01:cb:4e:7e (try 1)
[  441.653460] wlan0: deauthenticating from 00:24:01:cb:4e:7e by local choice (reason=3)
[  441.653539] wlan0: direct probe to AP 00:24:01:cb:4e:7e (try 1)
[  441.659762] wlan0: direct probe responded
[  441.659764] wlan0: authenticate with AP 00:24:01:cb:4e:7e (try 1)
[  441.666776] wlan0: authenticated
[  441.666799] wlan0: associate with AP 00:24:01:cb:4e:7e (try 1)
[  441.675283] wlan0: RX AssocResp from 00:24:01:cb:4e:7e (capab=0x431 status=12 aid=0)
[  441.675289] wlan0: AP denied association (code=12)
[  441.675314] wlan0: deauthenticating from 00:24:01:cb:4e:7e by local choice (reason=3)
[  441.741663] wlan0: direct probe to AP 00:24:01:cb:4e:7e (try 1)
[  441.744343] wlan0: direct probe responded
[  441.744350] wlan0: authenticate with AP 00:24:01:cb:4e:7e (try 1)
[  441.749920] wlan0: authenticated
[  441.749971] wlan0: associate with AP 00:24:01:cb:4e:7e (try 1)
[  441.752635] wlan0: RX AssocResp from 00:24:01:cb:4e:7e (capab=0x431 status=0 aid=1)
[  441.752643] wlan0: associated
[  441.755283] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  452.028137] wlan0: no IPv6 routers present
[  621.704247] wlan0: deauthenticating from 00:24:01:cb:4e:7e by local choice (reason=3)
[  621.841374] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1356.581243] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Here's the relevant ifconfig information:
```
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:9a:e4:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:564 (564.0 B)  TX bytes:14474 (14.4 KB)

```

And iwconfig:
```

wlan0     IEEE 802.11abg  Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


I've tried:
- reinstalling wicd
- uninstalling wicd and installing network-manager
- restarting
- shutting down and booting back up
- restarting the router
- sudo /etc/init.d/networking restart
- taking the interface down and back up with ifconfig

I haven't changed anything recently in regards to my wireless card, and all the fixes I've tried are things I've done before without an issue. The only thing I'm wondering about is if doing a hard reset might have broken something (I *know* this is a cardinal sin, but there's a whole 'nother problem I haven't been able to fix with the OS hanging every once in a while over a VPN daemon when it tries to shut down or restart -- I've left it for hours to see if it actually gets anywhere and no luck, won't do a soft reset). I'm nervous about reinstalling the driver just because I've never had to do it and drivers are a finicky business. I imagine there's a config error somewhere? (I hope?)

Any help would be much appreciated; I need this laptop for schoolwork.

---

### Post by chili555 on 2010-09-09
May I see:```
rfkill list all
sudo cat /var/log/syslog | grep -e wlan0 -e iwl
```The last command may produce several dozens of lines. Please post the last 20 or so.

---

### Post by Quinoa Rex on 2010-09-09
rfkill list all:
```

allyanncah@taliesin:~% rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

sudo cat /var/log/syslog | grep -e wlan0 -e iwl:
```


Sep  9 11:45:21 taliesin dhclient: Listening on LPF/wlan0/00:1f:3c:9a:e4:39
Sep  9 11:45:21 taliesin dhclient: Sending on   LPF/wlan0/00:1f:3c:9a:e4:39
Sep  9 11:45:22 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Sep  9 11:45:28 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Sep  9 11:45:29 taliesin kernel: [13057.996312] wlan0: no IPv6 routers present
Sep  9 11:45:37 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Sep  9 11:45:50 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep  9 11:45:58 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Sep  9 11:46:13 taliesin dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Sep  9 11:46:23 taliesin avahi-autoipd(wlan0)[11256]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Sep  9 11:46:23 taliesin avahi-autoipd(wlan0)[11256]: Successfully called chroot().
Sep  9 11:46:23 taliesin avahi-autoipd(wlan0)[11256]: Successfully dropped root privileges.
Sep  9 11:46:23 taliesin avahi-autoipd(wlan0)[11256]: Starting with address 169.254.8.19
Sep  9 11:46:28 taliesin avahi-autoipd(wlan0)[11256]: Callout BIND, address 169.254.8.19 on interface wlan0
Sep  9 11:46:28 taliesin avahi-daemon[1129]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.19.
Sep  9 11:46:28 taliesin avahi-daemon[1129]: New relevant interface wlan0.IPv4 for mDNS.
Sep  9 11:46:28 taliesin avahi-daemon[1129]: Registering new address record for 169.254.8.19 on wlan0.IPv4.
Sep  9 11:46:32 taliesin avahi-autoipd(wlan0)[11256]: Successfully claimed IP address 169.254.8.19
Sep  9 11:48:00 taliesin dhclient: Listening on LPF/wlan0/00:1f:3c:9a:e4:39
Sep  9 11:48:00 taliesin dhclient: Sending on   LPF/wlan0/00:1f:3c:9a:e4:39
Sep  9 11:48:00 taliesin dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Sep  9 11:48:00 taliesin avahi-autoipd(wlan0)[11256]: Got SIGTERM, quitting.
Sep  9 11:48:00 taliesin avahi-autoipd(wlan0)[11256]: Callout STOP, address 169.254.8.19 on interface wlan0
Sep  9 11:48:00 taliesin avahi-daemon[1129]: Withdrawing address record for 169.254.8.19 on wlan0.
Sep  9 11:48:00 taliesin avahi-daemon[1129]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.19.
Sep  9 11:48:00 taliesin avahi-daemon[1129]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep  9 11:48:00 taliesin kernel: [13209.725244] wlan0: deauthenticating from 00:24:01:cb:4e:7e by local choice (reason=3)
Sep  9 11:48:00 taliesin avahi-daemon[1129]: Withdrawing address record for fe80::21f:3cff:fe9a:e439 on wlan0.
Sep  9 11:48:00 taliesin kernel: [13209.853555] Registered led device: iwl-phy0::radio
Sep  9 11:48:00 taliesin kernel: [13209.853599] Registered led device: iwl-phy0::assoc
Sep  9 11:48:00 taliesin kernel: [13209.853637] Registered led device: iwl-phy0::RX
Sep  9 11:48:00 taliesin kernel: [13209.853675] Registered led device: iwl-phy0::TX
Sep  9 11:48:01 taliesin kernel: [13209.881113] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

