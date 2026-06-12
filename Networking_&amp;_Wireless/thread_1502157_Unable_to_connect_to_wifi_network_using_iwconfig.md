---
title: "Unable to connect to wifi network using iwconfig"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by muthu375 on 2010-06-05
[SIZE=3]_Environment_
OS : ubuntu 2.6.32-21-generic #32[/SIZE]
[SIZE=3]Installed as a VMWare on Windows 2003
WIFI Device: SMC Wireless Dongle

_Problem_
On Inserting a WIFI Dongle. I am able to see the new interface for the wifi interface as WLAN0 from ifconfig. Also iwconfig confirms the same.

i am able to use the iwlist to know the wifi networks.

I have my own router for testing purpose which is configured to work in DHCP mode, I am trying to connect to this wifi router

Then i issue the following set of commands to connect to wifi network.

iwlist wlan0 scan
sudo iwconfig wlan0 essid <mynetwork>
dhclient wlan0[/SIZE]
[SIZE=3]
And I get the following error.[/SIZE]

[SIZE=2][COLOR=Red][SIZE=1]There is already a pid file /var/run/dhclient.pid with pid 4798
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:13:f7:d4:21:03
Sending on   LPF/wlan0/00:13:f7:d4:21:03
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/SIZE]

[COLOR=Black]But If I am trying to connect via "Network Connections" from System/Preferences/NetworkConnections - It is getting connected and an IP is getting assigned for my ubuntu.

I checked in dmesg I get the following messages.[/COLOR]
[SIZE=1]
[ 1215.953664] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1226.936386] wlan0: no IPv6 routers present
[ 1256.773031] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 1290.329935] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 1290.359077] wlan0: direct probe responded
[ 1290.359090] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 1290.361799] wlan0: authenticated
[ 1290.361859] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 1290.370208] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 1290.370216] wlan0: associated
[ 1290.618016] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 1771.150071] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 1771.181026] wlan0: direct probe responded
[ 1771.181040] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 1771.183472] wlan0: authenticated
[ 1771.183536] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 1771.193730] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 1771.193738] wlan0: associated
[ 1771.442942] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 2219.255819] wlan0: direct probe to AP 00:19:15:af:05:19 (try 1)
[ 2219.282875] wlan0: direct probe responded
[ 2219.282947] wlan0: authenticate with AP 00:19:15:af:05:19 (try 1)
[ 2219.285640] wlan0: authenticated
[ 2219.285716] wlan0: associate with AP 00:19:15:af:05:19 (try 1)
[ 2219.295150] wlan0: RX AssocResp from 00:19:15:af:05:19 (capab=0x401 status=0 aid=1)
[ 2219.295158] wlan0: associated
[ 2219.540934] wlan0: deauthenticating from 00:19:15:af:05:19 by local choice (reason=3)
[ 3741.966469] wlan0: deauthenticating from 00:1a:2b:6a:d9:d2 by local choice (reason=3)
[ 3742.319886] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 1)
[ 3742.516843] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 2)
[ 3742.717048] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 3)
[ 3742.916354] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 timed out
[ 3758.112991] wlan0: deauthenticating from 00:16:38:f2:b2:1c by local choice (reason=3)
[ 3758.250211] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 1)
[ 3758.448130] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 2)
[ 3758.648510] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 (try 3)
[ 3758.848602] wlan0: direct probe to AP 00:1a:2b:6a:d9:d2 timed out
[ 3841.976598] eth0: no IPv6 routers present
[ 3921.904544] eth0: no IPv6 routers present
[ 8531.252924] eth0: no IPv6 routers present
[ 9228.961873] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/SIZE]


[SIZE=3][COLOR=Black]Can anyone please help me in this regard. I am waiting for your replies eagerly, with both eyes widely open as never before.

Thanks in advance.

Regards

[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Black]Muthu[/COLOR][/SIZE]

---

### Post by cookiecruncher on 2010-06-05
Not long ago I had a problem with my wireless connection, and all I did to remedy the situation was to hash out the section associated with 'wlan0' in my '/etc/network/interfaces' file, as detailed below:
```
$ cat interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider


# auto wlan0
# iface wlan0 inet manual


```.... and rebooted.  This restored my wireless connection, and internet.

My wireless connection was originally setup with 'System -> Preferences -> Network Connections'.

PS. I use a wireless DSL modem set to bridge mode and connect using 'pppoe' with 'pon dsl-provider', setup with 'pppoeconf'
Laptop is a Dell Latitude E6400 ATG

Good luck

---

### Post by muthu375 on 2010-06-05
[FONT=Arial][SIZE=3]Thanks for your reply, first of all.

The hashing worked for you as in the same file you are already having an entry for wlan0 which is an auto up. Later in the file itself you are changing it to manual, but you weren't giving any additional info, due to which your connectivity was an issue.

But I am trying to establish connection using iwconfig here.

Also following is the content for the file "/etc/network/interfaces" 

[/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=Red]auto lo
iface lo inet loopback

iface wlan0 inet dhcp
   wireless_mode managed
   wireless-essid WLAN_0519[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3]

Can somebody help me here, please :([/SIZE][/FONT]

---

