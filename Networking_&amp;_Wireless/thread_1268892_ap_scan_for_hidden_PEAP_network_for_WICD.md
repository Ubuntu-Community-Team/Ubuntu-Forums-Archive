---
title: "ap_scan for hidden PEAP network for WICD"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by misha680 on 2009-09-17
---
Summary of problem:
Hidden network, needs ap_scan = 2 on my machine
When I do "Connect to Hidden Network" in WICD it reports no networks found even though it is there
and connects fine through WPA supplicant.

Thank you
Misha
---

I am trying to connect to a PEAP network that is hidden. This template has worked for me in the past:

name = PEAP with IEEE8021X
author = Misha Koshelev
version = 2
require identity *Identity password *Password
-----
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="$_ESSID"
        scan_ssid=$_SCAN
    proto=RSN
    key_mgmt=IEEE8021X
    pairwise=CCMP
    eap=PEAP
    identity="$_IDENTITY"
    password="$_PASSWORD"
}

However, I require the ap_scan parameter to be 2 on my drivers. I am using the Broadcom WL module on Ubuntu Jaunty 9.04:

misha@misha-5101:/etc/network$ modinfo wl
filename:       /lib/modules/2.6.28-15-generic/volatile/wl.ko
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        ieee80211_crypt
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 
license:        MIXED/Proprietary
parm:           oneonly:int
parm:           piomode:int
parm:           nompc:int
parm:           name:string

The following in /etc/network/interfaces results in a successful connect:

auto eth1
iface eth1 inet dhcp
   wpa-driver wext
   wpa-ssid bcm-net-svcs
   wpa-ap-scan 2
   wpa-proto RSN
   wpa-pairwise CCMP TKIP
   wpa-group CCMP TKIP
   wpa-key-mgmt IEEE8021X
   wpa-eap PEAP
   wpa-identity identity
   wpa-password password

Note that changing the ap-scan parameter to 1 makes it fail to connect.

Thank you for any suggestions. I tried modifying the file in
/var/lib/wicd/configurations to read:

ap_scan=2
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="bcm-net-svcs"
        scan_ssid=1
    proto=RSN
    key_mgmt=IEEE8021X
    pairwise=CCMP
    eap=PEAP
    identity="identity"
    password="password"
}

but still no luck. Here are the networks wicd-client reports:

refreshing...
ESSID : MYHOME
ESSID : bcm-guest
ESSID : bcm-guest
ESSID : <hidden>
ESSID : bcm-guest
ESSID : Wireless Network
ESSID : bcm-guest
ESSID : bcm-guest
ESSID : bcm-guest
ESSID : marty matzuk's iMac G5
refreshing...
ESSID : MYHOME
ESSID : bcm-guest
ESSID : bcm-guest
ESSID : marty matzuk's iMac G5
ESSID : <hidden>
ESSID : hpsetup
ESSID : bcm-guest
ESSID : bcm-guest
ESSID : bcm-guest
refreshing...
refreshing...
refreshing...

Thank you
Misha

---

