---
title: "wifi config question: D-Link G520"
date: 2005-03-03
forum: Networking &amp; Wireless
---

### Post by mike_c on 2005-03-03
I gave up trying to get my Netgear wg311 wifi card working working under ndiswrapper, so I bought a D-Link DWL-G520.  This uses the Atheros chipset.  This PCI card is listed in the Ubunto wifi hardware compatiblity list as "works great" or something similar. I did a clean install of Ubunto.   The card is detected and configured as ath0.  Running :

```
iwlist ath0 scan

ath0     Scan completed:
             Cell 01 - Address: 00:09:5B:70:A5:62
                           ESSID: "router-name"
                           Mode: Master
                           Frequency: 2.462 GHz (Channel 11)
                           Quality=0/24 Signel level=-95 dBm  Noise level=-95 dBM
                           Encryption key: off
                           Bit Rate: 1 Mb/s
                           Bit Rate: 2 Mb/s
                           Bit Rate: 5 Mb/s
                           Bit Rate: 11 Mb/s
                           Extra: bcn_int=100
```

shows the WAP is detected, although I don't know how to interpret all of the information returned (in particular the signal quality info).  I have the WAP set up for wide open access, no encryption key.  Router ID is broadcast.  No MAC addr filtering.  ath0 is set up for DHCP, as is the router.  DHCP works fine with eth0 to the wired NIC from the same router.

I've disabled eth0 (the wired NIC works perfectly, but this computer MUST be deployed wireless) but the network is unreachable via the wifi card.  Running (as root):

```
iwconfig ath0 mode managed
iwconfig ath0 channel 11
iwconfig ath0 essid router-name
ifdown ath0
ifup ath0

```
gives the following output:

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0f:3d:af:07:24
Sending on LPF/ath0/00:0f:3d:af:07:24
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

It looks to me like DHCP is not working with the wifi card.  I don't understand the references to 255.255.255.255-- is this not supposed to be the router IP addr at 192.168.0.1?  I don't know what else to do.  I've tried using the gnome network configuration tool, which evidently fails without producing any meaningful diagnostic info.  

The relevant lines in /etc/network/interfaces are:

```
iface ath0 inet dhcp
wireless_essid router-name
wireless_mode managed
channel 11
auto ath0
```

**Can anyone help me get this working?**  What else should I try?  What other information can I provide?  I've spent much of the last three weeks struggling off and on with getting wireless networking going on this computer, without success.  I've reinstalled Ubuntu several times, and lost other configuration and set up work as a result.  I'm at my wit's end.  I'm not a linux newbie but I've never tried to get wifi working before.  It is driving me nuts and taking WAY too much energy and time.   ](*,) 

TIA
Mike C.

---

### Post by grakhul on 2005-03-06
Do you have wep or any type of security enabled on the wireless router?  If so try configuring the card without security enabled.  Then later on worry about security

---

