---
title: "prism2 wireless problems"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by pete_the_great on 2006-01-14
Hi all,
I'm fairly inexperienced with linux stuff, and am having some problems setting up the wireless connection for my laptop (running hoary). I'm not sure what the exact make of my wireless adapter is (I think it's a rebranded airvast of some form), but running lsusb gives

```
pete@damocles:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 124a:168b
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b4:0001 Cypress Semiconductor Corp. Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
Googling the 124a:168b points to something using a prism2 chipset. I've installed the linux-wlan-ng package, which seems to sort out the driver. The relevant part of the output from lshw gives: 

 ```
*-network:2
       description: Ethernet controller
       physical id: 3
       logical name: wlan0
       serial: 00:0a:e9:08:aa:6d
       capabilities: ethernet
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.1-pre25 multicast=yes
```
I've tweaked the wlan.conf file as described in the documetation for the linux-wlan-ng package, and created the file "wlancfg-petes_ssid":

```
#=======USER MIB SETTINGS=============================
# You can add the assignments for various MIB items
#  of your choosing to this variable, separated by 
#  whitespace.  The wlan-ng script will then set each one.
# Just uncomment the variable and set the assignments 
#  the way you want them.

#USER_MIBS="p2CnfRoamingMode=1 p2CnfShortPreamble=mixed"

#=======WEP===========================================
# [Dis/En]able WEP.  Settings only matter if PrivacyInvoked is true
lnxreq_hostWEPEncrypt=true      # true|false
lnxreq_hostWEPDecrypt=true      # true|false
dot11PrivacyInvoked=true	# true|false
dot11WEPDefaultKeyID=0		# 0|1|2|3
dot11ExcludeUnencrypted=true	# true|false, in AP this means WEP is required.

# If PRIV_GENSTR is not empty, use PRIV_GENTSTR to generate 
#  keys (just a convenience)
# add-ons/ in the tarball contains other key generators.
PRIV_GENERATOR=/sbin/nwepgen	# nwepgen, Neesus compatible
PRIV_KEY128=false		# keylength to generate
PRIV_GENSTR=""

# or set them explicitly.  Set genstr or keys, not both.
dot11WEPDefaultKey0= 00:00:00:00:00:00:00:00:00:00:00:00:00 # format: xx:xx:xx:xx:xx   or
dot11WEPDefaultKey1=		#         xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
dot11WEPDefaultKey2=		#  e.g.   01:20:03:40:05   or
dot11WEPDefaultKey3=		#         01:02:03:04:05:06:07:08:09:0a:0b:0c:0d
#=======SELECT STATION MODE===================
IS_ADHOC=n 			# y|n, y - adhoc, n - infrastructure

#======= INFRASTRUCTURE STATION  ===================
# What kind of authentication?
AuthType="sharedkey"		# opensystem | sharedkey (requires WEP)

#======= ADHOC STATION ============================
BCNINT=100			# Beacon interval (in Kus)
CHANNEL=6			# DS channel for BSS (1-14, depends 
				#   on regulatory domain)
BASICRATES="2 4"		# Rates for mgmt&ctl frames (in 500Kb/s)
OPRATES="2 4 11 22"		# Supported rates in BSS (in 500Kb/s)
```
I've been using this script to (attempt to) start the wireless connection:

```
#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="petes_ssid" authtype=sharedkey
sudo dhclient wlan0
```

which I took from this forum page: [http://ubuntuforums.org/showthread.php?t=5660](http://ubuntuforums.org/showthread.php?t=5660)

When I run this, I get the following

```
pete@damocles:~$  connect_wireless &
[3] 8261
pete@damocles:~$ message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
message=lnxreq_autojoin
  ssid='petes_ssid'
  authtype=sharedkey
  resultcode=success
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0a:e9:08:aa:6d
Sending on   LPF/wlan0/00:0a:e9:08:aa:6d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[3]+  Done                    connect_wireless
pete@damocles:~$
```
and apparently no internet. At this stage, ifconfig gives 

```
pete@damocles:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:D6:4B:1F
          inet6 addr: fe80::20d:87ff:fed6:4b1f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:8244 (8.0 KiB)
          Interrupt:19 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:553344 (540.3 KiB)  TX bytes:553344 (540.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0A:E9:08:AA:6D
          inet6 addr: fe80::20a:e9ff:fe08:aa6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

and iwconfig:

```
pete@damocles:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"petes_ssid"  Nickname:"petes_ssid"
          Mode:Auto  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=0/92  Signal level=-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pete@damocles:~$
```

Any help would be greatly appreciated.

---

