---
title: "MN-510 USB wireless adapter"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Antoine.L on 2006-06-01
I can't get it to work!  I plug it in, and the lights will turn on and blink when I try to use it, and the kernel acts like it's loading the proper module (prism2_usb) but this is what "ifconfig" looks like:
```
wlan0     Link encap:Ethernet  HWaddr 00:50:F2:C6:C3:F8
          inet6 addr: fe80::250:f2ff:fec6:c3f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:199296 (194.6 KiB)
```

So I try a "sudo ifdown wlan0; sudo ifup wlan0" which gives me:
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:50:f2:c6:c3:f8
Sending on   LPF/wlan0/00:50:f2:c6:c3:f8
Sending on   Socket/fallback
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:50:f2:c6:c3:f8
Sending on   LPF/wlan0/00:50:f2:c6:c3:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


My "/etc/network/interfaces":
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp
iface wlan0 inet dhcp
wireless-essid NETGEAR

```


my "/etc/wlan/wlan.conf":
```
# if you want temporary files to go elsewhere, change this.
TMPDIR=/tmp

##########
# Note:  To bind to a specific network, change the SSID to something different
#        and create the file /etc/wlan/wlancfg-<SSID> with your network-
#        specific settings.  If this file is not present, the settings in
#        /etc/wlancfg/wlancfg-DEFAULT are used.
#
# for example:
#    SSID_wlan0="linux-wlan"
# This expects a file called "/etc/wlan/wlancfg-linux-wlan" to be present.
#
# Use a SSID of "" to associate with any network in range.
#########

SSID_wlan0="NETGEAR"
ENABLE_wlan0=y
#SSID_wlan1=""
#ENABLE_wlan1=n
#SSID_wlan2=""
#ENABLE_wlan2=n

```

my "/etc/wlan/wlancfg-NETGEAR"
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
lnxreq_hostWEPEncrypt=false     # true|false
lnxreq_hostWEPDecrypt=false     # true|false
dot11PrivacyInvoked=false       # true|false
dot11WEPDefaultKeyID=0          # 0|1|2|3
dot11ExcludeUnencrypted=true    # true|false, in AP this means WEP is required.

# If PRIV_GENSTR is not empty, use PRIV_GENTSTR to generate
#  keys (just a convenience)
# add-ons/ in the tarball contains other key generators.
PRIV_GENERATOR=/sbin/nwepgen    # nwepgen, Neesus compatible
PRIV_KEY128=false               # keylength to generate
PRIV_GENSTR=""

# or set them explicitly.  Set genstr or keys, not both.
dot11WEPDefaultKey0=00:00:00:00:00 # format: xx:xx:xx:xx:xx
dot11WEPDefaultKey1=00:00:00:00:00 # format: xx:xx:xx:xx:xx
dot11WEPDefaultKey2=00:00:00:00:00 # format: xx:xx:xx:xx:xx
dot11WEPDefaultKey3=00:00:00:00:00 # format: xx:xx:xx:xx:xx
#=======SELECT STATION MODE===================
IS_ADHOC=n                      # y|n, y - adhoc, n - infrastructure

#======= INFRASTRUCTURE STATION  ===================
# What kind of authentication?
AuthType="opensystem"           # opensystem | sharedkey (requires WEP)

#======= ADHOC STATION ============================
BCNINT=100                      # Beacon interval (in Kus)
CHANNEL=6                       # DS channel for BSS (1-14, depends
                                #   on regulatory domain)
BASICRATES="2 4"                # Rates for mgmt&ctl frames (in 500Kb/s)
OPRATES="2 4 11 22"             # Supported rates in BSS (in 500Kb/s)

```

Maybe I'm just making a bone-headed mistake somewhere. because I have a feeling this shouldn't be this hard.
Can anyone think of anything else I should try?

(Also, I had the same problem with Breezy)

---

### Post by Antoine.L on 2006-06-01
Here's something else which I found interesting:

After getting the DHCP failures bringing the adapter up the command "iwconfig wlan0" gives the following:
```
wlan0     IEEE 802.11-DS  ESSID:"NETGEAR"  Nickname:"NETGEAR"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:50:FA:3E:C3:F8
          Bit Rate:2 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=5/92  Signal level=-95 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
The frequency indicates the adapter is trying to Tx/Rx on channel 1, but the access point is configured for channel 11.  The adapter also thinks it's supposed to be in ad-hoc mode for some reason (because it can't connect to the access point?)

Also, I have confirmed that the wireless setup on the access-point works with another computer (a laptop running XP)

---

### Post by Antoine.L on 2006-06-05
Bump 'cause it's still not working.

---

### Post by tormod on 2006-06-17
Please have a look at [https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb](https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb)
and information linked from there.

---

